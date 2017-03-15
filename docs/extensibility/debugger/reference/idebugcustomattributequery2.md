---
title: IDebugCustomAttributeQuery2 | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugCustomAttributeQuery2
helpviewer_keywords:
- IDebugCustomAttributeQuery interface
- IDebugCustomAttributeQuery2 interface
ms.assetid: 7cfa23e4-a05a-47a3-af6c-bd40c655014b
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
ms.openlocfilehash: 3dc93efba1403301724d126ea6db7176e07ea96f
ms.lasthandoff: 02/22/2017

---
# <a name="idebugcustomattributequery2"></a>IDebugCustomAttributeQuery2
Determina a existência de um atributo personalizado para esse campo e, se ele existir, retorna as informações de atributo.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
IDebugCustomAttributeQuery2 : IDebugCustomAttributeQuery  
```  
  
## <a name="notes-for-implementers"></a>Observações para implementadores  
 Um provedor de símbolo implementa essa interface no mesmo objeto que implementa [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) para oferecer suporte a atributos personalizados.  
  
## <a name="notes-for-callers"></a>Observações para chamadores  
 Use [QueryInterface](/visual-cpp/atl/queryinterface) para obter essa interface da [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) interface.  
  
## <a name="methods-in-vtable-order"></a>Métodos na ordem Vtable  
 A tabela a seguir mostra os métodos de **IDebugCustomAttributeQuery** interface.  
  
|Método|Descrição|  
|------------|-----------------|  
|[IsCustomAttributeDefined](../../../extensibility/debugger/reference/idebugcustomattributequery2-iscustomattributedefined.md)|Determina se um atributo personalizado por nome.|  
|[GetCustomAttributeByName](../../../extensibility/debugger/reference/idebugcustomattributequery2-getcustomattributebyname.md)|Obtém as informações de atributo para o atributo personalizado fornecido.|  
  
 Além de **IDebugCustomAttributeQuery** métodos, `IDebugCustomAttributeQuery2` implementa o método a seguir:  
  
|Método|Descrição|  
|------------|-----------------|  
|[EnumCustomAttributes](../../../extensibility/debugger/reference/idebugcustomattributequery2-enumcustomattributes.md)|Obtém um enumerador para todos os atributos personalizados anexados a esse campo.|  
  
## <a name="remarks"></a>Comentários  
 O [IEnumDebugCustomAttributes](../../../extensibility/debugger/reference/ienumdebugcustomattributes.md) método pode retornar um enumerador para todos os atributos personalizados definidos para esse campo.  
  
## <a name="requirements"></a>Requisitos  
 Cabeçalho: sh.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Consulte também  
 [Interfaces de provedor de símbolo](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)   
 [IEnumDebugCustomAttributes](../../../extensibility/debugger/reference/ienumdebugcustomattributes.md)
