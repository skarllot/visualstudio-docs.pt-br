---
title: IDebugPort2::GetPortRequest | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugPort2::GetPortRequest
helpviewer_keywords:
- IDebugPort2::GetPortRequest
ms.assetid: 14abf847-0675-4fa8-872e-971e00c84224
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
ms.openlocfilehash: 40adf83c864fe226feb5faeec941e385d7e7a030
ms.lasthandoff: 02/22/2017

---
# <a name="idebugport2getportrequest"></a>IDebugPort2::GetPortRequest
Obtém a descrição de uma porta que foi usada anteriormente para criar a porta (se disponível).  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
HRESULT GetPortRequest(   
   IDebugPortRequest2** ppRequest  
);  
```  
  
```c#  
int GetPortRequest(   
   out IDebugPortRequest2 ppRequest  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `ppRequest`  
 [out] Retorna um [IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md) objeto que representa a solicitação que foi usada para criar a porta.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna um código de erro.  Retorna `E_PORT_NO_REQUEST` se uma porta não foi criada usando um [IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md) solicitação de porta.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)   
 [IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md)   
 [Adicionar porta](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md)
