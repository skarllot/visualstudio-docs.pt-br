---
title: IDebugGenericFieldDefinition::GetFormalTypeParams | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- GetFormalTypeParams
- IDebugGenericFieldDefinition::GetFormalTypeParams
ms.assetid: cadbd6a1-bc7c-4aff-8777-5396b7a23c3e
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
ms.openlocfilehash: ef4c6325c46ec0a2591130fcc8b0fc25cdb96b49
ms.lasthandoff: 02/22/2017

---
# <a name="idebuggenericfielddefinitiongetformaltypeparams"></a>IDebugGenericFieldDefinition::GetFormalTypeParams
Recupera os parâmetros de tipo dado o número de parâmetros.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
HRESULT GetFormalTypeParams(  
   ULONG32                   cParams,  
   IDebugGenericParamField** ppParams,  
   ULONG32*                  pcParams  
);  
```  
  
```c#  
int GetFormalTypeParams(  
   uint                          cParams,  
   out IDebugGenericParamField[] ppParams,  
   ref uint                      pcParams  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `cParams`  
 [in] Número de parâmetros.  
  
 `ppParams`  
 [out] Matriz de parâmetros de tipo.  
  
 `pcParams`  
 [no, out] Número de parâmetros na `ppParams` matriz.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna um código de erro.  
  
## <a name="remarks"></a>Comentários  
 Retorne os parâmetros de tipo em ordem da esquerda para a direita. Por exemplo, o dicionário\<K, V > retorna IDebugFormalGenericParameters {K, V}.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugGenericFieldDefinition](../../../extensibility/debugger/reference/idebuggenericfielddefinition.md)
