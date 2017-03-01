---
title: IEEDataStorage | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IEEDataStorage
helpviewer_keywords:
- IEEDataStorage interface
ms.assetid: 704e932d-2325-410e-89c4-ce88c6ec19da
caps.latest.revision: 11
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
ms.openlocfilehash: dbdf85c65e6b496a5dcc9f89b6a78d69b142d041
ms.lasthandoff: 02/22/2017

---
# <a name="ieedatastorage"></a>IEEDataStorage
Essa interface representa uma matriz de bytes.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
IEEDataStorage : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Observações para implementadores  
 O avaliador de expressão (EE) implementa essa interface para representar uma matriz de bytes (usada por visualizadores de tipo para recuperar e alterar dados através de [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md) interface). Normalmente, o EE implementa essa interface para oferecer suporte a visualizadores de tipo externo.  
  
## <a name="notes-for-callers"></a>Observações para chamadores  
 Os métodos de `IPropertyProxyEESide` interface todos retornar essa interface. Chamar [GetPropertyProxy](../../../extensibility/debugger/reference/ipropertyproxyprovider-getpropertyproxy.md) para obter o [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md) interface. Chamar [QueryInterface](/visual-cpp/atl/queryinterface) em uma [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) interface para obter o [IPropertyProxyProvider](../../../extensibility/debugger/reference/ipropertyproxyprovider.md) interface.  
  
## <a name="methods-in-vtable-order"></a>Métodos na ordem Vtable  
 O `IEEDataStorage` interface implementa os métodos a seguir:  
  
|Método|Descrição|  
|------------|-----------------|  
|[GetData](../../../extensibility/debugger/reference/ieedatastorage-getdata.md)|Recupera o número especificado de bytes de dados para um buffer fornecido.|  
|[GetSize](../../../extensibility/debugger/reference/ieedatastorage-getsize.md)|Recupera o número de bytes de dados disponíveis.|  
  
## <a name="remarks"></a>Comentários  
 Essa interface é usada por um visualizador de tipo para acessar os dados mantidos por um objeto específico. Os dados serão tratados como uma matriz de bytes, permitindo que o Visualizador de tipo para manipulá-la de forma que é necessária para apresentá-lo ao usuário.  
  
 Um visualizador personalizado também pode usar essa interface, se desejado, embora normalmente, um visualizador personalizado usaria uma interface personalizada, [GetMemoryBytes](../../../extensibility/debugger/reference/idebugproperty2-getmemorybytes.md) ou [GetStringChars](../../../extensibility/debugger/reference/idebugproperty3-getstringchars.md) (de dados orientada a cadeia de caracteres).  
  
## <a name="requirements"></a>Requisitos  
 Cabeçalho: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Consulte também  
 [Interfaces de núcleo](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)   
 [Visualizador de tipo e o visualizador personalizado](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)
