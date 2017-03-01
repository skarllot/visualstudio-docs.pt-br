---
title: "Serviço de linguagem e pontos de extensão de Editor | Documentos do Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], new - extension points
ms.assetid: 91a6417e-a6fe-4bc2-9d9f-5173c634a99b
caps.latest.revision: 33
ms.author: gregvanl
manager: ghogen
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
ms.openlocfilehash: 8ff5f5f0ae5ac339f093fd1e2e7a86c30e415eea
ms.lasthandoff: 02/22/2017

---
# <a name="language-service-and-editor-extension-points"></a>Serviço de linguagem e pontos de extensão de Editor
O editor fornece pontos de extensão que você pode estender como partes do componente Managed Extensibility Framework (MEF), incluindo a maioria dos recursos de serviço de linguagem. Estas são as categorias de ponto de extensão principal:  
  
-   Tipos de conteúdo  
  
-   Tipos de classificação e formatos de classificação  
  
-   Margens e barras de rolagem  
  
-   Marcas  
  
-   Adornos  
  
-   Processadores de mouse  
  
-   Manipuladores de soltar  
  
-   Opções  
  
-   IntelliSense  
  
## <a name="extending-content-types"></a>Estendendo tipos de conteúdo  
 Tipos de conteúdo são as definições dos tipos de texto tratado pelo editor, por exemplo, "text", "código" ou "CSharp". Definir um novo tipo de conteúdo, declarando uma variável do tipo <xref:Microsoft.VisualStudio.Utilities.ContentTypeDefinition>e dando um nome exclusivo de novo tipo de conteúdo.</xref:Microsoft.VisualStudio.Utilities.ContentTypeDefinition> Para registrar o tipo de conteúdo com o editor, exportá-lo junto com os seguintes atributos:  
  
-   <xref:Microsoft.VisualStudio.Utilities.NameAttribute>é o nome do tipo de conteúdo.</xref:Microsoft.VisualStudio.Utilities.NameAttribute>  
  
-   <xref:Microsoft.VisualStudio.Utilities.BaseDefinitionAttribute>é o nome do tipo de conteúdo do qual esse tipo de conteúdo é derivado.</xref:Microsoft.VisualStudio.Utilities.BaseDefinitionAttribute> Um tipo de conteúdo pode herdar de vários outros tipos de conteúdo.  
  
 Porque o <xref:Microsoft.VisualStudio.Utilities.ContentTypeDefinition>classe é fechada, você pode exportá-lo sem nenhum parâmetro de tipo.</xref:Microsoft.VisualStudio.Utilities.ContentTypeDefinition>  
  
 O exemplo a seguir mostra os atributos de exportação em uma definição de tipo de conteúdo.  
  
```  
[Export]  
[Name("test")]  
[BaseDefinition("code")]  
[BaseDefinition("projection")]  
internal static ContentTypeDefinition TestContentTypeDefinition;  
```  
  
 Tipos de conteúdo podem ser baseados em zero ou mais tipos de conteúdo já existentes. Estes são os tipos internos:  
  
-   Qualquer: o tipo de conteúdo básico. Pai de todos os outros tipos de conteúdo.  
  
-   Texto: o tipo básico para projeção sem conteúdo. Herda de "qualquer".  
  
-   Texto sem formatação: para texto sem código. Herda de "text".  
  
-   Código: código de todos os tipos. Herda de "text".  
  
-   Inerte: exclui o texto de qualquer tipo de tratamento. Texto desse tipo de conteúdo nunca terá qualquer extensão aplicado a ele.  
  
-   Projeção: para o conteúdo dos buffers de projeção. Herda de "qualquer".  
  
-   IntelliSense: para o conteúdo do IntelliSense. Herda de "text".  
  
-   Sighelp: Ajuda da assinatura. Herda do "intellisense".  
  
-   Sighelp-doc: documentação de ajuda assinatura. Herda do "intellisense".  
  
 Estes são alguns dos tipos de conteúdo são definidos pelo Visual Studio e alguns dos idiomas que são hospedados no Visual Studio:  
  
-   Basic  
  
-   C/C++  
  
-   ConsoleOutput  
  
-   CSharp  
  
-   CSS  
  
-   ENC  
  
-   FindResults  
  
-   F#  
  
-   HTML  
  
-   JScript  
  
-   XAML  
  
-   XML  
  
 Para descobrir a lista de tipos de conteúdo disponíveis, importe o <xref:Microsoft.VisualStudio.Utilities.IContentTypeRegistryService>, que mantém a coleção de tipos de conteúdo para o editor.</xref:Microsoft.VisualStudio.Utilities.IContentTypeRegistryService> O código a seguir importa esse serviço como uma propriedade.  
  
```  
[Import]  
internal IContentTypeRegistryService ContentTypeRegistryService { get; set; }  
```  
  
 Para associar um tipo de conteúdo com uma extensão de nome de arquivo, use <xref:Microsoft.VisualStudio.Utilities.FileExtensionToContentTypeDefinition>.</xref:Microsoft.VisualStudio.Utilities.FileExtensionToContentTypeDefinition>  
  
> [!NOTE]
>  No Visual Studio, as extensões de nome de arquivo são registradas usando o <xref:Microsoft.VisualStudio.Shell.ProvideLanguageExtensionAttribute>em um pacote de serviço de linguagem.</xref:Microsoft.VisualStudio.Shell.ProvideLanguageExtensionAttribute> O <xref:Microsoft.VisualStudio.Utilities.FileExtensionToContentTypeDefinition>associa um tipo de conteúdo de MEF com uma extensão de nome de arquivo que foi registrada dessa maneira.</xref:Microsoft.VisualStudio.Utilities.FileExtensionToContentTypeDefinition>  
  
 Para exportar a extensão de nome de arquivo para a definição de tipo de conteúdo, você deve incluir os seguintes atributos:  
  
-   <xref:Microsoft.VisualStudio.Utilities.FileExtensionAttribute>: Especifica a extensão de nome de arquivo.</xref:Microsoft.VisualStudio.Utilities.FileExtensionAttribute>  
  
-   <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>: Especifica o tipo de conteúdo.</xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>  
  
 Porque o <xref:Microsoft.VisualStudio.Utilities.FileExtensionToContentTypeDefinition>classe é fechada, você pode exportá-lo sem nenhum parâmetro de tipo.</xref:Microsoft.VisualStudio.Utilities.FileExtensionToContentTypeDefinition>  
  
 O exemplo a seguir mostra os atributos de exportação em uma extensão de nome de arquivo a uma definição de tipo de conteúdo.  
  
```  
[Export]  
[FileExtension(".test")]  
[ContentType("test")]  
internal static FileExtensionToContentTypeDefinition TestFileExtensionDefinition;  
```  
  
 O <xref:Microsoft.VisualStudio.Utilities.IFileExtensionRegistryService>gerencia as associações entre extensões de nome de arquivo e tipos de conteúdo.</xref:Microsoft.VisualStudio.Utilities.IFileExtensionRegistryService>  
  
## <a name="extending-classification-types-and-classification-formats"></a>Estender tipos de classificação e classificação formatos  
 Você pode usar tipos de classificação para definir os tipos de texto para o qual você deseja fornecer tratamento diferente (por exemplo, a cor do texto de "palavra-chave" azul e o texto "comentário" verde). Definir um novo tipo de classificação, declarando uma variável do tipo <xref:Microsoft.VisualStudio.Text.Classification.ClassificationTypeDefinition>e dando a ele um nome exclusivo.</xref:Microsoft.VisualStudio.Text.Classification.ClassificationTypeDefinition>  
  
 Para registrar o tipo de classificação com o editor, exportá-lo junto com os seguintes atributos:  
  
-   <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: o nome do tipo de classificação.</xref:Microsoft.VisualStudio.Utilities.NameAttribute>  
  
-   <xref:Microsoft.VisualStudio.Utilities.BaseDefinitionAttribute>: o nome do tipo do qual herda esse tipo de classificação.</xref:Microsoft.VisualStudio.Utilities.BaseDefinitionAttribute> Todos os tipos de classificação herdarem de "text", e um tipo de classificação pode herdar de vários outros tipos de classificação.  
  
 Porque o <xref:Microsoft.VisualStudio.Text.Classification.ClassificationTypeDefinition>classe é fechada, você pode exportá-lo sem nenhum parâmetro de tipo.</xref:Microsoft.VisualStudio.Text.Classification.ClassificationTypeDefinition>  
  
 O exemplo a seguir mostra os atributos de exportação em uma definição de tipo de classificação.  
  
```  
[Export]  
[Name("csharp.test")]  
[BaseDefinition("test")]  
internal static ClassificationTypeDefinition CSharpTestDefinition;  
```  
  
 O <xref:Microsoft.VisualStudio.Language.StandardClassification.IStandardClassificationService>fornece acesso às classificações padrão.</xref:Microsoft.VisualStudio.Language.StandardClassification.IStandardClassificationService> Tipos de classificação internas incluem:  
  
-   "texto"  
  
-   "idioma natural" (derivado de "text")  
  
-   "linguagem formal" (derivado de "text")  
  
-   "string" (derivado de "literal")  
  
-   "caractere" (derivado de "literal")  
  
-   "numérica" (derivado de "literal")  
  
 Um conjunto de tipos de erro diferente de herdar de <xref:Microsoft.VisualStudio.Text.Adornments.ErrorTypeDefinition>.</xref:Microsoft.VisualStudio.Text.Adornments.ErrorTypeDefinition> Eles incluem os seguintes tipos de erro:  
  
-   "Erro de sintaxe"  
  
-   "Erro do compilador"  
  
-   "outro erro"  
  
-   "aviso"  
  
 Para descobrir a lista de tipos de classificação disponíveis, importe o <xref:Microsoft.VisualStudio.Text.Classification.IClassificationTypeRegistryService>, que mantém a coleção de tipos de classificação para o editor.</xref:Microsoft.VisualStudio.Text.Classification.IClassificationTypeRegistryService> O código a seguir importa esse serviço como uma propriedade.  
  
```  
[Import]  
internal IClassificationTypeRegistryService ClassificationTypeRegistryService { get; set; }  
```  
  
 Você pode definir uma definição de formato de classificação para o novo tipo de classificação. Derivar uma classe de <xref:Microsoft.VisualStudio.Text.Classification.ClassificationFormatDefinition>e exportá-lo com o tipo <xref:Microsoft.VisualStudio.Text.Classification.EditorFormatDefinition>, juntamente com os seguintes atributos:</xref:Microsoft.VisualStudio.Text.Classification.EditorFormatDefinition> </xref:Microsoft.VisualStudio.Text.Classification.ClassificationFormatDefinition>  
  
-   <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: o nome do formato.</xref:Microsoft.VisualStudio.Utilities.NameAttribute>  
  
-   <xref:Microsoft.VisualStudio.Utilities.DisplayNameAttribute>: o nome de exibição do formato.</xref:Microsoft.VisualStudio.Utilities.DisplayNameAttribute>  
  
-   <xref:Microsoft.VisualStudio.Text.Classification.UserVisibleAttribute>: Especifica se o formato é exibida no **fontes e cores** página do **opções** caixa de diálogo.</xref:Microsoft.VisualStudio.Text.Classification.UserVisibleAttribute>  
  
-   <xref:Microsoft.VisualStudio.Utilities.OrderAttribute>: a prioridade do formato.</xref:Microsoft.VisualStudio.Utilities.OrderAttribute> Os valores válidos são de <xref:Microsoft.VisualStudio.Text.Classification.Priority>.</xref:Microsoft.VisualStudio.Text.Classification.Priority>  
  
-   <xref:Microsoft.VisualStudio.Text.Classification.ClassificationTypeAttribute>: o nome da classificação de tipo ao qual esse formato é mapeado.</xref:Microsoft.VisualStudio.Text.Classification.ClassificationTypeAttribute>  
  
 O exemplo a seguir mostra os atributos de exportação em uma definição de formato de classificação.  
  
```  
[Export(typeof(EditorFormatDefinition))]  
[ClassificationType(ClassificationTypeNames = "test")]  
[Name("test")]  
[DisplayName("Test")]  
[UserVisible(true)]  
[Order(After = Priority.Default, Before = Priority.High)]  
internal sealed class TestFormat : ClassificationFormatDefinition  
```  
  
 Para descobrir a lista de formatos disponíveis, importe o <xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMapService>, que mantém a coleção de formatos para o editor.</xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMapService> O código a seguir importa esse serviço como uma propriedade.  
  
```  
[Import]  
internal IEditorFormatMapService FormatMapService { get; set; }  
```  
  
## <a name="extending-margins-and-scrollbars"></a>Estendendo margens e barras de rolagem  
 Margens e barras de rolagem são os elementos de exibição principal do editor, além da exibição de texto. Você pode fornecer qualquer número de margens além das margens padrão que aparecem em torno a exibição de texto.  
  
 Implementar um <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewMargin>interface para definir uma margem.</xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewMargin> Você também deve implementar o <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewMarginProvider>interface para criar a margem.</xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewMarginProvider>  
  
 Para registrar o provedor de margem com o editor, você deve exportar o provedor junto com os seguintes atributos:  
  
-   <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: o nome da margem.</xref:Microsoft.VisualStudio.Utilities.NameAttribute>  
  
-   <xref:Microsoft.VisualStudio.Utilities.OrderAttribute>: a ordem em que a margem é exibido, em relação as outras margens.</xref:Microsoft.VisualStudio.Utilities.OrderAttribute>  
  
     Estas são as margens internas:  
  
    -   "Barra de rolagem Horizontal do Wpf"  
  
    -   "Barra de rolagem Vertical do Wpf"  
  
    -   "Wpf linha número margem"  
  
     Margens horizontais que têm um atributo de ordem de `After="Wpf Horizontal Scrollbar"` são exibidos abaixo da margem interna e margens horizontais que têm um atributo de ordem de `Before ="Wpf Horizontal Scrollbar"` são exibidos acima da margem interna. Direita verticais margens que têm um atributo de ordem de `After="Wpf Vertical Scrollbar"` são exibidas à direita da barra de rolagem. Esquerda verticais margens que têm um atributo de ordem de `After="Wpf Line Number Margin"` aparecem à esquerda da margem de número de linha (se estiver visível).  
  
-   <xref:Microsoft.VisualStudio.Text.Editor.MarginContainerAttribute>: o tipo de margem (esquerda, direita, superior ou inferior).</xref:Microsoft.VisualStudio.Text.Editor.MarginContainerAttribute>  
  
-   <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>: o tipo de conteúdo (por exemplo, "text" ou "código") para o qual a margem é válida.</xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>  
  
 O exemplo a seguir mostra os atributos de exportação em um provedor de margem para a margem aparece à direita da margem de número de linha.  
  
```  
[Export(typeof(IWpfTextViewMarginProvider))]  
[Name("TestMargin")]  
[Order(Before = "Wpf Line Number Margin")]  
[MarginContainer(PredefinedMarginNames.Left)]  
[ContentType("text")]   
```  
  
## <a name="extending-tags"></a>Estendendo marcas  
 Marcas são uma maneira de associar dados com diferentes tipos de texto. Em muitos casos, os dados associados são exibidos como um efeito visual, mas não todas as marcas possuem uma apresentação visual. Você pode definir seu próprio tipo de marca implementando <xref:Microsoft.VisualStudio.Text.Tagging.ITag>.</xref:Microsoft.VisualStudio.Text.Tagging.ITag> Você também deve implementar <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601>para fornecer as marcas de um determinado conjunto de intervalos de texto e um <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider>para fornecer o marcador.</xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider> </xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> Você deve exportar o provedor de marcador junto com os seguintes atributos:  
  
-   <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>: o tipo de conteúdo (por exemplo, "text" ou "código") para o qual a sua marca é válida.</xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>  
  
-   <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute>: o tipo de marca.</xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute>  
  
 O exemplo a seguir mostra os atributos de exportação em um provedor de marcador.  
  
<CodeContentPlaceHolder>8</CodeContentPlaceHolder>  
 Os seguintes tipos de marca são internos:  
  
-   <xref:Microsoft.VisualStudio.Text.Tagging.ClassificationTag>: associado a um <xref:Microsoft.VisualStudio.Text.Classification.IClassificationType>.</xref:Microsoft.VisualStudio.Text.Classification.IClassificationType></xref:Microsoft.VisualStudio.Text.Tagging.ClassificationTag>  
  
-   <xref:Microsoft.VisualStudio.Text.Tagging.ErrorTag>: associadas a tipos de erro.</xref:Microsoft.VisualStudio.Text.Tagging.ErrorTag>  
  
-   <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>: associado um adorno.</xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>  
  
    > [!NOTE]
    >  Para obter um exemplo de um <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>, consulte a definição de HighlightWordTag na [passo a passo: texto realçando](../extensibility/walkthrough-highlighting-text.md).</xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>  
  
-   <xref:Microsoft.VisualStudio.Text.Tagging.OutliningRegionTag>: associadas a regiões que podem ser expandidos ou recolhidos na estrutura de tópicos.</xref:Microsoft.VisualStudio.Text.Tagging.OutliningRegionTag>  
  
-   <xref:Microsoft.VisualStudio.Text.Tagging.SpaceNegotiatingAdornmentTag>: define o espaço que ocupa um adorno em um modo de exibição de texto.</xref:Microsoft.VisualStudio.Text.Tagging.SpaceNegotiatingAdornmentTag> Para obter mais informações sobre negociação espaço ornamentos, consulte a seção a seguir.  
  
-   <xref:Microsoft.VisualStudio.Text.Editor.IntraTextAdornmentTag>: fornece espaçamento automático e dimensionamento para o adorno.</xref:Microsoft.VisualStudio.Text.Editor.IntraTextAdornmentTag>  
  
 Para localizar e usar marcas para buffers e modos de exibição, importe o <xref:Microsoft.VisualStudio.Text.Tagging.IViewTagAggregatorFactoryService>ou o <xref:Microsoft.VisualStudio.Text.Tagging.IBufferTagAggregatorFactoryService>, que oferecem um <xref:Microsoft.VisualStudio.Text.Tagging.ITagAggregator%601>do tipo solicitado.</xref:Microsoft.VisualStudio.Text.Tagging.ITagAggregator%601> </xref:Microsoft.VisualStudio.Text.Tagging.IBufferTagAggregatorFactoryService> </xref:Microsoft.VisualStudio.Text.Tagging.IViewTagAggregatorFactoryService> O código a seguir importa esse serviço como uma propriedade.  
  
```  
[Import]  
internal IViewTagAggregatorFactoryService ViewTagAggregatorFactoryService { get; set; }  
```  
  
#### <a name="tags-and-markerformatdefinitions"></a>Marcas e MarkerFormatDefinitions  
 Você pode estender o <xref:Microsoft.VisualStudio.Text.Classification.MarkerFormatDefinition>classe para definir a aparência de uma marca.</xref:Microsoft.VisualStudio.Text.Classification.MarkerFormatDefinition> Você deve exportar a classe (como uma <xref:Microsoft.VisualStudio.Text.Classification.EditorFormatDefinition>) com os seguintes atributos:</xref:Microsoft.VisualStudio.Text.Classification.EditorFormatDefinition>  
  
-   <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: o nome usado para fazer referência a esse formato</xref:Microsoft.VisualStudio.Utilities.NameAttribute>  
  
-   <xref:Microsoft.VisualStudio.Text.Classification.UserVisibleAttribute>: isso faz com que o formato seja exibido na interface do usuário</xref:Microsoft.VisualStudio.Text.Classification.UserVisibleAttribute>  
  
 No construtor, você pode definir o nome de exibição e a aparência da marca. <xref:Microsoft.VisualStudio.Text.Classification.EditorFormatDefinition.BackgroundColor%2A>Define a cor de preenchimento, e <xref:Microsoft.VisualStudio.Text.Classification.EditorFormatDefinition.ForegroundColor%2A>define a cor da borda.</xref:Microsoft.VisualStudio.Text.Classification.EditorFormatDefinition.ForegroundColor%2A></xref:Microsoft.VisualStudio.Text.Classification.EditorFormatDefinition.BackgroundColor%2A> O <xref:Microsoft.VisualStudio.Text.Classification.EditorFormatDefinition.DisplayName%2A>é o nome localizável da definição de formato.</xref:Microsoft.VisualStudio.Text.Classification.EditorFormatDefinition.DisplayName%2A>  
  
 Este é um exemplo de uma definição de formato:  
  
```  
[Export(typeof(EditorFormatDefinition))]  
[Name("MarkerFormatDefinition/HighlightWordFormatDefinition")]  
[UserVisible(true)]  
internal class HighlightWordFormatDefinition : MarkerFormatDefinition  
{  
    public HighlightWordFormatDefinition()  
    {  
        this.BackgroundColor = Colors.LightBlue;  
        this.ForegroundColor = Colors.DarkBlue;  
        this.DisplayName = "Highlight Word";   
        this.ZOrder = 5;  
    }  
}  
  
```  
  
 Para aplicar essa definição de formato a uma marca, fazer referência ao nome definido no atributo nome da classe (não o nome de exibição).  
  
> [!NOTE]
>  Para obter um exemplo de um <xref:Microsoft.VisualStudio.Text.Classification.MarkerFormatDefinition>, consulte a classe HighlightWordFormatDefinition na [passo a passo: texto realçando](../extensibility/walkthrough-highlighting-text.md).</xref:Microsoft.VisualStudio.Text.Classification.MarkerFormatDefinition>  
  
## <a name="extending-adornments"></a>Estendendo adornos  
 Adornos definem efeitos visuais que podem ser adicionados ao texto que é exibido em uma exibição de texto ou para o texto de exibição em si. Você pode definir seu próprios adorno como qualquer tipo de <xref:System.Windows.UIElement>.</xref:System.Windows.UIElement>  
  
 Em sua classe de adorno, você deve declarar um <xref:Microsoft.VisualStudio.Text.Editor.AdornmentLayerDefinition>.</xref:Microsoft.VisualStudio.Text.Editor.AdornmentLayerDefinition> Para registrar sua camada de adorno, exportá-lo junto com os seguintes atributos:  
  
-   <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: o nome do adorno.</xref:Microsoft.VisualStudio.Utilities.NameAttribute>  
  
-   <xref:Microsoft.VisualStudio.Utilities.OrderAttribute>: a ordenação de adorno em relação a outras camadas de adorno.</xref:Microsoft.VisualStudio.Utilities.OrderAttribute> A classe <xref:Microsoft.VisualStudio.Text.Editor.PredefinedAdornmentLayers>define quatro camadas padrão: seleção, estrutura de tópicos, cursor e texto.</xref:Microsoft.VisualStudio.Text.Editor.PredefinedAdornmentLayers>  
  
 O exemplo a seguir mostra os atributos de exportação em uma definição de camada de adorno.  
  
```  
[Export]  
[Name("TestEmbeddedAdornment")]  
[Order(After = PredefinedAdornmentLayers.Selection, Before = PredefinedAdornmentLayers.Text)]  
internal AdornmentLayerDefinition testLayerDefinition;  
```  
  
 Você deve criar uma segunda classe que implemente <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener>e trata sua <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener.TextViewCreated%2A>evento instanciando o adorno.</xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener.TextViewCreated%2A> </xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener> Você deve exportar essa classe junto com os seguintes atributos:  
  
-   <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>: o tipo de conteúdo (por exemplo, "text" ou "código") para o qual o adorno é válido.</xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>  
  
-   <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute>: o tipo de exibição de texto para o qual este adorno é válido.</xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute> A classe <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles>tem o conjunto de funções de exibição de texto predefinido.</xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles> Por exemplo, <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Document>é usado principalmente para modos de exibição de texto dos arquivos.</xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Document> <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Interactive>é usado para modos de exibição de texto que um usuário pode editar ou navegar usando um mouse e teclado.</xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Interactive> Exemplos de <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Interactive>modos de exibição são o modo de exibição de texto do editor e o **saída** janela.</xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Interactive>  
  
 O exemplo a seguir mostra os atributos de exportação no provedor de adorno.  
  
```  
[Export(typeof(IWpfTextViewCreationListener))]  
[ContentType("csharp")]  
[TextViewRole(PredefinedTextViewRoles.Document)]  
internal sealed class TestAdornmentProvider : IWpfTextViewCreationListener  
```  
  
 Um adorno de negociação de espaço é aquele que ocupam espaço no mesmo nível como o texto. Para criar esse tipo de adorno, você deve definir uma classe de marca que herda de <xref:Microsoft.VisualStudio.Text.Tagging.SpaceNegotiatingAdornmentTag>, que define a quantidade de espaço que ocupa o adorno.</xref:Microsoft.VisualStudio.Text.Tagging.SpaceNegotiatingAdornmentTag>  
  
 Assim como acontece com todos os adornos, você deve exportar a definição da camada de adorno.  
  
```  
[Export]  
[Name("TestAdornment")]  
[Order(After = DefaultAdornmentLayers.Text)]  
internal AdornmentLayerDefinition testAdornmentLayer;  
```  
  
 Para instanciar o adorno de negociação de espaço, você deve criar uma classe que implementa <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider>, além da classe que implementa <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener>(assim como acontece com outros tipos de adornos).</xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener> </xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider>  
  
 Para registrar o provedor de marcador, você deve exportá-lo junto com os seguintes atributos:  
  
-   <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>: o tipo de conteúdo (por exemplo, "text" ou "código") para o qual o adorno é válido.</xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>  
  
-   <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute>: o tipo de exibição de texto para o qual o tag ou um adorno é válido.</xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute> A classe <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles>tem o conjunto de funções de exibição de texto predefinido.</xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles> Por exemplo, <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Document>é usado principalmente para modos de exibição de texto dos arquivos.</xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Document> <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Interactive>é usado para modos de exibição de texto que um usuário pode editar ou navegar usando um mouse e teclado.</xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Interactive> Exemplos de <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Interactive>modos de exibição são o modo de exibição de texto do editor e o **saída** janela.</xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Interactive>  
  
-   <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute>: o tipo de marca ou adorno que você definiu.</xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute> Você deve adicionar um segundo <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute>para <xref:Microsoft.VisualStudio.Text.Tagging.SpaceNegotiatingAdornmentTag>.</xref:Microsoft.VisualStudio.Text.Tagging.SpaceNegotiatingAdornmentTag> </xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute>  
  
 O exemplo a seguir mostra os atributos de exportação no provedor de marcador para uma marca de adorno negociar espaço.  
  
```  
[Export(typeof(ITaggerProvider))]  
[ContentType("text")]  
[TextViewRole(PredefinedTextViewRoles.Document)]  
[TagType(typeof(SpaceNegotiatingAdornmentTag))]  
[TagType(typeof(TestSpaceNegotiatingTag))]  
internal sealed class TestTaggerProvider : ITaggerProvider  
```  
  
## <a name="extending-mouse-processors"></a>Estendendo o Mouse processadores  
 Você pode adicionar tratamento especial para entrada do mouse. Crie uma classe que herda de <xref:Microsoft.VisualStudio.Text.Editor.MouseProcessorBase>e substituir os eventos de mouse para a entrada que você deseja manipular.</xref:Microsoft.VisualStudio.Text.Editor.MouseProcessorBase> Você também deve implementar <xref:Microsoft.VisualStudio.Text.Editor.IMouseProcessorProvider>em uma segunda classe e exportá-lo junto com o <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>que especifica o tipo de conteúdo (por exemplo, "text" ou "código") para o qual o manipulador de mouse é válido.</xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> </xref:Microsoft.VisualStudio.Text.Editor.IMouseProcessorProvider>  
  
 O exemplo a seguir mostra os atributos de exportação em um provedor de processador de mouse.  
  
```  
[Export(typeof(IMouseProcessorProvider))]  
[Name("test mouse processor")]  
[ContentType("text")]  
[TextViewRole(PredefinedTextViewRoles.Interactive)]   
internal sealed class TestMouseProcessorProvider : IMouseProcessorProvider  
```  
  
## <a name="extending-drop-handlers"></a>Estendendo os manipuladores de soltar  
 Você pode personalizar o comportamento de manipuladores de soltar para tipos específicos de texto, criando uma classe que implementa <xref:Microsoft.VisualStudio.Text.Editor.DragDrop.IDropHandler>e uma segunda classe que implementa <xref:Microsoft.VisualStudio.Text.Editor.DragDrop.IDropHandlerProvider>para criar o manipulador de recebimento.</xref:Microsoft.VisualStudio.Text.Editor.DragDrop.IDropHandlerProvider> </xref:Microsoft.VisualStudio.Text.Editor.DragDrop.IDropHandler> Você deve exportar o manipulador de soltar junto com os seguintes atributos:  
  
-   <xref:Microsoft.VisualStudio.Text.Editor.DragDrop.DropFormatAttribute>: o formato de texto para que esse manipulador de recebimento é válido.</xref:Microsoft.VisualStudio.Text.Editor.DragDrop.DropFormatAttribute> Os seguintes formatos são tratados em ordem de prioridade do mais alto ao mais baixo:  
  
    1.  Qualquer formato personalizado  
  
    2.  FileDrop  
  
    3.  EnhancedMetafile  
  
    4.  WaveAudio  
  
    5.  RIFF  
  
    6.  DIF  
  
    7.  Localidade  
  
    8.  Paleta  
  
    9. PenData  
  
    10. Serializado  
  
    11. SymbolicLink  
  
    12. XAML  
  
    13. XamlPackage  
  
    14. TIFF  
  
    15. Bitmap  
  
    16. DIB  
  
    17. MetafilePicture  
  
    18. CSV  
  
    19. System.String  
  
    20. Formato HTML  
  
    21. UnicodeText  
  
    22. OEMText  
  
    23. Texto  
  
-   <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: o nome do manipulador de recebimento.</xref:Microsoft.VisualStudio.Utilities.NameAttribute>  
  
-   <xref:Microsoft.VisualStudio.Utilities.OrderAttribute>: a ordem do manipulador de soltar antes ou depois do manipulador de recebimento padrão.</xref:Microsoft.VisualStudio.Utilities.OrderAttribute> O manipulador de recebimento padrão para o Visual Studio é chamado de "DefaultFileDropHandler".  
  
 O exemplo a seguir mostra os atributos de exportação em um provedor de manipulador de recebimento.  
  
```  
[Export(typeof(IDropHandlerProvider))]  
[DropFormat("Text")]   
[Name("TestDropHandler")]  
[Order(Before="DefaultFileDropHandler")]   
internal class TestDropHandlerProvider : IDropHandlerProvider  
```  
  
## <a name="extending-editor-options"></a>Estendendo as opções do Editor  
 Você pode definir opções para ser válido somente em um determinado escopo, por exemplo, em uma exibição de texto. O editor fornece esse conjunto de opções predefinidas: opções de editor, opções de exibição e opções de exibição do Windows Presentation Foundation (WPF). Essas opções podem ser encontradas em <xref:Microsoft.VisualStudio.Text.Editor.DefaultOptions>, <xref:Microsoft.VisualStudio.Text.Editor.DefaultTextViewOptions>e <xref:Microsoft.VisualStudio.Text.Editor.DefaultWpfViewOptions>.</xref:Microsoft.VisualStudio.Text.Editor.DefaultWpfViewOptions> </xref:Microsoft.VisualStudio.Text.Editor.DefaultTextViewOptions> </xref:Microsoft.VisualStudio.Text.Editor.DefaultOptions>  
  
 Para adicionar uma nova opção, derive uma classe de uma dessas classes de definição de opção:  
  
-   <xref:Microsoft.VisualStudio.Text.Editor.EditorOptionDefinition%601></xref:Microsoft.VisualStudio.Text.Editor.EditorOptionDefinition%601>  
  
-   <xref:Microsoft.VisualStudio.Text.Editor.ViewOptionDefinition%601></xref:Microsoft.VisualStudio.Text.Editor.ViewOptionDefinition%601>  
  
-   <xref:Microsoft.VisualStudio.Text.Editor.WpfViewOptionDefinition%601></xref:Microsoft.VisualStudio.Text.Editor.WpfViewOptionDefinition%601>  
  
 O exemplo a seguir mostra como exportar uma definição de opção que tem um valor booleano.  
  
```  
[Export(typeof(EditorOptionDefinition))]  
internal sealed class TestOption : EditorOptionDefinition<bool>  
```  
  
## <a name="extending-intellisense"></a>Estendendo o IntelliSense  
 O IntelliSense é um termo geral para um grupo de recursos que fornecem informações sobre o texto estruturado e a conclusão de instrução para ele. Esses recursos incluem a conclusão de instrução, ajuda de assinatura, informações rápidas e lâmpadas. Conclusão de instrução ajuda os usuários a digitar um nome de membro ou palavra-chave de idioma corretamente. Ajuda da assinatura exibe a assinatura ou assinaturas para o método apenas digitado pelo usuário. Informação rápida exibe uma assinatura completa para um nome de tipo ou membro quando o mouse é posicionado sobre ele. Lâmpada fornecer ações adicionais para determinadas identificadores em determinados contextos, por exemplo, renomear todas as ocorrências de uma variável após uma ocorrência foi renomeada.  
  
 O design de um recurso IntelliSense é muito a mesma em todos os casos:  
  
-   Um IntelliSense *broker* é responsável por processo geral.  
  
-   Um IntelliSense *sessão* representa a sequência de eventos entre o disparo de apresentador e o envio ou o cancelamento da seleção. A sessão é normalmente disparada por alguns gesto do usuário.  
  
-   Um IntelliSense *controlador* é responsável por decidir quando a sessão deve começar e terminar. Ele também decide quando as informações devem ser confirmadas e quando a sessão deve ser cancelada.  
  
-   Um IntelliSense *fonte* fornece o conteúdo e decidir a melhor correspondência.  
  
-   Um IntelliSense *apresentador* é responsável por exibir o conteúdo.  
  
 Na maioria dos casos, é recomendável que você forneça pelo menos uma origem e um controlador. Você também pode fornecer um apresentador para personalizar a exibição.  
  
### <a name="implementing-an-intellisense-source"></a>Implementando uma origem do IntelliSense  
 Para personalizar uma fonte, você deve implementar uma (ou mais) das seguintes interfaces de origem:  
  
-   <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource></xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource>  
  
-   <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSource></xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSource>  
  
-   <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource></xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource>  
  
-   <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource></xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource>  
  
> [!IMPORTANT]
>  <xref:Microsoft.VisualStudio.Language.Intellisense.ISmartTagSource>foi preterida em favor de <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource>.</xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource></xref:Microsoft.VisualStudio.Language.Intellisense.ISmartTagSource>  
  
 Além disso, você deve implementar um provedor do mesmo tipo:  
  
-   <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSourceProvider></xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSourceProvider>  
  
-   <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSourceProvider></xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSourceProvider>  
  
-   <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSourceProvider></xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSourceProvider>  
  
-   <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSourceProvider></xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSourceProvider>  
  
> [!IMPORTANT]
>  <xref:Microsoft.VisualStudio.Language.Intellisense.ISmartTagSourceProvider>foi preterida em favor de <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSourceProvider>.</xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSourceProvider></xref:Microsoft.VisualStudio.Language.Intellisense.ISmartTagSourceProvider>  
  
 Você deve exportar o provedor junto com os seguintes atributos:  
  
-   <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: o nome da fonte.</xref:Microsoft.VisualStudio.Utilities.NameAttribute>  
  
-   <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>: o tipo de conteúdo (por exemplo, "text" ou "código") ao qual se aplica a fonte.</xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>  
  
-   <xref:Microsoft.VisualStudio.Utilities.OrderAttribute>: a ordem na qual a origem deve aparecer (em relação a outras fontes).</xref:Microsoft.VisualStudio.Utilities.OrderAttribute>  
  
-   O exemplo a seguir mostra os atributos de exportação em um provedor de fonte de conclusão.  
  
```  
Export(typeof(ICompletionSourceProvider))]  
[Name(" Test Statement Completion Provider")]  
[Order(Before = "default")]  
[ContentType("text")]  
internal class TestCompletionSourceProvider : ICompletionSourceProvider  
```  
  
 Para obter mais informações sobre a implementação de fontes do IntelliSense, consulte as instruções a seguir:  
  
 [Passo a passo: Exibindo Informaçãorápida dicas de ferramenta](../extensibility/walkthrough-displaying-quickinfo-tooltips.md)  
  
 [Passo a passo: Exibindo a Ajuda de assinatura](../extensibility/walkthrough-displaying-signature-help.md)  
  
 [Walkthrough: Displaying Statement Completion (Passo a passo: exibindo o preenchimento de declaração)](../extensibility/walkthrough-displaying-statement-completion.md)  
  
### <a name="implementing-an-intellisense-controller"></a>Implementando um controlador do IntelliSense  
 Para personalizar um controlador, você deve implementar o <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController>interface.</xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController> Além disso, você deve implementar um provedor de controlador junto com os seguintes atributos:  
  
-   <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: o nome do controlador.</xref:Microsoft.VisualStudio.Utilities.NameAttribute>  
  
-   <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>: o tipo de conteúdo (por exemplo, "text" ou "código") ao qual o controlador se aplica.</xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>  
  
-   <xref:Microsoft.VisualStudio.Utilities.OrderAttribute>: a ordem na qual o controlador deve aparecer (em relação a outros controladores).</xref:Microsoft.VisualStudio.Utilities.OrderAttribute>  
  
 O exemplo a seguir mostra os atributos de exportação em um provedor de controlador de conclusão.  
  
```  
Export(typeof(IIntellisenseControllerProvider))]  
[Name(" Test Controller Provider")]  
[Order(Before = "default")]  
[ContentType("text")]  
internal class TestIntellisenseControllerProvider : IIntellisenseControllerProvider  
```  
  
 Para obter mais informações sobre como usar o IntelliSense controladores, consulte as instruções a seguir:  
  
 [Passo a passo: Exibindo Informaçãorápida dicas de ferramenta](../extensibility/walkthrough-displaying-quickinfo-tooltips.md)
