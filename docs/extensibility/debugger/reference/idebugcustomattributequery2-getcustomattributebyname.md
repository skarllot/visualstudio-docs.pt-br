---
title: IDebugCustomAttributeQuery2::GetCustomAttributeByName | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugCustomAttributeQuery2::GetCustomAttributeByName
helpviewer_keywords:
- IDebugCustomAttributeQuery2::GetCustomAttributeByName
ms.assetid: 7428dfeb-8929-41b2-9b99-cb343a86c02d
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
ms.openlocfilehash: bc1b59d4f13029a765f11dfd4fe3dbe12778d00c
ms.lasthandoff: 02/22/2017

---
# <a name="idebugcustomattributequery2getcustomattributebyname"></a>IDebugCustomAttributeQuery2::GetCustomAttributeByName
Obtém os bytes de atributos personalizados, dado o nome do atributo personalizado.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
HRESULT GetCustomAttributeByName(   
   LPCOLESTR pszCustomAttributeName,  
   BYTE*     ppBlob,  
   DWORD*    pdwLen  
);  
```  
  
```c#  
int GetCustomAttributeByName(  
   [In] string        pszCustomAttributeName,   
   [In, Out] byte[]   ppBlob,   
   [In, Out] ref uint pdwLen  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pszCustomAttributeName`  
 [in] Uma cadeia de caracteres que contém o nome do atributo personalizado para procurar.  
  
 `ppBlob`  
 [no, out] Uma matriz é preenchida com os bytes de atributo personalizado.  
  
 `pdwLen`  
 [no, out] Especifica o número máximo de bytes a retornar o `ppBlob` de matriz e retorna o número de bytes gravados na matriz.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, Retorna S_OK ou retorna S_FALSE se o atributo personalizado não existe. Caso contrário, retornará um código de erro.  
  
## <a name="remarks"></a>Comentários  
 Definir o `ppBlob` atributos de parâmetro para um valor null para retornar o número de bytes disponíveis. Em seguida, alocar uma matriz e passar a matriz em para o `ppBlob` parâmetro.  
  
 Os bytes de atributo representam os dados brutos do atributo personalizado.  
  
 Se o `ppBlob` e `pdwLen` os parâmetros são definidos como um valor nulo, esse método pode ser usado para determinar se o atributo personalizado simplesmente existe. No entanto, é uma alternativa mais fácil chamar o [IsCustomAttributeDefined](../../../extensibility/debugger/reference/idebugcustomattributequery2-iscustomattributedefined.md) método.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugCustomAttributeQuery2](../../../extensibility/debugger/reference/idebugcustomattributequery2.md)   
 [IsCustomAttributeDefined](../../../extensibility/debugger/reference/idebugcustomattributequery2-iscustomattributedefined.md)
