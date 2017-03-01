---
title: IDebugSymbolProviderDirect::GetCurrentModulesState | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- GetCurrentModulesState
- IDebugSymbolProviderDirect::GetCurrentModulesState
ms.assetid: a0c85318-5686-4eed-b213-21f2b9e681e6
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
ms.openlocfilehash: 1d9b8bbfb9982bcb54a3ef90e89442b111fc9d58
ms.lasthandoff: 02/22/2017

---
# <a name="idebugsymbolproviderdirectgetcurrentmodulesstate"></a>IDebugSymbolProviderDirect::GetCurrentModulesState
Recupera informações sobre o grupo de símbolo do qual o provedor de símbolo é um membro.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
HRESULT GetCurrentModulesState(  
    DWORD*          pState,  
    unsigned long * count  
);  
```  
  
```c#  
int GetCurrentModulesState(  
    out uint pState,  
    out uint count  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pState`  
 [out] O estado do grupo de provedor de símbolo.  
  
 `count`  
 [out] Número de módulos no grupo.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna um código de erro.  
  
## <a name="remarks"></a>Comentários  
 O estado é alterado sempre que um módulo é adicionado ou removido do grupo de símbolo. Portanto, esse método pode ser usado para detectar se um grupo de símbolo foi modificado.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugSymbolProviderDirect](../../../extensibility/debugger/reference/idebugsymbolproviderdirect.md)
