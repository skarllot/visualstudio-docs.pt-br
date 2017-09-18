---
title: BP_REQUEST_INFO | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- BP_REQUEST_INFO
helpviewer_keywords:
- BP_REQUEST_INFO structure
ms.assetid: 42a31412-5b6b-47fe-a762-0c2bc769e1cc
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
ms.openlocfilehash: 2c468d76819566049054a0919655d5a30524cb59
ms.lasthandoff: 02/22/2017

---
# <a name="bprequestinfo"></a>BP_REQUEST_INFO
Contém as informações necessárias para implementar um ponto de interrupção.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
typedef struct _BP_REQUEST_INFO {  
   BPREQI_FIELDS   dwFields;  
   GUID            guidLanguage;  
   BP_LOCATION     bpLocation;  
   IDebugProgram2* pProgram;  
   BSTR            bstrProgramName;  
   IDebugThread2*  pThread;  
   BSTR            bstrThreadName;  
   BP_CONDITION    bpCondition;  
   BP_PASSCOUNT    bpPassCount;  
   BP_FLAGS        dwFlags;  
} BP_REQUEST_INFO;  
```  
  
```c#  
public struct BP_REQUEST_INFO {  
   public uint           dwFields;  
   public Guid           guidLanguage;  
   public BP_LOCATION    bpLocation;  
   public IDebugProgram2 pProgram;  
   public string         bstrProgramName;  
   public IDebugThread2  pThread;  
   public string         bstrThreadName;  
   public BP_CONDITION   bpCondition;  
   public BP_PASSCOUNT   bpPassCount;  
   public uint           dwFlags;  
};  
```  
  
## <a name="members"></a>Membros  
 `dwFields`  
 Uma combinação de sinalizadores do [BPREQI_FIELDS](../../../extensibility/debugger/reference/bpreqi-fields.md) enumeração que especifica quais campos estão preenchidos.  
  
 `guidLanguage`  
 O GUID do idioma.  
  
 `bpLocation`  
 O [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md) estrutura que especifica o tipo do local do ponto de interrupção.  
  
 `pProgram`  
 O [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) objeto que representa o aplicativo no qual o ponto de interrupção ocorre.  
  
 `bstrProgramName`  
 O nome do aplicativo no qual o ponto de interrupção ocorre.  
  
 `pThread`  
 O [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) objeto que representa o thread no qual o ponto de interrupção ocorre.  
  
 `bstrThreadName`  
 O nome do thread no qual o ponto de interrupção ocorre.  
  
 `bpCondition`  
 O [BP_CONDITION](../../../extensibility/debugger/reference/bp-condition.md) estrutura que descreve as condições sob as quais o ponto de interrupção será acionado.  
  
 `bpPassCount`  
 O [BP_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md) estrutura que contém as informações de contagem de passagem do ponto de interrupção.  
  
 `dwFlags`  
 Uma combinação de sinalizadores do [BP_FLAGS](../../../extensibility/debugger/reference/bp-flags.md) enumeração que especifica os sinalizadores para o ponto de interrupção solicitado.  
  
## <a name="remarks"></a>Comentários  
 Essa estrutura é retornada pelo [GetRequestInfo](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getrequestinfo.md) método.  
  
 Se você precisar obter o GUID do fornecedor do mecanismo de depuração, a restrição de ponto de interrupção ou o tracepoint, consulte o [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md) estrutura.  
  
## <a name="requirements"></a>Requisitos  
 Cabeçalho: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Consulte também  
 [Estruturas e uniões](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [GetRequestInfo](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getrequestinfo.md)   
 [BPREQI_FIELDS](../../../extensibility/debugger/reference/bpreqi-fields.md)   
 [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [BP_CONDITION](../../../extensibility/debugger/reference/bp-condition.md)   
 [BP_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md)   
 [BP_FLAGS](../../../extensibility/debugger/reference/bp-flags.md)   
 [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md)
