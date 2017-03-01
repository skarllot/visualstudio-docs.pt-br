---
title: IDebugPointerObject::Dereference | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugPointerObject::Dereference
helpviewer_keywords:
- IDebugPointerObject::Dereference method
ms.assetid: 196ec2cc-8569-4780-b217-23b24e7f50ca
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
ms.openlocfilehash: 06af31ef9bd784ad4dc4797eeb3d7ddbaf3ed8c6
ms.lasthandoff: 02/22/2017

---
# <a name="idebugpointerobjectdereference"></a>IDebugPointerObject::Dereference
Obtém o objeto apontado.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
HRESULT DeReference(   
   DWORD          dwIndex,  
   IDebugObject** ppObject  
);  
```  
  
```c#  
int Dereference(  
   uint             dwIndex,   
   out IDebugObject ppObject  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `dwIndex`  
 [in] Um deslocamento de byte simples desde o início do objeto apontado.  
  
 `ppObject`  
 [out] Retorna um [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) do objeto que representa o objeto apontado, além de deslocamento, se houver.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retornará S_OK; Caso contrário, retorna um código de erro. Retornará E_FAIL se este objeto não aponta para um outro objeto.  
  
## <a name="remarks"></a>Comentários  
 O objeto apontado pode ser um primitivo ou um tipo mais complexo, como uma classe ou estrutura.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugPointerObject](../../../extensibility/debugger/reference/idebugpointerobject.md)
