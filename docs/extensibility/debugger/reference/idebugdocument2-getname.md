---
title: IDebugDocument2::GetName | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugDocument2::GetName
helpviewer_keywords:
- IDebugDocument2::GetName
ms.assetid: 6f09ff09-b0cf-4472-8fc8-143991f0ceb1
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
ms.openlocfilehash: faa72dd511d285ce1d9a12ce6200d1efddf12feb
ms.lasthandoff: 02/22/2017

---
# <a name="idebugdocument2getname"></a>IDebugDocument2::GetName
Obtém o nome do documento em uma das várias formas.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
HRESULT GetName(   
   GETNAME_TYPE gnType,  
   BSTR*        pbstrFileName  
);  
```  
  
```c#  
int GetName(   
   enum_GETNAME_TYPE gnType,  
   out string        pbstrFileName  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `gnType`  
 [in] Um valor a partir de [GETNAME_TYPE](../../../extensibility/debugger/reference/getname-type.md) enumeração que determina o tipo de nome a ser retornado.  
  
 `pbstrFileName`  
 [out] Retorna uma cadeia de caracteres que contém o nome do documento.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna um código de erro.  
  
## <a name="remarks"></a>Comentários  
 Esse método pode, por exemplo, retornar o nome do documento como um título ou um nome de arquivo ou até mesmo parte de um nome de arquivo.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)   
 [GETNAME_TYPE](../../../extensibility/debugger/reference/getname-type.md)
