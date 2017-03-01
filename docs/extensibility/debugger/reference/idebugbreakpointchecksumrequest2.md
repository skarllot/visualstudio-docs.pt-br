---
title: IDebugBreakpointChecksumRequest2 | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- IDebugBreakpointChecksumRequest2 interface
ms.assetid: 9cfdbca5-052c-48e9-8411-e2e9e4065d00
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
ms.openlocfilehash: b54c044bd920967af59396f0bb10ac528b2b9847
ms.lasthandoff: 02/22/2017

---
# <a name="idebugbreakpointchecksumrequest2"></a>IDebugBreakpointChecksumRequest2
Representa uma soma de verificação de documento para uma solicitação de ponto de interrupção.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
IDebugBreakpointChecksumRequest2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Observações para implementadores  
 Implementado pelo [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] depurar o pacote e consumidos por mecanismos de depuração.  
  
## <a name="methods"></a>Métodos  
 A tabela a seguir mostra os métodos de `IDebugBreakpointChecksumRequest2`.  
  
|Método|Descrição|  
|------------|-----------------|  
|[GetChecksum](../../../extensibility/debugger/reference/idebugbreakpointchecksumrequest2-getchecksum.md)|Recupera a soma de verificação de documento para uma solicitação de ponto de interrupção recebe o identificador exclusivo do algoritmo de soma de verificação para usar.|  
|[IsChecksumEnabled](../../../extensibility/debugger/reference/idebugbreakpointchecksumrequest2-ischecksumenabled.md)|Determina se a soma de verificação está habilitada para este documento.|  
  
## <a name="requirements"></a>Requisitos  
 Cabeçalho: Msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll
