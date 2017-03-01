---
title: IDebugProperty3::DestroyObjectID | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugProperty3::DestroyObjectID
helpviewer_keywords:
- IDebugProperty3::DestroyObjectID
ms.assetid: bd08f356-cc67-4717-98c9-c3d00cad2040
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
ms.openlocfilehash: e5edb1969d2673e245bb6a7b3ca043fdea160fce
ms.lasthandoff: 02/22/2017

---
# <a name="idebugproperty3destroyobjectid"></a>IDebugProperty3::DestroyObjectID
Destrói a ID exclusiva associada a essa propriedade, indicando que o chamador não se importa identificar essa propriedade exclusivamente de todas as outras propriedades.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT DestroyObjectID(  
   void  
);  
```  
  
```c#  
int DestroyObjectID();  
```  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna um código de erro.  
  
## <a name="remarks"></a>Comentários  
 Se o mecanismo de depuração não precisar oferecer suporte a IDs exclusivas para uma propriedade (porque ele já rastreia exclusivamente internamente), em seguida, ele pode simplesmente retornar `E_NOTIMPL` para esse método.  
  
 Identificações exclusivas são criadas com uma chamada para o [CreateObjectID](../../../extensibility/debugger/reference/idebugproperty3-createobjectid.md) método quando o chamador deseja certificar-se de que esta propriedade é identificada exclusivamente entre todas as outras propriedades.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)   
 [CreateObjectID](../../../extensibility/debugger/reference/idebugproperty3-createobjectid.md)
