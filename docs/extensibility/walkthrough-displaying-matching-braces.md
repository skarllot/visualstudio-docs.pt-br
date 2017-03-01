---
title: 'Passo a passo: Exibindo chaves correspondentes | Documentos do Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], new - brace matching
ms.assetid: 5af08ac7-1d08-4ccf-997e-01aa6cb3d3d7
caps.latest.revision: 27
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
ms.openlocfilehash: 157f80ac1de5048286a64794bf2df8389d947b88
ms.lasthandoff: 02/22/2017

---
# <a name="walkthrough-displaying-matching-braces"></a>Passo a passo: Exibindo chaves correspondentes
Você pode implementar recursos de linguagem como correspondência definindo as chaves que você deseja corresponder e, em seguida, adicionar uma marca de marcador de texto para as chaves correspondentes quando o cursor estiver em uma das chaves de chaves. Você pode definir chaves no contexto de um idioma, você pode definir seu próprio tipo de conteúdo e extensão de nome do arquivo e aplicar as marcas apenas àquele tipo ou você pode aplicar marcas a um tipo de conteúdo existente (como "text"). A instrução a seguir mostra como aplicar marcas para o tipo de conteúdo "text" de correspondência de chaves.  
  
## <a name="prerequisites"></a>Pré-requisitos  
 A partir do Visual Studio 2015, você não instale o SDK do Visual Studio no Centro de download. Ele é fornecido como um recurso opcional na instalação do Visual Studio. Você também pode instalar o SDK do VS mais tarde. Para obter mais informações, consulte [instalar o SDK do Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-managed-extensibility-framework-mef-project"></a>Criando um projeto do Managed Extensibility Framework (MEF)  
  
#### <a name="to-create-a-mef-project"></a>Para criar um projeto MEF  
  
1.  Crie um projeto de classificação do Editor. Nomeie a solução `BraceMatchingTest`.  
  
2.  Adicione um modelo de item Editor classificador ao projeto. Para obter mais informações, consulte [criando uma extensão com um modelo de Item Editor](../extensibility/creating-an-extension-with-an-editor-item-template.md).  
  
3.  Exclua os arquivos de classe existentes.  
  
## <a name="implementing-a-brace-matching-tagger"></a>Implementando um marcador de correspondência de chaves  
 Para obter uma chave realçando efeito semelhante ao que é usado no Visual Studio, você pode implementar um marcador do tipo <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>.</xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag> O código a seguir mostra como definir o marcador para pares de chave em qualquer nível de aninhamento. Neste exemplo, os pares de chave []. [] e {} está definido no construtor do marcador, mas em uma implementação da linguagem completa os pares de chave relevante seriam definidos na especificação de linguagem.  
  
#### <a name="to-implement-a-brace-matching-tagger"></a>Para implementar um marcador de correspondência de chaves  
  
1.  Adicione um arquivo de classe e nomeie-a correspondência de chaves.  
  
2.  Importe os seguintes namespaces.  
  
     [!code-cs[&#1; VSSDKBraceMatchingTest](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_1.cs) ] 
     [!code-vb [VSSDKBraceMatchingTest n º&1;](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_1.vb)]  
  
3.  Definir uma classe `BraceMatchingTagger` que herda <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601>do tipo <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>.</xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag> </xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601>  
  
     [!code-cs[N º&2; VSSDKBraceMatchingTest](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_2.cs) ] 
     [!code-vb [VSSDKBraceMatchingTest n º&2;](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_2.vb)]  
  
4.  Adicione propriedades para a exibição de texto, o buffer de origem e o ponto de instantâneo atual e também um conjunto de pares de chave.  
  
     [!code-cs[N º&3; VSSDKBraceMatchingTest](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_3.cs) ] 
     [!code-vb [VSSDKBraceMatchingTest n º&3;](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_3.vb)]  
  
5.  No construtor de marcador, defina as propriedades e inscrever-se para o modo de exibição alteração eventos <xref:Microsoft.VisualStudio.Text.Editor.ITextCaret.PositionChanged>e <xref:Microsoft.VisualStudio.Text.Editor.ITextView.LayoutChanged>.</xref:Microsoft.VisualStudio.Text.Editor.ITextView.LayoutChanged> </xref:Microsoft.VisualStudio.Text.Editor.ITextCaret.PositionChanged> Neste exemplo, para fins ilustrativos, os pares correspondentes também são definidos no construtor.  
  
     [!code-cs[N º&4; VSSDKBraceMatchingTest](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_4.cs) ] 
     [!code-vb [VSSDKBraceMatchingTest n º&4;](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_4.vb)]  
  
6.  Como parte do <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601>implementação, declare um evento TagsChanged.</xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601>  
  
     [!code-cs[N º&5; VSSDKBraceMatchingTest](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_5.cs) ] 
     [!code-vb [VSSDKBraceMatchingTest n º&5;](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_5.vb)]  
  
7.  Os manipuladores de eventos atualize a posição atual do cursor do `CurrentChar` propriedade e acionar o evento TagsChanged.  
  
     [!code-cs[N º&6; VSSDKBraceMatchingTest](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_6.cs) ] 
     [!code-vb [VSSDKBraceMatchingTest n º&6;](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_6.vb)]  
  
8.  Implementar o <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601.GetTags%2A>método para que correspondam a chaves quando o caractere atual é uma chave de abertura ou quando o caractere anterior é um colchete de fechamento, como no Visual Studio.</xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601.GetTags%2A> Quando a correspondência for encontrada, esse método cria duas marcas, uma para a chave de abertura e outra para o colchete de fechamento.  
  
     [!code-cs[#7 VSSDKBraceMatchingTest](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_7.cs) ] 
     [!code-vb [VSSDKBraceMatchingTest&#7;](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_7.vb)]  
  
9. Os seguintes métodos privados localizar a chave correspondente em qualquer nível de aninhamento. O primeiro método encontra o caractere de fechamento que corresponde ao caractere aberto:  
  
     [!code-cs[N º&8; VSSDKBraceMatchingTest](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_8.cs)]
   [!code-vb[VSSDKBraceMatchingTest n º&8;  ](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_8.vb)]  
  
10. O método auxiliar a seguir localiza o caractere aberto que corresponde a um caractere de fechamento:  
  
     [!code-cs[N º&9; VSSDKBraceMatchingTest](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_9.cs) ] 
     [!code-vb [VSSDKBraceMatchingTest n º&9;](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_9.vb)]  
  
## <a name="implementing-a-brace-matching-tagger-provider"></a>Implementando um provedor de marcador de correspondência de chaves  
 Além de implementar um marcador, você também deve implementar e exportar um provedor de marcador. Nesse caso, o tipo de conteúdo do provedor é "text". Isso significa que a correspondência de colchetes aparecerá em todos os tipos de arquivos de texto, mas uma implementação mais completa se aplicariam a chave correspondente somente a um tipo específico de conteúdo.  
  
#### <a name="to-implement-a-brace-matching-tagger-provider"></a>Para implementar um provedor de marcador de correspondência de chave  
  
1.  Declarar um provedor de marcador que herda de <xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider>, nomeie-o BraceMatchingTaggerProvider e exportá-lo com um <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>de "text" e um <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute>de <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>.</xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag> </xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute> </xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> </xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider>  
  
     [!code-cs[N º&10; VSSDKBraceMatchingTest](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_10.cs) ] 
     [!code-vb [VSSDKBraceMatchingTest n º&10;](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_10.vb)]  
  
2.  Implementar o <xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider.CreateTagger%2A>método para instanciar um BraceMatchingTagger.</xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider.CreateTagger%2A>  
  
     [!code-cs[N º&11; VSSDKBraceMatchingTest](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_11.cs) ] 
     [!code-vb [VSSDKBraceMatchingTest n º&11;](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_11.vb)]  
  
## <a name="building-and-testing-the-code"></a>Compilar e testar o código  
 Para testar esse código, crie a solução BraceMatchingTest e executá-lo na instância experimental.  
  
#### <a name="to-build-and-test-bracematchingtest-solution"></a>Para compilar e testar a solução BraceMatchingTest  
  
1.  Compile a solução.  
  
2.  Quando você executa este projeto no depurador, uma segunda instância do Visual Studio é instanciada.  
  
3.  Crie um arquivo de texto e digite um texto que inclui chaves correspondentes.  
  
    ```  
    hello {  
    goodbye}  
  
    {}  
  
    {hello}  
    ```  
  
4.  Quando você posiciona o cursor antes de uma chave de abertura, essa chave e o colchete de fechamento correspondente deve estar realçado. Quando você posiciona o cursor logo após o colchete de fechamento, essa chave e a chave de abertura correspondente deve estar realçada.  
  
## <a name="see-also"></a>Consulte também  
 [Passo a passo: Vinculação de um tipo de conteúdo para uma extensão de nome de arquivo](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)
