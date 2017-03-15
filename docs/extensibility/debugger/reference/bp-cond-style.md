---
title: BP_COND_STYLE | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- BP_COND_STYLE
helpviewer_keywords:
- BP_COND_STYLE enumeration
ms.assetid: a93b1412-f447-48a1-af9d-38f3dbb3092f
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
ms.openlocfilehash: 2e4a1f2f2ce07b2ae6abfa80f2c21d44d8374205
ms.lasthandoff: 02/22/2017

---
# <a name="bpcondstyle"></a>BP_COND_STYLE
Especifica o estilo de condição de ponto de interrupção para pendente e associados a pontos de interrupção.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
enum enum_BP_COND_STYLE {   
   BP_COND_NONE         = 0x0000,  
   BP_COND_WHEN_TRUE    = 0x0001,  
   BP_COND_WHEN_CHANGED = 0x0002  
};  
typedef DWORD BP_COND_STYLE;  
```  
  
```c#  
public enum enum_BP_COND_STYLE {   
   BP_COND_NONE         = 0x0000,  
   BP_COND_WHEN_TRUE    = 0x0001,  
   BP_COND_WHEN_CHANGED = 0x0002  
};  
```  
  
## <a name="members"></a>Membros  
 BP_COND_NONE  
 Dispara o ponto de interrupção quando a posição do ponto de interrupção é atingida. Nenhuma condição de ponto de interrupção especificada.  
  
 BP_COND_WHEN_TRUE  
 Dispara o ponto de interrupção somente quando a expressão condicional associado com o ponto de interrupção é avaliada como `true`.  
  
 BP_COND_WHEN_CHANGED  
 Dispara o ponto de interrupção somente quando o valor da expressão condicional associada com o ponto de interrupção foi alterado de sua avaliação anterior.  
  
## <a name="remarks"></a>Comentários  
 Usado para o `styleCondition` membro do [BP_CONDITION](../../../extensibility/debugger/reference/bp-condition.md) estrutura.  
  
## <a name="requirements"></a>Requisitos  
 Cabeçalho: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Consulte também  
 [Enumerações](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [BP_CONDITION](../../../extensibility/debugger/reference/bp-condition.md)
