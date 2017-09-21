---
title: IDebugStackFrame3::InterceptCurrentException | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugStackFrame3::InterceptCurrentException
helpviewer_keywords:
- IDebugStackFrame3::InterceptCurrentException
ms.assetid: 116c7324-7645-4c15-b484-7a5cdd065ef5
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
ms.openlocfilehash: 18433ee94836f30a11ec1c603cf394b8b3535419
ms.lasthandoff: 02/22/2017

---
# <a name="idebugstackframe3interceptcurrentexception"></a>IDebugStackFrame3::InterceptCurrentException
Chamado pelo depurador no quadro de pilhas atual quando quer interceptar a exceção atual.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT InterceptCurrentException(  
   INTERCEPT_EXCEPTION_ACTION dwFlags,  
   UINT64*                    pqwCookie  
);  
```  
  
```c#  
int InterceptCurrentException(  
   uint dwFlags,   
   out  ulong pqwCookie  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `dwFlags`  
 [in] Especifica as ações diferentes. Atualmente, apenas o [INTERCEPT_EXCEPTION_ACTION](../../../extensibility/debugger/reference/intercept-exception-action.md) valor `IEA_INTERCEPT` é suportado e deve ser especificado.  
  
 `pqwCookie`  
 [out] Valor exclusivo que identifica uma exceção em particular.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retornará S_OK; Caso contrário, retorna um código de erro.  
  
 A seguir estão os retornos de erro mais comuns.  
  
|Erro|Descrição|  
|-----------|-----------------|  
|`E_EXCEPTION_CANNOT_BE_INTERCEPTED`|A exceção atual não pode ser interceptada.|  
|`E_EXCEPTION_CANNOT_UNWIND_ABOVE_CALLBACK`|O quadro atual da execução ainda não foi pesquisado para um manipulador.|  
|`E_INTERCEPT_CURRENT_EXCEPTION_NOT_SUPPORTED`|Este método não é suportado para esse quadro.|  
  
## <a name="remarks"></a>Comentários  
 Quando uma exceção é lançada, o depurador assumir o controle de tempo de execução em pontos-chave durante a processo de manipulação de exceção. Durante esses momentos chave, o depurador pode pedir o quadro de pilhas atual se o quadro deseja interceptar a exceção. Dessa forma, uma exceção interceptada é essencialmente um manipulador de exceção do sistema em funcionamento para um quadro de pilha, mesmo se esse quadro de pilha não tiver um manipulador de exceção (por exemplo, um bloco try/catch no código do programa).  
  
 Quando o depurador quer saber se a exceção deve ser interceptada, ele chama esse método no objeto de quadro de pilha atual. Esse método é responsável por gerenciar todos os detalhes da exceção. Se o [IDebugStackFrame3](../../../extensibility/debugger/reference/idebugstackframe3.md) interface não é implementada ou `InterceptStackException` método retorna qualquer erro, em seguida, o depurador continua processando a exceção normalmente.  
  
> [!NOTE]
>  Exceções podem ser interceptadas apenas em código gerenciado, ou seja, quando o programa que está sendo depurado está em execução em tempo de execução .NET. Claro, os implementadores de linguagem de terceiros podem implementar `InterceptStackException` em seus próprios mecanismos de depuração se assim escolherem.  
  
 Depois que a interceptação for concluída, uma [IDebugInterceptExceptionCompleteEvent2](../../../extensibility/debugger/reference/idebuginterceptexceptioncompleteevent2.md) é sinalizado.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugStackFrame3](../../../extensibility/debugger/reference/idebugstackframe3.md)   
 [INTERCEPT_EXCEPTION_ACTION](../../../extensibility/debugger/reference/intercept-exception-action.md)   
 [IDebugInterceptExceptionCompleteEvent2](../../../extensibility/debugger/reference/idebuginterceptexceptioncompleteevent2.md)
