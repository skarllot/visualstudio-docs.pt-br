---
title: IDebugMethodField::EnumStaticLocals | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugMethodField::EnumStaticLocals
helpviewer_keywords:
- IDebugMethodField::EnumStaticLocals method
ms.assetid: e0c522c4-f759-4c32-ae87-7abcb573e77d
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
ms.openlocfilehash: 34b574d99db893d96420354655fb61b404ef109a
ms.lasthandoff: 02/22/2017

---
# <a name="idebugmethodfieldenumstaticlocals"></a>IDebugMethodField::EnumStaticLocals
Cria um enumerador para variáveis locais estáticas do método.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
HRESULT EnumStaticLocals(   
   IEnumDebugFields** ppLocals  
);  
```  
  
```c#  
int EnumStaticLocals(  
   out IEnumDebugFields ppLocals  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `ppLocals`  
 [out] Retorna um [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) objeto que representa a lista de variáveis locais estáticas. Retorna um valor nulo se não houver nenhum locais estáticos.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, Retorna S_OK ou retorna S_FALSE se não houver nenhum locais estáticos. Caso contrário, retornará um código de erro.  
  
## <a name="remarks"></a>Comentários  
 Cada elemento é um [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) objeto representando diferentes tipos de variáveis locais estáticas. Chamar o [GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md) método em cada objeto para determinar exatamente o tipo de local estático o objeto representa.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)   
 [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
