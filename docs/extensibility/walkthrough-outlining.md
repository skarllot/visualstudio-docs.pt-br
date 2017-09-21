---
title: "Passo a passo: Estrutura de tópicos | Documentos do Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], new - outlining
ms.assetid: d75a44aa-265a-44d4-9c28-457f59c4ff9f
caps.latest.revision: 30
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
ms.openlocfilehash: d732e07e5b78716038680471d510732ad316c785
ms.lasthandoff: 02/22/2017

---
# <a name="walkthrough-outlining"></a>Instruções passo a passo: estrutura de tópicos
Você pode implementar recursos de linguagem como estrutura de tópicos definindo os tipos de regiões de texto que você deseja expandir ou recolher. Você pode definir regiões no contexto de um serviço de linguagem, você pode definir seu próprio tipo de conteúdo e extensão de nome do arquivo e aplicar a definição de região somente àquele tipo ou você pode aplicar as definições de região para um tipo de conteúdo existente (como "text"). Este passo a passo mostra como definir e exibir regiões de estrutura de tópicos.  
  
## <a name="prerequisites"></a>Pré-requisitos  
 A partir do Visual Studio 2015, você não instale o SDK do Visual Studio no Centro de download. Ele é fornecido como um recurso opcional na instalação do Visual Studio. Você também pode instalar o SDK do VS mais tarde. Para obter mais informações, consulte [instalar o SDK do Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-managed-extensibility-framework-mef-project"></a>Criando um projeto do Managed Extensibility Framework (MEF)  
  
#### <a name="to-create-a-mef-project"></a>Para criar um projeto MEF  
  
1.  Crie um projeto do VSIX. Nomeie a solução `OutlineRegionTest`.  
  
2.  Adicione um modelo de item Editor classificador ao projeto. Para obter mais informações, consulte [criando uma extensão com um modelo de Item Editor](../extensibility/creating-an-extension-with-an-editor-item-template.md).  
  
3.  Exclua os arquivos de classe existentes.  
  
## <a name="implementing-an-outlining-tagger"></a>Implementando um marcador de estrutura de tópicos  
 Regiões de estrutura de tópicos são marcados por um tipo de marca (<xref:Microsoft.VisualStudio.Text.Tagging.OutliningRegionTag>).</xref:Microsoft.VisualStudio.Text.Tagging.OutliningRegionTag> Essa marca fornece o padrão de comportamento de estrutura de tópicos. A região de estrutura de tópicos pode ser expandida ou recolhida. A região de estrutura de tópicos é marcada por um sinal de adição, se ele estiver recolhido ou um sinal de menos se ele é expandido e a região expandida é delimitada por uma linha vertical.  
  
 As etapas a seguir mostram como definir um marcador que cria regiões de estrutura de tópicos para todas as regiões são delimitadas por "[" e "]".  
  
#### <a name="to-implement-an-outlining-tagger"></a>Para implementar um marcador de estrutura de tópicos  
  
1.  Adicione um arquivo de classe e nomeie-o `OutliningTagger`.  
  
2.  Importe os seguintes namespaces.  
  
     [!code-cs[&#1; VSSDKOutlineRegionTest](../extensibility/codesnippet/CSharp/walkthrough-outlining_1.cs) ] 
     [!code-vb [VSSDKOutlineRegionTest n º&1;](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_1.vb)]  
  
3.  Crie uma classe denominada `OutliningTagger`, e a implementar <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601>:</xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601>  
  
     [!code-cs[N º&2; VSSDKOutlineRegionTest](../extensibility/codesnippet/CSharp/walkthrough-outlining_2.cs) ] 
     [!code-vb [VSSDKOutlineRegionTest n º&2;](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_2.vb)]  
  
4.  Adicione alguns campos para acompanhar o instantâneo e o buffer de texto e acumular os conjuntos de linhas que devem ser marcadas como regiões de estrutura de tópicos. Esse código inclui uma lista de objetos de região (a ser definido mais tarde) que representam as regiões de estrutura de tópicos.  
  
     [!code-cs[N º&3; VSSDKOutlineRegionTest](../extensibility/codesnippet/CSharp/walkthrough-outlining_3.cs) ] 
     [!code-vb [VSSDKOutlineRegionTest n º&3;](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_3.vb)]  
  
5.  Adicione um construtor de marcador que inicializa os campos, analisa o buffer e adiciona um manipulador de eventos para o <xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed>evento.</xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed>  
  
     [!code-cs[N º&4; VSSDKOutlineRegionTest](../extensibility/codesnippet/CSharp/walkthrough-outlining_4.cs) ] 
     [!code-vb [VSSDKOutlineRegionTest n º&4;](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_4.vb)]  
  
6.  Implementar o <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601.GetTags%2A>método, que instancia a marca abrange.</xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601.GetTags%2A> Este exemplo assume que as extensões no <xref:Microsoft.VisualStudio.Text.NormalizedSpanCollection>passado para o método são contíguos, embora isso possa não ser sempre o caso.</xref:Microsoft.VisualStudio.Text.NormalizedSpanCollection> Esse método cria um novo intervalo de marca para cada uma das regiões de estrutura de tópicos.  
  
     [!code-cs[N º&5; VSSDKOutlineRegionTest](../extensibility/codesnippet/CSharp/walkthrough-outlining_5.cs) ] 
     [!code-vb [VSSDKOutlineRegionTest n º&5;](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_5.vb)]  
  
7.  Declarar uma `TagsChanged` manipulador de eventos.  
  
     [!code-cs[N º&6; VSSDKOutlineRegionTest](../extensibility/codesnippet/CSharp/walkthrough-outlining_6.cs) ] 
     [!code-vb [VSSDKOutlineRegionTest n º&6;](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_6.vb)]  
  
8.  Adicionar uma `BufferChanged` manipulador de eventos que responde a <xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed>eventos analisando o buffer de texto.</xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed>  
  
     [!code-cs[#7 VSSDKOutlineRegionTest](../extensibility/codesnippet/CSharp/walkthrough-outlining_7.cs) ] 
     [!code-vb [VSSDKOutlineRegionTest&#7;](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_7.vb)]  
  
9. Adicione um método que analisa o buffer. O exemplo fornecido aqui é apenas para fins ilustrativos. Analisa o buffer de forma síncrona em regiões de estrutura de tópicos aninhadas.  
  
     [!code-cs[N º&8; VSSDKOutlineRegionTest](../extensibility/codesnippet/CSharp/walkthrough-outlining_8.cs)]
   [!code-vb[VSSDKOutlineRegionTest n º&8;  ](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_8.vb)]  
  
10. O método auxiliar a seguir obtém um valor inteiro que representa o nível de estrutura de tópicos, que 1 é o par de chave à esquerda.  
  
     [!code-cs[N º&9; VSSDKOutlineRegionTest](../extensibility/codesnippet/CSharp/walkthrough-outlining_9.cs) ] 
     [!code-vb [VSSDKOutlineRegionTest n º&9;](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_9.vb)]  
  
11. O método auxiliar a seguir converte uma região (definida mais tarde neste tópico) em um SnapshotSpan.  
  
     [!code-cs[N º&10; VSSDKOutlineRegionTest](../extensibility/codesnippet/CSharp/walkthrough-outlining_10.cs) ] 
     [!code-vb [VSSDKOutlineRegionTest n º&10;](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_10.vb)]  
  
12. O código a seguir é apenas para fins ilustrativos. Ele define uma classe PartialRegion que contém o número da linha e o deslocamento do início de uma região de estrutura de tópicos e também uma referência para a região pai (se houver). Isso permite que o analisador configurar aninhados regiões de estrutura de tópicos. Uma classe derivada de região contém uma referência para o número da linha do final de uma região de estrutura de tópicos.  
  
     [!code-cs[N º&11; VSSDKOutlineRegionTest](../extensibility/codesnippet/CSharp/walkthrough-outlining_11.cs) ] 
     [!code-vb [VSSDKOutlineRegionTest n º&11;](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_11.vb)]  
  
## <a name="implementing-a-tagger-provider"></a>Implementando um provedor de marcador  
 Você deve exportar um provedor de marcador para o marcador. O provedor de marcador cria um `OutliningTagger` um buffer do tipo de conteúdo "text" ou outra retorna um `OutliningTagger` se o buffer já tenha um.  
  
#### <a name="to-implement-a-tagger-provider"></a>Para implementar um provedor de marcador  
  
1.  Crie uma classe denominada `OutliningTaggerProvider` que implementa <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider>e exportá-lo com os atributos ContentType e TagType.</xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider>  
  
     [!code-cs[#12 VSSDKOutlineRegionTest](../extensibility/codesnippet/CSharp/walkthrough-outlining_12.cs) ] 
     [!code-vb [VSSDKOutlineRegionTest&#12;](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_12.vb)]  
  
2.  Implementar o <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider.CreateTagger%2A>método adicionando um `OutliningTagger` para as propriedades do buffer.</xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider.CreateTagger%2A>  
  
     [!code-cs[VSSDKOutlineRegionTest&13;](../extensibility/codesnippet/CSharp/walkthrough-outlining_13.cs) ] 
     [!code-vb [VSSDKOutlineRegionTest&13;](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_13.vb)]  
  
## <a name="building-and-testing-the-code"></a>Compilar e testar o código  
 Para testar esse código, crie a solução OutlineRegionTest e executá-lo na instância experimental.  
  
#### <a name="to-build-and-test-the-outlineregiontest-solution"></a>Para compilar e testar a solução OutlineRegionTest  
  
1.  Compile a solução.  
  
2.  Quando você executa este projeto no depurador, uma segunda instância do Visual Studio é instanciada.  
  
3.  Crie um arquivo de texto. Digite um texto que inclui a chave de abertura e a chave de fechamento.  
  
    ```  
    [  
       Hello  
    ]  
    ```  
  
4.  Deve haver uma região de estrutura de tópicos que inclui as duas chaves. Você poderá clicar no sinal de subtração à esquerda da chave de abertura para recolher a região de estrutura de tópicos. Quando a região é recolhido, o símbolo de reticências (...) deve aparecer à esquerda da região recolhida e um pop-up que contém o texto **focalizar texto** deve aparecer quando você move o ponteiro sobre o botão de reticências.  
  
## <a name="see-also"></a>Consulte também  
 [Passo a passo: Vinculação de um tipo de conteúdo para uma extensão de nome de arquivo](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)
