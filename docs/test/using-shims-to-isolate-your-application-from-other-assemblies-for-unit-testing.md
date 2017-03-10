---
title: "Usando shims para isolar seu aplicativo de outros assemblies para testes de unidade | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d2a34de2-6527-4c21-8b93-2f268ee894b7
caps.latest.revision: 12
caps.handback.revision: 12
ms.author: "mlearned"
manager: "douge"
---
# Usando shims para isolar seu aplicativo de outros assemblies para testes de unidade
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

**Correção de tipos** são uma das duas tecnologias que usa o Microsoft Fakes Framework para permitir que você isole facilmente os componentes em teste do ambiente.  Shims desviam chamadas para métodos específicos para o código que você escreve como parte de seu teste.  Muitos métodos retornam resultados diferentes dependente de condições externas, mas um shim fica sob o controle do seu teste e pode retornar resultados consistentes em cada chamada.  Isso torna muito mais fácil escrever seus testes.  
  
 Use shims para isolar o código de assemblies que não fazem parte de sua solução.  Para isolar os componentes de sua solução uns dos outros, é recomendável que você use stubs.  
  
 Para uma visão geral e rápida iniciam orientação, consulte [Isolando código em teste com falsificação da Microsoft](../test/isolating-code-under-test-with-microsoft-fakes.md)  
  
 **Requisitos**  
  
-   O Visual Studio Enterprise  
  
 Consulte [vídeo \(1h 16\): código de Un\-testable testes com Fakes no Visual Studio 2012](http://go.microsoft.com/fwlink/?LinkId=261837)  
  
## Neste tópico  
 Aqui está o que você aprenderá neste tópico:  
  
 [Exemplo: O bug do ano 2000](../test/using-shims-to-isolate-your-application-from-other-assemblies-for-unit-testing.md#BKMK_Example__The_Y2K_bug)  
  
 [Como usar Shims](../test/using-shims-to-isolate-your-application-from-other-assemblies-for-unit-testing.md#BKMK_Fakes_requirements)  
  
-   [Adicionar Assemblies Fakes](#AddFakes)  
  
-   [Use ShimsContext](#ShimsContext)  
  
-   [Escreva testes com correções](#WriteTests)  
  
 [Correções para tipos diferentes de métodos](../test/using-shims-to-isolate-your-application-from-other-assemblies-for-unit-testing.md#BKMK_Shim_basics)  
  
-   [Métodos estáticos](../test/using-shims-to-isolate-your-application-from-other-assemblies-for-unit-testing.md#BKMK_Static_methods)  
  
-   [Métodos de instância (para todas as instâncias)](../test/using-shims-to-isolate-your-application-from-other-assemblies-for-unit-testing.md#BKMK_Instance_methods__for_all_instances_)  
  
-   [Métodos de instância (para uma instância de tempo de execução)](../test/using-shims-to-isolate-your-application-from-other-assemblies-for-unit-testing.md#BKMK_Instance_methods__for_one_instance_)  
  
-   [Construtores](../test/using-shims-to-isolate-your-application-from-other-assemblies-for-unit-testing.md#BKMK_Constructors)  
  
-   [Membros base](../test/using-shims-to-isolate-your-application-from-other-assemblies-for-unit-testing.md#BKMK_Base_members)  
  
-   [Construtores estáticos](../test/using-shims-to-isolate-your-application-from-other-assemblies-for-unit-testing.md#BKMK_Static_constructors)  
  
-   [Finalizadores](../test/using-shims-to-isolate-your-application-from-other-assemblies-for-unit-testing.md#BKMK_Finalizers)  
  
-   [Métodos particulares](../test/using-shims-to-isolate-your-application-from-other-assemblies-for-unit-testing.md#BKMK_Private_methods)  
  
-   [Interfaces de associação](../test/using-shims-to-isolate-your-application-from-other-assemblies-for-unit-testing.md#BKMK_Binding_interfaces)  
  
 [Alterando o comportamento padrão](../test/using-shims-to-isolate-your-application-from-other-assemblies-for-unit-testing.md#BKMK_Changing_the_default_behavior)  
  
 [Ambiente detectando acessa](../test/using-shims-to-isolate-your-application-from-other-assemblies-for-unit-testing.md#BKMK_Detecting_environment_accesses)  
  
 [Simultaneidade](../test/using-shims-to-isolate-your-application-from-other-assemblies-for-unit-testing.md#BKMK_Concurrency)  
  
 [Chamar o método original do método de correção](../test/using-shims-to-isolate-your-application-from-other-assemblies-for-unit-testing.md#BKMK_Calling_the_original_method_from_the_shim_method)  
  
 [Limitações](../test/using-shims-to-isolate-your-application-from-other-assemblies-for-unit-testing.md#BKMK_Limitations)  
  
##  <a name="BKMK_Example__The_Y2K_bug"></a> Exemplo: O bug do ano 2000  
 Vamos considerar um método que gera uma exceção em 1º de janeiro de 2000:  
  
```c#  
// code under test  
public static class Y2KChecker {  
    public static void Check() {  
        if (DateTime.Now == new DateTime(2000, 1, 1))  
            throw new ApplicationException("y2kbug!");  
    }  
}  
  
```  
  
 Esse método de teste é particularmente problemático porque depende do programa `DateTime.Now`, um método que depende do computador do relógio, um dependente do ambiente, o método não\-determinística.  Além disso, o `DateTime.Now` é uma propriedade estática para um tipo de stub não pode ser usado aqui.  Esse problema é um sintoma do problema isolamento em testes de unidade: programas que chamam APIs de banco de dados diretamente, se comunicam com serviços da web e assim por diante são difíceis de teste de unidade porque sua lógica depende do ambiente.  
  
 Isso é onde os tipos de correção devem ser usados.  Tipos de shims fornecem um mecanismo para desviar de qualquer método do .NET em um delegado definido pelo usuário.  Tipos de shims são o código gerado pelo gerador de falsificações e usarem delegados, o que chamamos de tipos de shims, para especificar as novas implementações do método.  
  
 O teste a seguir mostra como usar o tipo de correção, `ShimDateTime`, para fornecer uma implementação personalizada de Now:  
  
```c#  
//unit test code  
// create a ShimsContext cleans up shims   
using (ShimsContext.Create()  
    // hook delegate to the shim method to redirect DateTime.Now  
    // to return January 1st of 2000  
    ShimDateTime.NowGet = () => new DateTime(2000, 1, 1);  
    Y2KChecker.Check();  
}  
  
```  
  
##  <a name="BKMK_Fakes_requirements"></a> Como usar Shims  
  
###  <a name="AddFakes"></a> Adicionar Assemblies Fakes  
  
1.  No Gerenciador de Soluções, expanda as **Referências** de seu projeto de teste de unidade.  
  
    -   Se você estiver trabalhando no Visual Basic, selecione **Mostrar Todos os Arquivos** na barra de ferramentas do Gerenciador de Soluções para ver a lista Referências.  
  
2.  Selecione o assembly que contém as definições de classes para o qual você deseja criar correções.  Por exemplo, se você quiser usar shims DateTime, selecione System. dll  
  
3.  No menu de atalhos, escolha **Adicionar Assembly do Fakes**.  
  
###  <a name="ShimsContext"></a> Use ShimsContext  
 Ao usar tipos de shims em uma estrutura de teste de unidade, você deve encapsular o código de teste em um `ShimsContext` para controlar o tempo de vida de seus correções.  Se nós não exige isso, suas shims deve durar até que o AppDomain é desligado.  A maneira mais fácil de criar um `ShimsContext` é usando estático `Create()` método conforme mostrado no código a seguir:  
  
```c#  
//unit test code  
[Test]  
public void Y2kCheckerTest() {  
  using(ShimsContext.Create()) {  
    ...  
  } // clear all shims  
}  
  
```  
  
 É fundamental para adequadamente exibir cada contexto de correção.  Como regra geral, sempre chamar o `ShimsContext.Create` dentro de um `using` instrução para garantir a correta limpar as correções registradas.  Por exemplo, você pode registrar uma correção para um método de teste que substitui o `DateTime.Now` método com um delegado que sempre retorna o primeiro de janeiro de 2000.  Se você esquecer de limpar a correção registrada no método de teste, o restante da execução do teste sempre retornaria o primeiro de janeiro de 2000 como o Now valor.  Isso pode ser suprising e confuso.  
  
###  <a name="WriteShims"></a> Escrever um teste com correções  
 No código de teste, insira um *desvio* para o método que você deseja forjar.  Por exemplo:  
  
```c#  
[TestClass]  
public class TestClass1  
{   
        [TestMethod]  
        public void TestCurrentYear()  
        {  
            int fixedYear = 2000;  
  
            using (ShimsContext.Create())  
            {  
              // Arrange:  
                // Detour DateTime.Now to return a fixed date:  
                System.Fakes.ShimDateTime.NowGet =   
                () =>  
                { return new DateTime(fixedYear, 1, 1); };  
  
                // Instantiate the component under test:  
                var componentUnderTest = new MyComponent();  
  
              // Act:  
                int year = componentUnderTest.GetTheCurrentYear();  
  
              // Assert:   
                // This will always be true if the component is working:  
                Assert.AreEqual(fixedYear, year);  
            }  
        }  
}  
  
```  
  
```vb#  
<TestClass()> _  
Public Class TestClass1  
    <TestMethod()> _  
    Public Sub TestCurrentYear()  
        Using s = Microsoft.QualityTools.Testing.Fakes.ShimsContext.Create()  
            Dim fixedYear As Integer = 2000  
            ' Arrange:  
            ' Detour DateTime.Now to return a fixed date:  
            System.Fakes.ShimDateTime.NowGet = _  
                Function() As DateTime  
                    Return New DateTime(fixedYear, 1, 1)  
                End Function  
  
            ' Instantiate the component under test:  
            Dim componentUnderTest = New MyComponent()  
            ' Act:  
            Dim year As Integer = componentUnderTest.GetTheCurrentYear  
            ' Assert:   
            ' This will always be true if the component is working:  
            Assert.AreEqual(fixedYear, year)  
        End Using  
    End Sub  
End Class  
```  
  
 Os nomes das classes de shims são compostos pelo prefixo `Fakes.Shim` adicionado ao nome do tipo original.  
  
 Corrige os trabalho inserindo *desvios* no código do aplicativo em teste.  Sempre que ocorre uma chamada para o método original, o sistema Fakes executa um desvio, em vez de chamar o método real, seu código de correção é chamada.  
  
 Observe que os desvios são criados e excluídos em tempo de execução.  Você sempre deve criar um desvio na vida de um `ShimsContext`.  Quando é descartado, qualquer correções criadas enquanto ele estava ativo são removidas.  É a melhor maneira de fazer isso dentro de um `using` instrução.  
  
 Talvez você veja um erro de compilação informando que o namespace Fakes não existe.  Às vezes, esse erro aparece quando houver outros erros de compilação.  Corrija os outros erros e ela desaparecerá.  
  
##  <a name="BKMK_Shim_basics"></a> Correções para tipos diferentes de métodos  
 Tipos de shims permitem que você substitua qualquer método do .NET, incluindo métodos estáticos ou métodos não virtuais, com seus próprios delegados.  
  
###  <a name="BKMK_Static_methods"></a> Métodos estáticos  
 As propriedades para anexar shims para métodos estáticos são colocadas em um tipo de correção.  Cada propriedade tem apenas um setter que pode ser usado para anexar um delegado para o método de destino.  Por exemplo, dada a classe `MyClass` com um método estático `MyMethod`:  
  
```c#  
//code under test  
public static class MyClass {  
    public static int MyMethod() {  
        ...  
    }  
}  
```  
  
 É possível anexar uma correção para `MyMethod` que sempre retorna 5:  
  
```c#  
// unit test code  
ShimMyClass.MyMethod = () =>5;  
```  
  
###  <a name="BKMK_Instance_methods__for_all_instances_"></a> Métodos de instância \(para todas as instâncias\)  
 De maneira semelhante aos métodos estáticos, os métodos de instância permitem para todas as instâncias.  As propriedades para anexar essas correções são colocadas em um tipo aninhado chamado AllInstances para evitar confusão.  Por exemplo, dada a classe `MyClass` com um método de instância `MyMethod`:  
  
```c#  
// code under test  
public class MyClass {  
    public int MyMethod() {  
        ...  
    }  
}  
```  
  
 Você pode anexar uma correção para `MyMethod` que sempre retorna 5, independentemente da instância:  
  
```c#  
// unit test code  
ShimMyClass.AllInstances.MyMethod = () => 5;  
```  
  
 A estrutura do tipo gerado de ShimMyClass parece com o código a seguir:  
  
```c#  
// Fakes generated code  
public class ShimMyClass : ShimBase<MyClass> {  
    public static class AllInstances {  
        public static Func<MyClass, int>MyMethod {  
            set {  
                ...  
            }  
        }  
    }  
}  
```  
  
 Observe que simula a passa a instância de tempo de execução como o primeiro argumento do delegado nesse caso.  
  
###  <a name="BKMK_Instance_methods__for_one_instance_"></a> Métodos de instância \(para uma instância de tempo de execução\)  
 Métodos de instância também permitem pelo delegates diferentes, com base no receptor da chamada.  Isso permite que o mesmo método de instância para comportamentos diferentes por instância do tipo.  As propriedades para configurar essas correções são métodos de instância do tipo shim em si.  Cada tipo de correção instanciado também é associado uma instância bruta de um tipo com shims.  
  
 Por exemplo, dada a classe `MyClass` com um método de instância `MyMethod`:  
  
```c#  
// code under test  
public class MyClass {  
    public int MyMethod() {  
        ...  
    }  
}  
```  
  
 Podemos configurar dois tipos de correção de MyMethod que primeiro sempre retorna 5 e o segundo sempre retorna 10:  
  
```c#  
// unit test code  
var myClass1 = new ShimMyClass()  
{  
    MyMethod = () => 5  
};  
var myClass2 = new ShimMyClass { MyMethod = () => 10 };  
```  
  
 A estrutura do tipo gerado de ShimMyClass parece com o código a seguir:  
  
```c#  
// Fakes generated code  
public class ShimMyClass : ShimBase<MyClass> {  
    public Func<int> MyMethod {  
        set {  
            ...  
        }  
    }  
    public MyClass Instance {  
        get {  
            ...  
        }  
    }  
}  
```  
  
 A instância de tipo com shims real pode ser acessada por meio da propriedade de instância:  
  
```c#  
// unit test code  
var shim = new ShimMyClass();  
var instance = shim.Instance;  
```  
  
 O tipo de correção também tem uma conversão implícita para o tipo com shims, para poder usar o tipo de correção é normalmente simplesmente:  
  
```c#  
// unit test code  
var shim = new ShimMyClass();  
MyClass instance = shim; // implicit cast retrieves the runtime  
                         // instance  
```  
  
###  <a name="BKMK_Constructors"></a> Construtores  
 Construtores também permitem para anexar os tipos de shims para objetos futuros.  Cada construtor é exposto como um método estático construtor no tipo de correção.  Por exemplo, dada a classe `MyClass` com um construtor que recebe um número inteiro:  
  
```c#  
// code under test  
public class MyClass {  
    public MyClass(int value) {  
        this.Value = value;  
    }  
    ...  
}  
```  
  
 Configuramos o tipo de correção do construtor de modo que todas as instâncias futuras retorna \-5 quando o getter de valor é chamado, independentemente do valor no construtor:  
  
```c#  
// unit test code  
ShimMyClass.ConstructorInt32 = (@this, value) => {  
    var shim = new ShimMyClass(@this) {  
        ValueGet = () => -5  
    };  
};  
```  
  
 Observe que cada tipo de correção expõe dois construtores.  O construtor padrão deve ser usado quando uma nova instância é necessária, enquanto o construtor que recebe uma instância com shims como argumento deve ser usado em apenas correções de construtor:  
  
```c#  
// unit test code  
public ShimMyClass() { }  
public ShimMyClass(MyClass instance) : base(instance) { }  
```  
  
 A estrutura do tipo gerado de ShimMyClass lembra o código seguintes:  
  
```c#  
// Fakes generated code  
public class ShimMyClass : ShimBase<MyClass>  
{  
    public static Action<MyClass, int> ConstructorInt32 {  
        set {  
            ...  
        }  
    }  
  
    public ShimMyClass() { }  
    public ShimMyClass(MyClass instance) : base(instance) { }  
    ...  
}  
```  
  
###  <a name="BKMK_Base_members"></a> Membros base  
 As propriedades de correção dos membros base podem ser acessadas, criando uma correção para o tipo base e passar a instância de filho como um parâmetro para o construtor da classe base de correção.  
  
 Por exemplo, dada a classe `MyBase` com um método de instância `MyMethod` e um subtipo `MyChild`:  
  
```c#  
public abstract class MyBase {  
    public int MyMethod() {  
        ...  
    }  
}  
  
public class MyChild : MyBase {  
}  
  
```  
  
 Podemos configurar um shim de `MyBase` Criando um novo `ShimMyBase` correção:  
  
```c#  
// unit test code  
var child = new ShimMyChild();  
new ShimMyBase(child) { MyMethod = () => 5 };  
```  
  
 Observe que o tipo de correção de filho é implicitamente convertido para a instância filho quando passado como um parâmetro para o construtor base shim.  
  
 A estrutura do tipo gerado de ShimMyChild e ShimMyBase se parece com o código a seguir:  
  
```c#  
// Fakes generated code  
public class ShimMyChild : ShimBase<MyChild> {  
    public ShimMyChild() { }  
    public ShimMyChild(Child child)  
        : base(child) { }  
}  
public class ShimMyBase : ShimBase<MyBase> {  
    public ShimMyBase(Base target) { }  
    public Func<int> MyMethod  
    { set { ... } }  
}  
```  
  
###  <a name="BKMK_Static_constructors"></a> Construtores estáticos  
 Tipos de shims expõem um método estático `StaticConstructor` por usar shims o construtor estático de um tipo.  Uma vez que construtores estáticos são executados uma vez, você precisa garantir que a correção é configurada antes de qualquer membro do tipo é acessado.  
  
###  <a name="BKMK_Finalizers"></a> Finalizadores  
 Não há suporte para os finalizadores em falsificações.  
  
###  <a name="BKMK_Private_methods"></a> Métodos particulares  
 O gerador de código Fakes criará as propriedades de correção para métodos particulares que possuem apenas tipos visíveis na assinatura, ou seja  tipos de parâmetro e tipo de retorno é visível.  
  
###  <a name="BKMK_Binding_interfaces"></a> Interfaces de associação  
 Quando um tipo com shims implementa uma interface, o gerador de código emite um método que permite associar todos os membros de interface de uma vez.  
  
 Por exemplo, dada uma classe `MyClass` que implementa `IEnumerable<int>`:  
  
```c#  
public class MyClass : IEnumerable<int> {  
    public IEnumerator<int> GetEnumerator() {  
        ...  
    }  
    ...  
}  
  
```  
  
 É possível usar o shim as implementações de `IEnumerable<int>` em MyClass chamando o método Bind:  
  
```c#  
// unit test code  
var shimMyClass = new ShimMyClass();  
shimMyClass.Bind(new List<int> { 1, 2, 3 });  
  
```  
  
 A estrutura do tipo gerado de ShimMyClass se parece com o código a seguir:  
  
```c#  
// Fakes generated code  
public class ShimMyClass : ShimBase<MyClass> {  
    public ShimMyClass Bind(IEnumerable<int> target) {  
        ...  
    }  
}  
  
```  
  
##  <a name="BKMK_Changing_the_default_behavior"></a> Alterando o comportamento padrão  
 Cada tipo de correção gerado contém uma instância do `IShimBehavior` interface por meio do `ShimBase<T>.InstanceBehavior` propriedade.  O comportamento é usado sempre que um cliente chama um membro de instância não foi explicitamente corrigido.  
  
 Se o comportamento não foi explicitamente definido, ele usará a instância retornada pela estático `ShimsBehaviors.Current` propriedade.  Por padrão, essa propriedade retorna um comportamento que gerou uma exceção `NotImplementedException`.  
  
 Esse comportamento pode ser alterado a qualquer momento definindo a `InstanceBehavior` propriedade em qualquer instância de correção.  Por exemplo, o trecho a seguir altera a correção para um comportamento que não faz nada ou retorna o valor padrão do tipo de retorno — ou seja, Default \(t\):  
  
```c#  
// unit test code  
var shim = new ShimMyClass();  
//return default(T) or do nothing  
shim.InstanceBehavior = ShimsBehaviors.DefaultValue;  
  
```  
  
 O comportamento pode também ser modificado globalmente para todas as instâncias com shims para os quais o `InstanceBehavior` propriedade não foi explicitamente definida pela configuração estática `ShimsBehaviors.Current` propriedade:  
  
```c#  
// unit test code  
// change default shim for all shim instances  
// where the behavior has not been set  
ShimsBehaviors.Current =   
    ShimsBehaviors.DefaultValue;  
  
```  
  
##  <a name="BKMK_Detecting_environment_accesses"></a> Ambiente detectando acessa  
 É possível anexar um comportamento a todos os membros, incluindo métodos estáticos, de um tipo específico, atribuindo a `ShimsBehaviors.NotImplemented` comportamento para a propriedade estática `Behavior` do tipo correspondente de correção:  
  
```c#  
// unit test code  
// assigning the not implemented behavior  
ShimMyClass.Behavior = ShimsBehaviors.NotImplemented;  
// shorthand  
ShimMyClass.BehaveAsNotImplemented();  
  
```  
  
##  <a name="BKMK_Concurrency"></a> Simultaneidade  
 Tipos de shims se aplicam a todos os threads no AppDomain e não tem afinidade de thread.  Isso é importante se você planeja usar um executor de teste que oferecem suporte a simultaneidade: testes que envolvem tipos de shims não podem ser executados simultaneamente.  Essa propriedade não é enfored pelo tempo de execução falsificações.  
  
##  <a name="BKMK_Calling_the_original_method_from_the_shim_method"></a> Chamar o método original do método de correção  
 Imagine que gostaríamos de realmente escrever o texto para o sistema de arquivos depois de validar o nome do arquivo passado para o método.  Nesse caso, queremos chamar o método original no meio do método de correção.  
  
 A primeira abordagem para resolver esse problema é encapsular uma chamada para o método original usando um delegado e `ShimsContext.ExecuteWithoutShims()` como no código a seguir:  
  
```c#  
// unit test code  
ShimFile.WriteAllTextStringString = (fileName, content) => {  
  ShimsContext.ExecuteWithoutShims(() => {  
  
      Console.WriteLine("enter");  
      File.WriteAllText(fileName, content);  
      Console.WriteLine("leave");  
  });  
};  
  
```  
  
 Outra abordagem é definir a correção null, chame o método original e restaurar a correção.  
  
```c#  
// unit test code  
ShimsDelegates.Action<string, string> shim = null;  
shim = (fileName, content) => {  
  try {  
    Console.WriteLine("enter”);  
    // remove shim in order to call original method  
    ShimFile.WriteAllTextStringString = null;  
    File.WriteAllText(fileName, content);  
  }  
  finally  
  {  
    // restore shim  
    ShimFile.WriteAllTextStringString = shim;  
    Console.WriteLine("leave");  
  }  
};  
// initialize the shim  
ShimFile.WriteAllTextStringString = shim;  
  
```  
  
##  <a name="BKMK_Limitations"></a> Limitações  
 Correções não podem ser usadas em todos os tipos de base class library do .NET **mscorlib** e **System**.  
  
## Recursos externos  
  
### Diretriz  
 [Teste para entrega contínua com o Visual Studio 2012 – capítulo 2: testes de unidade: Testando o interior](http://go.microsoft.com/fwlink/?LinkID=255188)  
  
## Consulte também  
 [Isolando código em teste com falsificação da Microsoft](../test/isolating-code-under-test-with-microsoft-fakes.md)   
 [blog do Peter Provost: corretivos em Visual Studio 2012](http://www.peterprovost.org/blog/2012/04/25/visual-studio-11-fakes-part-2)   
 [vídeo \(1h 16\): código de Un\-testable testes com Fakes no Visual Studio 2012](http://go.microsoft.com/fwlink/?LinkId=261837)