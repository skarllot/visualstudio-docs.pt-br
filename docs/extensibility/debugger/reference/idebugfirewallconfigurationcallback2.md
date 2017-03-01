---
title: IDebugFirewallConfigurationCallback2 | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- IDebugFirewallConfigurationCallback2 interface
ms.assetid: 0827361c-b97c-4851-9898-ab6d88c81811
caps.latest.revision: 8
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
ms.openlocfilehash: 7c0fbdc149627085d46dc87ace0caac8a6640083
ms.lasthandoff: 02/22/2017

---
# <a name="idebugfirewallconfigurationcallback2"></a>IDebugFirewallConfigurationCallback2
Permite que um mecanismo de depuração que usa DCOM para perguntar a [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] interface do usuário para certificar-se de que o firewall não bloqueará a depuração remota.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
IDebugFirewallConfigurationCallback2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Observações para implementadores  
 Implementado pelo objeto de porta de depuração do Gerenciador de sessão.  
  
## <a name="methods"></a>Métodos  
 A tabela a seguir mostra os métodos de `IDebugFirewallConfigurationCallback2`.  
  
|Método|Descrição|  
|------------|-----------------|  
|[EnsureDCOMUnblocked](../../../extensibility/debugger/reference/idebugfirewallconfigurationcallback2-ensuredcomunblocked.md)|Solicita que o firewall não bloqueie a depuração remota.|  
  
## <a name="requirements"></a>Requisitos  
 Cabeçalho: Msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll
