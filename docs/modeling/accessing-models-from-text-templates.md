---
title: Acessando modelos a partir de modelos de texto | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- text templates, accessing models
ms.assetid: cf65395a-0ca3-4826-89c7-b1869562685c
caps.latest.revision: 33
author: alancameronwills
ms.author: awills
manager: douge
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: e76f9737ec4eafc5113cb2f07e43cb28abd7f787
ms.lasthandoff: 02/22/2017

---
# <a name="accessing-models-from-text-templates"></a>Acessando modelos a partir de modelos (templates) de texto
Usando modelos de texto, você pode criar arquivos de relatório, arquivos de código fonte e outros arquivos de texto baseados em modelos de linguagem específica do domínio. Para obter informações básicas sobre modelos de texto, consulte [de geração de código e modelos de texto T4](../modeling/code-generation-and-t4-text-templates.md). Os modelos de texto funcionarão no modo experimental quando você estiver depurando seu DSL e também funcionará em um computador em que você implantou a DSL.  
  
> [!NOTE]
>  Quando você cria uma solução DSL, o modelo de texto de exemplo ** \*. TT** arquivos são gerados no projeto de depuração. Quando você altera os nomes das classes de domínio, esses modelos deixarão de funcionar. No entanto, eles incluem as diretivas básicas que você precisa e fornecem exemplos que você pode atualizar para corresponder a DSL.  
  
 Para acessar um modelo de um modelo de texto:  
  
-   Defina a propriedade de herdar de diretiva do modelo para <xref:Microsoft.VisualStudio.TextTemplating.VSHost.ModelingTextTransformation>.</xref:Microsoft.VisualStudio.TextTemplating.VSHost.ModelingTextTransformation> Fornece acesso à loja.  
  
-   Especifica processadores de diretriz para a DSL que você deseja acessar. Isso carrega os assemblies da DSL para que você possa usar suas classes de domínio, propriedades e relações no código do modelo de texto. Ele também carrega o arquivo de modelo que você especificar.  
  
 A `.tt` arquivo semelhante ao exemplo a seguir é criado na depuração de projeto quando você cria um novo [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] solução do modelo de linguagem mínima de DSL.  
  
```  
<#@ template inherits="Microsoft.VisualStudio.TextTemplating.VSHost.ModelingTextTransformation" #>  
<#@ output extension=".txt" #>  
<#@ MyLanguage processor="MyLanguageDirectiveProcessor" requires="fileName='Sample.myDsl1'" #>  
  
This text will be output directly.  
  
This is the name of the model: <#= this.ModelRoot.Name #>  
  
Here is a list of elements in the model:  
<#  
  // When you change the DSL Definition, some of the code below may not work.  
  foreach (ExampleElement element in this.ExampleModel.Elements)  
  {#>  
<#= element.Name #>  
<#      
  }  
#>  
  
```  
  
 Observe os seguintes pontos sobre esse modelo:  
  
-   O modelo pode usar as classes de domínio, propriedades e relações que você definiu na definição de DSL.  
  
-   O modelo carrega o arquivo de modelo que você especificar na `requires` propriedade.  
  
-   Uma propriedade em `this` contém o elemento raiz. A partir daí, seu código pode navegar para outros elementos do modelo. O nome da propriedade normalmente é o mesmo que a classe de domínio raiz de sua DSL. Neste exemplo, é `this.ExampleModel`.  
  
-   Embora o idioma no qual os fragmentos de código são escritos for c#, você pode gerar o texto de qualquer tipo. Como alternativa você pode escrever o código em [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] adicionando a propriedade `language="VB"` para o `template` diretiva.  
  
-   Para depurar o modelo, adicione `debug="true"` para o `template` diretiva. O modelo será aberto em outra instância do [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] se ocorrer uma exceção. Se você quiser interromper o depurador em um ponto específico no código, a instrução insert`System.Diagnostics.Debugger.Break();`  
  
     Para obter mais informações, consulte [depurando um modelo de texto T4](../modeling/debugging-a-t4-text-template.md).  
  
## <a name="about-the-dsl-directive-processor"></a>Sobre o processador de diretriz DSL  
 O modelo pode usar as classes de domínio que você definiu em sua definição de DSL. Isso é colocado uma diretiva que geralmente aparece no início do modelo. No exemplo anterior, é a seguinte:  
  
```  
<#@ MyLanguage processor="MyLanguageDirectiveProcessor" requires="fileName='Sample.myDsl1'" #>  
```  
  
 O nome da diretiva ( `MyLanguage`, neste exemplo) é derivado do nome de sua DSL. Ele invoca um *processador de diretriz* que é gerado como parte de sua DSL. Você pode encontrar o seu código-fonte em **Dsl\GeneratedCode\DirectiveProcessor.cs**.  
  
 O processador de diretriz DSL executa duas tarefas principais:  
  
-   Ele insere efetivamente diretivas de assembly e importar para o modelo que faz referência a DSL. Isso permite que você use suas classes de domínio no código do modelo.  
  
-   Ele carrega o arquivo que você especificar na `requires` parâmetro e define uma propriedade `this` que se refere ao elemento raiz do modelo carregado.  
  
## <a name="validating-the-model-before-running-the-template"></a>Validação do modelo antes de executar o modelo  
 Você pode fazer com o modelo a ser validado antes do modelo é executado.  
  
```  
<#@ MyLanguage processor="MyLanguageDirectiveProcessor" requires="fileName='Sample.myDsl1';validation='open|load|save|menu'" #>  
  
```  
  
 Observe que:  
  
1.  O `filename` e `validation` os parâmetros são separados com ";" e não deve haver outros separadores ou espaços.  
  
2.  A lista de categorias de validação determina quais métodos de validação serão executados. Várias categorias devem ser separadas por "|" e não deve haver outros separadores ou espaços.  
  
 Se um erro for encontrado, ele será relatado na janela de erros e o arquivo de resultado irá conter uma mensagem de erro.  
  
##  <a name="a-namemultiplea-accessing-multiple-models-from-a-text-template"></a><a name="Multiple"></a>Acessar vários modelos de um modelo de texto  
  
> [!NOTE]
>  Esse método permite que você leia vários modelos no mesmo modelo, mas não dá suporte a referências do ModelBus. Para ler os modelos que estão interconectados por referências do ModelBus, consulte [usando o Visual Studio ModelBus em um modelo de texto](../modeling/using-visual-studio-modelbus-in-a-text-template.md).  
  
 Se você deseja acessar mais de um modelo a partir do mesmo modelo de texto, você deve chamar o processador de diretriz gerado uma vez para cada modelo. Você deve especificar o nome do arquivo de cada modelo de `requires` parâmetro. Você deve especificar os nomes que você deseja usar para a classe de domínio raiz no `provides` parâmetro. Você deve especificar valores diferentes para o `provides` parâmetros de cada uma das chamadas de diretiva. Por exemplo, suponha que você tenha três arquivos de modelo chamados Library.xyz, School.xyz e Work.xyz. Para acessá-los a partir do mesmo modelo de texto, você deve escrever três chamadas de diretiva que se assemelhem a páginas a seguir.  
  
```  
<#@ ExampleModel processor="<YourLanguageName>DirectiveProcessor" requires="fileName='Library.xyz'" provides="ExampleModel=LibraryModel" #>  
<#@ ExampleModel processor="<YourLanguageName>DirectiveProcessor" requires="fileName='School.xyz'" provides="ExampleModel=SchoolModel" #>  
<#@ ExampleModel processor="<YourLanguageName>DirectiveProcessor" requires="fileName='Work.xyz'" provides="ExampleModel=WorkModel" #>  
```  
  
> [!NOTE]
>  Esse código de exemplo é para um idioma que é baseado no modelo de solução de linguagem mínima.  
  
 Para acessar os modelos no modelo de texto, agora você pode escrever código semelhante ao código no exemplo a seguir.  
  
```c#  
<#  
foreach (ExampleElement element in this.LibraryModel.Elements)  
...  
foreach (ExampleElement element in this.SchoolModel.Elements)  
...  
foreach (ExampleElement element in this.WorkModel.Elements)  
...  
#>  
```  
  
```vb#  
<#  
For Each element As ExampleElement In Me.LibraryModel.Elements  
...  
For Each element As ExampleElement In Me.SchoolModel.Elements  
...  
For Each element As ExampleElement In Me.WorkModel.Elements  
...  
#>  
```  
  
## <a name="loading-models-dynamically"></a>Carregando modelos dinamicamente  
 Se você quiser determinar em tempo de execução que modelos para carregar, você pode carregar um arquivo de modelo dinamicamente no código do programa, em vez de usar a diretiva de DSL específico.  
  
 No entanto, uma das funções da diretiva específica DSL é importar o namespace DSL, para que o código de modelo pode usar as classes de domínio definidas dessa DSL. Porque você não estiver usando a diretiva, você deve adicionar ** \<assembly >** e ** \<importar >** diretivas para todos os modelos que você pode carregar. Isso é fácil se os modelos diferentes que você pode carregar todas as instâncias da mesma DSL.  
  
 Para carregar o arquivo, o método mais eficiente é usar [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ModelBus. Em um cenário típico, o modelo de texto usará uma diretiva específica de DSL para carregar o primeiro modelo como de costume. Esse modelo conteria referências do ModelBus para outro modelo. Você pode usar o ModelBus para abrir o modelo de referência e acessar um elemento específico. Para obter mais informações, consulte [usando o Visual Studio ModelBus em um modelo de texto](../modeling/using-visual-studio-modelbus-in-a-text-template.md).  
  
 Em um cenário menos comum, você talvez queira abrir um arquivo de modelo para os quais você tem apenas um nome de arquivo, e que talvez não seja no atual [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] projeto. Nesse caso, você pode abrir o arquivo usando a técnica descrita no [como: abrir um modelo de arquivo no código do programa](../modeling/how-to-open-a-model-from-file-in-program-code.md).  
  
## <a name="generating-multiple-files-from-a-template"></a>Gerar vários arquivos de um modelo  
 Se você quiser gerar um vários arquivos – por exemplo, para gerar um arquivo separado para cada elemento em um modelo, há várias abordagens possíveis. Por padrão, somente um arquivo é produzido de cada arquivo de modelo.  
  
### <a name="splitting-a-long-file"></a>Dividindo um arquivo longo  
 Nesse método, você pode usar um modelo para gerar um único arquivo, separado por um delimitador. Em seguida, dividir o arquivo em suas partes. Há dois modelos, primeiro para gerar o arquivo único e o outro para dividi-la.  
  
 **LoopTemplate.t4** gera o único arquivo longo. Observe que a extensão do arquivo é ".t4", porque ele não deve ser processado diretamente quando você clica em **transformar todos os modelos**. Este modelo utiliza um parâmetro que especifica a cadeia de caracteres do delimitador que separa os segmentos:  
  
```  
<#@ template ninherits="Microsoft.VisualStudio.TextTemplating.VSHost.ModelingTextTransformation" #>  
<#@ parameter name="delimiter" type="System.String" #>  
<#@ output extension=".txt" #>  
<#@ MyDSL processor="MyDSLDirectiveProcessor" requires="fileName='SampleModel.mydsl1';validation='open|load|save|menu'" #>  
<#  
  // Create a file segment for each element:  
  foreach (ExampleElement element in this.ExampleModel.Elements)   
  {   
    // First item is the delimiter:  
#>  
<#= string.Format(delimiter, element.Id) #>  
  
   Element: <#= element.Name #>  
<#  
   // Here you generate more content derived from the element.  
  }  
#>  
  
```  
  
 `LoopSplitter.tt`chama `LoopTemplate.t4`e, em seguida, divide o arquivo resultante em seus segmentos. Observe que esse modelo não tem um modelo de modelagem, porque ela não ler o modelo.  
  
```  
<#@ template hostspecific="true" language="C#" #>  
<#@ output extension=".txt" #>  
<#@ import namespace="Microsoft.VisualStudio.TextTemplating" #>  
<#@ import namespace="System.Runtime.Remoting.Messaging" #>  
<#@ import namespace="System.IO" #>  
  
<#  
  // Get the local path:  
  string itemTemplatePath = this.Host.ResolvePath("LoopTemplate.t4");  
  string dir = Path.GetDirectoryName(itemTemplatePath);  
  
  // Get the template for generating each file:  
  string loopTemplate = File.ReadAllText(itemTemplatePath);  
  
  Engine engine = new Engine();  
  
  // Pass parameter to new template:  
  string delimiterGuid = Guid.NewGuid().ToString();  
  string delimiter = "::::" + delimiterGuid + ":::";  
  CallContext.LogicalSetData("delimiter", delimiter + "{0}:::");   
  string joinedFiles = engine.ProcessTemplate(loopTemplate, this.Host);  
  
  string [] separateFiles = joinedFiles.Split(new string [] {delimiter}, StringSplitOptions.None);  
  
  foreach (string nameAndFile in separateFiles)   
  {   
     if (string.IsNullOrWhiteSpace(nameAndFile)) continue;  
     string[] parts = nameAndFile.Split(new string[]{":::"}, 2, StringSplitOptions.None);  
     if (parts.Length < 2) continue;  
#>  
 Generate: [<#= dir #>] [<#= parts[0] #>]  
<#  
     // Generate a file from this item:  
     File.WriteAllText(Path.Combine(dir, parts[0] + ".txt"), parts[1]);    
  }  
#>  
  
```
