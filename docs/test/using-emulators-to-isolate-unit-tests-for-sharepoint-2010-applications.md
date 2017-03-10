---
title: "Usando emuladores para isolar testes de unidade para aplicativos do Sharepoint 2010 | Microsoft Docs"
ms.custom: ""
ms.date: "12/11/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: b681164c-c87a-4bd7-be48-ed77e1578471
caps.latest.revision: 15
caps.handback.revision: 15
ms.author: "mlearned"
manager: "douge"
---
# Usando emuladores para isolar testes de unidade para aplicativos do Sharepoint 2010
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

O pacote Microsoft.SharePoint.Emulators fornece um conjunto de bibliotecas que ajudam você a criar testes de unidade isolada para aplicativos do Microsoft SharePoint 2010.  Usam emuladores [correções](../test/using-shims-to-isolate-your-application-from-other-assemblies-for-unit-testing.md) do [Microsoft Fakes](../test/isolating-code-under-test-with-microsoft-fakes.md) framework de isolamento para criar objetos na memória leves que imitam os objetos e métodos da API do SharePoint mais comuns.  Quando um método do SharePoint não é emulado, ou quando você deseja alterar o comportamento padrão de um emulador, você pode criar Fakes shims para fornecer os resultados desejados.  
  
 Classes e métodos de teste existentes podem ser facilmente convertidos para ser executado no contexto do emulador.  Esse recurso permite criar testes de uso dual.  Um teste de uso dual pode alternar entre testes de integração com a API do SharePoint real e testes de unidade isolado que usam os emuladores.  
  
##  <a name="BKMK_In_this_topic"></a> Neste tópico  
 [Requisitos](#BKMK_Requirements)  
  
 [O exemplo de AppointmentsWebPart](#BKMK_The_AppointmentsWebPart_example)  
  
 [Conversão de um teste existente](#BKMK_Converting_an_existing_test)  
  
-   [Adicionar o pacote de emuladores para um projeto de teste](#BKMK_Adding_the_Emulators_package_to_a_test_project)  
  
-   [Executando um método de teste com emulação](#BKMK__Running_a_test_method_in_the_emulation_context)  
  
 [Criando métodos e classes de uso dual](#BKMK_Creating_dual_use_classes_and_methods)  
  
 [Usando TestInitialize e TestCleanup atributos para criar um uso dual classe de teste](#BKMK_Using_TestInitialize_and_TestCleanup_attributes_to_create_a_dual_use_test_class)  
  
 [Não emulados SharePoint métodos de tratamento](#BKMK_Handling_non_emulated_SharePoint_methods)  
  
 [Emulação de escrever testes do zero e um resumo](#BKMK_Writing_emulation_tests_from_scratch__and_a_summary)  
  
 [Exemplo](#BKMK_Example)  
  
 [Tipos de SharePoint emulados](#BKMK_Emulated_SharePoint_types)  
  
##  <a name="BKMK_Requirements"></a> Requisitos  
  
-   Microsoft SharePoint 2010 \(servidor do SharePoint 2010 ou SharePoint 2010 Foundation\)  
  
-   Microsoft Visual Studio Enterprise  
  
-   Pacote NuGet de emuladores do Microsoft SharePoint  
  
 Você também deve estar familiarizado com o [Noções básicas de teste de unidade no Visual Studio](../test/unit-test-basics.md) e algum conhecimento de [Microsoft Fakes](../test/isolating-code-under-test-with-microsoft-fakes.md).  
  
##  <a name="BKMK_The_AppointmentsWebPart_example"></a> O exemplo de AppointmentsWebPart  
 O AppointmentsWebPart permite exibir e gerenciar uma lista de seus compromissos do SharePoint.  
  
 ![Web Part de compromissos](../test/media/ut_emulators_appointmentswebpart.png "UT\_EMULATORS\_AppointmentsWebPart")  
  
 Vou testar dois métodos da web part neste exemplo:  
  
-   O `ScheduleAppointment` método valida os valores de item de lista passados para o método e cria uma nova entrada em uma lista em uma web do SharePoint especificada.  
  
-   O `GetAppointmentsForToday` método retorna os detalhes de compromissos de hoje.  
  
 [Neste tópico](#BKMK_In_this_topic)  
  
##  <a name="BKMK_Converting_an_existing_test"></a> Conversão de um teste existente  
 Em um teste típico de um método em um componente do SharePoint, o método de teste cria um site temporário no SharePoint Foundation e adiciona os componentes do SharePoint para o site que requer que o código em teste.  O método de teste cria e executa uma instância do componente.  No final do teste, o site é interrompido.  
  
 O `ScheduleAppointment` método do nosso código em teste é provavelmente um dos primeiros métodos gravados para o componente:  
  
```  
// method under test  
public bool ScheduleAppointment(SPWeb web, string listName, string name,   
    string phone, string email, string age, DateTime date, out string errorMsg)  
{  
    errorMsg = string.Empty;  
    var badFormat = this.checkInput(name, phone, email, age);  
    if (badFormat)  
    {  
        errorMsg = "Bad Format";  
        return false;  
    }  
    var exists = this.CheckDuplicate(listName, web, name, phone, email, age, date);  
    if (exists)  
    {  
        errorMsg = "Item already exists";  
        return false;  
    }  
    SPListItemCollection items = web.Lists[listName].Items;  
    // create item and populate fields  
    SPListItem item = items.Add();  
    item["Name"] = name;  
    item["Phone"] = phone;  
    item["Email"] = email;  
    item["Age"] = age;  
    item["Date"] = date.ToString("D");  
    item.Update();  
    return true;  
}  
  
```  
  
 O primeiro teste da funcionalidade no `ScheduleAppointment` método teria esta aparência:  
  
```c#  
  
[TestMethod]  
public void ScheduleAppointmentReturnsTrueWhenNewAppointmentIsCreated()  
{  
    using( var site = new SPSite("http://localhost"))  
    using (var webPart = new BookAnAppointmentWebPart())  
    {  
        // Arrange  
        string errorMsg = string.Empty;  
        DateTime date = DateTime.Now;  
        SPList list = AddListToSiteHelper(site);  
  
        // Act  
        bool success = webPart.ScheduleAppointment(site.RootWeb, list.Title,  
            "Raisa Pokrovskaya", "425-555-0163", "raisa@outlook.com", "55", date,   
            out errorMsg);  
        list.Delete();  
  
        // Assert  
        Assert.IsTrue(success);  
    }  
}  
```  
  
 Embora esse método teste verifique o `ScheduleAppointment` corretamente, o método adiciona uma nova entrada à lista, é mais um teste de integração da web part que um teste do comportamento específico do seu código.  As dependências externas para o SharePoint e a API do SharePoint podem fazer com que o teste falhar por razões que não seja o código do usuário na `ScheduleAppointment` método.  A sobrecarga na criação e destruição de site do SharePoint também pode fazer o teste muito lento para ser executado como uma parte normal do processo de codificação.  Apenas executar a instalação e a destruição do site para cada método de teste constitui o problema da criação eficiente desenvolvedor de testes de unidade.  
  
 Microsoft SharePoint emuladores oferecem um conjunto de objeto e o método "doubles" que imitam o comportamento das APIs do SharePoint mais comuns.  Os métodos emulados são implementações leves a API do SharePoint que não necessitam do SharePoint ser executado.  Usando o Microsoft Fakes para desviar chamadas para a API do SharePoint para dobra o método dos emuladores do SharePoint, você isolar seus testes e certifique\-se de que você está testando o código desejado.  Quando você chama os métodos do SharePoint que não são emulados, você pode usar falsificações diretamente para criar o comportamento desejado.  
  
 [Neste tópico](#BKMK_In_this_topic)  
  
###  <a name="BKMK_Adding_the_Emulators_package_to_a_test_project"></a> Adicionar o pacote de emuladores para um projeto de teste  
 Para adicionar os emuladores do SharePoint a um projeto de teste:  
  
1.  Selecione o projeto de teste no Solution Explorer.  
  
2.  Escolha **Manage NuGet Packages...** no menu de atalho.  
  
3.  Pesquisa o **Online** categoria `Microsoft.SharePoint.Emulators`, e, em seguida, escolha **instalar**.  
  
 ![Pacote do NuGet de emuladores do SharePoint](../test/media/ut_emulators_nuget.png "UT\_EMULATORS\_Nuget")  
  
 [Neste tópico](#BKMK_In_this_topic)  
  
###  <a name="BKMK__Running_a_test_method_in_the_emulation_context"></a> Executando um método de teste com emulação  
 Instalando o pacote adiciona as referências às bibliotecas necessárias para seus projetos.  Para que seja fácil de usar emuladores em uma classe de teste existente, adicione os namespaces `Microsoft.SharePoint.Emulators` e `Microsoft.QualityTools.Testing.Emulators`.  
  
 Para habilitar a emulação de seus métodos de teste, encapsular o corpo do método em um `using` instrução cria uma `SharePointEmulationScope` objeto.  Por exemplo:  
  
```c#  
  
[TestMethod]  
public void ScheduleAppointmentReturnsTrueWhenNewAppointmentIsCreated()  
{  
    // create the emulation scope with a using statement  
    using (new SharePointEmulationScope())  
    using( var site = new SPSite("http://localhost"))  
    using (var webPart = new BookAnAppointmentWebPart())  
    {  
        // Arrange  
        string errorMsg = string.Empty;  
        DateTime date = DateTime.Now;  
        SPList list = AddListToSiteHelper(site);  
  
        // Act  
        bool success = webPart.ScheduleAppointment(site.RootWeb, list.Title,  
            "Raisa Pokrovskaya", "425-555-0163", "raisa@outlook.com", "55", date,   
            out errorMsg);  
        list.Delete();  
  
        // Assert  
        Assert.IsTrue(success);  
    }  
}  
  
```  
  
 Quando o método de teste é executado, o tempo de execução do emulador chama Microsoft Fakes para dinamicamente injetar código em métodos do SharePoint para desviar as chamadas para esses métodos para delegados que são declarados em Microsoft.SharePoint.Fakes.dll.  Microsoft.SharePoint.Emulators.dll implementa os delegados para métodos emulados, imitando atentamente o comportamento real do SharePoint.  Quando o método de teste ou o componente em teste chama um método do SharePoint, o comportamento resultante é que a emulação.  
  
 ![Fluxo de execução do emulador](../test/media/ut_emulators_flowchart.png "UT\_EMULATORS\_FlowChart")  
  
 [Neste tópico](#BKMK_In_this_topic)  
  
##  <a name="BKMK_Creating_dual_use_classes_and_methods"></a> Criando métodos e classes de uso dual  
 Para criar métodos que podem ser usados para testes de unidade isolado que usam emuladores e ambos os testes de integração com a API do SharePoint real, use o construtor sobrecarregado `SharePointEmulationScope(EmulationMode)` para encapsular o código do seu método de teste.  Os dois valores da `EmulationMode` enum especificar se o escopo usa emuladores \(`EmulationMode.Enabled`\) ou se o escopo usa a API do SharePoint \(`EmulationMode.Passthrough`\).  
  
 Por exemplo, eis como você pode modificar o teste anterior para uso dual:  
  
```c#  
  
// class level field specifies emulation mode  
private const EmulationMode emulatorMode = EmulationMode.Enabled;  
  
[TestMethod]  
public void ScheduleAppointmentReturnsTrueWhenNewAppointmentIsCreated()  
{  
    // emulation scope determined by emulatorMode  
    using( SharePointEmulationScope(emulatorMode))  
    using( var site = new SPSite("http://localhost"))  
    using (var webPart = new BookAnAppointmentWebPart())  
    {  
        // Arrange  
        string errorMsg = string.Empty;  
        DateTime date = DateTime.Now;  
        SPList list = AddListToSiteHelper(site);  
  
        // Act  
        bool success = webPart.ScheduleAppointment(site.RootWeb, list.Title,  
            "Raisa Pokrovskaya", "425-555-0163", "raisa@outlook.com", "55", date,   
            out errorMsg);  
        list.Delete();  
  
        // Assert  
        Assert.IsTrue(success);  
    }  
}  
```  
  
 [Neste tópico](#BKMK_In_this_topic)  
  
##  <a name="BKMK_Using_TestInitialize_and_TestCleanup_attributes_to_create_a_dual_use_test_class"></a> Usando TestInitialize e TestCleanup atributos para criar um uso dual classe de teste  
 Se você executar todos ou a maioria dos testes em uma classe usando `SharePointEmulationScope`, você pode tirar proveito das técnicas de nível de classe para definir o modo de emulação.  
  
-   Testar métodos de classe atribuída com <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestInitializeAttribute> e <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestCleanupAttribute> pode criar e destruir o escopo.  
  
-   Definindo a `EmulationMode` a classe nível pode permitir que você automatize a alteração do modo entre `EmulationMode.Enabled` e `EmulationMode.Passthrough`.  
  
 Um método de classe é atribuído com `[TestInitialize]` é executado no início de cada método de teste e um método que é atribuído com `[TestCleanup]` é executado no final de cada método de teste.  Você pode declarar um campo particular para o `SharePointEmulationScope` no nível da classe de objeto, inicializá\-lo no `TestInitialize` atribuído método e descarte o objeto no `TestCleanup` atribuído método.  
  
 Você pode usar qualquer método que você escolher para automatizar a seleção do `EmulationMode`.  Uma maneira é verificar a existência de um símbolo usando as diretivas do pré\-processador.  Por exemplo, para executar os métodos de teste em uma classe usando emuladores, você pode definir um símbolo como `USE_EMULATION` no arquivo de projeto de teste ou na linha de comando de compilação.  Se o símbolo é definido, um nível de classe `EmulationMode` constante é declarada e definida como `Enabled`.  Caso contrário, a constante é definida como `Passthrough`.  
  
 Aqui está um exemplo de classe de teste que demonstra como usar as diretivas do pré\-processador e `TestInitialize` e `TestCleanup` atribuído métodos para definir o modo de emulação.  
  
```c#  
//namespace declarations  
...  
  
namspace MySPAppTests   
{  
    [TestClass]  
    public class BookAnAppointmentWebPartTests  
    {  
  
        // emulationScope is a class level field  
        private SharePointEmulationScope emulationScope;  
  
        // preprocessor directives determine the value of emulatorMode  
        #if USE_EMULATION private const EmulationMode emulatorMode = EmulationMode.Enabled; #else private const EmulationMode emulatorMode = EmulationMode.Passthrough; #endif  
  
        // InitializeTest sets the emulation scope at the beginning of each test method  
        [TestInitialize] public void InitializeTest() { this.emulationScope = new SharePointEmulationScope(emulatorMode); }  
  
        // CleanupTest disposes the emulation scope at the end of each test method  
        [TestCleanup] public void CleanupTest() { this.emulationScope.Dispose(); }  
  
        [TestMethod]  
        public void ScheduleAppointmentReturnsTrueWhenNewAppointmentIsCreated()  
        {  
            // remove the SharePointEmulationScope using statement from the method  
            using( var site = new SPSite("http://localhost"))  
            using (var webPart = new BookAnAppointmentWebPart())  
            {  
                // Arrange  
                string errorMsg = string.Empty;  
                DateTime date = DateTime.Now;  
                SPList list = AddListToSiteHelper(site);  
  
                // Act  
                bool success = webPart.ScheduleAppointment(site.RootWeb, list.Title,  
                    "Raisa Pokrovskaya", "425-555-0163", "raisa@outlook.com", "55", date,   
                    out errorMsg);  
                list.Delete()  
  
                // Assert  
                Assert.IsTrue(success);  
            }  
        }  
  
        ...// More tests  
  
    }  
}  
  
```  
  
 [Neste tópico](#BKMK_In_this_topic)  
  
##  <a name="BKMK_Handling_non_emulated_SharePoint_methods"></a> Não emulados SharePoint métodos de tratamento  
 Nem todos os tipos do SharePoint são emulados e nem todos os métodos em alguns tipos emulados são emulados.  Se o código em teste chama um método do SharePoint que não é emulado, o método gera uma `NotSupportedException` exceção.  Quando ocorre uma exceção, você pode adicionar um shim Fakes para o método do SharePoint.  
  
 **Configurando o Sharepoint Fakes**  
  
 Chamar explicitamente o Microsoft Fakes correções:  
  
1.  Se você quiser usar shims uma classe do SharePoint que não é emulada, edite o arquivo Microsoft.SharePoint.fakes e adicione a classe à lista de classes com shims.  Consulte o [Configurando a geração de código de stubs e shims](http://msdn.microsoft.com/library/hh708916.aspx#bkmk_configuring_code_generation_of_stubs) seção [Geração de código, compilação e convenções de nomenclatura no Microsoft Fakes](../test/code-generation-compilation-and-naming-conventions-in-microsoft-fakes.md).  
  
     ![Pasta de falsificações no Solution Explorer](../test/media/ut_emulators_fakesfilefolder.png "UT\_EMULATORS\_FakesFileFolder")  
  
2.  Recompile o projeto de teste pelo menos uma vez depois de instalar o pacote do Microsoft SharePoint emuladores e se você editou o arquivo Microsoft.SharePoint.Fakes.  Criando o projeto cria e preenche um **FakesAssembly** pasta na pasta raiz do projeto em disco.  
  
     ![Pasta FakesAssembly](../test/media/ut_emulators_fakesassemblyfolder.png "UT\_EMULATORS\_FakesAssemblyFolder")  
  
3.  Adicione uma referência para o **Microsoft.SharePoint.14.0.0.0.Fakes.dll** assembly está localizado no **FakesAssembly** pasta.  
  
4.  \(Opcional\) Adicionar uma diretiva de namespace para a classe de teste para `Microsoft.QualityTools.Testing.Fakes`, `Microsoft.SharePoint.Fakes` e qualquer namespace aninhado de `Microsoft.SharePoint.Fakes`que você deseja usar.  
  
 **Implementando o delegado de correção para um método do SharePoint**  
  
 Em nosso projeto de exemplo, o `GetAppointmentsForToday` chamadas de método do [SPList.GetItems\(SPQuery\)](http://msdn.microsoft.com/library/ms457534.aspx) método de API do SharePoint.  
  
```c#  
// method under test  
public string GetAppointmentsForToday(string listName, SPWeb web)  
{  
    SPList list = web.Lists[listName];  
    DateTime today = DateTime.Now;  
    var listQuery = new SPQuery { Query = String.Format( "<Where><Eq><FieldRef Name='Date'/>" + "<Value Type='Text'>{0}</Value>" + "</Eq></Where>", today.ToString("D")) };  
    var result = new System.Text.StringBuilder();  
    foreach (SPListItem item in list.GetItems(listQuery))  
    {  
        result.AppendFormat("Name: {0}, Phone: {1}, Email: {2}, Age: {3}, Date: {4}\n",   
            item["Name"], item["Phone"], item["Email"], item["Age"], item["Date"]);  
    }  
    return result.ToString();  
}  
  
```  
  
 O `SPList.GetItems(SPQuery)` versão sobrecarregados `GetItems` método não é emulado.  Portanto, apenas envolvendo um teste existente para `GetAppointmentsForToday` em `SharePoint.Emulation.Scope` falharia.  Para criar um teste de trabalho, você precisa escrever uma implementação do delegado Fakes `ShimSPList.GetItemsSPQuery` que retorna os resultados que você deseja para o teste.  
  
 Aqui está uma modificação de um método de teste existente, `GetAppointmentsForTodayReturnsOnlyTodaysAppointments`, que implementa um delegado falsificações.  As alterações necessárias sejam chamadas nos comentários:  
  
> [!IMPORTANT]
>  Testar métodos que criam explicitamente Fakes shims lançar um `ShimNotSupported` exceção quando o teste é executado no `EmulationMode.Passthrough` contexto.  Para evitar esse problema, use uma variável para definir o `EmulationMode` valor e encapsular qualquer código Fakes em um `if` instrução que testa o valor.  
  
```c#  
// class level field to set emulation mode  
private const EmulationMode emulatorMode = EmulationMode.Enabled  
  
[TestMethod]  
public void GetAppointmentsForTodayReturnsOnlyTodaysAppointments()  
{  
  
    // create the emulation scope with a using statement  
    using (var emulationScope = new SharePointEmulationScope(emulatorMode))  
    using( var site = new SPSite("http://localhost"))  
    using (var webPart = new BookAnAppointmentWebPart())  
    {  
        // Arrange  
        DateTime date = DateTime.Now;  
        SPList list = AddListToSiteHelper(site);  
        // insert 2 items into list  
        AddItemsToListHelper(list, new string[] {"Raisa Pokrovskaya", "425-555-0163",  
            "raisa@outlook.com", "55", date.ToString("D") });  
        AddItemsToListHelper(list, new string[] {"Francis Totten", "313-555-0100",  
            "francis@contoso.com", "42", date.AddDays(1).ToString("D") });  
  
        // use Fakes shims only if emulation is enabled  
        if (emulatorMode == EmulationMode.Enabled) { var sList = new ShimSPList(list); sList.GetItemsSPQuery = (query) => { var shim = new ShimSPListItemCollection(); shim.Bind(new[] { list.Items[0] }); return shim.Instance; } }  
  
        // Act  
        string result = webPart.GetAppointmentsForToday(list.Title, site.RootWeb);  
        list.Delete();  
  
        // Assert  
        Assert.IsTrue(result.Contains(String.Format(  
            "Name: Raisa Pokrovskaya, Phone: 425-555-0163, Email: raisa@outlook.com," +  
            "Age: 55, Date: {0}", date.ToString("D"))));  
        Assert.IsFalse(result.Contains("Name: Francis Totten"));  
    }  
}  
  
```  
  
 Nesse método, nós primeiro teste que emulação está habilitada.  Se for, podemos criar um objeto de correção de falsificações para nosso `SPList` lista e, em seguida, criar e atribuir um método para sua `GetItemsSPQuery` delegar.  O representante usa os Fakes `Bind` método para adicionar o item de lista correta para o `ShimSPListItemCollection` que é retornado ao chamador.  
  
 [Neste tópico](#BKMK_In_this_topic)  
  
##  <a name="BKMK_Writing_emulation_tests_from_scratch__and_a_summary"></a> Emulação de escrever testes do zero e um resumo  
 Embora as técnicas para criar testes de uso dual descritos nas seções anteriores e emulação supõem que você está convertendo testes existentes, você também pode usar as técnicas para escrever testes a partir do zero.  A lista a seguir resume essas técnicas:  
  
-   Para usar emuladores em um projeto de teste, adicione o pacote do Microsoft.SharePoint.Emulators NuGet ao projeto.  
  
-   Para usar emuladores em um método de teste, crie uma `SharePointEmulationScope` objeto no início do método.  Todas as APIs do SharePoint com suporte será ser emulada até que o escopo é descartado.  
  
-   Escreva seu código de teste, como se estivesse escrevendo\-lo contra a API do SharePoint real.  O contexto de emulação automaticamente contorna as chamadas para métodos do SharePoint em seus emuladores.  
  
-   Nem todos os objetos do SharePoint são emulados e nem todos os métodos de alguns objetos emulados são emulados.  Um `NotSupportedException` exceção é gerada quando você usa um método ou um objeto não emulados.  Quando isso ocorre, crie explicitamente um delegado de correção de falsificações para o método para retornar o comportamento necessário.  
  
-   Para criar testes de uso dual, use o `SharePointEmulationScope(EmulationMode)` construtor para criar o objeto de escopo de emulação.  O `EmulationMode` valor Especifica se as chamadas do SharePoint são emuladas ou executadas em um site do SharePoint real.  
  
-   Se todas ou a maioria de seus métodos de teste em uma classe de teste executado no contexto de emulação, você pode usar um nível de classe `TestInitialize` atribuído um método para criar a `SharePointEmulationScope` objeto e um campo de nível de classe para definir o modo de emulação.  Isso ajudará você a automatizar a alteração do modo de emulação.  Em seguida, usar um `TestCleanup` atribuído o método dispose do objeto de escopo.  
  
 [Neste tópico](#BKMK_In_this_topic)  
  
##  <a name="BKMK_Example"></a> Exemplo  
 Aqui está um exemplo final que incorpora as técnicas de emulador do SharePoint descritas acima:  
  
```c#  
using System;   
//other namespace declarations  
...   
// code under test  
using MySPApps;  
using Microsoft.SharePoint;  
// unit testing and emulators  
using Microsoft.VisualStudio.TestTools.UnitTesting;  
using Microsoft.QualityTools.Testing.Emulators;  
using Microsoft.SharePoint.Emulators;  
// explicit Fakes shims  
using Microsoft.QualityTools.Testing.Fakes;  
using Microsoft.SharePoint.Fakes  
  
namspace MySPAppTests   
{  
    [TestClass]  
    public class BookAnAppointmentWebPartTests  
    {  
  
        // emulationScope is a class level field  
        private SharePointEmulationScope emulationScope;  
  
        // preprocessor directives determine the value of emulatorMode  
        #if USE_EMULATION  
            private const EmulationMode emulatorMode = EmulationMode.Enabled;  
        #else  
            private const EmulationMode emulatorMode = EmulationMode.Passthrough;  
        #endif  
  
        // InitializeTest sets the emulation scope at the beginning of each test method  
        [TestInitialize]  
        public void InitializeTest()  
        {  
            this.emulationScope = new SharePointEmulationScope(emulatorMode);  
        }  
  
        // CleanupTest disposes the emulation scope at the end of each test method  
        [TestCleanup]  
        public void Cleanup()  
        {  
            this.emulationScope.Dispose();  
        }  
  
        [TestMethod]  
        public void ScheduleAppointmentReturnsTrueWhenNewAppointmentIsCreated()  
        {  
            // remove the SharePointEmulationScope using statement from the method  
            using( var site = new SPSite("http://localhost"))  
            using (var webPart = new BookAnAppointmentWebPart())  
            {  
                // Arrange  
                string errorMsg = string.Empty;  
                DateTime date = DateTime.Now;  
                SPList list = AddListToSiteHelper(site);  
  
                // Act  
                bool success = webPart.ScheduleAppointment(site.RootWeb, list.Title,  
                    "Raisa Pokrovskaya", "425-555-0163", "raisa@outlook.com", "55", date,   
                    out errorMsg);  
                list.Delete()  
  
                // Assert  
                Assert.IsTrue(success);  
            }  
        }  
  
        [TestMethod]  
        public void GetAppointmentsForTodayReturnsOnlyTodaysAppointments()  
        {  
  
            // remove the SharePointEmulationScope using statement from the method  
            using( var site = new SPSite("http://localhost"))  
            using (var webPart = new BookAnAppointmentWebPart())  
            {  
                // Arrange  
                DateTime date = DateTime.Now;  
                SPList list = AddListToSiteHelper(site);  
                // insert 2 items into list  
                AddItemsToListHelper(list, new string[] {"Raisa Pokrovskaya", "425-555-0163",  
                    "raisa@outlook.com", "55", date.ToString("D") });  
                AddItemsToListHelper(list, new string[] {"Francis Totten", "313-555-0100",  
                    "francis@contoso.com", "42", date.AddDays(1).ToString("D") });  
  
                // use Fakes shims only if emulation is enabled  
                if (emulatorMode == EmulationMode.Enabled)  
                {  
                    var sList = new ShimSPList(list);  
  
                    sList.GetItemsSPQuery = (query) =>  
                    {  
                        var shim = new ShimSPListItemCollection();  
                        shim.Bind(new[] { list.Items[0] });  
                        return shim.Instance;  
                    }  
                }  
  
                // Act  
                string result = webPart.GetAppointmentsForToday(list.Title, site.RootWeb);  
                list.Delete();  
  
                // Assert  
                Assert.IsTrue(result.Contains(String.Format(  
                    "Name: Raisa Pokrovskaya, Phone: 425-555-0163, Email: raisa@outlook.com," +  
                    "Age: 55, Date: {0}", date.ToString("D"))));  
                Assert.IsFalse(result.Contains("Name: Francis Totten"));  
            }  
        }  
  
        ...// More tests  
  
    }  
}  
  
```  
  
##  <a name="BKMK_Emulated_SharePoint_types"></a> Tipos de SharePoint emulados  
 [Microsoft.SharePoint.SPField](http://msdn.microsoft.com/library/Microsoft.SharePoint.SPField)  
  
 [Microsoft.SharePoint.SPFieldIndex](http://msdn.microsoft.com/library/Microsoft.SharePoint.SPFieldIndex)  
  
 [Microsoft.SharePoint.SPFieldIndexCollection](http://msdn.microsoft.com/library/Microsoft.SharePoint.SPFieldIndexCollection)  
  
 [Microsoft.SharePoint.SPFieldLink](http://msdn.microsoft.com/library/Microsoft.SharePoint.SPFieldLink)  
  
 [Microsoft.SharePoint.SPFieldLinkCollection](http://msdn.microsoft.com/library/Microsoft.SharePoint.SPFieldLinkCollection)  
  
 [Microsoft.SharePoint.SPFieldUrlValue](http://msdn.microsoft.com/library/Microsoft.SharePoint.SPFieldUrlValue)  
  
 [Microsoft.SharePoint.SPFile](http://msdn.microsoft.com/library/Microsoft.SharePoint.SPFile)  
  
 [Microsoft.SharePoint.SPFileCollection](http://msdn.microsoft.com/library/Microsoft.SharePoint.SPFileCollection)  
  
 [Microsoft.SharePoint.SPFolder](http://msdn.microsoft.com/library/Microsoft.SharePoint.SPFolder)  
  
 [Microsoft.SharePoint.SPFolderCollection](http://msdn.microsoft.com/library/Microsoft.SharePoint.SPFolderCollection)  
  
 [Microsoft.SharePoint.SPItem](http://msdn.microsoft.com/library/Microsoft.SharePoint.SPItem)  
  
 [Microsoft.SharePoint.SPItemEventDataCollection](http://msdn.microsoft.com/library/Microsoft.SharePoint.SPItemEventDataCollection)  
  
 [Microsoft.SharePoint.SPItemEventProperties](http://msdn.microsoft.com/library/Microsoft.SharePoint.SPItemEventProperties)  
  
 [Microsoft.SharePoint.SPList](http://msdn.microsoft.com/library/Microsoft.SharePoint.SPList)  
  
 [Microsoft.SharePoint.SPListCollection](http://msdn.microsoft.com/library/Microsoft.SharePoint.SPListCollection)  
  
 [Microsoft.SharePoint.SPListEventProperties](http://msdn.microsoft.com/library/%20Microsoft.SharePoint.SPListEventProperties)  
  
 [Microsoft.SharePoint.SPListItem](http://msdn.microsoft.com/library/Microsoft.SharePoint.SPListItem)  
  
 [Microsoft.SharePoint.SPListItemCollection](http://msdn.microsoft.com/library/Microsoft.SharePoint.SPListItemCollection)  
  
 [Microsoft.SharePoint.SPQuery](http://msdn.microsoft.com/library/Microsoft.SharePoint.SPQuery)  
  
 [Microsoft.SharePoint.SPRoleAssignment](http://msdn.microsoft.com/library/Microsoft.SharePoint.SPRoleAssignment)  
  
 [Microsoft.SharePoint.SPRoleAssignmentCollection](http://msdn.microsoft.com/library/Microsoft.SharePoint.SPRoleAssignmentCollection)  
  
 [Microsoft.SharePoint.SPSecurableObject](http://msdn.microsoft.com/library/Microsoft.SharePoint.SPSecurableObject)  
  
 [Microsoft.SharePoint.SPSecurity](http://msdn.microsoft.com/library/Microsoft.SharePoint.SPSecurity)  
  
 [Microsoft.SharePoint.SPSite](http://msdn.microsoft.com/library/Microsoft.SharePoint.SPSite)  
  
 [Microsoft.SharePoint.SPUser](http://msdn.microsoft.com/library/Microsoft.SharePoint.SPUser)  
  
 [Microsoft.SharePoint.SPUserCollection](http://msdn.microsoft.com/library/Microsoft.SharePoint.SPUserCollection)  
  
 [Microsoft.SharePoint.SPView](http://msdn.microsoft.com/library/Microsoft.SharePoint.SPView)  
  
 [Microsoft.SharePoint.SPViewCollection](http://msdn.microsoft.com/library/Microsoft.SharePoint.SPViewCollection)  
  
 [Microsoft.SharePoint.SPViewContext](http://msdn.microsoft.com/library/Microsoft.SharePoint.SPViewContext)  
  
 [Microsoft.SharePoint.SPWeb](http://msdn.microsoft.com/library/Microsoft.SharePoint.SPW)   
## Consulte também  
[Teste de unidade de código](../test/unit-test-your-code.md)  
[Testando os aplicativos do SharePoint 2010 com testes de interface do usuário codificada](../test/testing-sharepoint-2010-applications-with-coded-ui-tests.md)  
[Testes de desempenho na Web e carregamento para aplicativos do SharePoint 2010 e 2013](/devops-test-docs/test/web-performance-and-load-testing-sharepoint-2010-and-2013-applications)  
[Developing SharePoint Solutions](/office-dev/office-dev/developing-sharepoint-solutions)