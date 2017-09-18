---
title: IDebugReference2::SetValueAsString | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugReference2::SetValueAsString
helpviewer_keywords:
- IDebugReference2::SetValueAsString
ms.assetid: 9a508ced-fd54-44f5-bb42-ec15c80384d7
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
ms.openlocfilehash: c7f6f31a34127e8533cfa77ff4d47143c578f24c
ms.lasthandoff: 02/22/2017

---
# <a name="idebugreference2setvalueasstring"></a>IDebugReference2::SetValueAsString
Define o valor de uma referência de uma cadeia de caracteres. Reservado para uso futuro.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
HRESULT SetValueAsString (   
   LPCOLESTR pszValue,  
   DWORD     dwRadix,  
   DWORD     dwTimeout  
);  
```  
  
```c#  
int SetValueAsString (   
   string pszValue,  
   uint   dwRadix,  
   uint   dwTimeout  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pszValue`  
 [in] O valor como uma cadeia de caracteres.  
  
 `dwRadix`  
 [in] A base a ser usada na formatação de todas as informações numéricas.  
  
 `dwTimeout`  
 [in] Tempo máximo, em milissegundos, para aguardar antes de retornar desse método. Use `INFINITE` para aguardar indefinidamente.  
  
## <a name="return-value"></a>Valor de retorno  
 Sempre retorna `E_NOTIMPL`.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)
