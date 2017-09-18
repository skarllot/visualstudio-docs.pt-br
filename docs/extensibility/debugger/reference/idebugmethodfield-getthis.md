---
title: IDebugMethodField::GetThis | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugMethodField::GetThis
helpviewer_keywords:
- IDebugMethodField::GetThis method
ms.assetid: cc235bea-e909-4d8c-ab54-936736c803fc
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
ms.openlocfilehash: ef9b53e5ffade5cb372f13df30aef18dc3340fed
ms.lasthandoff: 02/22/2017

---
# <a name="idebugmethodfieldgetthis"></a>IDebugMethodField::GetThis
Obtém o `this` (`Me` na [!INCLUDE[vbprvb](../../../code-quality/includes/vbprvb_md.md)]) ponteiro do objeto que contém o método.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
HRESULT GetThis(   
   IDebugClassField** ppClass  
);  
```  
  
```c#  
int GetThis(  
   out IDebugClassField ppClass  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `ppClass`  
 [out] Retorna um [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md) objeto que representa o ponteiro "this".  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retornará S_OK; Caso contrário, retorna um código de erro.  
  
## <a name="remarks"></a>Comentários  
 Em linguagens orientadas a objeto, normalmente há um ponteiro implícito para a instanciação atual de uma classe. Isso é conhecido como `this` em c / C++ e como `Me` em [!INCLUDE[vbprvb](../../../code-quality/includes/vbprvb_md.md)].  
  
## <a name="see-also"></a>Consulte também  
 [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)   
 [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)
