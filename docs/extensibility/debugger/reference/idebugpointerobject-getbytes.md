---
title: IDebugPointerObject::GetBytes | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugPointerObject::GetBytes
helpviewer_keywords:
- IDebugPointerObject::GetBytes method
ms.assetid: e986c188-87fb-4b51-86e9-ee6a0035bdab
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
ms.openlocfilehash: 26b360104aaf5777337a5c8d3a6bc4d629eb5a0d
ms.lasthandoff: 02/22/2017

---
# <a name="idebugpointerobjectgetbytes"></a>IDebugPointerObject::GetBytes
Obtém o valor apontado como uma série de bytes consecutivos.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
HRESULT GetBytes(   
   DWORD  dwStart,  
   DWORD  dwCount,  
   BYTE*  pBytes,  
   DWORD* pdwBytes  
);  
```  
  
```c#  
int GetBytes(  
   uint       dwStart,   
   uint       dwCount,   
   out byte[] pBytes,   
   out uint   pdwBytes  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `dwStart`  
 [in] Um deslocamento, em bytes, desde o início do objeto apontado.  
  
 `dwCount`  
 [in] O número de bytes a serem recuperados.  
  
 `pBytes`  
 [no, out] Uma matriz que é preenchida com o valor como uma série de bytes consecutivos, começando no deslocamento especificado do objeto apontado.  
  
 `pdwBytes`  
 [out] Retorna o número de bytes realmente recuperados.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retornará S_OK; Caso contrário, retorna um código de erro.  
  
## <a name="remarks"></a>Comentários  
 Esse método é usado se o ponteiro, conforme representado por esse [IDebugPointerObject](../../../extensibility/debugger/reference/idebugpointerobject.md) aponta para um tipo primitivo ou uma matriz de tipos primitivos (ou seja, uma matriz que pode ser representado por uma simple sequência de bytes).  
  
## <a name="see-also"></a>Consulte também  
 [IDebugPointerObject](../../../extensibility/debugger/reference/idebugpointerobject.md)   
 [SetBytes](../../../extensibility/debugger/reference/idebugpointerobject-setbytes.md)
