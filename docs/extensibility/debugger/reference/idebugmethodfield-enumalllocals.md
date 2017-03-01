---
title: IDebugMethodField::EnumAllLocals | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugMethodField::EnumAllLocals
helpviewer_keywords:
- IDebugMethodField::EnumAllLocals method
ms.assetid: 0bc7cc13-2628-4bd8-8c06-4d2aa6755ea8
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
ms.openlocfilehash: 7840070660e4178f37020b3bd2d3750e2776fd97
ms.lasthandoff: 02/22/2017

---
# <a name="idebugmethodfieldenumalllocals"></a>IDebugMethodField::EnumAllLocals
Cria um enumerador para todas as variáveis locais do método, inclusive aquelas geradas internamente por um compilador.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
HRESULT EnumAllLocals(   
   IDebugAddress*     pAddress,  
   IEnumDebugFields** ppLocals  
);  
```  
  
```c#  
int EnumAllLocals(  
   IDebugAddress        pAddress,   
   out IEnumDebugFields ppLocals  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pAddress`  
 [in] Um [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) que representa um endereço de depuração dentro do método, apontando para um determinado escopo ou contexto de objeto.  
  
 `ppLocals`  
 [out] Retorna um [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) objeto que representa a lista de todos os locais no escopo especificado; caso contrário, retornará um valor nulo, indicando que não há locais.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, Retorna S_OK ou retorna S_FALSE se não houver nenhum locais. Caso contrário, retornará um código de erro.  
  
## <a name="remarks"></a>Comentários  
 Somente as variáveis definidas dentro do bloco que contém o endereço de depuração determinado são enumeradas. Esse método inclui qualquer locais geradas pelo compilador. Se tudo o que é necessário são os locais definidos explicitamente na origem, chamada de [EnumLocals](../../../extensibility/debugger/reference/idebugmethodfield-enumlocals.md) método.  
  
 Um método pode conter vários contextos ou blocos de escopo.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)   
 [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)   
 [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)   
 [EnumLocals](../../../extensibility/debugger/reference/idebugmethodfield-enumlocals.md)
