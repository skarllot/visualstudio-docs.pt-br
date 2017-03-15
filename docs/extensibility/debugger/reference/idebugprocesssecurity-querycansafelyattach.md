---
title: IDebugProcessSecurity::QueryCanSafelyAttach | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- IDebugProcessSecurity::QueryCanSafelyAttach
ms.assetid: 63ec1ae8-27da-4574-aa15-1c986fe9fe58
caps.latest.revision: 4
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
ms.openlocfilehash: bd37974453939cb0af7d5a4ff2cd1ff2b5d0315c
ms.lasthandoff: 02/22/2017

---
# <a name="idebugprocesssecurityquerycansafelyattach"></a>IDebugProcessSecurity::QueryCanSafelyAttach
Esse método permite que o fornecedor de porta exibir um aviso antes do usuário anexar a um processo não é seguro.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
HRESULT QueryCanSafelyAttach();  
```  
  
```c#  
int QueryCanSafelyAttach();  
```  
  
## <a name="return-value"></a>Valor de retorno  
 Os valores de retorno são os seguintes:  
  
-   `S_OK`: Anexar a processo é seguro e nenhuma caixa de diálogo de aviso é mostrada.  
  
-   `S_FALSE`: Anexando poderia ser um problema de segurança e uma caixa de diálogo com um aviso é mostrada.  
  
-   `FAILURE`: Anexar a processo falhará.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugProcessSecurity](../../../extensibility/debugger/reference/idebugprocesssecurity.md)
