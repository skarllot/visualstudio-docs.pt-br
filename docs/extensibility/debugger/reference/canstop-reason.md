---
title: CANSTOP_REASON | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CANSTOP_REASON
helpviewer_keywords:
- CANSTOP_REASON enumeration
ms.assetid: 6da944eb-36cd-4a8c-8d71-544c775cfcc1
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
ms.openlocfilehash: cce6acec5227a1861791d89cb352bb662ed515e2
ms.lasthandoff: 02/22/2017

---
# <a name="canstopreason"></a>CANSTOP_REASON
Usado para determinar se um programa pode interromper a execução depois de atingir um ponto específico na execução.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
enum enum_CANSTOP_REASON {   
   CANSTOP_ENTRYPOINT = 0x0000,  
   CANSTOP_STEPIN     = 0x0001  
};  
typedef DWORD CANSTOP_REASON;  
```  
  
```c#  
public enum enum_CANSTOP_REASON {   
   CANSTOP_ENTRYPOINT = 0x0000,  
   CANSTOP_STEPIN     = 0x0001  
};  
```  
  
## <a name="members"></a>Membros  
 CANSTOP_ENTRYPOINT  
 Especifica o ponto de entrada de um determinado programa.  
  
 CANSTOP_STEPIN  
 Especifica a entrar em uma função.  
  
## <a name="remarks"></a>Comentários  
 Passada como um argumento para o [GetReason](../../../extensibility/debugger/reference/idebugcanstopevent2-getreason.md) método para confirmar com a sessão de depuração Manager (SDM) se for okey parar depois de atingir o ponto de entrada do programa, ou depois de entrar em uma função ou método.  
  
## <a name="requirements"></a>Requisitos  
 Cabeçalho: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Consulte também  
 [Enumerações](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [GetReason](../../../extensibility/debugger/reference/idebugcanstopevent2-getreason.md)
