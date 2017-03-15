---
title: IDebugAddress2::GetProcessID | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugAddress2::GetProcessID
helpviewer_keywords:
- IDebugAddress2::GetProcessID method
ms.assetid: 2c18889d-074a-4b95-87b4-bf1a067f44ed
caps.latest.revision: 6
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
ms.openlocfilehash: a1bffaac59baf40db94037697775ad4ba005f5c7
ms.lasthandoff: 02/22/2017

---
# <a name="idebugaddress2getprocessid"></a>IDebugAddress2::GetProcessID
Recupera a ID do processo que possui o objeto representado por esse [IDebugAddress2](../../../extensibility/debugger/reference/idebugaddress2.md) interface.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetProcessID (  
   DWORD* pProcID  
);  
```  
  
```c#  
int GetProcessID (  
   out uint pProcID  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pProcID`  
 [out] A ID de processo.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retornará S_OK; Caso contrário, retorna um código de erro.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugAddress2](../../../extensibility/debugger/reference/idebugaddress2.md)
