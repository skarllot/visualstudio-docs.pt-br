---
title: IDebugPortSupplier2::RemovePort | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugPortSupplier2::RemovePort
helpviewer_keywords:
- IDebugPortSupplier2::RemovePort
ms.assetid: f5c1fbf2-9084-46f2-a682-7db963928df2
caps.latest.revision: 9
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
ms.openlocfilehash: 7c07adf8793c49c41ad544cf4225df090c115655
ms.lasthandoff: 02/22/2017

---
# <a name="idebugportsupplier2removeport"></a>IDebugPortSupplier2::RemovePort
Remove uma porta.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
HRESULT RemovePort(   
   IDebugPort2* pPort  
);  
```  
  
```c#  
int RemovePort(   
   IDebugPort2 pPort  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pPort`  
 [in] Um [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) objeto que representa a porta a ser removido.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna um código de erro.  
  
## <a name="remarks"></a>Comentários  
 Esse método remove a porta a porta do interno da lista de fornecedores de portas ativas.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)   
 [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)
