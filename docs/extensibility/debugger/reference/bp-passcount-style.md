---
title: BP_PASSCOUNT_STYLE | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- BP_PASSCOUNT_STYLE
helpviewer_keywords:
- BP_PASSCOUNT_STYLE structure
ms.assetid: 0a647047-e2d5-4724-a0b8-68108425ecad
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
ms.openlocfilehash: 441963c3981f7fde21a2c466496d02bfe6d0ecca
ms.lasthandoff: 02/22/2017

---
# <a name="bppasscountstyle"></a>BP_PASSCOUNT_STYLE
Especifica a condição associada com a contagem de passagem de ponto de interrupção que faz com que o ponto de interrupção seja acionado.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
enum enum_BP_PASSCOUNT_STYLE {   
   BP_PASSCOUNT_NONE             = 0x0000,  
   BP_PASSCOUNT_EQUAL            = 0x0001,  
   BP_PASSCOUNT_EQUAL_OR_GREATER = 0x0002,  
   BP_PASSCOUNT_MOD              = 0x0003  
};  
typedef DWORD BP_PASSCOUNT_STYLE;  
```  
  
```c#  
public enum enum_BP_PASSCOUNT_STYLE {   
   BP_PASSCOUNT_NONE             = 0x0000,  
   BP_PASSCOUNT_EQUAL            = 0x0001,  
   BP_PASSCOUNT_EQUAL_OR_GREATER = 0x0002,  
   BP_PASSCOUNT_MOD              = 0x0003  
};  
```  
  
## <a name="members"></a>Membros  
 BP_PASSCOUNT_NONE  
 Não especifica nenhum estilo de contagem de passagem de ponto de interrupção.  
  
 BP_PASSCOUNT_EQUAL  
 Define o estilo de contagem de passagem de ponto de interrupção igual. O ponto de interrupção é disparado quando o número de vezes que o ponto de interrupção é atingido igual à contagem de passagem.  
  
 BP_PASSCOUNT_EQUAL_OR_GREATER  
 Define o estilo de contagem de passagem de ponto de interrupção como igual ou maior. O ponto de interrupção é disparado quando o número de vezes que o ponto de interrupção é atingido é igual ou maior que a contagem de passagem.  
  
 BP_PASSCOUNT_MOD  
 Especifica um módulo passar contagem. Por exemplo, se a contagem de passagem é do tipo `BP_PASSCOUNT_MOD` e o valor de contagem de passagem é 4, o ponto de interrupção é disparado sempre que a contagem de ocorrências é um múltiplo de 4.  
  
## <a name="remarks"></a>Comentários  
 Usado para o `stylePassCount` membro do [BP_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md) que por sua vez é um membro da estrutura a [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) e [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md) estruturas.  
  
## <a name="requirements"></a>Requisitos  
 Cabeçalho: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Consulte também  
 [Enumerações](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [BP_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md)   
 [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md)   
 [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md)
