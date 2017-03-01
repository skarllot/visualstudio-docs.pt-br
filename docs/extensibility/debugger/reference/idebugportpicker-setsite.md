---
title: IDebugPortPicker::SetSite | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- IDebugPortPicker::SetSite
ms.assetid: 7319e187-adfe-4b3f-aec9-521356fb5a8a
caps.latest.revision: 6
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
ms.openlocfilehash: 4a5170ec9f5ad3bbe10291567b654e5e47dc891a
ms.lasthandoff: 02/22/2017

---
# <a name="idebugportpickersetsite"></a>IDebugPortPicker::SetSite
Define o provedor de serviço.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
HRESULT SetSite(  
   IServiceProvider * pSP  
);  
```  
  
```c#  
public int SetSite(  
   IServiceProvider pSP  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pSP`  
 [in] Referência para a interface do provedor de serviços.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna um código de erro.  
  
## <a name="remarks"></a>Comentários  
 Esse método será chamado antes de quaisquer outros métodos são chamados.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugPortPicker](../../../extensibility/debugger/reference/idebugportpicker.md)
