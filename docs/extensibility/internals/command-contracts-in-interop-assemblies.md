---
title: Comando contratos em Assemblies de interoperabilidade | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- command handling with interop assemblies, command contracts
- interop assemblies, command contracts
ms.assetid: 57245708-f539-42dc-8963-2754a48f0189
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
ms.openlocfilehash: 6655bf8fc2fbfce975dafa2d0ba78dd80c15ee25
ms.lasthandoff: 02/22/2017

---
# <a name="command-contracts-in-interop-assemblies"></a>Comando contratos em Assemblies de interoperabilidade
O contrato básico para tratamento de comandos por meio de <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>interface é que o ambiente chama o <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A>método para determinar se há suporte para o comando e, em caso afirmativo, para determinar seu estado e texto.</xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> </xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> Em seguida, o ambiente chama o <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A>método para executar o comando.</xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A>  
  
 O <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A>método é tratado de forma idêntica para todos os comandos.</xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> Comunicação, se necessário (por exemplo, com listas suspensas) é gerenciada pelo chamar o <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A>método com os parâmetros apropriados.</xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> A interpretação desses parâmetros depende do comando especificado.  
  
 Se o destino do comando retorna valores de parâmetro de saída, o chamador sempre é responsável por liberar quaisquer recursos que foram alocados. Como esse parâmetro é uma variante, limpando a variante libera os recursos.  
  
 Em casos em que os comandos devem operar em uma janela de hierarquia, o <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>interface deve ser usada.</xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> O <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>interface tem um contrato semelhante com métodos semelhantes: <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A>e <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.ExecCommand%2A>.</xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.ExecCommand%2A> </xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A> </xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>  
  
## <a name="see-also"></a>Consulte também  
 [Como os VSPackages adicionar elementos de Interface do usuário](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [Roteamento de comando em VSPackages](../../extensibility/internals/command-routing-in-vspackages.md)   
 [Implementação](../../extensibility/internals/command-implementation.md)
