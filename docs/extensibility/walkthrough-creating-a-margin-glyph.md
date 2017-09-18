---
title: 'Passo a passo: Criando um glifo de margem | Documentos do Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], new - margin glyph
ms.assetid: 814185db-24f9-417f-b3b1-7c5aabb42b45
caps.latest.revision: 29
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
ms.openlocfilehash: f178200514b1452152f196dc97c30c276e3824aa
ms.lasthandoff: 02/22/2017

---
# <a name="walkthrough-creating-a-margin-glyph"></a>Passo a passo: Criando um glifo de margem
Você pode personalizar a aparência das margens editor usando extensões de editor personalizado. Este passo a passo coloca um glifo personalizado na margem do indicador sempre que a palavra "todo" aparece em um comentário do código.  
  
## <a name="prerequisites"></a>Pré-requisitos  
 A partir do Visual Studio 2015, você não instale o SDK do Visual Studio no Centro de download. Ele é fornecido como um recurso opcional na instalação do Visual Studio. Você também pode instalar o SDK do VS mais tarde. Para obter mais informações, consulte [instalar o SDK do Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-mef-project"></a>Criando um projeto MEF  
  
1.  Crie um projeto c# VSIX. (No **novo projeto** caixa de diálogo, selecione **Visual c# / extensibilidade**, em seguida, **projeto VSIX**.) Nomeie a solução `TodoGlyphTest`.  
  
2.  Adicione um item de projeto do classificador de Editor. Para obter mais informações, consulte [criando uma extensão com um modelo de Item Editor](../extensibility/creating-an-extension-with-an-editor-item-template.md).  
  
3.  Exclua os arquivos de classe existentes.  
  
## <a name="defining-the-glyph"></a>Definir o glifo  
 Define um glifo Implementando o <xref:Microsoft.VisualStudio.Text.Editor.IGlyphFactory>interface.</xref:Microsoft.VisualStudio.Text.Editor.IGlyphFactory>  
  
#### <a name="to-define-the-glyph"></a>Para definir o glifo  
  
1.  Adicione um arquivo de classe e nomeie-o `TodoGlyphFactory`.  
  
2.  Adicione o seguinte usando declarações.  
  
     [!code-cs[&#1; VSSDKTodoGlyphTest](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_1.cs) ] 
     [!code-vb [VSSDKTodoGlyphTest n º&1;](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_1.vb)]  
  
3.  Adicione uma classe chamada `TodoGlyphFactory` que implementa <xref:Microsoft.VisualStudio.Text.Editor.IGlyphFactory>.</xref:Microsoft.VisualStudio.Text.Editor.IGlyphFactory>  
  
     [!code-cs[N º&2; VSSDKTodoGlyphTest](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_2.cs) ] 
     [!code-vb [VSSDKTodoGlyphTest n º&2;](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_2.vb)]  
  
4.  Adicione um campo particular que define as dimensões do glifo.  
  
     [!code-cs[N º&3; VSSDKTodoGlyphTest](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_3.cs) ] 
     [!code-vb [VSSDKTodoGlyphTest n º&3;](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_3.vb)]  
  
5.  Implementar `GenerateGlyph` definindo o elemento de interface do usuário do usuário de glifo. `TodoTag`é definido mais adiante neste passo a passo.  
  
     [!code-cs[N º&4; VSSDKTodoGlyphTest](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_4.cs) ] 
     [!code-vb [VSSDKTodoGlyphTest n º&4;](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_4.vb)]  
  
6.  Adicione uma classe chamada `TodoGlyphFactoryProvider` que implementa <xref:Microsoft.VisualStudio.Text.Editor.IGlyphFactoryProvider>.</xref:Microsoft.VisualStudio.Text.Editor.IGlyphFactoryProvider> Exportar esta classe com um <xref:Microsoft.VisualStudio.Utilities.NameAttribute>de "TodoGlyph", um <xref:Microsoft.VisualStudio.Utilities.OrderAttribute>de VsTextMarker depois, um <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>de "código" e um <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute>de TodoTag.</xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute> </xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> </xref:Microsoft.VisualStudio.Utilities.OrderAttribute> </xref:Microsoft.VisualStudio.Utilities.NameAttribute>  
  
     [!code-cs[N º&5; VSSDKTodoGlyphTest](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_5.cs) ] 
     [!code-vb [VSSDKTodoGlyphTest n º&5;](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_5.vb)]  
  
7.  Implementar o <xref:Microsoft.VisualStudio.Text.Editor.IGlyphFactoryProvider.GetGlyphFactory%2A>método instanciando a `TodoGlyphFactory`.</xref:Microsoft.VisualStudio.Text.Editor.IGlyphFactoryProvider.GetGlyphFactory%2A>  
  
     [!code-cs[N º&6; VSSDKTodoGlyphTest](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_6.cs) ] 
     [!code-vb [VSSDKTodoGlyphTest n º&6;](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_6.vb)]  
  
## <a name="defining-a-todo-tag-and-tagger"></a>Definindo uma marca de tarefas pendentes e marcador  
 Defina o relacionamento entre o elemento de interface do usuário que você definiu nas etapas anteriores e margem do indicador, criando um tipo de marca e o marcador e exportá-lo usando um provedor de marcador.  
  
#### <a name="to-define-a-todo-tag-and-tagger"></a>Para definir uma marca de tarefas pendentes e um marcador  
  
1.  Adicione um novo arquivo de classe ao projeto e denomine- `TodoTagger`.  
  
2.  Adicione as seguintes importações.  
  
     [!code-cs[#7 VSSDKTodoGlyphTest](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_7.cs) ] 
     [!code-vb [VSSDKTodoGlyphTest&#7;](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_7.vb)]  
  
3.  Adicione uma classe chamada `TodoTag`.  
  
     [!code-cs[N º&8; VSSDKTodoGlyphTest](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_8.cs) ] 
     [!code-vb [VSSDKTodoGlyphTest n º&8;](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_8.vb)]  
  
4.  Modificar a classe denominada `TodoTagger` que implementa <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601>do tipo `TodoTag`.</xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601>  
  
     [!code-cs[N º&9; VSSDKTodoGlyphTest](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_9.cs) ] 
     [!code-vb [VSSDKTodoGlyphTest n º&9;](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_9.vb)]  
  
5.  Para o `TodoTagger` classe, adicione campos privados para um <xref:Microsoft.VisualStudio.Text.Classification.IClassifier>e para o texto a ser localizado na classificação abrange.</xref:Microsoft.VisualStudio.Text.Classification.IClassifier>  
  
     [!code-cs[N º&10; VSSDKTodoGlyphTest](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_10.cs) ] 
     [!code-vb [VSSDKTodoGlyphTest n º&10;](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_10.vb)]  
  
6.  Adicione um construtor que define o classificador.  
  
     [!code-cs[N º&11; VSSDKTodoGlyphTest](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_11.cs) ] 
     [!code-vb [VSSDKTodoGlyphTest n º&11;](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_11.vb)]  
  
7.  Implementar o <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601.GetTags%2A>método localizando todos os a classificação abrange cujos nomes incluem a palavra "comentário" e cujo texto inclui o texto de pesquisa.</xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601.GetTags%2A> Sempre que o texto de pesquisa for encontrado, volta produzem um novo <xref:Microsoft.VisualStudio.Text.Tagging.TagSpan%601>do tipo `TodoTag`.</xref:Microsoft.VisualStudio.Text.Tagging.TagSpan%601>  
  
     [!code-cs[#12 VSSDKTodoGlyphTest](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_12.cs) ] 
     [!code-vb [VSSDKTodoGlyphTest&#12;](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_12.vb)]  
  
8.  Declarar uma `TagsChanged` eventos.  
  
     [!code-cs[VSSDKTodoGlyphTest&13;](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_13.cs) ] 
     [!code-vb [VSSDKTodoGlyphTest&13;](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_13.vb)]  
  
9. Adicione uma classe chamada `TodoTaggerProvider` que implementa <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider>e exportá-lo com um <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>de "código" e um <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute>de TodoTag.</xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute> </xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> </xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider>  
  
     [!code-cs[#14 VSSDKTodoGlyphTest](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_14.cs)]
   [!code-vb[VSSDKTodoGlyphTest&#14;  ](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_14.vb)]  
  
10. Importar <xref:Microsoft.VisualStudio.Text.Classification.IClassifierAggregatorService>.</xref:Microsoft.VisualStudio.Text.Classification.IClassifierAggregatorService>  
  
     [!code-cs[#15 VSSDKTodoGlyphTest](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_15.cs) ] 
     [!code-vb [VSSDKTodoGlyphTest&15;](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_15.vb)]  
  
11. Implementar o <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider.CreateTagger%2A>método instanciando a `TodoTagger`.</xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider.CreateTagger%2A>  
  
     [!code-cs[N º&16; VSSDKTodoGlyphTest](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_16.cs) ] 
     [!code-vb [VSSDKTodoGlyphTest&16;](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_16.vb)]  
  
## <a name="building-and-testing-the-code"></a>Compilar e testar o código  
 Para testar esse código, crie a solução TodoGlyphTest e executá-lo na instância experimental.  
  
#### <a name="to-build-and-test-the-todoglyphtest-solution"></a>Para compilar e testar a solução TodoGlyphTest  
  
1.  Compile a solução.  
  
2.  Execute o projeto pressionando F5. Uma segunda instância do Visual Studio é instanciada.  
  
3.  Certifique-se de que está mostrando a margem do indicador. (No **ferramentas** menu, clique em **opções**. No **Editor de texto** página, certifique-se de que **margem do indicador** está selecionada.)  
  
4.  Abra um arquivo de código que tem comentários. Adicione a palavra "todo" para uma das seções de comentário.  
  
5.  Um círculo azul claro que tem um contorno azul escuro deve aparecer na margem do indicador à esquerda da janela de código.
