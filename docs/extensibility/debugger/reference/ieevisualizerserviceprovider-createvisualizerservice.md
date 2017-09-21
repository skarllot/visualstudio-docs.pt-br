---
title: IEEVisualizerServiceProvider::CreateVisualizerService | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IEEVisualizerServiceProvider::CreateVisualizerService
helpviewer_keywords:
- IEEVisualizerServiceProvider::CreateVisualizerService method
ms.assetid: f366f7c9-358d-46c8-993f-32ff86539833
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
ms.openlocfilehash: 05b913396cffd438ae42a8dcf76064385fe14bae
ms.lasthandoff: 02/22/2017

---
# <a name="ieevisualizerserviceprovidercreatevisualizerservice"></a>IEEVisualizerServiceProvider::CreateVisualizerService
Esse método cria um serviço do visualizador.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT CreateVisualizerService(  
   IDebugBinder*              binder,  
   IDebugSymbolProvider*      pSymProv,  
   IDebugAddress*             pAddress,  
   IEEVisualizerDataProvider* dataProvider,  
   IEEVisualizerService**     ppService  
);  
```  
  
```c#  
int CreateVisualizerService(  
   IDebugBinder binder,  
   IDebugSymbolProvider      pSymProv,  
   IDebugAddress             pAddress,  
   IEEVisualizerDataProvider dataProvider,  
   out IEEVisualizerService  ppService  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `binder`  
 [in] O [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md) objeto passado para [EvaluateSync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md).  
  
 `pSymProv`  
 [in] O [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md) objeto passado para `IDebugParsedExpression::EvaluateSync`.  
  
 `pAddress`  
 [in] O [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) objeto passado para `IDebugParsedExression::EvaluateSync`.  
  
 `dataProvider`  
 [in] Um objeto que implementa o [IEEVisualizerDataProvider](../../../extensibility/debugger/reference/ieevisualizerdataprovider.md) interface (fornecido pelo avaliador de expressão).  
  
 `ppService`  
 [out] O serviço criado.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna um código de erro.  
  
## <a name="remarks"></a>Comentários  
 O `binder`, `pSymProv`, e `pAddress` parâmetros foram passados para o `IDebugParsedExpression::EvaluateSync` método. `CreateVisualizerService`deve ser chamado apenas de `IDebugParsedExpression::EvaluateSync` como parte do suporte de um avaliador de expressão para visualizadores de tipo.  
  
## <a name="see-also"></a>Consulte também  
 [IEEVisualizerServiceProvider](../../../extensibility/debugger/reference/ieevisualizerserviceprovider.md)   
 [EvaluateSync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)   
 [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)   
 [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)   
 [IEEVisualizerDataProvider](../../../extensibility/debugger/reference/ieevisualizerdataprovider.md)
