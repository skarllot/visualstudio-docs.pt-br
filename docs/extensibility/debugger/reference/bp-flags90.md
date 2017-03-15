---
title: BP_FLAGS90 | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- BP_FLAGS90 enumeration
ms.assetid: 3e5a06c5-fb30-4b8a-b2d5-4a0570fc80bd
caps.latest.revision: 7
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
ms.openlocfilehash: 4dfb7dc681519b37fe5cb9cd20e4bca22d800b96
ms.lasthandoff: 02/22/2017

---
# <a name="bpflags90"></a>BP_FLAGS90
Enumera os valores válidos para sinalizadores opcionais. Os sinalizadores opcionais podem ser usados para especificar informações adicionais quando você definir um ponto de interrupção. Esta enumeração estende o [BP_FLAGS](../../../extensibility/debugger/reference/bp-flags.md) enumeração.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
enum enum_BP_FLAGS90  
{  
   // VS 8.0 values  
   BP90_FLAG_NONE               = 0x0000,  
   BP90_FLAG_MAP_DOCPOSITION    = 0x0001,  
   BP90_FLAG_DONT_STOP          = 0x0002,  
  
   // Values added in VS 9.0  
   BP90_FLAG_TRACEPOINT_CONTINUE = 0x0004,  
};  
typedef DWORD BP_FLAGS90;  
```  
  
```c#  
public enum enum_BP_FLAGS90  
{  
   // VS 8.0 values  
   BP90_FLAG_NONE                = 0x0000,  
   BP90_FLAG_MAP_DOCPOSITION     = 0x0001,  
   BP90_FLAG_DONT_STOP           = 0x0002,  
  
   // Values added in VS 9.0  
   BP90_FLAG_TRACEPOINT_CONTINUE = 0x0004,  
};  
```  
  
#### <a name="parameters"></a>Parâmetros  
 BP90_FLAG_NONE  
 Não especifica que nenhum sinalizador de ponto de interrupção.  
  
 BP90_FLAG_MAP_DOCPOSITION  
 Especifica que o mecanismo de depuração (DE) deve mapear o ponto de interrupção usando a posição do documento. Isso é aplicável somente a pontos de interrupção definidos em arquivos de origem orientado por script, como Active Server Pages (ASP).  
  
 BP90_FLAG_DONT_STOP  
 Especifica que o ponto de interrupção deve ser processado pelo mecanismo de depuração, mas que o mecanismo de depuração, por fim, não deve parar lá; ou seja, um [IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md) o objeto de evento não deve ser enviado. Esse sinalizador é projetado para ser usado principalmente com pontos de rastreamento.  
  
 BP90_FLAG_TRACEPOINT_CONTINUE  
 Usado pelo mecanismo de depuração nativa para determinar se o estado de revisão deve ser desmarcado. Ele difere BP90_FLAG_DONT_STOP porque BP90_FLAG_DONT_STOP não está definido se o ponto de rastreamento executa uma macro.  
  
## <a name="requirements"></a>Requisitos  
 Cabeçalho: Msdbg90.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Consulte também  
 [Enumerações](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
