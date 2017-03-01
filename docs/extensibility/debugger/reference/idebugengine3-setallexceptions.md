---
title: IDebugEngine3::SetAllExceptions | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugEngine3::SetAllExceptions
helpviewer_keywords:
- IDebugEngine3::SetAllExceptions
ms.assetid: 8f03a6ac-a854-42f7-933c-a2df1b351975
caps.latest.revision: 10
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
ms.openlocfilehash: 714152419bb8adf6074eac698805dfc106927d2c
ms.lasthandoff: 02/22/2017

---
# <a name="idebugengine3setallexceptions"></a>IDebugEngine3::SetAllExceptions
Esse método define o estado de todas as exceções pendentes.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT SetAllExceptions(  
   EXCEPTION_STATE dwState  
);  
```  
  
```c#  
int SetAllExceptions(  
   enum_EXCEPTION_STATE dwState  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `dwState`  
 [in] Um do [EXCEPTION_STATE](../../../extensibility/debugger/reference/exception-state.md) valores.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retornará o código de erro.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugEngine3](../../../extensibility/debugger/reference/idebugengine3.md)   
 [EXCEPTION_STATE](../../../extensibility/debugger/reference/exception-state.md)
