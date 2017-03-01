---
title: IEEVisualizerService::GetValueDisplayStringCount | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- IEEVisualizerService::GetValueDisplayStringCount
- GetValueDisplayStringCount
ms.assetid: d683a833-fbfb-4042-84df-6905124a268a
caps.latest.revision: 10
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
ms.openlocfilehash: 9b354b9070444edd3855665e6563c70a24a461fc
ms.lasthandoff: 02/22/2017

---
# <a name="ieevisualizerservicegetvaluedisplaystringcount"></a>IEEVisualizerService::GetValueDisplayStringCount
Recupera o número de cadeias de caracteres do valor a ser exibida para o campo ou propriedade especificada.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
HRESULT GetValueDisplayStringCount (  
   DWORD         displayKind,   
   IDebugField * propertyOrField,   
   ULONG *       pcelt  
);  
```  
  
```c#  
int GetValueDisplayStringCount (  
   uint        displayKind,   
   IDebugField propertyOrField,   
   out ulong   pcelt  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `displayKind`  
 [in] O valor do [DisplayKind](../../../extensibility/debugger/reference/displaykind.md) enumeração.  
  
 `propertyOrField`  
 [in] Um [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) interface que representa uma propriedade ou campo.  
  
 `pcelt`  
 [out] Retorna o número de cadeias de caracteres de valor para exibir.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna um código de erro.  
  
## <a name="see-also"></a>Consulte também  
 [IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md)
