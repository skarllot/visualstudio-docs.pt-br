---
title: IDebugStackFrame2::EnumProperties | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugStackFrame2::EnumProperties
helpviewer_keywords:
- IDebugStackFrame2::EnumProperties
ms.assetid: 334bb95e-c7e0-4008-9f06-8c3999e47ee8
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
ms.openlocfilehash: 9aab0b2e6b4c3c442093612814c685d93a239540
ms.lasthandoff: 02/22/2017

---
# <a name="idebugstackframe2enumproperties"></a>IDebugStackFrame2::EnumProperties
Cria um enumerador para propriedades associadas com o quadro de pilha, como variáveis locais.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
HRESULT EnumProperties (   
   DEBUGPROP_INFO_FLAGS      dwFieldSpec,  
   UINT                      nRadix,  
   REFIID                    refiid,  
   DWORD                     dwTimeout,  
   ULONG*                    pcelt,  
   IEnumDebugPropertyInfo2** ppEnum  
);  
```  
  
```c#  
int EnumProperties (   
   enum_DEBUGPROP_INFO_FLAGS   dwFieldSpec,  
   uint                        nRadix,  
   ref Guid                    refiid,  
   uint                        dwTimeout,  
   out uint                    pcelt,  
   out IEnumDebugPropertyInfo2 ppEnum  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `dwFieldSpec`  
 [in] Uma combinação de sinalizadores do [DEBUGPROP_INFO_FLAGS](../../../extensibility/debugger/reference/debugprop-info-flags.md) enumeração que especifica quais campos no enumerado [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) estruturas devem ser preenchidos.  
  
 `nRadix`  
 [in] A base a ser usada na formatação de todas as informações numéricas.  
  
 `refiid`  
 [in] Um GUID de um filtro usado para selecionar quais [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) estruturas devem ser enumerados, como `guidFilterLocals`.  
  
 `dwTimeout`  
 [in] Tempo máximo, em milissegundos, para aguardar antes de retornar desse método. Use `INFINITE` para aguardar indefinidamente.  
  
 `pcelt`  
 [out] Retorna o número de propriedades enumerados. Isso é o mesmo que chamar o [GetCount](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2-getcount.md) método.  
  
 `ppEnum`  
 [out] Retorna um [IEnumDebugPropertyInfo2](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md) objeto que contém uma lista das propriedades desejadas.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna um código de erro.  
  
## <a name="remarks"></a>Comentários  
 Como esse método permite que todas as propriedades selecionadas sejam recuperadas com uma única chamada, é mais rápido do que chamar sequencialmente o [GetDebugProperty](../../../extensibility/debugger/reference/idebugstackframe2-getdebugproperty.md) e [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) métodos.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)   
 [DEBUGPROP_INFO_FLAGS](../../../extensibility/debugger/reference/debugprop-info-flags.md)   
 [IEnumDebugPropertyInfo2](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md)   
 [GetCount](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2-getcount.md)   
 [GetDebugProperty](../../../extensibility/debugger/reference/idebugstackframe2-getdebugproperty.md)   
 [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)
