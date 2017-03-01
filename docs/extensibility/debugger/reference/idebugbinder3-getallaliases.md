---
title: IDebugBinder3::GetAllAliases | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugBinder3::GetAllAliases
helpviewer_keywords:
- IDebugBinder3::GetAllAliases method
ms.assetid: 1f9ab2ee-2ab3-4a61-8b99-95dd7fdf3511
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
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: e3663d77938a3986f5ea5fcd59bcfc0fae52b626
ms.lasthandoff: 02/22/2017

---
# <a name="idebugbinder3getallaliases"></a>IDebugBinder3::GetAllAliases
Esse método recupera uma lista de aliases do programa.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetAllAliases(  
   UINT          uRequest,  
   IDebugAlias** ppAliases,  
   UINT*         puFetched  
);  
```  
  
```c#  
int GetAllAliases(  
   uint          uRequest,   
   IDebugAlias[] ppAliases,   
   out uint      puFetched  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `uRequest`  
 [in] O número máximo de aliases para retornar (Especifica o comprimento da matriz passada em `ppAliases`).  
  
 `ppAliases`  
 [no, out] Matriz preencherem com aliases (se esse for um valor nulo e `uRequest` é 0, a contagem de aliases que podem ser retornados será retornada por `puFetched`).  
  
 `puFetched`  
 [out] Retorna o número de aliases obtido.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna um código de erro.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugBinder3](../../../extensibility/debugger/reference/idebugbinder3.md)
