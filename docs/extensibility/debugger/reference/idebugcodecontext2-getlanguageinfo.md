---
title: IDebugCodeContext2::GetLanguageInfo | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugCodeContext2::GetLanguageInfo
helpviewer_keywords:
- IDebugCodeContext2::GetLanguageInfo
ms.assetid: 03002ef1-9fe6-44b6-b23b-ef7b86b2b21b
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
ms.openlocfilehash: a840c7ac29cfb900716f163c0fb77cd8f4c35751
ms.lasthandoff: 02/22/2017

---
# <a name="idebugcodecontext2getlanguageinfo"></a>IDebugCodeContext2::GetLanguageInfo
Obtém as informações de idioma para este contexto de código.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
HRESULT GetLanguageInfo(   
   BSTR* pbstrLanguage,  
   GUID* pguidLanguage  
);  
```  
  
```c#  
int GetLanguageInfo(   
   ref string pbstrLanguage,  
   ref Guid pguidLanguage  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pbstrLanguage`  
 [no, out] Retorna uma cadeia de caracteres que contém o nome do idioma, como "C++".  
  
 `pguidLanguage`  
 [no, out] Retorna o GUID para o idioma do contexto do código, por exemplo, `guidCPPLang`.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna um código de erro.  
  
## <a name="remarks"></a>Comentários  
 Pelo menos um dos parâmetros deve retornar um valor não nulo.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)
