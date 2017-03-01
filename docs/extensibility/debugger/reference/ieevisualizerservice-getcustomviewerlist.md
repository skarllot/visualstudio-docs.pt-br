---
title: IEEVisualizerService::GetCustomViewerList | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IEEVisualizerService::GetCustomViewerList
helpviewer_keywords:
- IEEVisualizerService::GetCustomViewerList method
ms.assetid: 249d26ca-914f-43af-a400-8162477223f4
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
ms.openlocfilehash: ed6db8b68fcfa0e0c5a8016de2993c01c9864be7
ms.lasthandoff: 02/22/2017

---
# <a name="ieevisualizerservicegetcustomviewerlist"></a>IEEVisualizerService::GetCustomViewerList
Esse método retorna uma lista de visualizadores de tipo que esse serviço conhece.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetCustomViewerList(  
   ULONG                celtSkip,  
   ULONG                celtRequested,  
   DEBUG_CUSTOM_VIEWER* rgViewers,  
   ULONG*               pceltFetched  
);  
```  
  
```c#  
int GetCustomViewerList(  
   uint                  celtSkip,  
   uint                  celtRequested,  
   DEBUG_CUSTOM_VIEWER[] rgViewers,  
   out uint              pceltFetched  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `celtSkip`  
 [in] Número de visualizadores para ignorar.  
  
 `celRequested`  
 [in] Número de visualizadores para recuperar (também especifica o tamanho da `rgViewers` matriz).  
  
 `rgViewers`  
 [no, out] Matriz de [DEBUG_CUSTOM_VIEWER](../../../extensibility/debugger/reference/debug-custom-viewer.md) estruturas devem ser preenchidos.  
  
 `pceltFetched`  
 [out] Número de visualizadores realmente recuperados.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna um código de erro.  
  
## <a name="remarks"></a>Comentários  
 [GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md) passa a solicitação para esse método como parte de seu suporte para visualizadores de tipo. Se o avaliador de expressão também fornece visualizadores personalizados para o mesmo tipo, ele pode acrescentar adequadamente preenchido [DEBUG_CUSTOM_VIEWER](../../../extensibility/debugger/reference/debug-custom-viewer.md) estruturas para os visualizadores personalizados à lista. Verifique se [GetCustomViewerCount](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewercount.md) reflete os visualizadores adicionais.  
  
 Consulte [tipo de visualizador e visualizador personalizado](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md) para obter detalhes sobre as diferenças entre os visualizadores e visualizadores.  
  
## <a name="see-also"></a>Consulte também  
 [IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md)   
 [DEBUG_CUSTOM_VIEWER](../../../extensibility/debugger/reference/debug-custom-viewer.md)   
 [GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md)   
 [GetCustomViewerCount](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewercount.md)   
 [Visualizador de tipo e o visualizador personalizado](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)
