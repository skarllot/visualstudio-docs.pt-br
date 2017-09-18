---
title: IDebugArrayField::GetRank | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugArrayField::GetRank
helpviewer_keywords:
- IDebugArrayField::GetRank method
ms.assetid: 2364b876-5be1-4bab-9b8f-3b6121da35c6
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
ms.openlocfilehash: 56563e05c7b7569580140a941886925f717ae1ce
ms.lasthandoff: 02/22/2017

---
# <a name="idebugarrayfieldgetrank"></a>IDebugArrayField::GetRank
Obtém a classificação ou o número de dimensões da matriz.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
HRESULT GetRank(   
   DWORD* pdwRank  
);  
```  
  
```c#  
int GetRank(  
   out uint pdwRank  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pdwRank`  
 [out] Retorna a classificação.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retornará S_OK; Caso contrário, retorna um código de erro.  
  
## <a name="remarks"></a>Comentários  
 A classificação de uma matriz corresponde ao número de dimensões. Em C++ e c#, matrizes multidimensionais são realmente matrizes de matrizes em, portanto, pode ser considerados apenas uma matriz unidimensional (e o `GetRank` método sempre retorna 1). Em [!INCLUDE[vbprvb](../../../code-quality/includes/vbprvb_md.md)], por outro lado, matrizes multidimensionais são tratados de maneira diferente, e a classificação de tal uma matriz reflete o número de dimensões (e o `GetRank` método sempre retorna o número de dimensões).  
  
## <a name="see-also"></a>Consulte também  
 [IDebugArrayField](../../../extensibility/debugger/reference/idebugarrayfield.md)
