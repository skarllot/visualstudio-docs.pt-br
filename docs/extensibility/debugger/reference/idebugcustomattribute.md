---
title: IDebugCustomAttribute | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugCustomAttribute
helpviewer_keywords:
- IDebugCustomAttribute interface
ms.assetid: c5ae41e9-00b9-4cca-871d-b8de9ef390d1
caps.latest.revision: 13
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
ms.openlocfilehash: 777c7e2abda973d691384e26f858d96f81604e61
ms.lasthandoff: 02/22/2017

---
# <a name="idebugcustomattribute"></a>IDebugCustomAttribute
Essa interface representa um atributo personalizado, e ele pode fornecer o nome, o pai e o tipo de classe do atributo.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
IDebugCustomAttribute : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Observações para implementadores  
 Um provedor de símbolo implementa essa interface para oferecer suporte a atributos personalizados associados a um símbolo. Ele geralmente é implementado em seu próprio objeto.  
  
## <a name="notes-for-callers"></a>Observações para chamadores  
 Uma chamada para [próxima](../../../extensibility/debugger/reference/ienumdebugcustomattributes-next.md) retorna essa interface. Uma chamada para o [EnumCustomAttributes](../../../extensibility/debugger/reference/idebugcustomattributequery2-enumcustomattributes.md) método retorna o [IEnumDebugCustomAttributes](../../../extensibility/debugger/reference/ienumdebugcustomattributes.md) interface.  
  
## <a name="methods-in-vtable-order"></a>Métodos na ordem Vtable  
 A tabela a seguir mostra os métodos de `IDebugCustomAttribute`.  
  
|Método|Descrição|  
|------------|-----------------|  
|[GetParentField](../../../extensibility/debugger/reference/idebugcustomattribute-getparentfield.md)|Obtém o campo ao qual o atributo atual está anexado.|  
|[GetAttributeTypeField](../../../extensibility/debugger/reference/idebugcustomattribute-getattributetypefield.md)|Obtém o tipo de classe de atributo personalizado.|  
|[GetName](../../../extensibility/debugger/reference/idebugcustomattribute-getname.md)|Obtém o nome do atributo personalizado.|  
|[GetAttributeBytes](../../../extensibility/debugger/reference/idebugcustomattribute-getattributebytes.md)|Obtém as informações do atributo como um blob de bytes.|  
  
## <a name="remarks"></a>Comentários  
 Um atributo personalizado é uma estrutura c# que fornece metadados personalizados associados a uma determinada classe ou método.  
  
## <a name="requirements"></a>Requisitos  
 Cabeçalho: sh.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Consulte também  
 [Interfaces de provedor de símbolo](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)   
 [IDebugCustomAttributeQuery2](../../../extensibility/debugger/reference/idebugcustomattributequery2.md)   
 [IEnumDebugCustomAttributes](../../../extensibility/debugger/reference/ienumdebugcustomattributes.md)
