---
title: IDebugPendingBreakpoint2::SetPassCount | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugPendingBreakpoint2::SetPassCount
helpviewer_keywords:
- SetPassCount method
- IDebugPendingBreakpoint2::SetPassCount method
ms.assetid: 08ddd328-57eb-42e0-baa9-8424dcd1bf04
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
ms.openlocfilehash: 22a6d8201782bf58a194463b3256240f8358d9a4
ms.lasthandoff: 02/22/2017

---
# <a name="idebugpendingbreakpoint2setpasscount"></a>IDebugPendingBreakpoint2::SetPassCount
Define ou altera a contagem de passagem associada com o ponto de interrupção pendente.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
HRESULT SetPassCount(   
   BP_PASSCOUNT bpPassCount  
);  
```  
  
```c#  
int SetPassCount(   
   BP_PASSCOUNT bpPassCount  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `bpPassCount`  
 [in] A [BP_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md) estrutura que contém a contagem de passagem.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna um código de erro. Retorna `E_BP_DELETED` se o ponto de interrupção foi excluído.  
  
## <a name="remarks"></a>Comentários  
 Qualquer conta de passagem que foi previamente associada com o ponto de interrupção pendente é perdida. Todos os pontos de interrupção associados desse pendentes ponto de interrupção são chamados para definir sua contagem de passagem para o `bpPassCount` parâmetro.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)   
 [BP_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md)
