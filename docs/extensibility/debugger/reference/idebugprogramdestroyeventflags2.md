---
title: IDebugProgramDestroyEventFlags2 | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- IDebugProgramDestroyEventFlags2 interface
ms.assetid: d384ff71-dc71-40b9-a871-801f8b6a3418
caps.latest.revision: 7
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
ms.openlocfilehash: c342fe1d4ac8f8f54f78e165d7a65c392302c17e
ms.lasthandoff: 02/22/2017

---
# <a name="idebugprogramdestroyeventflags2"></a>IDebugProgramDestroyEventFlags2
Permite que um mecanismo de depuração substituir o comportamento padrão da [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] UI ao encerrar uma sessão de depuração.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
IDebugProgramDestroyEventFlags2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Observações para implementadores  
 Essa interface é implementada pelos mecanismos de depuração. É útil para hosts que podem criar e destruir vários programas durante a vida útil de um processo.  
  
## <a name="methods"></a>Métodos  
 A tabela a seguir mostra os métodos de `IDebugProgramDestroyEventFlags2`.  
  
|Método|Descrição|  
|------------|-----------------|  
|[GetFlags](../../../extensibility/debugger/reference/idebugprogramdestroyeventflags2-getflags.md)|Recupera o programa destruir sinalizadores.|  
  
## <a name="remarks"></a>Comentários  
 O comportamento padrão do [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] interface do usuário é retornar ao modo de design depois que todos os programas enviou um programa destruir o evento. Essa interface permite que um mecanismo de depuração alterar esse comportamento.  
  
## <a name="requirements"></a>Requisitos  
 Cabeçalho: Msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll
