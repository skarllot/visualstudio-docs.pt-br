---
title: IDebugBreakpointUnboundEvent2::GetBreakpoint | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugBreakpointUnboundEvent2::GetBreakpoint
helpviewer_keywords:
- IDebugBreakpointUnboundEvent2::GetBreakpoint
ms.assetid: ad73a207-b778-4dc5-b645-5ec668a63333
caps.latest.revision: 12
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
ms.openlocfilehash: fe462357604de349cd9e72aa04d67be5ba57f81b
ms.lasthandoff: 02/22/2017

---
# <a name="idebugbreakpointunboundevent2getbreakpoint"></a>IDebugBreakpointUnboundEvent2::GetBreakpoint
Obtém o ponto de interrupção não vinculado.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
HRESULT GetBreakpoint(   
   IDebugBoundBreakpoint2** ppBP  
);  
```  
  
```c#  
int GetBreakpoint(   
   out IDebugBoundBreakpoint2 ppBP  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `ppBP`  
 [out] Retorna um [IDebugBoundBreakpoint2](../../../extensibility/debugger/reference/idebugboundbreakpoint2.md) objeto que representa o ponto de interrupção não vinculado.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna um código de erro.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como implementar esse método para um **CBreakpointUnboundDebugEventBase** objeto expõe o [IDebugBreakpointUnboundEvent2](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2.md) interface.  
  
```cpp#  
STDMETHODIMP CBreakpointUnboundDebugEventBase::GetBreakpoint(  
    IDebugBoundBreakpoint2 **ppbp)  
{  
    HRESULT hRes = E_FAIL;  
  
    if ( ppbp )  
    {  
        if ( m_pbp )  
        {  
            IDebugBoundBreakpoint2 *pibp;  
  
            hRes = m_pbp->QueryInterface(IID_IDebugBoundBreakpoint2, (void **) & pibp);  
  
            if ( S_OK == hRes )  
                *ppbp = pibp;  
        }  
        else  
            hRes = E_FAIL;  
    }  
    else  
        hRes = E_INVALIDARG;  
  
    return ( hRes );  
}  
```  
  
## <a name="see-also"></a>Consulte também  
 [IDebugBreakpointUnboundEvent2](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2.md)   
 [IDebugBoundBreakpoint2](../../../extensibility/debugger/reference/idebugboundbreakpoint2.md)
