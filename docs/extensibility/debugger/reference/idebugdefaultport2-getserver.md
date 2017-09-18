---
title: IDebugDefaultPort2::GetServer | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugDefaultPort2::GetServer
helpviewer_keywords:
- IDebugDefaultPort2::GetServer
ms.assetid: cacb4b74-0f39-471c-af38-54b73f5b2868
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
ms.openlocfilehash: 7afe3a23b6ba4d5465b0b24c9568a51fd028d0f8
ms.lasthandoff: 02/22/2017

---
# <a name="idebugdefaultport2getserver"></a>IDebugDefaultPort2::GetServer
Esse método obtém uma interface para o servidor que essa porta é no.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetServer(  
   IDebugCoreServer3** ppServer  
);  
```  
  
```c#  
int GetServer(  
   out IDebugCoreServer3 ppServer  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `ppServer`  
 [out] Retorna um objeto que implementa o [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md) interface.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna um código de erro.  
  
## <a name="remarks"></a>Comentários  
 O [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md) é implementada pelo Visual Studio e representa o servidor que a porta está localizada em.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugDefaultPort2](../../../extensibility/debugger/reference/idebugdefaultport2.md)   
 [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)
