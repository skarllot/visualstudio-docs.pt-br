---
title: "Passo a passo: Personalizando a exibição de texto | Documentos do Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], new - customizing the view
ms.assetid: 32d32ac8-22ff-4de7-af69-bd46ec4ad9bf
caps.latest.revision: 22
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
ms.openlocfilehash: e40368ed6aaf68b747f19cffe4e378a89ff6c0b5
ms.lasthandoff: 02/22/2017

---
# <a name="walkthrough-customizing-the-text-view"></a>Passo a passo: Personalizando a exibição de texto
Você pode personalizar uma exibição de texto, modifique qualquer uma das propriedades a seguir em seu mapa de formatação do editor:  
  
-   Margem do indicador  
  
-   Cursor de inserção  
  
-   Cursor de substituição  
  
-   Texto selecionado  
  
-   Texto selecionado inativo (ou seja, texto selecionado que perdeu o foco)  
  
-   Espaço em branco visível  
  
## <a name="prerequisites"></a>Pré-requisitos  
 A partir do Visual Studio 2015, você não instale o SDK do Visual Studio no Centro de download. Ele é fornecido como um recurso opcional na instalação do Visual Studio. Você também pode instalar o SDK do VS mais tarde. Para obter mais informações, consulte [instalar o SDK do Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-mef-project"></a>Criando um projeto MEF  
  
1.  Crie um projeto c# VSIX. (No **novo projeto** caixa de diálogo, selecione **Visual c# / extensibilidade**, em seguida, **projeto VSIX**.) Nomeie a solução `ViewPropertyTest`.  
  
2.  Adicione um modelo de item Editor classificador ao projeto. Para obter mais informações, consulte [criando uma extensão com um modelo de Item Editor](../extensibility/creating-an-extension-with-an-editor-item-template.md).  
  
3.  Exclua os arquivos de classe existentes.  
  
## <a name="defining-the-content-type"></a>Definindo o tipo de conteúdo  
  
1.  Adicione um arquivo de classe e nomeie-o `ViewPropertyModifier`.  
  
2.  Adicione o seguinte `using` diretivas:  
  
     [!code-cs[&#1; VSSDKViewPropertyTest](../extensibility/codesnippet/CSharp/walkthrough-customizing-the-text-view_1.cs) ] 
     [!code-vb [VSSDKViewPropertyTest n º&1;](../extensibility/codesnippet/VisualBasic/walkthrough-customizing-the-text-view_1.vb)]  
  
3.  Declare uma classe denominada `TestViewCreationListener` que herda de <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener>.</xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener> Exporte esta classe com os seguintes atributos:  
  
    -   <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>para especificar o tipo de conteúdo ao qual este ouvinte se aplica.</xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>  
  
    -   <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute>para especificar a função deste ouvinte.</xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute>  
  
     [!code-cs[N º&2; VSSDKViewPropertyTest](../extensibility/codesnippet/CSharp/walkthrough-customizing-the-text-view_2.cs)]
     [!code-vb[VSSDKViewPropertyTest n º&2;](../extensibility/codesnippet/VisualBasic/walkthrough-customizing-the-text-view_2.vb)]  
  
4.  Nessa classe, importar <xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMapService>.</xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMapService>  
  
     [!code-cs[N º&3; VSSDKViewPropertyTest](../extensibility/codesnippet/CSharp/walkthrough-customizing-the-text-view_3.cs) ] 
     [!code-vb [VSSDKViewPropertyTest n º&3;](../extensibility/codesnippet/VisualBasic/walkthrough-customizing-the-text-view_3.vb)]  
  
## <a name="changing-the-view-properties"></a>Alterando as propriedades de exibição  
  
1.  Implementar o <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener.TextViewCreated%2A>método para que as propriedades de exibição são alteradas quando o modo de exibição é aberto.</xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener.TextViewCreated%2A> Para fazer a alteração, primeiro localize a <xref:System.Windows.ResourceDictionary>que corresponde à proporção do modo de exibição que você deseja localizar.</xref:System.Windows.ResourceDictionary> Em seguida, altere a propriedade apropriada no dicionário de recursos e defina as propriedades. Em lote as chamadas para o <xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMap.SetProperties%2A>método chamando o <xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMap.BeginBatchUpdate%2A>método antes de definir as propriedades e, em seguida, o <xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMap.EndBatchUpdate%2A>depois de definir as propriedades.</xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMap.EndBatchUpdate%2A> </xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMap.BeginBatchUpdate%2A> </xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMap.SetProperties%2A>  
  
     [!code-cs[N º&4; VSSDKViewPropertyTest](../extensibility/codesnippet/CSharp/walkthrough-customizing-the-text-view_4.cs) ] 
     [!code-vb [VSSDKViewPropertyTest n º&4;](../extensibility/codesnippet/VisualBasic/walkthrough-customizing-the-text-view_4.vb)]  
  
## <a name="building-and-testing-the-code"></a>Compilar e testar o código  
  
1.  Compile a solução.  
  
     Quando você executa este projeto no depurador, uma segunda instância do Visual Studio é instanciada.  
  
2.  Crie um arquivo de texto e digite algum texto.  
  
    -   O cursor de inserção deve ser magenta e o cursor de substituição deve ser turquesa.  
  
    -   Margem do indicador (à esquerda do modo de exibição de texto) deve ser a luz verde.  
  
3.  Selecione o texto que você acabou de digitar. A cor do texto selecionado deve ser clara rosa.  
  
4.  Embora o texto estiver selecionado, clique em qualquer lugar fora da janela de texto. A cor do texto selecionado deve ser rosa escuro.  
  
5.  Ative o espaço em branco visível. (No **editar** , aponte para **avançado** e, em seguida, clique em **exibir espaço em branco**). Digite algumas guias no texto. As setas vermelhas que representam as guias devem ser exibidas.  
  
## <a name="see-also"></a>Consulte também  
 [Serviço de linguagem e pontos de extensão de Editor](../extensibility/language-service-and-editor-extension-points.md)
