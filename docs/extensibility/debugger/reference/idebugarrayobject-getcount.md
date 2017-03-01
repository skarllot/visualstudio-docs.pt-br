---
title: IDebugArrayObject::GetCount | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugArrayObject::GetCount
helpviewer_keywords:
- IDebugArrayObject::GetCount method
ms.assetid: 7931f3f7-033c-4bf8-8abd-95183952ebb0
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
ms.openlocfilehash: 707f3c56ddbf57f1e88f130d1c2ce4b71a9acaa4
ms.lasthandoff: 02/22/2017

---
# <a name="idebugarrayobjectgetcount"></a>IDebugArrayObject::GetCount
Obtém a contagem de elementos na matriz.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
[C++]  
HRESULT GetCount(   
   DWORD* pdwElements  
);  
```  
  
```  
[C#]  
int GetCount(  
   out uint pdwElements  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pdwElements`  
 [out] Retorna a contagem.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retornará S_OK; Caso contrário, retorna um código de erro.  
  
## <a name="remarks"></a>Comentários  
 Esse método vê todos os elementos de um objeto de matriz como uma matriz unidimensional, mesmo se o objeto de matriz é multidimensional. Por exemplo, dada a matriz `myarray[3][2][6]`, esse método retornará 36 no `pdwElements` parâmetro. Use o [GetElement](../../../extensibility/debugger/reference/idebugarrayobject-getelement.md) método para recuperar os elementos individuais, um por vez.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md)
