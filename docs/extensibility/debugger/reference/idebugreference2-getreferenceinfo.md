---
title: IDebugReference2::GetReferenceInfo | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugReference2::GetReferenceInfo
helpviewer_keywords:
- IDebugReference2::GetReferenceInfo
ms.assetid: ae611714-f114-4cf2-b5bb-37461e6ff289
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
ms.openlocfilehash: 796ea8b2460ea596e257fd67b356e844e3898c77
ms.lasthandoff: 02/22/2017

---
# <a name="idebugreference2getreferenceinfo"></a>IDebugReference2::GetReferenceInfo
Obtém o [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) estrutura que descreve uma referência. Reservado para uso futuro.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
HRESULT GetReferenceInfo (   
   DEBUGREF_INFO_FLAGS   dwFields,  
   DWORD                 nRadix,  
   DWORD                 dwTimeout,  
   IDebugReference2**    rgpArgs,  
   DWORD                 dwArgCount,  
   DEBUG_REFERENCE_INFO* pReferenceInfo  
);  
```  
  
```c#  
int GetReferenceInfo (   
   enum_DEBUGREF_INFO_FLAGS  dwFields,  
   uint                      nRadix,  
   uint                      dwTimeout,  
   IDebugReference2[]        rgpArgs,  
   uint                      dwArgCount,  
   DEBUG_REFERENCE_INFO[]    pReferenceInfo  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `dwFields`  
 [in] Uma combinação de sinalizadores do [DEBUGREF_INFO_FLAGS](../../../extensibility/debugger/reference/debugref-info-flags.md) enumeração que determinam os campos a serem preenchidos no [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) estrutura.  
  
 `nRadix`  
 [in] A base a ser usada na formatação de todas as informações numéricas.  
  
 `dwTimeout`  
 [in] Tempo máximo, em milissegundos, para aguardar antes de retornar desse método. Use `INFINITE` para aguardar indefinidamente.  
  
 `rgpArgs`  
 [in] Uma matriz de [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) objetos. Reservado para uso futuro; Defina como um valor nulo.  
  
 `dwArgCount`  
 [in] O número de argumentos de referência na `rgpArgs` matriz. Reservado para uso futuro; Defina como 0.  
  
 `pReferenceInfo`  
 [out] A [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) estrutura é preenchida com uma descrição da propriedade.  
  
## <a name="return-value"></a>Valor de retorno  
 Sempre retorna `E_NOTIMPL`.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)   
 [DEBUGREF_INFO_FLAGS](../../../extensibility/debugger/reference/debugref-info-flags.md)   
 [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md)
