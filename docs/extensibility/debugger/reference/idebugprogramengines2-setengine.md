---
title: IDebugProgramEngines2::SetEngine | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugProgramEngines2::SetEngine
helpviewer_keywords:
- IDebugProgramEngines2::SetEngine
ms.assetid: c05857ee-89cf-455e-8f1e-300cce4a2eab
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
ms.openlocfilehash: e9234ccdd8fd9a408e5e8cde9fd2e85737e0f671
ms.lasthandoff: 02/22/2017

---
# <a name="idebugprogramengines2setengine"></a>IDebugProgramEngines2::SetEngine
O programa ou o nó de programa informa qual mecanismo de depuração (DE) usar para depurá-lo.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
HRESULT SetEngine(   
   REFGUID guidEngine  
);  
```  
  
```c#  
int SetEngine(   
   ref Guid guidEngine  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `guidEngine`  
 [in] O GUID do DE.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna um código de erro.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugProgramEngines2](../../../extensibility/debugger/reference/idebugprogramengines2.md)
