---
title: IPropertyProxyEESide | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IPropertyProxyEESide
helpviewer_keywords:
- IPropertyProxyEESide interface
ms.assetid: cf227cf8-39d9-4758-8f7e-a697aebb1926
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
ms.openlocfilehash: be625a57f4fcab14bf67585cb275074f23391d4f
ms.lasthandoff: 02/22/2017

---
# <a name="ipropertyproxyeeside"></a>IPropertyProxyEESide
Essa interface fornece métodos para exibir dados sobre o objeto associado. Essa interface é parte do suporte para visualizadores de tipo.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
IPropertyProxyEESide : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Observações para implementadores  
 Um avaliador de expressão implementa essa interface para oferecer suporte a visualizadores de tipo.  
  
## <a name="notes-for-callers"></a>Observações para chamadores  
 Chamar [GetPropertyProxy](../../../extensibility/debugger/reference/ipropertyproxyprovider-getpropertyproxy.md) para obter essa interface. Chamar [QueryInterface](/visual-cpp/atl/queryinterface) em uma [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) interface para obter o [IPropertyProxyProvider](../../../extensibility/debugger/reference/ipropertyproxyprovider.md) interface.  
  
## <a name="methods-in-vtable-order"></a>Métodos na ordem Vtable  
 Os seguintes métodos são implementados por esta interface:  
  
|Método|Descrição|  
|------------|-----------------|  
|[InitSourceDataProvider](../../../extensibility/debugger/reference/ipropertyproxyeeside-initsourcedataprovider.md)|Inicializa um provedor de fonte de dados para que os dados do objeto podem ser acessados.|  
|[GetManagedViewerCreationData](../../../extensibility/debugger/reference/ipropertyproxyeeside-getmanagedviewercreationdata.md)|Recupera informações sobre o assembly do objeto.|  
|[GetInitialData](../../../extensibility/debugger/reference/ipropertyproxyeeside-getinitialdata.md)|Obtém os dados iniciais para o objeto.|  
|[CreateReplacementObject](../../../extensibility/debugger/reference/ipropertyproxyeeside-createreplacementobject.md)|Cria uma cópia de um armazenamento de dados existente.|  
|[InPlaceUpdateObject](../../../extensibility/debugger/reference/ipropertyproxyeeside-inplaceupdateobject.md)|Cria uma referência para um armazenamento de dados existente.|  
|[ResolveAssemblyRef](../../../extensibility/debugger/reference/ipropertyproxyeeside-resolveassemblyref.md)|Recupera informações sobre um assembly específico no contexto do assembly que contém esse objeto.|  
  
## <a name="remarks"></a>Comentários  
 Um visualizador de tipo usa essa interface para acessar os valores associados com o objeto que esta interface é parte do. Os dados são acessados por meio de [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md) interface, que fornece uma exibição somente leitura dos dados.  
  
## <a name="requirements"></a>Requisitos  
 Cabeçalho: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Consulte também  
 [Interfaces de núcleo](../../../extensibility/debugger/reference/core-interfaces.md)   
 [Visualizador de tipo e o visualizador personalizado](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)   
 [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)   
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
