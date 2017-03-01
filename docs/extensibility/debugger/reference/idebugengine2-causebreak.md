---
title: IDebugEngine2::CauseBreak | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugEngine2::CauseBreak
helpviewer_keywords:
- IDebugEngine2::CauseBreak
ms.assetid: 17fe4698-b04e-4798-8412-80e0da60c387
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
ms.openlocfilehash: 1385dd7d1cda48f39c17615755fc07c7c7570eea
ms.lasthandoff: 02/22/2017

---
# <a name="idebugengine2causebreak"></a>IDebugEngine2::CauseBreak
Solicitações de todos os programas que estão sendo depurado por esse mecanismo de depuração (DE) para interromper a execução da próxima vez que um de seus threads tentará executar.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
HRESULT CauseBreak(   
   void   
);  
```  
  
```c#  
int CauseBreak();  
```  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna um código de erro.  
  
## <a name="remarks"></a>Comentários  
 Esse método é assíncrono: um [IDebugBreakEvent2](../../../extensibility/debugger/reference/idebugbreakevent2.md) evento é enviado quando o programa tenta executar depois que este método é chamado em seguida.  
  
## <a name="see-also"></a>Consulte também  
 [CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md)   
 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
