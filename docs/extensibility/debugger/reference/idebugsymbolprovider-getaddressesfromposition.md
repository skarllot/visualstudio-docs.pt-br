---
title: IDebugSymbolProvider::GetAddressesFromPosition | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugSymbolProvider::GetAddressesFromPosition
helpviewer_keywords:
- IDebugSymbolProvider::GetAddressesFromPosition method
ms.assetid: 1b0f02cb-8ace-4614-88f3-0e10239012b3
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
ms.openlocfilehash: 28c913ca924274c946b3ce52a964a3efbae6dc5c
ms.lasthandoff: 02/22/2017

---
# <a name="idebugsymbolprovidergetaddressesfromposition"></a>IDebugSymbolProvider::GetAddressesFromPosition
Esse método mapeia uma posição de documento em uma matriz de endereços de depuração.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
HRESULT GetAddressesFromPosition(   
   IDebugDocumentPosition2* pDocPos,  
   BOOL                     fStatmentOnly,  
   IEnumDebugAddresses**    ppEnumBegAddresses,  
   IEnumDebugAddresses**    ppEnumEndAddresses  
);  
```  
  
```c#  
int GetAddressesFromPosition(   
   IDebugDocumentPosition2  pDocPos,  
   bool                     fStatmentOnly,  
   out IEnumDebugAddresses  ppEnumBegAddresses,  
   out IEnumDebugAddresses  ppEnumEndAddresses  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pDocPos`  
 [in] A posição do documento.  
  
 `fStatmentOnly`  
 [in] Se TRUE, limita os endereços de depuração para uma única instrução.  
  
 `ppEnumBegAddresses`  
 [out] Retorna um enumerador para os endereços iniciais de depuração associados com esta instrução ou linha.  
  
 `ppEnumEndAddresses`  
 [out] Retorna um [IEnumDebugAddresses](../../../extensibility/debugger/reference/ienumdebugaddresses.md) enumerador para os endereços de depuração final associados com esta instrução ou linha.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna um código de erro.  
  
## <a name="remarks"></a>Comentários  
 Uma posição de documento normalmente indica um intervalo de linhas de origem. Este método fornece inicial e final depuração endereços associados a essas linhas. Algumas linguagens permitem que as instruções que abrangem várias linhas e linhas que contém mais de uma instrução. Este método fornece um sinalizador para limitar os endereços de depuração para uma única instrução.  
  
 É possível que uma única instrução ter vários endereços de depuração, como no caso de modelos.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)   
 [GetAddressesFromContext](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromcontext.md)   
 [IEnumDebugAddresses](../../../extensibility/debugger/reference/ienumdebugaddresses.md)
