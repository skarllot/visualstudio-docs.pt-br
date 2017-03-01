---
title: "Editor de importações | Documentos do Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], new - services
ms.assetid: 8d096de3-33b4-427a-a122-4aeff8a72da0
caps.latest.revision: 19
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
ms.sourcegitcommit: 5658ecf52637a38bc3c2a5ad9e85b2edebf7d445
ms.openlocfilehash: 2c7daddb7cd40dd0e5d24f01df141ce30ba713f9
ms.lasthandoff: 02/22/2017

---
# <a name="editor-imports"></a>Editor de importações
Você pode importar um número de serviços de editor, fábricas e os agentes que fornecem a extensão com diferentes tipos de acesso para o editor de núcleo. Por exemplo, você pode importar o <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService>fornecer um <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigator>para um determinado tipo de conteúdo.</xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigator> </xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService> (Este navegador permite que executar diferentes tipos de pesquisas em um buffer de texto).  
  
 Para usar uma importação de editor, importá-lo como um campo ou propriedade de uma classe que exporta uma parte de componente Managed Extensibility Framework.  
  
> [!NOTE]
>  Para obter mais informações sobre o Managed Extensibility Framework, consulte [Managed Extensibility Framework (MEF)](http://msdn.microsoft.com/Library/6c61b4ec-c6df-4651-80f1-4854f8b14dde).  
  
## <a name="import-syntax"></a>Sintaxe de importação  
 O exemplo a seguir mostra como importar o editor de serviço de fábrica de opções.  
  
```  
[Import]  
internal IEditorOptionsFactoryService EditorOptions { get; set; }  
```  
  
 Se você deseja importar o serviço como um campo e não uma propriedade, você deve configurá-lo `null` na declaração para evitar os avisos do compilador sobre não atribuir a uma variável:  
  
```  
[Import]  
internal IEditorOptionsFactoryService m_editorOptions = null;  
```  
  
 Para obter mais exemplos do uso de importações, consulte as instruções a seguir:  
  
 [Passo a passo: Criando um glifo de margem](../extensibility/walkthrough-creating-a-margin-glyph.md)  
  
 [Passo a passo: Personalizando a exibição de texto](../extensibility/walkthrough-customizing-the-text-view.md)  
  
 [Passo a passo: Realçando texto](../extensibility/walkthrough-highlighting-text.md)  
  
 [Passo a passo: Exibindo Informaçãorápida dicas de ferramenta](../extensibility/walkthrough-displaying-quickinfo-tooltips.md)  
  
 [Passo a passo: Exibindo a Ajuda de assinatura](../extensibility/walkthrough-displaying-signature-help.md)  
  
 [Walkthrough: Displaying Statement Completion (Passo a passo: exibindo o preenchimento de declaração)](../extensibility/walkthrough-displaying-statement-completion.md)  
  
 [Passo a passo: exibindo SmartTags](../misc/walkthrough-displaying-smarttags.md)  
  
## <a name="importing-the-service-provider"></a>Importando o provedor de serviços  
 Você também pode importar um <xref:Microsoft.VisualStudio.Shell.SVsServiceProvider>(encontrado no assembly Microsoft.VisualStudio.Shell.Immutable.10.0) da mesma maneira para obter acesso aos serviços do Visual Studio:</xref:Microsoft.VisualStudio.Shell.SVsServiceProvider>  
  
```  
[Import]  
internal SVsServiceProvider ServiceProvider = null;   
```  
  
 Consulte [passo a passo: acessando o objeto DTE de uma extensão de Editor](../extensibility/walkthrough-accessing-the-dte-object-from-an-editor-extension.md) para obter mais informações.  
  
## <a name="services"></a>Serviços  
 Editor de serviços são entidades geralmente única que fornecem um serviço e são compartilhadas entre vários componentes.  
  
|Importar|Fornece|  
|------------|--------------|  
|<xref:Microsoft.VisualStudio.Utilities.IFileExtensionRegistryService></xref:Microsoft.VisualStudio.Utilities.IFileExtensionRegistryService>|A relação entre as extensões de arquivo e <xref:Microsoft.VisualStudio.Utilities.IContentType>objetos.</xref:Microsoft.VisualStudio.Utilities.IContentType>|  
|<xref:Microsoft.VisualStudio.Utilities.IContentTypeRegistryService></xref:Microsoft.VisualStudio.Utilities.IContentTypeRegistryService>|A coleção de <xref:Microsoft.VisualStudio.Utilities.IContentType>objetos.</xref:Microsoft.VisualStudio.Utilities.IContentType>|  
|<xref:Microsoft.VisualStudio.Editor.IVsFontsAndColorsInformationService></xref:Microsoft.VisualStudio.Editor.IVsFontsAndColorsInformationService>|<xref:Microsoft.VisualStudio.Editor.IVsFontsAndColorsInformation>objetos</xref:Microsoft.VisualStudio.Editor.IVsFontsAndColorsInformation>|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService></xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService>|Muitos objetos de adaptador do editor:<br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow></xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer></xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator></xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView></xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>|  
|<xref:Microsoft.VisualStudio.Text.IncrementalSearch.IIncrementalSearchFactoryService></xref:Microsoft.VisualStudio.Text.IncrementalSearch.IIncrementalSearchFactoryService>|Um <xref:Microsoft.VisualStudio.Text.IncrementalSearch.IIncrementalSearch>objeto para um modo de exibição de texto especificado.</xref:Microsoft.VisualStudio.Text.IncrementalSearch.IIncrementalSearch>|  
|<xref:Microsoft.VisualStudio.Text.ITextBufferFactoryService></xref:Microsoft.VisualStudio.Text.ITextBufferFactoryService>|An <xref:Microsoft.VisualStudio.Text.ITextBuffer>.</xref:Microsoft.VisualStudio.Text.ITextBuffer>|  
|<xref:Microsoft.VisualStudio.Text.ITextDocumentFactoryService></xref:Microsoft.VisualStudio.Text.ITextDocumentFactoryService>|An <xref:Microsoft.VisualStudio.Text.ITextDocument>.</xref:Microsoft.VisualStudio.Text.ITextDocument>|  
|<xref:Microsoft.VisualStudio.Text.Differencing.IDifferenceService></xref:Microsoft.VisualStudio.Text.Differencing.IDifferenceService>|Um <xref:Microsoft.VisualStudio.Text.Differencing.IDifferenceCollection%601>das diferenças.</xref:Microsoft.VisualStudio.Text.Differencing.IDifferenceCollection%601>|  
|<xref:Microsoft.VisualStudio.Text.Differencing.IHierarchicalStringDifferenceService></xref:Microsoft.VisualStudio.Text.Differencing.IHierarchicalStringDifferenceService>|Um <xref:Microsoft.VisualStudio.Text.Differencing.IHierarchicalDifferenceCollection>das diferenças.</xref:Microsoft.VisualStudio.Text.Differencing.IHierarchicalDifferenceCollection>|  
|<xref:Microsoft.VisualStudio.Text.Projection.IProjectionBufferFactoryService></xref:Microsoft.VisualStudio.Text.Projection.IProjectionBufferFactoryService>|Um <xref:Microsoft.VisualStudio.Text.Projection.IProjectionBuffer>ou <xref:Microsoft.VisualStudio.Text.Projection.IElisionBuffer>.</xref:Microsoft.VisualStudio.Text.Projection.IElisionBuffer> </xref:Microsoft.VisualStudio.Text.Projection.IProjectionBuffer>|  
|<xref:Microsoft.VisualStudio.Text.Projection.IBufferGraphFactoryService></xref:Microsoft.VisualStudio.Text.Projection.IBufferGraphFactoryService>|Um <xref:Microsoft.VisualStudio.Text.Projection.IBufferGraph>para um conjunto de <xref:Microsoft.VisualStudio.Text.ITextBuffer>objetos.</xref:Microsoft.VisualStudio.Text.ITextBuffer> </xref:Microsoft.VisualStudio.Text.Projection.IBufferGraph>|  
|<xref:Microsoft.VisualStudio.Text.Classification.IClassifierAggregatorService></xref:Microsoft.VisualStudio.Text.Classification.IClassifierAggregatorService>|Uma <xref:Microsoft.VisualStudio.Text.Classification.IClassifier>para <xref:Microsoft.VisualStudio.Text.ITextBuffer>.</xref:Microsoft.VisualStudio.Text.ITextBuffer> </xref:Microsoft.VisualStudio.Text.Classification.IClassifier>|  
|<xref:Microsoft.VisualStudio.Text.Classification.IViewClassifierAggregatorService></xref:Microsoft.VisualStudio.Text.Classification.IViewClassifierAggregatorService>|Uma <xref:Microsoft.VisualStudio.Text.Classification.IClassifier>para <xref:Microsoft.VisualStudio.Text.Editor.ITextView>.</xref:Microsoft.VisualStudio.Text.Editor.ITextView> </xref:Microsoft.VisualStudio.Text.Classification.IClassifier>|  
|<xref:Microsoft.VisualStudio.Text.Classification.IClassificationFormatMapService></xref:Microsoft.VisualStudio.Text.Classification.IClassificationFormatMapService>|Uma <xref:Microsoft.VisualStudio.Text.Classification.IClassificationFormatMap>para <xref:Microsoft.VisualStudio.Text.Editor.ITextView>.</xref:Microsoft.VisualStudio.Text.Editor.ITextView> </xref:Microsoft.VisualStudio.Text.Classification.IClassificationFormatMap>|  
|<xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMapService></xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMapService>|Uma <xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMap>para <xref:Microsoft.VisualStudio.Text.Editor.ITextView>.</xref:Microsoft.VisualStudio.Text.Editor.ITextView> </xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMap>|  
|<xref:Microsoft.VisualStudio.Text.Classification.IClassificationTypeRegistryService></xref:Microsoft.VisualStudio.Text.Classification.IClassificationTypeRegistryService>|Mantém a coleção de <xref:Microsoft.VisualStudio.Text.Classification.IClassificationType>objetos.</xref:Microsoft.VisualStudio.Text.Classification.IClassificationType>|  
|<xref:Microsoft.VisualStudio.Text.Tagging.IBufferTagAggregatorFactoryService></xref:Microsoft.VisualStudio.Text.Tagging.IBufferTagAggregatorFactoryService>|Um <xref:Microsoft.VisualStudio.Text.Tagging.ITagAggregator%601>para um buffer de texto.</xref:Microsoft.VisualStudio.Text.Tagging.ITagAggregator%601>|  
|<xref:Microsoft.VisualStudio.Text.Tagging.IViewTagAggregatorFactoryService></xref:Microsoft.VisualStudio.Text.Tagging.IViewTagAggregatorFactoryService>|Um <xref:Microsoft.VisualStudio.Text.Tagging.ITagAggregator%601>para uma exibição de texto.</xref:Microsoft.VisualStudio.Text.Tagging.ITagAggregator%601>|  
|<xref:Microsoft.VisualStudio.Text.Editor.IEditorOptionsFactoryService></xref:Microsoft.VisualStudio.Text.Editor.IEditorOptionsFactoryService>|O <xref:Microsoft.VisualStudio.Text.Editor.IEditorOptions>para o escopo especificado.</xref:Microsoft.VisualStudio.Text.Editor.IEditorOptions>|  
|<xref:Microsoft.VisualStudio.Text.Editor.IScrollMapFactoryService></xref:Microsoft.VisualStudio.Text.Editor.IScrollMapFactoryService>|Um <xref:Microsoft.VisualStudio.Text.Editor.IScrollMap>para uma exibição de texto.</xref:Microsoft.VisualStudio.Text.Editor.IScrollMap>|  
|<xref:Microsoft.VisualStudio.Text.Editor.ISmartIndentationService></xref:Microsoft.VisualStudio.Text.Editor.ISmartIndentationService>|Uma <xref:Microsoft.VisualStudio.Text.Editor.ISmartIndent>para <xref:Microsoft.VisualStudio.Text.Editor.ITextView>.</xref:Microsoft.VisualStudio.Text.Editor.ITextView> </xref:Microsoft.VisualStudio.Text.Editor.ISmartIndent>|  
|<xref:Microsoft.VisualStudio.Text.Editor.ISmartIndentationService></xref:Microsoft.VisualStudio.Text.Editor.ISmartIndentationService>|Obtém o recuo automático por meio de <xref:Microsoft.VisualStudio.Text.Editor.ISmartIndentProvider>objetos.</xref:Microsoft.VisualStudio.Text.Editor.ISmartIndentProvider>|  
|<xref:Microsoft.VisualStudio.Text.Editor.ITextEditorFactoryService></xref:Microsoft.VisualStudio.Text.Editor.ITextEditorFactoryService>|Gerencia o <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewHost>para <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextView>.</xref:Microsoft.VisualStudio.Text.Editor.IWpfTextView> </xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewHost>|  
|<xref:Microsoft.VisualStudio.Text.Formatting.IFormattedTextSourceFactoryService></xref:Microsoft.VisualStudio.Text.Formatting.IFormattedTextSourceFactoryService>|An <xref:Microsoft.VisualStudio.Text.Formatting.IFormattedLineSource>.</xref:Microsoft.VisualStudio.Text.Formatting.IFormattedLineSource>|  
|<xref:Microsoft.VisualStudio.Text.Formatting.IRtfBuilderService></xref:Microsoft.VisualStudio.Text.Formatting.IRtfBuilderService>|Gera texto formatado em RTF de um conjunto de intervalos de instantâneo.|  
|<xref:Microsoft.VisualStudio.Text.Formatting.ITextAndAdornmentSequencerFactoryService></xref:Microsoft.VisualStudio.Text.Formatting.ITextAndAdornmentSequencerFactoryService>|Uma <xref:Microsoft.VisualStudio.Text.Formatting.ITextAndAdornmentSequencer>para <xref:Microsoft.VisualStudio.Text.Editor.ITextView>.</xref:Microsoft.VisualStudio.Text.Editor.ITextView> </xref:Microsoft.VisualStudio.Text.Formatting.ITextAndAdornmentSequencer>|  
|<xref:Microsoft.VisualStudio.Text.Formatting.ITextParagraphPropertiesFactoryService></xref:Microsoft.VisualStudio.Text.Formatting.ITextParagraphPropertiesFactoryService>|Um <xref:System.Windows.Media.TextFormatting.TextParagraphProperties>para formatação de linhas de texto em uma exibição.</xref:System.Windows.Media.TextFormatting.TextParagraphProperties>|  
|<xref:Microsoft.VisualStudio.Text.Operations.IEditorOperationsFactoryService></xref:Microsoft.VisualStudio.Text.Operations.IEditorOperationsFactoryService>|Um <xref:Microsoft.VisualStudio.Text.Operations.IEditorOperations>objeto para <xref:Microsoft.VisualStudio.Text.Editor.ITextView>.</xref:Microsoft.VisualStudio.Text.Editor.ITextView> </xref:Microsoft.VisualStudio.Text.Operations.IEditorOperations>|  
|<xref:Microsoft.VisualStudio.Text.Operations.ITextSearchService></xref:Microsoft.VisualStudio.Text.Operations.ITextSearchService>|Pesquisa um instantâneo de texto.|  
|<xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService></xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService>|Um <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigator>para um <xref:Microsoft.VisualStudio.Text.ITextBuffer>por <xref:Microsoft.VisualStudio.Utilities.IContentType>.</xref:Microsoft.VisualStudio.Utilities.IContentType> </xref:Microsoft.VisualStudio.Text.ITextBuffer> </xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigator>|  
|<xref:Microsoft.VisualStudio.Text.Outlining.IOutliningManagerService></xref:Microsoft.VisualStudio.Text.Outlining.IOutliningManagerService>|Um <xref:Microsoft.VisualStudio.Text.Outlining.IOutliningManager>para uma exibição de texto.</xref:Microsoft.VisualStudio.Text.Outlining.IOutliningManager>|  
|<xref:Microsoft.VisualStudio.Language.Intellisense.IGlyphService></xref:Microsoft.VisualStudio.Language.Intellisense.IGlyphService>|Um conjunto padrão de glifos.|  
|<xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseSessionStackMapService></xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseSessionStackMapService>|Uma <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseSessionStack>para <xref:Microsoft.VisualStudio.Text.Editor.ITextView>.</xref:Microsoft.VisualStudio.Text.Editor.ITextView> </xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseSessionStack>|  
|<xref:Microsoft.VisualStudio.Language.Intellisense.IWpfKeyboardTrackingService></xref:Microsoft.VisualStudio.Language.Intellisense.IWpfKeyboardTrackingService>|Faixas de tratamento de teclado.|  
|<xref:Microsoft.VisualStudio.Language.StandardClassification.IStandardClassificationService></xref:Microsoft.VisualStudio.Language.StandardClassification.IStandardClassificationService>|Padrão <xref:Microsoft.VisualStudio.Text.Classification.IClassificationType>objetos.</xref:Microsoft.VisualStudio.Text.Classification.IClassificationType>|  
|<xref:Microsoft.VisualStudio.Text.Operations.ITextUndoHistoryRegistry></xref:Microsoft.VisualStudio.Text.Operations.ITextUndoHistoryRegistry>|Mantém a relação entre os buffers de texto e <xref:Microsoft.VisualStudio.Text.Operations.ITextUndoHistory>objetos.</xref:Microsoft.VisualStudio.Text.Operations.ITextUndoHistory>|  
  
## <a name="other-imports"></a>Outras importações  
 Fábricas de provedor e os agentes são geralmente entidades que podem ter várias instâncias em vários componentes.  
  
|Importar|Fornece|  
|------------|--------------|  
|<xref:Microsoft.VisualStudio.Text.Adornments.IErrorProviderFactory></xref:Microsoft.VisualStudio.Text.Adornments.IErrorProviderFactory>|Um <xref:Microsoft.VisualStudio.Text.Tagging.SimpleTagger%601>do tipo <xref:Microsoft.VisualStudio.Text.Tagging.ErrorTag>) para o buffer fornecido.</xref:Microsoft.VisualStudio.Text.Tagging.ErrorTag> </xref:Microsoft.VisualStudio.Text.Tagging.SimpleTagger%601>|  
|<xref:Microsoft.VisualStudio.Text.Adornments.ITextMarkerProviderFactory></xref:Microsoft.VisualStudio.Text.Adornments.ITextMarkerProviderFactory>|Um marcador de marcador de texto (um <xref:Microsoft.VisualStudio.Text.Tagging.SimpleTagger%601>do tipo <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>).</xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag> </xref:Microsoft.VisualStudio.Text.Tagging.SimpleTagger%601>|  
|<xref:Microsoft.VisualStudio.Text.Adornments.IToolTipProviderFactory></xref:Microsoft.VisualStudio.Text.Adornments.IToolTipProviderFactory>|Um <xref:Microsoft.VisualStudio.Text.Adornments.IToolTipProvider>para um determinado <xref:Microsoft.VisualStudio.Text.Editor.ITextView>.</xref:Microsoft.VisualStudio.Text.Editor.ITextView> </xref:Microsoft.VisualStudio.Text.Adornments.IToolTipProvider>|  
|<xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionBroker></xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionBroker>|An <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSession>.</xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSession>|  
|<xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoBroker></xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoBroker>|An <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSession>.</xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSession>|  
|<xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpBroker></xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpBroker>|An <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSession>.</xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSession>|  
  
## <a name="see-also"></a>Consulte também  
 [Serviço de linguagem e pontos de extensão de Editor](../extensibility/language-service-and-editor-extension-points.md)
