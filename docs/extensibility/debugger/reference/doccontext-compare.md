---
title: DOCCONTEXT_COMPARE | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- DOCCONTEXT_COMPARE
helpviewer_keywords:
- DOCCONTEXT_COMPARE enumeration
ms.assetid: ed947c34-b07e-4b69-8381-b6e7cb842862
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
ms.openlocfilehash: 275f869bbcd20237ec935f2daedf72fef99bc769
ms.lasthandoff: 02/22/2017

---
# <a name="doccontextcompare"></a>DOCCONTEXT_COMPARE
Especifica os critérios para comparar dois contextos de documento.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
enum enum_DOCCONTEXT_COMPARE {   
   DOCCONTEXT_EQUAL         = 0x0001,  
   DOCCONTEXT_LESS_THAN     = 0x0002,  
   DOCCONTEXT_GREATER_THAN  = 0x0003,  
   DOCCONTEXT_SAME_DOCUMENT = 0x0004  
};  
typedef DWORD DOCCONTEXT_COMPARE;  
```  
  
```c#  
enum enum_DOCCONTEXT_COMPARE {   
   DOCCONTEXT_EQUAL         = 0x0001,  
   DOCCONTEXT_LESS_THAN     = 0x0002,  
   DOCCONTEXT_GREATER_THAN  = 0x0003,  
   DOCCONTEXT_SAME_DOCUMENT = 0x0004  
};  
```  
  
## <a name="members"></a>Membros  
 DOCCONTEXT_EQUAL  
 Localize o contexto de documento primeiro na lista que é igual ao contexto do documento de destino.  
  
 DOCCONTEXT_LESS_THAN  
 Localize o contexto de documento primeiro na lista que é menor que o contexto do documento de destino.  
  
 DOCCONTEXT_GREATER_THAN  
 Localize o contexto de documento primeiro na lista que é maior do que o contexto do documento de destino.  
  
 DOCCONTEXT_SAME_DOCUMENT  
 Localize o contexto de documento primeiro na lista que está no mesmo documento como o contexto do documento de destino.  
  
## <a name="remarks"></a>Comentários  
 Passada como um argumento para o [comparar](../../../extensibility/debugger/reference/idebugdocumentcontext2-compare.md) método.  
  
 Esses valores são usados para especificar um critério de comparação para localizar o contexto de documento primeiro em uma lista. Um contexto de documento recebe uma lista de contextos de documento de comparar a próprio contra por meio de `IDebugDocumentContext2::Compare` método. O contexto de documento primeiro na lista para a qual o operador de comparação é `true` é retornado.  
  
## <a name="requirements"></a>Requisitos  
 Cabeçalho: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Consulte também  
 [Enumerações](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [Compare](../../../extensibility/debugger/reference/idebugdocumentcontext2-compare.md)
