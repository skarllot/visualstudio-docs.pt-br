---
title: "Objetos de contexto de seleção | Documentos do Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- selection, tracking
- selection, context objects
ms.assetid: 7308ea8f-a42c-47e5-954e-7dee933dce7a
caps.latest.revision: 13
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
ms.openlocfilehash: 3fa5093ee38c364a4766160f8642755bc0b2a23f
ms.lasthandoff: 02/22/2017

---
# <a name="selection-context-objects"></a>Objetos de contexto da seleção
O [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ambiente de desenvolvimento integrado (IDE) usa um objeto de contexto global de seleção para determinar o que deve ser exibido no IDE. Cada janela no IDE pode ter seu próprio objeto de contexto de seleção enviado para o contexto de seleção global. O IDE atualiza o contexto da seleção global com valores de uma janela quando essa janela tem o foco. Para obter mais informações, consulte [comentários para o usuário](../../extensibility/internals/feedback-to-the-user.md).  
  
 Cada quadro de janela ou um site no IDE tem um serviço chamado <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection>.</xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection> O objeto criado pelo VSPackage que é localizado no quadro da janela deve chamar o `QueryService` método para obter um ponteiro para o <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection>interface.</xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection>  
  
 Janelas de quadro podem manter partes de suas informações de contexto de seleção sejam propagadas para o contexto de seleção global quando eles são iniciados. Isso é útil para janelas de ferramenta que pode ser necessário iniciar com uma seleção vazia.  
  
 Modificando os seleção global contexto aciona eventos VSPackages pode monitorar. Os VSPackages pode executar as seguintes tarefas ao implementar `IVsTrackSelectionEx` e <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection>interfaces:</xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection>  
  
-   Atualize o arquivo ativo no momento em uma hierarquia.  
  
-   Monitore as alterações a determinados tipos de elementos. Por exemplo, se o VSPackage usa um relacionamento especial **propriedades** janela, você pode monitorar as alterações no active **propriedades** janela e reinicie sua quando necessário.  
  
 A sequência a seguir mostra a sequência normal de seleção de controle.  
  
1.  O IDE recupera o contexto da seleção da janela recém-aberta e o coloca no contexto global de seleção. Se o contexto de seleção Usar HIERARCHY_DONTPROPAGATE ou SELCONTAINER_DONTPROPAGATE, essa informação não é propagada para o contexto global. Para obter mais informações, consulte [comentários para o usuário](../../extensibility/internals/feedback-to-the-user.md).  
  
2.  Eventos de notificação são transmitidos para qualquer VSPackage que solicitou.  
  
3.  O VSPackage age sobre os eventos que ele recebe ao executar atividades como a atualização de uma hierarquia, reativando uma ferramenta ou outras tarefas semelhantes.  
  
## <a name="see-also"></a>Consulte também  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx></xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection></xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection>   
 [Hierarquias no Visual Studio](../../extensibility/internals/hierarchies-in-visual-studio.md)   
 [Seleção e moeda no IDE](../../extensibility/internals/selection-and-currency-in-the-ide.md)   
 [Tipos de projeto](../../extensibility/internals/project-types.md)
