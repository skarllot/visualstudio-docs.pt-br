---
title: IDebugBinder3::GetEEService | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugBinder3::GetEEService
helpviewer_keywords:
- IDebugBinder3::GetEEService method
ms.assetid: eb07aa40-8cd9-4a52-a4c7-4affd2307a01
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
ms.openlocfilehash: 19e223d0a5252d454c97d11fbc8794fff59a3e47
ms.lasthandoff: 02/22/2017

---
# <a name="idebugbinder3geteeservice"></a>IDebugBinder3::GetEEService
Esse método retorna um serviço solicitado.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetEEService(  
   [in] GUID        vendor,  
   [in] GUID        language,  
   [in] GUID        iid,  
   [out] IUnknown** ppService  
);  
```  
  
```c#  
Int GetEEService(  
   Guid       vendor,  
   Guid       language,  
   Guid       iid,  
   out object ppService  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `vendor`  
 [in] `GUID` de um fornecedor (um valor nulo é aceitável).  
  
 `language`  
 [in] `GUID` de um idioma (um valor nulo é aceitável).  
  
 `iid`  
 [in] `IID` do serviço para obter.  
  
 `ppService`  
 [out] Uma interface para o serviço solicitado.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna um código de erro.  
  
## <a name="remarks"></a>Comentários  
 Passar o `IID` para o [IEEVisualizerServiceProvider](../../../extensibility/debugger/reference/ieevisualizerserviceprovider.md) interface (`IID_IEEVisualizerServiceProvider`) para ver se o serviço Visualizador de tipo está disponível. Se assim, o avaliador de expressão pode obter o [IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md) interface para oferecer suporte a visualizadores de tipo. Consulte [visualizando e exibindo dados](../../../extensibility/debugger/visualizing-and-viewing-data.md) para obter detalhes.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugBinder3](../../../extensibility/debugger/reference/idebugbinder3.md)   
 [IEEVisualizerServiceProvider](../../../extensibility/debugger/reference/ieevisualizerserviceprovider.md)   
 [IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md)   
 [Visualizando e exibindo dados](../../../extensibility/debugger/visualizing-and-viewing-data.md)
