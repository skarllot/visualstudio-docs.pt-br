---
title: OPTNAMECHANGEPFN | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- OPTNAMECHANGEPFN
helpviewer_keywords:
- OPTNAMECHANGEPFN callback function
ms.assetid: 147303f3-c7f1-438a-81b7-db891ea3d076
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
ms.openlocfilehash: f4a7adda4b71cc8a4b8cefac065cbec0dd72c83f
ms.lasthandoff: 02/22/2017

---
# <a name="optnamechangepfn"></a>OPTNAMECHANGEPFN
Essa é uma função de retorno de chamada especificada em uma chamada para o [SccSetOption](../extensibility/sccsetoption-function.md) (usando a opção `SCC_OPT_NAMECHANGEPFN`) e é usado para comunicar alterações de nome feitas pelo controle de origem plug-in para o IDE.  
  
## <a name="signature"></a>Assinatura  
  
```cpp#  
typedef void (*OPTNAMECHANGEPFN)(  
   LPVOID pvCallerData,  
   LPCSTR pszOldName,  
   LPCSTR pszNewName  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 pvCallerData  
 [in] Valor de usuário especificado em uma chamada anterior para o [SccSetOption](../extensibility/sccsetoption-function.md) (usando a opção `SCC_OPT_USERDATA`).  
  
 pszOldName  
 [in] O nome original do arquivo.  
  
 pszNewName  
 [in] O nome do arquivo foi renomeado para.  
  
## <a name="return-value"></a>Valor de retorno  
 Nenhum.  
  
## <a name="remarks"></a>Comentários  
 Se um arquivo é renomeado durante uma operação de controle de origem, o plug-in de controle de origem pode notificar o IDE sobre a alteração do nome por meio desse retorno de chamada.  
  
 Se o IDE não oferece suporte para esse retorno de chamada, ele não chamará o [SccSetOption](../extensibility/sccsetoption-function.md) especificá-lo. Se o plug-in não suporta esse retorno de chamada, ele retornará `SCC_E_OPNOTSUPPORTED` da `SccSetOption` quando o IDE tenta definir o retorno de chamada de função.  
  
## <a name="see-also"></a>Consulte também  
 [Funções de retorno de chamada implementadas pelo IDE](../extensibility/callback-functions-implemented-by-the-ide.md)   
 [SccSetOption](../extensibility/sccsetoption-function.md)
