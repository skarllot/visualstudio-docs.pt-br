---
title: IDebugSymbolProvider::GetContextFromAddress | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugSymbolProvider::GetContextFromAddress
helpviewer_keywords:
- IDebugSymbolProvider::GetContextFromAddress method
ms.assetid: 7a27d56f-20d4-4e5c-af7b-7307d3aff0a1
caps.latest.revision: 11
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
ms.openlocfilehash: 56c5f8e2a6433b23d8533fd2aec5792a4949475a
ms.lasthandoff: 02/22/2017

---
# <a name="idebugsymbolprovidergetcontextfromaddress"></a>IDebugSymbolProvider::GetContextFromAddress
Esse método mapeia um endereço de depuração em um contexto de documento.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
HRESULT GetContextFromAddress(   
   IDebugAddress*           pAddress,  
   IDebugDocumentContext2** ppDocContext  
);  
```  
  
```c#  
int GetContextFromAddress(  
   IDebugAddress              pAddress,   
   out IDebugDocumentContext2 ppDocContext  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pAddress`  
 [in] O endereço de depuração, conforme representado por um [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) interface.  
  
 `ppDocContext`  
 [out] Retorna um contexto de documento, conforme representado por um [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) interface.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna um código de erro.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)   
 [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)   
 [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)
