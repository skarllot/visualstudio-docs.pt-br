---
title: IDebugEngine2::SetException | Microsoft Docs
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
ms.translationtype: MT
ms.sourcegitcommit: 4a36302d80f4bc397128e3838c9abf858a0b5fe8
ms.openlocfilehash: 2d7d1631c1b5179d51a80b2094766c4ed053ac36
ms.contentlocale: pt-br
ms.lasthandoff: 09/26/2017

---
# <a name="idebugengine2setexception"></a>IDebugEngine2::SetException
Especifica como o mecanismo de depuração (DE) deve tratar uma exceção especificada.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT SetException(   
   EXCEPTION_INFO* pException  
);  
```  
  
```csharp  
int SetException(   
   EXCEPTION_INFO[] pException  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pException`  
 [in] Um [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md) estrutura que descreve a exceção e depurá-lo.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retorna `S_OK`; caso contrário, retorna um código de erro.  
  
## <a name="remarks"></a>Comentários  
 A DE pode ser instruída para parar o programa de gerar uma exceção na primeira instância, a segunda oportunidade, ou não.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)   
 [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md)
