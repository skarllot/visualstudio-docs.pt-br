---
title: "Informações de parâmetro um Service1 de idioma herdado | Documentos do Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- language services, method tips
- method tips
- language services, parameter info tooltip
- IVsMethodData interface
- Parameter Info (IntelliSense)
ms.assetid: f367295e-45b6-45d2-9ec8-77481743beef
caps.latest.revision: 11
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
ms.openlocfilehash: 03db0a205d53751b244a6f8aaf4bd51b1b5e027f
ms.lasthandoff: 02/22/2017

---
# <a name="parameter-info-in-a-legacy-language-service"></a>Informações de parâmetro em um serviço de linguagem herdado
A dica de ferramenta de informações do parâmetro IntelliSense fornece aos usuários com dicas sobre onde eles estão em uma construção de linguagem.  
  
 Serviços de linguagem herdada são implementados como parte de um VSPackage, mas a maneira mais recente para implementar recursos de serviço de linguagem é usar extensões MEF. Para obter mais informações, consulte [estendendo o Editor e serviços de linguagem](../../extensibility/extending-the-editor-and-language-services.md).  
  
> [!NOTE]
>  É recomendável que você comece a usar o novo editor de API assim que possível. Isso irá melhorar o desempenho do seu serviço de linguagem e lhe permitem tirar proveito dos novos recursos do editor.  
  
## <a name="how-parameter-info-tooltips-work"></a>Como funciona a dica de ferramenta de informações de parâmetro  
 Quando você digita uma instrução no editor, o VSPackage exibe uma janela de pequena dica de ferramenta contendo a definição de linha que está sendo digitada. Por exemplo, se você digitar uma instrução Microsoft Foundation Classes (MFC) (como `pMainFrame ->UpdateWindow`) e pressione o parêntese de abertura tecla para iniciar a lista de parâmetros, uma dica de método aparece exibindo a definição do `UpdateWindow` método.  
  
 Dicas de ferramentas de informações de parâmetro são geralmente usadas em conjunto com a conclusão de instrução. Eles são mais úteis para os idiomas que têm parâmetros ou outras informações formatadas após a palavra-chave ou o nome do método.  
  
 As dicas de ferramentas de informações de parâmetro são iniciadas pelo serviço de linguagem através de interceptação de comando. Para interceptar caracteres de usuário, o objeto de serviço de linguagem deve implementar o <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>interface e passar a exibição de texto em um ponteiro para sua <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>implementação, chamando o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A>método o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>interface.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> </xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A> </xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> </xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> O filtro de comando intercepta comandos digitados na janela de código. Monitore as informações de comando para saber quando exibir informações de parâmetro para o usuário. Você pode usar o mesmo filtro de comando para conclusão de instrução, marcadores de erro e assim por diante.  
  
 Quando você digita uma palavra-chave para a qual o serviço de linguagem pode fornecer dicas, em seguida, o serviço de linguagem cria um <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow>objeto e chama o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateTipWindow%2A>método o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>interface para notificar o IDE para exibir uma dica.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> </xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateTipWindow%2A> </xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow> Crie o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow>objeto usando `VSLocalCreateInstance` e especificando o coclass `CLSID_VsMethodTipWindow`.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow> `VsLocalCreateInstance`é uma função definida no vsdoc.h de arquivo de cabeçalho que chama `QueryService` para o registro local e chamadas `CreateInstance` nesse objeto para o `CLSID_VsMethodTipWindow`.  
  
## <a name="providing-a-method-tip"></a>Fornecendo uma dica de método  
 Para fornecer uma dica de método, chamar o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow.SetMethodData%2A>método o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow>interface, passando a implementação do <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData>interface.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData> </xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow> </xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow.SetMethodData%2A>  
  
 Quando seu <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData>classe é invocada, seus métodos são chamados na seguinte ordem:</xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData>  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetContextStream%2A></xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetContextStream%2A>  
  
     Retorna a posição e o comprimento dos dados relevantes no buffer de texto atual. Isso instrui o IDE não ocultar esses dados com a janela de dica de ferramenta.  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetCurMethod%2A></xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetCurMethod%2A>  
  
     Retorna o número de método (índice baseado em zero) a ser exibido inicialmente. Por exemplo, se você retornar zero, o primeiro método sobrecarregado inicialmente é apresentado.  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetOverloadCount%2A></xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetOverloadCount%2A>  
  
     Retorna o número de métodos sobrecarregados que são aplicáveis no contexto atual. Se você retornar um valor maior que 1 para esse método, a exibição de texto exibe e setas para você. Se você clicar na seta para baixo, o IDE chama o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.NextMethod%2A>método.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.NextMethod%2A> Se você clicar na seta para cima, o IDE chama o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.PrevMethod%2A>método.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.PrevMethod%2A>  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetMethodText%2A></xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetMethodText%2A>  
  
     O texto da dica de ferramenta informações do parâmetro é construído durante várias chamadas para o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetMethodText%2A>e <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetParameterText%2A>métodos.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetParameterText%2A> </xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetMethodText%2A>  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetParameterCount%2A></xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetParameterCount%2A>  
  
     Retorna o número de parâmetros para exibir no método.  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetParameterText%2A></xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetParameterText%2A>  
  
     Se você retornar um número de método correspondente com a sobrecarga que você deseja exibir, esse método é chamado, seguido por uma chamada para o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.UpdateView%2A>método.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.UpdateView%2A>  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.UpdateView%2A></xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.UpdateView%2A>  
  
     Informa o serviço de linguagem para atualizar o editor quando uma dica de método é exibida. No <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.UpdateView%2A>método, chame o seguinte:</xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.UpdateView%2A>  
  
    ```  
    <pTxWin> ->UpdateTipWindow(<pTip>, UTW_CONTENTCHANGED | UTW_CONTEXTCHANGED).  
    ```  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.OnDismiss%2A></xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.OnDismiss%2A>  
  
     Você recebe uma chamada para o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.OnDismiss%2A>método quando você fechar a janela de dica de método.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.OnDismiss%2A>
