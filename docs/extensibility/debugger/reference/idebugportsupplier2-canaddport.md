---
title: IDebugPortSupplier2::CanAddPort | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugPortSupplier2::CanAddPort
helpviewer_keywords:
- IDebugPortSupplier2::CanAddPort
ms.assetid: 41f69e0a-e82c-473d-8b7a-0c40fc5730fc
caps.latest.revision: 8
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
ms.openlocfilehash: 1df781c3994bb37000d2054f45cc6d7e48503c26
ms.lasthandoff: 02/22/2017

---
# <a name="idebugportsupplier2canaddport"></a>IDebugPortSupplier2::CanAddPort
Verifica se um fornecedor de porta pode adicionar novas portas.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
HRESULT CanAddPort(   
   void   
);  
```  
  
```c#  
int CanAddPort();  
```  
  
## <a name="return-value"></a>Valor de retorno  
 Se a porta pode ser adicionada, retornará `S_OK`; caso contrário, retorna `S_FALSE` para indicar que nenhuma porta pode ser adicionada a esse fornecedor de porta.  
  
## <a name="remarks"></a>Comentários  
 Chamar esse método antes de chamar o [adicionar porta](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md) método desde o último método cria a porta, bem como adicionar, que pode ser uma operação demorada.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)   
 [Adicionar porta](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md)
