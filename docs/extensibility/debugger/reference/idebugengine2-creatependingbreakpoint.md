---
title: IDebugEngine2::CreatePendingBreakpoint | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugEngine2::CreatePendingBreakpoint
helpviewer_keywords:
- IDebugEngine2::CreatePendingBreakpoint
ms.assetid: 92e85b90-a931-48d9-89a7-a6edcb83ae5a
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
ms.openlocfilehash: 420dad6462f78bec12a2851389c36dd39831ecfc
ms.lasthandoff: 02/22/2017

---
# <a name="idebugengine2creatependingbreakpoint"></a>IDebugEngine2::CreatePendingBreakpoint
Cria um ponto de interrupção pendente no mecanismo de depuração (DE).  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
HRESULT CreatePendingBreakpoint(   
   IDebugBreakpointRequest2*  pBPRequest,  
   IDebugPendingBreakpoint2** ppPendingBP  
);  
```  
  
```c#  
int CreatePendingBreakpoint(   
   IDebugBreakpointRequest2     pBPRequest,  
   out IDebugPendingBreakpoint2 ppPendingBP  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pBPRequest`  
 [in] Um [IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md) objeto que descreve o ponto de interrupção pendente para criar.  
  
 `ppPendingBP`  
 [out] Retorna um [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md) objeto que representa o ponto de interrupção pendente.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna um código de erro. Normalmente retorna `E_FAIL` se o `pBPRequest` parâmetro não corresponde a qualquer linguagem compatível com o DE se o `pBPRequest` parâmetro é inválido ou está incompleto.  
  
## <a name="remarks"></a>Comentários  
 Um ponto de interrupção pendente é essencialmente uma coleção de todas as informações necessárias para associar um ponto de interrupção ao código. O ponto de interrupção pendente retornado desse método não está associado ao código até que o [ligar](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md) método é chamado.  
  
 Para cada pendentes ponto de interrupção conjuntos do usuário, o Gerenciador de sessão de depuração (SDM) chama esse método em cada DE anexado. É responsabilidade DE verificar se o ponto de interrupção é válido para programas em execução em que DE.  
  
 Quando o usuário define um ponto de interrupção em uma linha de código, o DE é livre para associar o ponto de interrupção à linha mais próxima do documento que corresponde a esse código. Isso possibilita que o usuário defina um ponto de interrupção na primeira linha de uma instrução de várias linha, mas vinculá-lo na última linha (em que todo o código é atribuído nas informações de depuração).  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como implementar esse método para um simples `CProgram` objeto. Implementação do `IDebugEngine2::CreatePendingBreakpoint` , em seguida, foi possível encaminhar todas as chamadas para essa implementação do método em cada programa.  
  
```  
HRESULT CProgram::CreatePendingBreakpoint(IDebugBreakpointRequest2* pBPRequest, IDebugPendingBreakpoint2** ppPendingBP)     
{    
  
   // Create and initialize the CPendingBreakpoint object.  
   CComObject<CPendingBreakpoint> *pPending;    
   CComObject<CPendingBreakpoint>::CreateInstance(&pPending);    
   pPending->Initialize(pBPRequest, m_pInterp, m_pCallback, m_pEngine);    
   return pPending->QueryInterface(ppPendingBP);    
}    
```  
  
## <a name="see-also"></a>Consulte também  
 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)   
 [Ligação](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md)   
 [IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md)   
 [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)
