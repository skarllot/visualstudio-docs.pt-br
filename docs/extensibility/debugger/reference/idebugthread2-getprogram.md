---
title: IDebugThread2::GetProgram | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugThread2::GetProgram
helpviewer_keywords:
- IDebugThread2::GetProgram
ms.assetid: 8c9c5ea1-2031-472e-bc8f-30e22e754566
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
ms.openlocfilehash: 7183d1794ed499e967aabed1eba264cc70bfd16a
ms.lasthandoff: 02/22/2017

---
# <a name="idebugthread2getprogram"></a>IDebugThread2::GetProgram
Obtém o programa no qual um thread está em execução.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
HRESULT GetProgram (   
   IDebugProgram2** ppProgram  
);  
```  
  
```c#  
int GetProgram (   
   out IDebugProgram2 ppProgram  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `ppProgram`  
 [out] Retorna um [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) que representa o programa esse thread está sendo executado no objeto.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna um código de erro.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
