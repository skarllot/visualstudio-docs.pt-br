---
title: IDebugProperty3::GetStringChars | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugProperty3::GetStringChars
helpviewer_keywords:
- IDebugProperty3::GetStringChars
ms.assetid: 832c37f3-85cb-4227-8ab2-f27a80eafe90
caps.latest.revision: 7
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
ms.sourcegitcommit: b743df25d0d17465de411211f5b0b6893bf67f9b
ms.openlocfilehash: a9433d9914f647c43d8190fb15fb35a99bf77a7b
ms.lasthandoff: 02/22/2017

---
# <a name="idebugproperty3getstringchars"></a>IDebugProperty3::GetStringChars
Recupera a cadeia de caracteres associada a essa propriedade e as armazena em um buffer fornecido pelo usuário.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetStringChars(  
   ULONG  buflen,  
   WCHAR* rgString,  
   ULONG* pceltFetched  
);  
```  
  
```c#  
int GetStringChars(  
   uint       buflen,   
   out string rgString,   
   out uint   pceltFetched  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `buflen`  
 [in] Número máximo de caracteres pode conter o buffer fornecido pelo usuário.  
  
 `rgString`  
 [out] Retorna a cadeia de caracteres.  
  
 [C++ somente], `rgString` é um ponteiro para um buffer que receberá os caracteres Unicode da cadeia de caracteres. Esse buffer deve ser pelo menos `buflen` caracteres (não em bytes) de tamanho.  
  
 `pceltFetched`  
 [out] Onde o número de caracteres armazenados em buffer é retornado. (Pode ser `NULL` em C++.)  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna um código de erro.  
  
## <a name="remarks"></a>Comentários  
 No C++, tome cuidado para garantir que o buffer é pelo menos `buflen` caracteres Unicode. Observe que um caractere Unicode é 2 bytes de comprimento.  
  
> [!NOTE]
>  No C++, a cadeia de caracteres retornada não inclui um caractere nulo de terminação. Se especificado, `pceltFetched` especificará o número de caracteres na cadeia de caracteres.  
  
## <a name="example"></a>Exemplo  
 
```cpp  
CStringW RetrievePropertyString(IDebugProperty2 *pPropInfo)  
{  
    CStringW returnString = L"";  
    CComQIPtr<IDebugProperty3> pProp3 = pPropInfo->pProperty;  
    If (pProp3 != NULL) {  
        ULONG dwStrLen = 0;  
        HRESULT hr;  
        hr = pProp3->GetStringCharLength(&dwStrLen);  
        if (SUCCEEDED(hr) && dwStrLen > 0) {  
            ULONG dwRead;  
            CStrBufW buf(returnString,dwStrLen,CStrBuf::SET_LENGTH);  
            hr = pProp3->GetStringChars(dwStrLen,  
                                        reinterpret_cast<WCHAR*>(static_cast<CStringW::PXSTR>(buf)),  
                                        &dwRead);  
        }  
    }  
    return(returnString);
}
```    
  
## <a name="see-also"></a>Consulte também  
 [GetStringCharLength](../../../extensibility/debugger/reference/idebugproperty3-getstringcharlength.md)   
 [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
