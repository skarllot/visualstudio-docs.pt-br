---
title: Barra suspensa | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - drop-down bar
ms.assetid: 4bb621bd-72f5-43d5-916f-9f66617da049
caps.latest.revision: 12
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
ms.openlocfilehash: 816ee96903ee216a23c08f22366a45ce9ce80753
ms.lasthandoff: 02/22/2017

---
# <a name="drop-down-bar"></a>Barra de menu suspenso
A barra de menu suspenso é fornecida na parte superior da janela de código e contém duas listas suspensas.  
  
## <a name="drop-down-bar-interfaces"></a>Interfaces de barra de menu suspenso  
 Em [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)], por exemplo, a barra de menu suspenso contém listas de [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)] itens e [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)] funções de membro de itens, como mostrado na figura a seguir.  
  
 ![Barras suspensas](~/extensibility/media/vsdropdown_bar.gif "vsDropdown_bar")  
Barra de menu suspenso  
  
 Ao implementar uma barra de menu suspenso, há quatro interfaces de importância fundamental:  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarClient></xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarClient>  
  
     Implemente essa interface para inserir o conteúdo da barra de menu suspenso. Cada combinação suspensas pode conter texto sem formatação ou texto decorativo (negrito, sublinhado ou itálico), pode ter fonte esmaecido cores ou cores de fonte do texto de janela e, opcionalmente, pode fornecer um bitmap pequeno ao lado do item de lista suspensa. Como o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet>interface, imagens de bitmap são fornecidas em listas de imagens.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet> Cada combinação suspensas pode ter uma lista de imagem diferente; No entanto, cada lista de imagens deve conter imagens da mesma altura. Além disso, usando o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarClient.GetComboTipText%2A>método, você pode fornecer uma dica de ferramenta para cada combinação.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarClient.GetComboTipText%2A>  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarManager></xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarManager>  
  
     Chame essa interface para criar ou destruir a barra suspensa para uma janela de código. Essa interface também pode ser usada para determinar se uma barra suspensa já está anexada a uma janela de código chamando o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarManager.GetDropdownBar%2A>método.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarManager.GetDropdownBar%2A> Chamada <xref:System.Runtime.InteropServices.Marshal.QueryInterface%2A>para <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarManager>de <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow>.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow> </xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarManager> </xref:System.Runtime.InteropServices.Marshal.QueryInterface%2A>  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBar></xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBar>  
  
     Chame essa interface para se comunicar diretamente com a barra de menu suspenso. Você pode usar essa interface para forçar uma atualização de lista suspensa da barra conteúdo ou para alterar a seleção de uma das caixas de listagem.  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextManagerEvents></xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextManagerEvents>  
  
     Se você registrou o `ShowDropdownBarOption` em sua chave de registro do serviço de linguagem, em seguida, o Gerenciador de janelas de código deve monitorar esse evento para sincronizar com as preferências do usuário sobre se a barra suspensa deve ser exibida. Se você não registrar essa opção em sua chave de serviço de linguagem, a opção de mostrar ou ocultar a barra suspensa está desabilitada no **opções** menu.  
  
## <a name="attaching-a-drop-down-bar-to-a-code-window"></a>Anexar uma barra de menu suspenso em uma janela de código  
 Para anexar uma barra de menu suspenso para a janela de código quando ele é criado, um serviço de linguagem deve ser anexado à lista suspensa da barra quando o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager.AddAdornments%2A>método é chamado.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager.AddAdornments%2A> Se uma chamada para o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarManager.GetDropdownBar%2A>método indica que uma barra suspensa ainda não existir, em seguida, chame <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarManager.AddDropdownBar%2A>.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarManager.AddDropdownBar%2A> </xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarManager.GetDropdownBar%2A> Para acessar o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarManager>da interface, chame <xref:System.Runtime.InteropServices.Marshal.QueryInterface%2A>do <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow>ponteiro retornado para você quando seu <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager>implementação foi anexada.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager> </xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow> </xref:System.Runtime.InteropServices.Marshal.QueryInterface%2A> </xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarManager>  
  
## <a name="see-also"></a>Consulte também  
 [Personalizando o Windows de código usando a API herdada](../extensibility/customizing-code-windows-by-using-the-legacy-api.md)   
 [Suporte para a barra de navegação em um serviço de linguagem herdado](../extensibility/internals/support-for-the-navigation-bar-in-a-legacy-language-service.md)
