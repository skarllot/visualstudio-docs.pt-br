---
title: IDebugEnumField::GetValueFromStringCaseInsensitive | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugEnumField::GetValueFromStringCaseInsensitive
helpviewer_keywords:
- IDebugEnumField::GetValueFromStringCaseInsensitive method
ms.assetid: ef95b38e-d9b2-4fb5-a166-7c2e14641dc7
caps.latest.revision: 8
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
ms.openlocfilehash: cac471a6a3ea7cdbdeee90abfee42375d09859a3
ms.lasthandoff: 02/22/2017

---
# <a name="idebugenumfieldgetvaluefromstringcaseinsensitive"></a>IDebugEnumField::GetValueFromStringCaseInsensitive
Esse método usa uma pesquisa diferencia maiusculas de minúsculas para retornar o valor associado ao nome de uma constante de enumeração.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
HRESULT GetValueFromStringCaseInsensitive(  
   LPCOLESTR  pszValue,  
   ULONGLONG* pvalue  
);  
```  
  
```c#  
int GetValueFromStringCaseInsensitive(  
   string    pszValue,   
   out ulong pValue  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pszValue`  
 [in] Uma cadeia de caracteres especificando o nome para o qual obter o valor. Observe que para C++, essa é uma cadeia de caracteres largos.  
  
 `pValue`  
 [out] Retorna o valor numérico associado.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna `S_FALSE`, se o nome não é parte de enumeração ou um código de erro.  
  
## <a name="remarks"></a>Comentários  
 Esse método diferencia maiusculas de minúsculas. Se for necessária uma pesquisa diferencia maiusculas de minúsculas (por exemplo, em uma linguagem como C++ onde os nomes diferenciam maiusculas de minúsculas), use [GetValueFromString](../../../extensibility/debugger/reference/idebugenumfield-getvaluefromstring.md).  
  
## <a name="see-also"></a>Consulte também  
 [IDebugEnumField](../../../extensibility/debugger/reference/idebugenumfield.md)   
 [GetValueFromString](../../../extensibility/debugger/reference/idebugenumfield-getvaluefromstring.md)
