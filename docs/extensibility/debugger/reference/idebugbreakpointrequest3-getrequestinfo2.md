---
title: IDebugBreakpointRequest3::GetRequestInfo2 | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugBreakpointRequest3::GetRequestInfo2
helpviewer_keywords:
- IDebugBreakpointRequest3::GetRequestInfo2
ms.assetid: 33942e4a-0a0a-49e8-a693-004954f6d38a
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
ms.openlocfilehash: b92efe86d039cd292f5baca7ad49d2a66f808ef1
ms.lasthandoff: 02/22/2017

---
# <a name="idebugbreakpointrequest3getrequestinfo2"></a>IDebugBreakpointRequest3::GetRequestInfo2
Esse método obtém as informações de solicitação de ponto de interrupção que descreve esta solicitação de ponto de interrupção.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
HRESULT GetRequestInfo2(  
   BPREQI_FIELDS      dwFields,  
   BP_REQUEST_INFO2*  bBPRequestInfo  
);  
```  
  
```c#  
int GetRequestInfo2(  
   enum_BPREQI_FIELDS  dwFields,   
   BP_REQUEST_INFO2[]  bBPRequestInfo  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `dwFields`  
 [in] Uma combinação de sinalizadores do [BPREQI_FIELDS](../../../extensibility/debugger/reference/bpreqi-fields.md) enumeração que determinam quais campos de `pBPRequestInfo` devem ser preenchidos.  
  
 `bBPRequestInfo`  
 [out] O [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md) estrutura a ser preenchido.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retornará o código de erro.  
  
## <a name="remarks"></a>Comentários  
 Há mais informações nesta solicitação que é retornado a partir de [GetRequestInfo](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getrequestinfo.md) método.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugBreakpointRequest3](../../../extensibility/debugger/reference/idebugbreakpointrequest3.md)   
 [GetRequestInfo](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getrequestinfo.md)   
 [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md)   
 [BPREQI_FIELDS](../../../extensibility/debugger/reference/bpreqi-fields.md)
