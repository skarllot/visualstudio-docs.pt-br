---
title: IDebugPortSupplier2::AddPort | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugPortSupplier2::AddPort
helpviewer_keywords:
- IDebugPortSupplier2::AddPort
ms.assetid: df491161-6bf3-4fcc-b478-b9ec88ec995f
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
ms.openlocfilehash: 28a7cdd3f791f111332dcd73b71a65171ebaef65
ms.lasthandoff: 02/22/2017

---
# <a name="idebugportsupplier2addport"></a>IDebugPortSupplier2::AddPort
Adiciona uma porta.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
HRESULT AddPort(   
   IDebugPortRequest2* pRequest,  
   IDebugPort2**       ppPort  
);  
```  
  
```c#  
int AddPort(   
   IDebugPortRequest2 pRequest,  
   out IDebugPort2    ppPort  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pRequest`  
 [in] Um [IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md) objeto que descreve a porta a ser adicionado.  
  
 `ppPort`  
 [out] Retorna um [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) objeto que representa a porta.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna um código de erro.  
  
## <a name="remarks"></a>Comentários  
 Na verdade, esse método cria a porta solicitada, bem como adicioná-lo para a lista interna do fornecedor de porta de portas ativas. O [CanAddPort](../../../extensibility/debugger/reference/idebugportsupplier2-canaddport.md) método pode ser chamado primeiro, para evitar possíveis atrasos demorados.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)   
 [IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md)   
 [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)   
 [CanAddPort](../../../extensibility/debugger/reference/idebugportsupplier2-canaddport.md)
