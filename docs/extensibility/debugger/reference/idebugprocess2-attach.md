---
title: IDebugProcess2::Attach | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugProcess2::Attach
helpviewer_keywords:
- IDebugProcess2::Attach
ms.assetid: 40d78417-fde2-45c3-96c9-16e06bd9008d
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
ms.openlocfilehash: 3630bdab351011dc024755c15ee0285db330db92
ms.lasthandoff: 02/22/2017

---
# <a name="idebugprocess2attach"></a>IDebugProcess2::Attach
Anexa o Gerenciador de sessão de depuração (SDM) para o processo.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
HRESULT Attach(   
   IDebugEventCallback2* pCallback,  
   GUID*                 rgguidSpecificEngines,  
   DWORD                 celtSpecificEngines,  
   HRESULT*              rghrEngineAttach  
);  
```  
  
```c#  
int Attach(   
   IDebugEventCallback2 pCallback,  
   Guid[]               rgguidSpecificEngines,  
   uint                 celtSpecificEngines,  
   int[]                rghrEngineAttach  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pCallback`  
 [in] Um [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) objeto que é usado para notificação de eventos de depuração.  
  
 `rgguidSpecificEngines`  
 [in] Uma matriz de GUIDs de mecanismos de depuração a ser usado para depurar programas em execução no processo. Esse parâmetro pode ser um valor nulo. Consulte comentários para obter detalhes.  
  
 `celtSpecificEngines`  
 [in] O número de depuração mecanismos no `rgguidSpecificEngines` matriz e o tamanho da `rghrEngineAttach` matriz.  
  
 `rghrEngineAttach`  
 [no, out] Uma matriz de códigos HRESULT retornado pelos mecanismos de depuração. O tamanho dessa matriz é especificado no `celtSpecificEngines` parâmetro. Cada código é normalmente `S_OK` ou `S_ATTACH_DEFERRED`. O último indica que o DE atualmente está conectado a nenhum programa.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna um código de erro. A tabela a seguir mostra outros valores possíveis.  
  
|Valor|Descrição|  
|-----------|-----------------|  
|`E_ATTACH_DEBUGGER_ALREADY_ATTACHED`|O processo especificado já está anexado ao depurador.|  
|`E_ATTACH_DEBUGGEE_PROCESS_SECURITY_VIOLATION`|Ocorreu uma violação de segurança durante o procedimento de conexão.|  
|`E_ATTACH_CANNOT_ATTACH_TO_DESKTOP`|Um processo da área de trabalho não é possível anexar o depurador.|  
  
## <a name="remarks"></a>Comentários  
 Anexar a um processo anexa o SDM para todos os programas em execução no processo que pode ser depurado pelos mecanismos de depuração (DE) especificados na `rgguidSpecificEngines` matriz. Definir o `rgguidSpecificEngines` parâmetro para um valor nulo de valor ou incluir `GUID_NULL` na matriz para anexar a todos os programas no processo.  
  
 Todos os eventos de depuração que ocorrem no processo são enviados para o determinado [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) objeto. Isso `IDebugEventCallback2` objeto é fornecido quando o SDM chama esse método.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
