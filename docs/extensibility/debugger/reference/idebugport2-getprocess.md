---
title: IDebugPort2::GetProcess | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugPort2::GetPortSupplier
helpviewer_keywords:
- IDebugPort2::GetPortSupplier
ms.assetid: 3e2431b0-0e19-450d-8e1d-d7c314c8f872
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
ms.openlocfilehash: 9ac8ce25feb21f2deaae733da6ff8bfc58ae79b0
ms.lasthandoff: 02/22/2017

---
# <a name="idebugport2getprocess"></a>IDebugPort2::GetProcess
Obtém o processo especificado em execução em uma porta.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
HRESULT GetProcess(   
   AD_PROCESS_ID    ProcessId,  
   IDebugProcess2** ppProcess  
);  
```  
  
```c#  
int GetProcess(   
   AD_PROCESS_ID      ProcessId,  
   out IDebugProcess2 ppProcess  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `ProcessId`  
 [in] Um [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md) estrutura que especifica o identificador do processo.  
  
 `ppProcess`  
 [out] Retorna um [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) objeto que representa o processo.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna um código de erro.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)   
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)   
 [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md)
