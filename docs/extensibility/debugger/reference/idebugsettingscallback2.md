---
title: IDebugSettingsCallback2 | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- IDebugSettingsCallback2 interface
ms.assetid: 7e525d0b-7d7a-4d1c-8b78-e1398fa922f2
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
ms.openlocfilehash: c2b91c89eecfd68d1d0b58b04654416d2eafd451
ms.lasthandoff: 02/22/2017

---
# <a name="idebugsettingscallback2"></a>IDebugSettingsCallback2
Habilita o mecanismos para ler as configurações de métrica de depuração remotamente.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
IDebugSettingsCallback2D : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Observações para implementadores  
 Essa interface é implementada pelo retorno de chamada de evento do Gerenciador de sessão de depuração e consumido por mecanismos de depuração. Ele também pode ser usado localmente em vez de. lib Dbgmetric [d].  
  
## <a name="methods"></a>Métodos  
 A tabela a seguir mostra os métodos de `IDebugSettingsCallback2`.  
  
|Método|Descrição|  
|------------|-----------------|  
|[EnumEEs](../../../extensibility/debugger/reference/idebugsettingscallback2-enumees.md)|Enumera os avaliadores de expressão disponível considerando os identificadores de idioma e o fornecedor.|  
|[GetEELocalObject](../../../extensibility/debugger/reference/idebugsettingscallback2-geteelocalobject.md)|Recupera um objeto local de avaliador de expressão dado a métrica.|  
|[GetEEMetricDword](../../../extensibility/debugger/reference/idebugsettingscallback2-geteemetricdword.md)|Recupera um valor que corresponde à métrica do avaliador de expressão especificada.|  
|[GetEEMetricFile](../../../extensibility/debugger/reference/idebugsettingscallback2-geteemetricfile.md)|Recupera o arquivo métrica de avaliador de expressão recebe o nome ou a métrica.|  
|[GetEEMetricGuid](../../../extensibility/debugger/reference/idebugsettingscallback2-geteemetricguid.md)|Recupera o identificador exclusivo para uma métrica do avaliador de expressão recebe seu nome.|  
|[GetEEMetricString](../../../extensibility/debugger/reference/idebugsettingscallback2-geteemetricstring.md)|Recupera a cadeia de caracteres do valor de uma métrica do avaliador de expressão recebe seu nome.|  
|[GetMetricDword](../../../extensibility/debugger/reference/idebugsettingscallback2-getmetricdword.md)|Recupera o valor de uma métrica recebe seu nome.|  
|[GetMetricGuid](../../../extensibility/debugger/reference/idebugsettingscallback2-getmetricguid.md)|Recupera o identificador exclusivo de uma métrica recebe seu nome.|  
|[GetMetricString](../../../extensibility/debugger/reference/idebugsettingscallback2-getmetricstring.md)|Recupera a cadeia de caracteres do valor da métrica recebe seu nome.|  
  
## <a name="requirements"></a>Requisitos  
 Cabeçalho: Msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra uma função que usa um **IDebugSettingsCallback2** objeto como um parâmetro.  
  
```cpp#  
HRESULT GetDebugSettingsCallback (IDebugSettingsCallback2 **ppCallback)  
{  
    HRESULT hRes = E_FAIL;  
  
    if ( ppCallback )  
   {  
        if ( EVAL(m_pdec) )  
            hRes = m_pdec->QueryInterface(IID_IDebugSettingsCallback2, (void **)ppCallback);  
        else  
            hRes = E_FAIL;  
    }  
    else  
        hRes = E_INVALIDARG;  
  
    return ( hRes );  
}  
```
