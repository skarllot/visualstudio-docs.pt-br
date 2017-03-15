---
title: IDebugProgram3::ExecuteOnThread | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- IDebugProgram3::ExecuteOnThread
ms.assetid: 2f5211e3-7a3f-47bf-9595-dfc8b4895d0d
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
ms.openlocfilehash: 535a7cd2925b2c88aad0e45f5d6f0c34b3259b6e
ms.lasthandoff: 02/22/2017

---
# <a name="idebugprogram3executeonthread"></a>IDebugProgram3::ExecuteOnThread
Executa o programa de depurador. O thread é retornado para fornecer as informações do depurador em qual thread o usuário está exibindo ao executar o programa.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
HRESULT ExecuteOnThread(  
   [in] IDebugThread2* pThread)  
```  
  
```c#  
int ExecuteOnThread(  
   IDebugThread2 pThread  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pThread`  
 [in] Um [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) objeto.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna um código de erro.  
  
## <a name="remarks"></a>Comentários  
 Há três maneiras diferentes que um depurador pode continuar a execução após a interrupção:  
  
-   Execute: Cancelar qualquer etapa anterior e executar até o próximo ponto de interrupção e assim por diante.  
  
-   Etapa: Cancelar qualquer etapa antiga e executar até que a nova etapa seja concluída.  
  
-   Continuar: Executar novamente e deixar qualquer etapa antiga ativa.  
  
 O thread passado para `ExecuteOnThread` é útil ao decidir qual etapa para cancelar. Se você não souber o thread em execução execute cancela todas as etapas. Com conhecimento do thread, você somente precisa cancelar a etapa de thread ativo.  
  
## <a name="see-also"></a>Consulte também  
 [Executar](../../../extensibility/debugger/reference/idebugprogram2-execute.md)   
 [IDebugProgram3](../../../extensibility/debugger/reference/idebugprogram3.md)
