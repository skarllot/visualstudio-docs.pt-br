---
title: "Como: usar o contexto de interface do usuário baseada em regras para extensões do Visual Studio | Documentos do Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8dd2cd1d-d8ba-49b9-870a-45acf3a3259d
caps.latest.revision: 7
ms.author: gregvanl
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 1ce891987975bba1dead1d94ada20ff914233e57
ms.lasthandoff: 02/22/2017

---
# <a name="how-to-use-rule-based-ui-context-for-visual-studio-extensions"></a>Como: usar o contexto de interface do usuário baseada em regras para extensões do Visual Studio
O Visual Studio permite o carregamento de VSPackages quando determinados conhecidos <xref:Microsoft.VisualStudio.Shell.UIContext>s são ativados.</xref:Microsoft.VisualStudio.Shell.UIContext> No entanto, nestes contextos de interface do usuário não são bastante refinado, não deixando os autores de extensão nenhuma opção, mas para selecionar um contexto de interface do usuário disponíveis que ativa antes do ponto realmente desejasse VSPackage para carregar. Para obter uma lista de contextos de interface de usuário bem conhecidos, consulte <xref:Microsoft.VisualStudio.Shell.KnownUIContexts>.</xref:Microsoft.VisualStudio.Shell.KnownUIContexts>  
  
 Carregar pacotes pode ter um impacto no desempenho e carregá-los antes que eles sejam necessários não é a prática recomendada. O Visual Studio 2015 introduziu o conceito de contextos da interface do usuário baseada em regras, um mecanismo que permite que os autores de extensão definir as condições precisas sob o qual um contexto de interface do usuário é ativado e carregados VSPackages associados.  
  
## <a name="rule-based-ui-context"></a>Contexto de interface do usuário baseada em regra  
 Uma "regra" consiste em um novo contexto de interface do usuário (GUID) e uma expressão booleana que faz referência a um ou mais "termos" combinado com lógica "e", "ou", "não" operações. "Termos" são avaliados dinamicamente em tempo de execução e a expressão é avaliada novamente sempre que qualquer uma de suas alterações de termos. Quando a expressão for avaliada como true, o contexto de interface do usuário associado é ativado. Caso contrário, o contexto de interface do usuário é desativado.  
  
 Contexto de interface de usuário baseada em regras pode ser usado em uma variedade de formas:  
  
1.  Especifica restrições de visibilidade para comandos e janelas de ferramenta. Você pode ocultar as janelas de ferramentas/comandos até que a regra de contexto da interface do usuário seja atendida.  
  
2.  Como auto carregar restrições: pacotes de carregamento automático somente quando a regra for atendida  
  
3.  Tarefa atrasada: atrasar o carregamento até que um intervalo especificado e a regra ainda seja atendida.  
  
 O mecanismo pode ser usado por qualquer extensão do Visual Studio.  
  
## <a name="create-a-rule-based-ui-context"></a>Criar um contexto de interface do usuário baseada em regra  
 Suponha que você tenha uma extensão chamada TestPackage, que oferece um comando de menu que se aplica somente a arquivos com extensão ". config". Antes de VS2015, a melhor opção era carregar TestPackage quando <xref:Microsoft.VisualStudio.Shell.KnownUIContexts.SolutionExistsAndFullyLoadedContext%2A>contexto de interface do usuário foi ativado.</xref:Microsoft.VisualStudio.Shell.KnownUIContexts.SolutionExistsAndFullyLoadedContext%2A> Isso não é eficiente, pois a solução carregada não pode conter até um arquivo. config. Vamos consulte como contexto de interface de usuário baseada em regras pode ser usado para ativar um contexto de interface do usuário somente quando um arquivo com extensão. config está selecionado e carregar TestPackage quando o contexto da interface do usuário é ativado.  
  
1.  Definir um novo GUID UIContext e adicionar a classe de VSPackage <xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute>e <xref:Microsoft.VisualStudio.Shell.ProvideUIContextRuleAttribute>.</xref:Microsoft.VisualStudio.Shell.ProvideUIContextRuleAttribute> </xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute>  
  
     Por exemplo, vamos supor que um novo UIContext "UIContextGuid" deve ser adicionado. O GUID criado (você pode criar um GUID clicando em ferramentas-> criar guid) é "8B40D5E2-5626-42AE-99EF-3DD1EFF46E7B". Você, em seguida, adicione o seguinte em sua classe de pacote:  
  
    ```c#  
    public const string UIContextGuid = "8B40D5E2-5626-42AE-99EF-3DD1EFF46E7B";  
    ```  
  
     Para os atributos, adicione o seguinte: (os detalhes desses atributos serão explicados posteriormente)  
  
    ```c#  
    [ProvideAutoLoad(TestPackage.UIContextGuid)]      
    [ProvideUIContextRule(TestPackage.UIContextGuid,  
        name: "Test auto load",   
        expression: "DotConfig",  
        termNames: new[] { "DotConfig" },  
        termValues: new[] { "HierSingleSelectionName:.config$" })]  
    ```  
  
     Esses metadados definem o novo GUID UIContext (8B40D5E2-5626-42AE-99EF-3DD1EFF46E7B) e uma expressão referindo-se a um único termo, "DotConfig". O termo "DotConfig" é avaliada como true, sempre que a seleção atual na hierarquia de ativo tem um nome que corresponda ao padrão da expressão regular "\\. config$" (termina com ". config"). O valor (padrão) define um nome opcional para a regra útil para depuração.  
  
     Os valores do atributo são adicionados ao pkgdef gerado durante o tempo de compilação posteriormente.  
  
2.  No arquivo VSCT para comandos do TestPackage, adicione o sinalizador "DynamicVisibility" para os comandos apropriados:  
  
    ```xml  
    <CommandFlag>DynamicVisibility</CommandFlag>  
    ```  
  
3.  Na seção Visibilidades o VSCT, ligar os comandos apropriados para o novo UIContext GUID definido em #1:  
  
    ```xml  
    <VisibilityConstraints>   
        <VisibilityItem guid="guidTestPackageCmdSet" id="TestId"  context="guidTestUIContext"/>   
    </VisibilityConstraints>  
    ```  
  
4.  Na seção símbolos, adicione a definição do UIContext:  
  
    ```xml  
    <GuidSymbol name="guidTestUIContext" value="{8B40D5E2-5626-42AE-99EF-3DD1EFF46E7B}" />  
    ```  
  
     Agora, os comandos de menu de contexto para arquivos Config ficará visíveis apenas quando o item selecionado no solution explorer é um arquivo de "config" e o pacote não será carregado até que um desses comandos é selecionado.  
  
 Em seguida, vamos usar um depurador para confirmar que o pacote carrega apenas quando é esperado. Para depurar TestPackage:  
  
1.  Definir um ponto de interrupção no <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A>método.</xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A>  
  
2.  Crie o TestPackage e iniciar a depuração.  
  
3.  Criar um projeto ou abrir um.  
  
4.  Selecione qualquer arquivo com uma extensão diferente. config. O ponto de interrupção não deve ser atingido.  
  
5.  Selecione o arquivo App. config.  
  
 O TestPackage carrega e para no ponto de interrupção.  
  
## <a name="adding-more-rules-for-ui-context"></a>Adicionar mais regras de contexto da interface do usuário  
 Como as regras de contexto da interface do usuário são expressões Boolianas, você pode adicionar mais restrito de regras para um contexto de interface do usuário. Por exemplo, no contexto da interface do usuário acima, você pode especificar que a regra se aplica somente quando uma solução com um projeto é carregada. Dessa forma, os comandos serão exibidos se você abrir um arquivo ". config" como um arquivo autônomo, e não como parte de um projeto.  
  
```c#  
[ProvideAutoLoad(TestPackage.UIContextGuid)]      
[ProvideUIContextRule(TestPackage.UIContextGuid,    
    name: "Test auto load",  
    expression: "(SingleProject | MultipleProjects) & DotConfig",    
    termNames: new[] { "SingleProject", "MultipleProjects","DotConfig" },     
    termValues: new[] { VSConstants.UICONTEXT_SolutionHasSingleProject_string , VSConstants.UICONTEXT_SolutionHasMultipleProjects_string , "HierSingleSelectionName:.config$" })]  
```  
  
 Agora a expressão fizer referência a três termos. Os primeiros dois termos, "SingleProject" e "MultipleProjects", consultem outros contextos de interface de usuário conhecida (pelas suas GUIDs). O terceiro termo, "DotConfig" é o contexto de interface de usuário baseada em regras definido anteriormente.  
  
## <a name="delayed-activation"></a>Ativação atrasada  
 Regras podem ter um "atraso" opcional. O atraso é especificado em milissegundos. Se estiver presente, o atraso faz com que a ativação ou desativação de contexto de interface de usuário da regra com esse intervalo de tempo de atraso. Se as alterações de regra de volta antes do intervalo de atraso, em seguida, nada acontece. Esse mecanismo pode ser usado para as etapas de inicialização - especialmente a inicialização única sem depender de temporizadores ou se registrar para notificações ociosas "balancear".  
  
 Por exemplo, você pode especificar a regra de carga de teste para ter um atraso de 100 milissegundos:  
  
```c#  
[ProvideAutoLoad(TestPackage.UIContextGuid)]  
[ProvideUIContextRule(TestPackage.UIContextGuid,   
    name: "Test auto load",  
    expression: "DotConfig",   
    termNames: new[] { "DotConfig" },  
    termValues: new[] { "HierSingleSelectionName:.config$" },   
    delay: 100)]  
```  
  
## <a name="term-types"></a>Tipos de termo  
 Aqui estão os vários tipos de termo que têm suporte:  
  
|||  
|-|-|  
|{nnnnnnnn-nnnn-nnnn-nnnn-nnnnnnnnnnnn}|O GUID se refere a um contexto de interface do usuário. O termo será verdadeiro sempre que o contexto da interface do usuário está ativo e FALSO caso contrário.|  
|HierSingleSelectionName:\<padrão >|O termo será verdadeiro sempre que a seleção na hierarquia de ativo é um único item e o nome do item selecionado corresponde à expressão regular do .net fornecida pelo "padrão".|  
|UserSettingsStoreQuery:\<consulta >|"consulta" representa um caminho completo para o armazenamento de configurações do usuário que deve ser avaliada como um valor diferente de zero. A consulta é dividida em uma "coleção" e "propertyName" em que a última barra.|  
|ConfigSettingsStoreQuery:\<consulta >|"consulta" representa um caminho completo para o armazenamento de configurações de configuração que deve ser avaliada como um valor diferente de zero. A consulta é dividida em uma "coleção" e "propertyName" em que a última barra.|  
|ActiveProjectFlavor:\<projectTypeGuid >|O termo será verdadeiro sempre que o projeto selecionado no momento é tipo (agregado) e tem um tipo correspondente ao tipo de projeto determinado GUID.|  
|ActiveEditorContentType:\<contentType >|O termo será verdadeiro quando o documento selecionado é um editor de texto com o tipo de conteúdo especificado.|  
|ActiveProjectCapability:\<expressão >|O termo é verdadeiro quando os recursos de projeto ativo corresponde à expressão fornecida. Uma expressão pode ser algo como VB | CSharp|  
|SolutionHasProjectCapability:\<expressão >|Semelhante ao anterior, mas termo é verdadeiro quando a solução tem qualquer projeto carregado que corresponde à expressão.|  
|SolutionHasProjectFlavor:\<projectTypeGuid >|O termo será verdadeiro sempre que uma solução tem projeto que é tipo (agregado) e tem um tipo correspondente ao tipo de projeto determinado GUID.|


  
## <a name="compatibility-with-cross-version-extension"></a>Compatibilidade com extensão entre versões  
 Regra baseados em contextos de interface do usuário é um recurso novo no Visual Studio 2015 e não deve ser portado para versões anteriores. Isso cria um problema com extensões/pacotes destinados a várias versões do Visual Studio que teria de ser carregados automaticamente no Visual Studio 2013 e versões anteriores, mas pode se beneficiar de contextos de interface do usuário com base em regra para impedir que sejam carregados automaticamente no Visual Studio 2015.  
  
 Para oferecer suporte a esses pacotes, AutoLoadPackages entradas no registro agora podem fornecer um sinalizador em seu campo de valor para indicar que a entrada deve ser ignorada no Visual Studio 2015 e acima. Isso pode ser feito pela adição de uma opção de sinalizadores para <xref:Microsoft.VisualStudio.Shell.PackageAutoLoadFlags>.</xref:Microsoft.VisualStudio.Shell.PackageAutoLoadFlags> Os VSPackages agora pode adicionar **SkipWhenUIContextRulesActive** opção para suas <xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute>atributo para indicar a entrada deve ser ignorada no Visual Studio 2015 e superior.</xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute>  
  
## <a name="extensible-ui-context-rules"></a>Regras de contexto da interface do usuário extensível  
 Às vezes, pacotes não podem usar regras de contexto de interface de usuário estáticas. Por exemplo, suponha que você tenha um pacote de extensibilidade de suporte, de modo que o estado do comando é baseado nos tipos de editor que são suportados por provedores MEF importados. O comando é habilitado se existe uma extensão com suporte o tipo de edição atual. Nesses casos o pacote propriamente dito não pode usar uma regra estática do contexto de interface do usuário, desde que os termos seriam alterados dependendo de qual MEF extensões estão disponíveis.  
  
 Para oferecer suporte a esses pacotes, contextos de interface do usuário com base em regra oferecer suporte a uma expressão codificada "*" que indica todos os termos abaixo será associado com ou. Isso permite que o pacote mestre definir uma regra conhecida com base em contexto de interface do usuário e vincular seu estado de comando para esse contexto. Depois qualquer extensão MEF direcionado para o pacote mestre pode adicionar seus termos para editores que ele oferece suporte sem afetar outros termos ou a expressão mestre.  
  
 O construtor <xref:Microsoft.VisualStudio.Shell.ProvideExtensibleUIContextRuleAttribute.%23ctor%2A>documentação mostra a sintaxe para regras de contexto da interface do usuário extensíveis.</xref:Microsoft.VisualStudio.Shell.ProvideExtensibleUIContextRuleAttribute.%23ctor%2A>
