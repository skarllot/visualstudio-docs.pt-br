---
title: IDebugCoreServer3::DiagnoseWebDebuggingError | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugCoreServer3::DiagnoseWebDebuggingError
helpviewer_keywords:
- IDebugCoreServer3::DiagnoseWebDebuggingError
ms.assetid: 8c4570ca-ae55-42f2-bbaa-8d8e75d2fa19
caps.latest.revision: 8
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
ms.openlocfilehash: 04a8ecbb1bfdc7f14f6b493df7f1dc9e16b53cd6
ms.lasthandoff: 02/22/2017

---
# <a name="idebugcoreserver3diagnosewebdebuggingerror"></a>IDebugCoreServer3::DiagnoseWebDebuggingError
Tenta determinar o motivo pelo qual um auto-attach falhou.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
HRESULT DiagnoseWebDebuggingError(  
   LPCWSTR pszUrl  
);  
```  
  
```c#  
int DiagnoseWebDebuggingError(  
   string pszUrl  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pszUrl`  
 [in] Não usado no momento; deve sempre ser definido como um valor nulo.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna um código de erro. Estes são os outros códigos de retorno típicos:  
  
|Código|Descrição|  
|----------|-----------------|  
|`S_WEBDBG_UNABLE_TO_DIAGNOSE`|Não é possível determinar por que o servidor remoto falhou ao iniciar a depuração.|  
|`S_WEBDBG_DEBUG_VERB_BLOCKED`|Não é possível depurar em um servidor remoto, possivelmente devido a permissões insuficientes ou porque o verbo DEBUG não está habilitado.|  
|`E_WEBDBG_DEBUG_VERB_BLOCKED`|O servidor web foi bloqueado e está bloqueando o verbo DEBUG, que é necessário para habilitar a depuração.|  
  
## <a name="see-also"></a>Consulte também  
 [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)
