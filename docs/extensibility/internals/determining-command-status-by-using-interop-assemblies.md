---
title: Determinar o Status de comando usando Assemblies de interoperabilidade | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- interop assemblies, determining command status
- command handling with interop assemblies, status
ms.assetid: 2f5104d1-7b4c-4ca0-a626-50530a8f7f5c
caps.latest.revision: 18
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
ms.openlocfilehash: fb5476a125582a3efb826b29220fbf7dd4e373d2
ms.lasthandoff: 02/22/2017

---
# <a name="determining-command-status-by-using-interop-assemblies"></a>Determinar o Status de comando usando Assemblies de interoperabilidade
Um VSPackage deve controlar do estado dos comandos pode manipular. O ambiente não pode determinar quando um comando tratado no VSPackage fica habilitado ou desabilitado. É responsabilidade do VSPackage para informar o ambiente sobre estados de comando, por exemplo, o estado do geral comandos como **Recortar**, **cópia**, e **colar**.  
  
## <a name="status-notification-sources"></a>Fontes de notificação de status  
 O ambiente recebe informações sobre comandos por meio de 'VSPackages <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A>método, que é parte da implementação do VSPackage do <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>interface.</xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> </xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> O ambiente chama o <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A>método do VSPackage sob duas condições:</xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A>  
  
-   Quando um usuário abre um menu principal ou um menu de contexto (clicando), o ambiente executa o <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A>método em todos os comandos no menu para determinar seu estado.</xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A>  
  
-   Quando o VSPackage solicita que o ambiente de atualizar a interface do usuário (UI) atual. Isso ocorre como comandos que são visíveis no momento para o usuário, como o **Recortar**, **cópia**, e **colar** agrupamento na barra de ferramentas padrão, que tornam-se habilitados e desabilitados em resposta às ações do usuário e o contexto.  
  
 Uma vez que o shell hospeda vários VSPackages, desempenho do shell seria inaceitável degradar se fosse necessário sondar cada VSPackage para determinar o status do comando. Em vez disso, o VSPackage ativamente deve notificar o ambiente quando sua interface do usuário for alterada no momento da alteração. Para obter mais informações sobre a notificação de atualização, consulte [atualizar a Interface do usuário](../../extensibility/updating-the-user-interface.md).  
  
## <a name="status-notification-failure"></a>Falha de notificação de status  
 Falha do VSPackage para notificar o ambiente de um comando de alteração de estado pode colocar a interface do usuário em um estado inconsistente. Lembre-se de que qualquer um dos seus comandos de menu de contexto ou menu podem ser colocados em uma barra de ferramentas do usuário. Portanto, atualizar a interface do usuário somente quando abre um menu de contexto ou menu não é suficiente.  
  
## <a name="see-also"></a>Consulte também  
 [Como os VSPackages adicionar elementos de Interface do usuário](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [Implementação](../../extensibility/internals/command-implementation.md)
