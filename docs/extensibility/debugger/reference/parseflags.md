---
title: PARSEFLAGS | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- PARSEFLAGS
helpviewer_keywords:
- PARSEFLAGS enumeration
ms.assetid: 47943f0a-54cb-4493-a62e-5dba97bd4c35
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
ms.translationtype: MT
ms.sourcegitcommit: 4a36302d80f4bc397128e3838c9abf858a0b5fe8
ms.openlocfilehash: 86589a8f3886592ad1659b646b0a983a9f31f48b
ms.contentlocale: pt-br
ms.lasthandoff: 09/26/2017

---
# <a name="parseflags"></a>PARSEFLAGS
Especifica como analisar uma expressão.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
enum enum_PARSEFLAGS {   
   PARSE_EXPRESSION            = 0x0001,  
   PARSE_FUNCTION_AS_ADDRESS   = 0x0002,  
   PARSE_DESIGN_TIME_EXPR_EVAL = 0x1000  
};  
typedef DWORD PARSEFLAGS;  
```  
  
```csharp  
public enum enum_PARSEFLAGS {   
   PARSE_EXPRESSION            = 0x0001,  
   PARSE_FUNCTION_AS_ADDRESS   = 0x0002,  
   PARSE_DESIGN_TIME_EXPR_EVAL = 0x1000  
};  
```  
  
## <a name="members"></a>Membros  
 PARSE_EXPRESSION  
 Indica que a expressão não é uma instrução.  
  
 PARSE_FUNCTION_AS_ADDRESS  
 Indica que a expressão deve ser analisada (e posteriormente avaliado) como um endereço.  
  
 PARSE_DESIGN_TIME_EXPR_EVAL  
 Indica que a expressão está sendo analisada durante o tempo de design (ou seja, quando um designer é aberto).  
  
## <a name="remarks"></a>Comentários  
 Passado como um parâmetro para o [ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) e [analisar](../../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) métodos.  
  
## <a name="requirements"></a>Requisitos  
 Cabeçalho: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Consulte também  
 [Enumerações](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md)   
 [Analisar](../../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md)
