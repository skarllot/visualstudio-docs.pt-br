---
title: IDebugEngine2::SetException | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugEngine2::SetException
helpviewer_keywords:
- IDebugEngine2::SetException
ms.assetid: e6f5ec48-09e8-4b9b-9dc9-55f8d883f1b7
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
ms.openlocfilehash: ab78d776c54f476d651a5c92f63d2f5f2fccacc8
ms.lasthandoff: 02/22/2017

---
# <a name="idebugengine2setexception"></a>IDebugEngine2::SetException
Especifica como o mecanismo de depuração (DE) deve tratar de uma determinada exceção.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
HRESULT SetException(   
   EXCEPTION_INFO* pException  
);  
```  
  
```c#  
int SetException(   
   EXCEPTION_INFO[] pException  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pException`  
 [in] Um [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md) estrutura que descreve a exceção e depurá-lo.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna um código de erro.  
  
## <a name="remarks"></a>Comentários  
 A DE podia ser instruída para interromper o programa gera uma exceção na primeira oportunidade, segunda chance, ou não.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)   
 [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md)
