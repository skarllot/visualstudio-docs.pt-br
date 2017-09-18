---
title: IDebugDocumentContext2::Compare | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugDocumentContext2::Compare
helpviewer_keywords:
- IDebugDocumentContext2::Compare
ms.assetid: 2327b1ba-52d0-42fb-a01e-63cb4b332d2f
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
ms.openlocfilehash: cbb8b3b44caccbd43d81e1bd9748fbd6124d32b1
ms.lasthandoff: 02/22/2017

---
# <a name="idebugdocumentcontext2compare"></a>IDebugDocumentContext2::Compare
Compara este contexto de documento para uma determinada matriz de contextos de documento.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
HRESULT Compare(   
   DOCCONTEXT_COMPARE       compare,  
   IDebugDocumentContext2** rgpDocContextSet,  
   DWORD                    dwDocContextSetLen,  
   DWORD*                   pdwDocContext  
);  
```  
  
```c#  
int Compare(   
   enum_ DOCCONTEXT_COMPARE compare,  
   IDebugDocumentContext2[] rgpDocContextSet,  
   uint                     dwDocContextSetLen,  
   out uint                 pdwDocContext  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `compare`  
 [in] Um valor a partir de [DOCCONTEXT_COMPARE](../../../extensibility/debugger/reference/doccontext-compare.md) enumeração que especifica o tipo de comparação.  
  
 `rgpDocContextSet`  
 [in] Uma matriz de [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) objetos que representam os contextos de documento que estão sendo comparados para.  
  
 `dwDocContextSetLen`  
 [in] O comprimento da matriz de contextos de documento a ser comparado.  
  
 `pdwDocContext`  
 [out] Retorna o índice de `rgpDocContextSet` matriz do contexto primeiro documento que satisfaz a comparação.  
  
## <a name="return-value"></a>Valor de retorno  
 Retorna `S_OK` se uma correspondência foi encontrada. Retorna `S_FALSE` se nenhuma correspondência foi encontrada. Caso contrário, retornará um código de erro.  
  
## <a name="remarks"></a>Comentários  
 O [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) objetos que são passados na matriz devem ser implementados pelo mecanismo de depuração mesmo que implementa o `IDebugDocumentContext2` do objeto que está sendo chamada; caso contrário, a comparação não é válida.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)   
 [DOCCONTEXT_COMPARE](../../../extensibility/debugger/reference/doccontext-compare.md)
