---
title: "Servi&#231;os do Windows Communication Foundation e WCF Data Services no Visual Studio | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Serviços de dados WCF"
  - "Serviços WCF, vinculando a"
  - "Serviços WCF, métodos assíncronos de serviço"
  - "referências de serviço [Visual Studio]"
  - "WCF Data Services"
  - "chamadas assíncronas"
  - "referências [Visual Studio] do serviço, compartilhamento de tipo"
  - "pontos de extremidade [WCF]"
  - "métodos assíncronos de serviço"
  - "pontos de extremidade de referências de serviço [Visual Studio]"
  - "Serviços WCF, compartilhamento de tipo"
  - "O Windows Communication Foundation no Visual Studio"
  - "serviços do WCF"
  - "Serviço WCF, o Visual Studio"
  - "Serviços de dados WCF"
  - "serviços no Visual Studio"
  - "associação de dados [Visual Studio], WCF"
  - "pontos de extremidade de serviço [Visual Studio]"
  - "referências de serviço [Visual Studio], chamadas assíncronas"
  - "serviços Windows Communication Foundation"
  - "compartilhamento de tipo em serviços WCF"
  - "Serviços WCF, pontos de extremidade"
  - "método de serviço, chamado de forma assíncrona [Visual Studio]"
ms.assetid: d56f12cb-e139-4fec-b3e4-488383356642
caps.latest.revision: 26
caps.handback.revision: 24
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Servi&#231;os do Windows Communication Foundation e WCF Data Services no Visual Studio
Visual Studio fornece ferramentas para trabalhar com o Windows Communication Foundation \(WCF\) e [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)], tecnologias da Microsoft para a criação de aplicativos distribuídos. Este tópico fornece uma introdução aos serviços de um [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] perspectiva. Para obter a documentação completa, consulte [WCF Data Services 4.5](../Topic/WCF%20Data%20Services%204.5.md).  
  
## O que é o WCF?  
 [!INCLUDE[vsindigo](../data-tools/includes/vsindigo_md.md)] é um framework unificado para criar aplicativos distribuídos seguros, confiáveis, transacionados e interoperáveis. Ele substitui as tecnologias de comunicação entre processos mais antigas, como serviços Web ASMX, .NET Remoting, Enterprise Services \(DCOM\) e MSMQ. WCF reúne a funcionalidade de todas essas tecnologias em um modelo de programação unificado. Isso simplifica a experiência de desenvolvimento de aplicativos distribuídos.  
  
#### O que são o WCF Data Services  
 [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)] são serviços que interagem diretamente com um banco de dados, permitindo que você retorne dados usando verbos HTTP, como GET, POSTAGEM, PUT ou DELETE. Em geral, [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)] são uma boa opção para aplicativos que são usados para criar, atualizar ou excluir registros em um banco de dados. Para obter mais informações, consulte [WCF Data Services 4.5](http://go.microsoft.com/fwlink/?LinkID=119952).  
  
### Modelo de programação WCF  
 O modelo de programação WCF baseia\-se na comunicação entre duas entidades: um serviço WCF e um cliente do WCF. O modelo de programação é encapsulado no <xref:System.ServiceModel> namespace o [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)].  
  
#### Serviço WCF  
 Um serviço WCF baseia\-se em uma interface que define um contrato entre o cliente e o serviço. Ele é marcado com um <xref:System.ServiceModel.ServiceContractAttribute> de atributo, conforme mostrado no código a seguir:  
  
 [!code-cs[WCFWalkthrough#6](../data-tools/codesnippet/CSharp/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio_1.cs)]
 [!code-vb[WCFWalkthrough#6](../data-tools/codesnippet/VisualBasic/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio_1.vb)]  
  
 [!code-cs[WCFWalkthrough#1](../data-tools/codesnippet/CSharp/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio_2.cs)]
 [!code-vb[WCFWalkthrough#1](../data-tools/codesnippet/VisualBasic/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio_2.vb)]  
  
 Definir funções ou métodos que são expostos por um serviço WCF, marcando\-os com um <xref:System.ServiceModel.OperationContractAttribute> atributo. Além disso, você pode expor dados serializados marcando um tipo composto com um <xref:System.Runtime.Serialization.DataContractAttribute> atributo. Isso permite que a ligação de dados em um cliente.  
  
 Depois que uma interface e seus métodos são definidos, elas são encapsuladas em uma classe que implementa a interface. Uma única classe de serviço WCF pode implementar vários contratos de serviço.  
  
 Um serviço WCF é exposto para consumo por meio do que é conhecido como um *endpoint*. O ponto de extremidade fornece a única maneira de se comunicar com o serviço; não é possível acessar o serviço por meio de uma referência direta, como você faria com outras classes.  
  
 Um ponto de extremidade consiste em um endereço, uma ligação e um contrato. O endereço define onde o serviço está localizado; Isso pode ser uma URL, um endereço FTP, uma rede ou caminho local. Uma associação define o modo como você se comunica com o serviço. Ligações do WCF fornecem um modelo versátil para especificar um protocolo, como HTTP ou FTP, um mecanismo de segurança como autenticação do Windows ou nomes de usuário e senhas e muito mais. Um contrato inclui as operações que são expostas pela classe de serviço WCF.  
  
 Vários pontos de extremidade podem ser expostos para um único serviço WCF. Isso permite que diferentes clientes se comuniquem com o mesmo serviço de maneiras diferentes. Por exemplo, um serviço de banco pode fornecer um ponto de extremidade para os funcionários e outro para clientes externos, cada um com um endereço diferente, associação, e\/ou de contrato.  
  
#### Cliente do WCF  
 Um cliente WCF consiste em uma *proxy* que permite que um aplicativo para se comunicar com um serviço WCF e um ponto de extremidade que corresponde a um ponto de extremidade definido para o serviço. O proxy gerado no lado do cliente no arquivo App. config e inclui informações sobre os tipos e métodos que são expostos pelo serviço. Para serviços que expõem vários pontos de extremidade, o cliente pode selecionar aquele que melhor atenda às suas necessidades, por exemplo, para se comunicar por HTTP e usar a autenticação do Windows.  
  
 Depois que um cliente WCF foi criado, faça referência o serviço em seu código como faria qualquer outro objeto. Por exemplo, para chamar o `GetData` método mostrado anteriormente, você deve escrever o código semelhante ao seguinte:  
  
 [!code-cs[WCFWalkthrough#3](../data-tools/codesnippet/CSharp/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio_3.cs)]
 [!code-vb[WCFWalkthrough#3](../data-tools/codesnippet/VisualBasic/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio_3.vb)]  
  
## Ferramentas do WCF no Visual Studio  
 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] fornece ferramentas para ajudá\-lo a criar serviços WCF e clientes do WCF. Para uma explicação passo a passo que demonstra as ferramentas, consulte [Passo a passo: Criando um serviço WCF simples no Windows Forms](../data-tools/walkthrough-creating-a-simple-wcf-service-in-windows-forms.md).  
  
### Criando e Testando serviços WCF  
 Você pode usar o WCF [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] modelos como uma base para criar rapidamente seu próprio serviço. Em seguida, você pode usar WCF serviço automático Host e cliente de teste do WCF para depurar e testar o serviço. Juntos, essas ferramentas fornecem uma rápida e conveniente de depuração e ciclo de testes e eliminam a necessidade de confirmar a um modelo de hospedagem mais cedo.  
  
#### Modelos do WCF  
 WCF [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] modelos fornecem uma estrutura de classe básica para o desenvolvimento de serviço. Vários modelos WCF estão disponíveis no **Adicionar novo projeto** caixa de diálogo. Isso inclui projetos de biblioteca de serviços WCF, Sites do serviço WCF e modelos de Item de serviço do WCF.  
  
 Quando você seleciona um modelo, os arquivos são adicionados para um contrato de serviço, uma implementação de serviço e uma configuração de serviço. Todos os atributos necessários já foram adicionados, criando um tipo simple de "Hello World" do serviço, e você não tivesse de escrever nenhum código. É claro, convém adicionar código para fornecer funções e métodos para o serviço do mundo real, mas os modelos fornecem os princípios básicos.  
  
 Para saber mais sobre modelos do WCF, consulte [Modelos do Visual Studio do WCF](../Topic/WCF%20Visual%20Studio%20Templates.md).  
  
#### Host de serviço do WCF  
 Quando você iniciar o [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] do depurador \(pressionando F5\) para um projeto de serviço do WCF, o Host de serviço do WCF é iniciada automaticamente para hospedar o serviço localmente. Host de serviço WCF enumera os serviços em um projeto de serviço do WCF, carrega a configuração do projeto e cria uma instância de um host para cada serviço que encontrar.  
  
 Usando o Host de serviço WCF, você pode testar um serviço WCF sem escrever código extra ou confirmar a um host específico durante o desenvolvimento.  
  
 Para saber mais sobre o Host de serviço do WCF, consulte [Host de serviço do WCF \(WcfSvcHost.exe\)](../Topic/WCF%20Service%20Host%20\(WcfSvcHost.exe\).md).  
  
#### Cliente de teste do WCF  
 A ferramenta de cliente de teste do WCF permite que você teste parâmetros de entrada, enviem essa entrada para um serviço WCF e visualize a resposta que o serviço envia de volta. Ele fornece um serviço conveniente testar experiência ao combinar com o Host de serviço WCF. A ferramenta pode ser encontrada na pasta \\Common7\\IDE, que para Visual Studio 2015 instalado na unidade c: está aqui: **C:\\Program Files \(x86\) \\Microsoft Visual Studio 14.0\\Common7\\IDE\\**.  
  
 Quando você pressiona F5 para depurar um projeto de serviço do WCF, o cliente de teste do WCF abre e exibe uma lista de pontos de extremidade de serviço que são definidos no arquivo de configuração. Você pode testar os parâmetros e iniciar o serviço e repita esse processo para testar e validar seu serviço continuamente.  
  
 Para saber mais sobre o cliente de teste do WCF, consulte [Cliente de Teste do WCF \(WcfTestClient.exe\)](../Topic/WCF%20Test%20Client%20\(WcfTestClient.exe\).md).  
  
### Acessando serviços WCF no Visual Studio  
 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] simplifica a tarefa de criação de clientes do WCF, gerar automaticamente um proxy e um ponto de extremidade para serviços que você adiciona usando o **Add Service Reference** caixa de diálogo. Todas as informações de configuração necessárias são adicionadas ao arquivo App. config. A maioria das vezes, tudo o que você precisa fazer é instanciar o serviço para usá\-lo.  
  
 O **Add Service Reference** caixa de diálogo permite que você insira o endereço de um serviço ou para procurar por um serviço que é definido em sua solução. A caixa de diálogo retorna uma lista de serviços e as operações fornecidas por esses serviços. Ele também permite que você defina o espaço para nome pelo qual você irá referenciar os serviços no código.  
  
 O **Configurar referências de serviço** caixa de diálogo permite que você personalize a configuração de um serviço. Você pode alterar o endereço de um serviço, especificar o nível de acesso, comportamento assíncrono e tipos de contrato de mensagem e configurar a reutilização de tipo.  
  
## Como: selecionar um ponto de extremidade de serviço  
 Alguns serviços do Windows Communication Foundation \(WCF\) expõem vários pontos de extremidade por meio do qual um cliente pode se comunicar com o serviço. Por exemplo, um serviço pode expor um ponto de extremidade que usa um nome de usuário e associação de HTTP \/ segurança de senha e um segundo ponto de extremidade que usa FTP e autenticação do Windows. O primeiro ponto de extremidade pode ser usado por aplicativos que acessam o serviço de fora de um firewall, enquanto o segundo pode ser usado em uma intranet.  
  
 Nesse caso, você pode especificar o `endpointConfigurationName` como um parâmetro para o construtor uma referência de serviço.  
  
 [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
#### Para selecionar um ponto de extremidade de serviço  
  
1.  Adicione uma referência a um serviço WCF clicando no nó do projeto no Gerenciador de soluções e escolhendo **Adicionar referência de serviço**  
  
2.  No Editor de códigos, adicione um construtor para a referência de serviço:  
  
    ```vb#  
    Dim proxy As New ServiceReference.Service1Client(  
    ```  
  
    ```c#  
    ServiceReference.Service1Client proxy = new ServiceReference.Service1Client(  
    ```  
  
    > [!NOTE]
    >  Substitua *ServiceReference* com o namespace para a referência de serviço e a substituição *Service1Client* com o nome do serviço.  
  
3.  Será exibida uma lista do IntelliSense com as sobrecargas do construtor. Selecione o `endpointConfigurationName As String` de sobrecarga.  
  
4.  Após a sobrecarga, digite `=` *ConfigurationName*, onde *ConfigurationName* é o nome do ponto de extremidade que você deseja usar.  
  
    > [!NOTE]
    >  Se você não souber os nomes dos pontos de extremidade disponíveis, você pode encontrá\-los no arquivo App. config.  
  
#### Para localizar os pontos de extremidade disponíveis para um serviço WCF  
  
1.  Em **Solution Explorer**, clique no arquivo App. config para o projeto que contém a referência de serviço e, em seguida, clique em **Abrir**. O arquivo será exibido no Editor de códigos.  
  
2.  Pesquise o `<Client>` marca no arquivo.  
  
3.  Pesquisar sob o `<Client>` marca para uma marca que começa com `<Endpoint>`.  
  
     Se a referência de serviço fornece vários pontos de extremidade, haverá duas ou mais `<Endpoint` marcas.  
  
4.  Dentro de `<EndPoint>` marca, você encontrará um `name="`*SomeService*`"` parâmetro \(onde *SomeService* representa um nome de ponto de extremidade\). Esse é o nome do ponto de extremidade que pode ser passado para o `endpointConfigurationName As String` sobrecarga de um construtor para uma referência de serviço.  
  
## Como: chamar um método de serviço de forma assíncrona  
 A maioria dos métodos nos serviços do Windows Communication Foundation \(WCF\) pode ser chamado de forma síncrona ou assíncrona. Chamando um método de forma assíncrona permite que seu aplicativo continuar a trabalhar enquanto o método está sendo chamado ao operar em uma conexão lenta.  
  
 Por padrão, quando uma referência de serviço é adicionada a um projeto ele é configurado para chamar métodos de forma síncrona. Você pode alterar o comportamento para chamar métodos de forma assíncrona, alterando uma configuração no **Configure Service Reference** caixa de diálogo.  
  
> [!NOTE]
>  Essa opção é definida em uma base por serviço. Se um método para um serviço é chamado de forma assíncrona, todos os métodos devem ser chamados de forma assíncrona.  
  
 [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
#### Para chamar um método de serviço de forma assíncrona  
  
1.  Em **Solution Explorer**, selecione a referência de serviço.  
  
2.  Sobre o **projeto** menu, clique em **Configure Service Reference**.  
  
3.  No **Configure Service Reference** caixa de diálogo, selecione o **Gerar operações assíncronas** caixa de seleção.  
  
## Como: associar dados retornados por um serviço  
 Você pode associar dados retornados por um serviço Windows Communication Foundation \(WCF\) para um controle, exatamente como você pode vincular qualquer outra fonte de dados a um controle. Quando você adiciona uma referência a um serviço WCF, se o serviço contém tipos compostos que retornam dados, eles são adicionados automaticamente para o **fontes de dados** janela.  
  
#### Para associar um controle a único campo de dados retornado por um serviço WCF  
  
1.  Sobre o **dados** menu, clique em **Show Data Sources**. O **fontes de dados** janela será exibida.  
  
2.  No **fontes de dados** janela, expanda o nó para a referência de serviço. Quaisquer tipos compostos retornados pelo serviço serão exibidos.  
  
3.  Expanda um nó para um tipo. Os campos de dados para esse tipo serão exibidos.  
  
4.  Selecione um campo e clique na seta suspensa para exibir uma lista de controles que estão disponíveis para o tipo de dados.  
  
5.  Clique no tipo de controle que você deseja associar a.  
  
6.  Arraste o campo para um formulário. O controle será adicionado ao formulário junto com um <xref:System.Windows.Forms.BindingSource> componente e um <xref:System.Windows.Forms.BindingNavigator> componente.  
  
7.  Repita as etapas 4 embora 6 para outros campos que você deseja associar.  
  
#### Para associar um controle a tipo composto retornado por um serviço WCF  
  
1.  Sobre o **dados** menu, selecione **Show Data Sources**. O **fontes de dados** janela será exibida.  
  
2.  No **fontes de dados** janela, expanda o nó para a referência de serviço. Quaisquer tipos compostos retornados pelo serviço serão exibidos.  
  
3.  Selecione um nó para um tipo e clique na seta suspensa para exibir uma lista das opções disponíveis.  
  
4.  Clique em **DataGridView** para exibir os dados em uma grade ou **detalhes** para exibir os dados em controles individuais.  
  
5.  Arraste o nó para o formulário. Os controles serão adicionados ao formulário junto com um <xref:System.Windows.Forms.BindingSource> componente e um <xref:System.Windows.Forms.BindingNavigator> componente.  
  
## Como: configurar um serviço para reutilizar os tipos existentes  
 Quando uma referência de serviço é adicionada a um projeto, quaisquer tipos definidos no serviço são gerados no projeto local. Em muitos casos, isso cria tipos duplicados quando usa um serviço comum [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] tipos ou quando os tipos são definidos em uma biblioteca compartilhada.  
  
 Para evitar esse problema, os tipos em assemblies referenciados são compartilhados por padrão. Se você quiser desabilitar o compartilhamento para um ou mais assemblies de tipo, você pode fazer isso no **Configurar referências de serviço** caixa de diálogo.  
  
#### Para desabilitar o compartilhamento de tipo em um único assembly  
  
1.  Em **Solution Explorer**, selecione a referência de serviço.  
  
2.  Sobre o **projeto** menu, clique em **Configure Service Reference**.  
  
3.  No **Configurar referências de serviço** caixa de diálogo, selecione **usar novamente os tipos em assemblies referenciados especificados**.  
  
4.  Marque a caixa de seleção para cada assembly no qual você deseja habilitar o compartilhamento de tipo. Para desabilitar o compartilhamento de um conjunto de tipos, deixe a caixa de seleção desmarcada.  
  
#### Para desabilitar o compartilhamento de tipo em todos os assemblies  
  
1.  Em **Solution Explorer**, selecione a referência de serviço.  
  
2.  Sobre o **projeto** menu, clique em **Configure Service Reference**.  
  
3.  No **Configurar referências de serviço** caixa de diálogo, desmarque o **usar novamente os tipos em assemblies referenciados** caixa de seleção.  
  
## Tópicos relacionados  
  
|Título|Descrição|  
|------------|---------------|  
|[Passo a passo: Criando um serviço WCF simples no Windows Forms](../data-tools/walkthrough-creating-a-simple-wcf-service-in-windows-forms.md)|Fornece uma demonstração passo a passo de criação e utilização de serviços WCF no [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].|  
|[Passo a passo: Criando um WCF Data Service com WPF e o Entity Framework](../data-tools/walkthrough-creating-a-wcf-data-service-with-wpf-and-entity-framework.md)|Fornece uma demonstração passo a passo de como criar e usar [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)] em [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].|  
|[Utilizando as ferramentas de desenvolvimento do WCF](../Topic/Using%20the%20WCF%20Development%20Tools.md)|Discute como criar e testar os serviços WCF em [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].|  
|[How to: Add, Update, or Remove a Service Reference](../Topic/How%20to:%20Add,%20Update,%20or%20Remove%20a%20Service%20Reference.md)|Descreve como adicionar, atualizar ou remover serviços WCF de um projeto.|  
|[How to: Add, Update, or Remove a WCF Data Service Reference](../data-tools/how-to-add-update-or-remove-a-wcf-data-service-reference.md)|Descreve como referenciar e usar [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)] em [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].|  
|[Troubleshooting Service References](../data-tools/troubleshooting-service-references.md)|Apresenta alguns erros comuns que podem ocorrer com referências de serviço e como evitá\-los.|  
|[Depurando serviços WCF](../debugger/debugging-wcf-services.md)|Descreve problemas comuns de depuração e técnicas que você pode encontrar ao depurar serviços WCF.|  
|[Windows Communication Foundation Authentication Service Overview](../Topic/Windows%20Communication%20Foundation%20Authentication%20Service%20Overview.md)|Descreve como usar o WCF para fornecer um serviço de função para um site da Web.|  
|[Instruções passo a passo: criando um aplicativo de dados de N camadas](../data-tools/walkthrough-creating-an-n-tier-data-application.md)|Fornece instruções passo a passo para criar um dataset tipado e separar o código TableAdapter e conjunto de dados em vários projetos.|  
|[Configure Service Reference Dialog Box](../data-tools/configure-service-reference-dialog-box.md)|Descreve os elementos de interface do usuário da **Configure Service Reference** caixa de diálogo.|  
  
## Referência  
 <xref:System.ServiceModel>  
  
 <xref:System.Data.Services>  
  
## Consulte também  
 [Ferramentas de dados do Visual Studio para .NET](../data-tools/visual-studio-data-tools-for-dotnet.md)