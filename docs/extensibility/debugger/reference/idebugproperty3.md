---
title: IDebugProperty3 | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugProperty3
helpviewer_keywords:
- IDebugProperty3 interface
ms.assetid: 8f9be68d-4490-4eca-8f6b-8a10ed77e226
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
ms.openlocfilehash: a56d2c10837ebe6441388ba1d6f09304e46dc28e
ms.lasthandoff: 02/22/2017

---
# <a name="idebugproperty3"></a>IDebugProperty3
Essa interface oferece suporte para:  
  
-   Recuperando uma cadeia de caracteres longa arbitrária associada à propriedade.  
  
-   Associando a propriedade de uma ID exclusiva.  
  
-   Recuperando uma lista de visualizadores personalizados para a propriedade.  
  
-   Definindo o valor de uma propriedade com a capacidade de relatar os erros resultantes  
  
## <a name="syntax"></a>Sintaxe  
  
```  
IDebugProperty3 : IDebugProperty2  
```  
  
## <a name="notes-for-implementers"></a>Observações para implementadores  
 O mecanismo de depuração (DE) implementa essa interface no mesmo objeto que implementa [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) para fornecer suporte para cadeias de caracteres longas, IDs de propriedade e visualizadores personalizados.  
  
## <a name="notes-for-callers"></a>Observações para chamadores  
 Chamar [QueryInterface](/visual-cpp/atl/queryinterface) em um `IDebugProperty2` interface para obter essa interface.  
  
## <a name="methods-in-vtable-order"></a>Métodos na ordem Vtable  
 Além dos métodos herdados de `IDebugProperty2`, o `IDebugProperty3` interface expõe os métodos a seguir.  
  
|Método|Descrição|  
|------------|-----------------|  
|[GetStringCharLength](../../../extensibility/debugger/reference/idebugproperty3-getstringcharlength.md)|Retorna o comprimento da cadeia de caracteres associada à propriedade.|  
|[GetStringChars](../../../extensibility/debugger/reference/idebugproperty3-getstringchars.md)|Retorna a cadeia de caracteres em um buffer fornecido pelo usuário.|  
|[CreateObjectID](../../../extensibility/debugger/reference/idebugproperty3-createobjectid.md)|Cria uma ID exclusiva para essa propriedade.|  
|[DestroyObjectID](../../../extensibility/debugger/reference/idebugproperty3-destroyobjectid.md)|Destrói a ID exclusiva para essa propriedade.|  
|[GetCustomViewerCount](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewercount.md)|Retorna o número de visualizadores personalizados que essa propriedade pode ser exibida com.|  
|[GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md)|Retorna a lista de visualizadores personalizados que essa propriedade pode ser exibida com.|  
|[SetValueAsStringWithError](../../../extensibility/debugger/reference/idebugproperty3-setvalueasstringwitherror.md)|Define o valor dessa propriedade, retornando uma mensagem de erro se algo deu errado.|  
  
## <a name="remarks"></a>Comentários  
 [SetValueAsStringWithError](../../../extensibility/debugger/reference/idebugproperty3-setvalueasstringwitherror.md) é a maneira preferencial para o Gerenciador de sessão de depuração (SDM) para definir o valor da propriedade.  
  
## <a name="requirements"></a>Requisitos  
 Cabeçalho: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Consulte também  
 [Interfaces de núcleo](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [IDebugCustomViewer](../../../extensibility/debugger/reference/idebugcustomviewer.md)
