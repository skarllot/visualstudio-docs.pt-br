---
title: IDebugProgramPublisher2::UnpublishProgram | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugProgramPublisher2::UnpublishProgram
helpviewer_keywords:
- IDebugProgramPublisher2::UnpublishProgram
ms.assetid: 627e7d38-b2ac-4873-9a40-37ff7f47cd1d
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
ms.openlocfilehash: 6c52fb643d978979fa68af886db9f85dac697184
ms.lasthandoff: 02/22/2017

---
# <a name="idebugprogrampublisher2unpublishprogram"></a>IDebugProgramPublisher2::UnpublishProgram
Faz com que um programa não está disponível para ser depurado.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT UnpublishProgram(  
   IUnknown* pDebuggeeInterface  
);  
```  
  
```c#  
int UnpublishProgram(  
   object pDebuggeeInterface  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pDebuggeeInterface`  
 [in] Um `IUnknown` interface para o programa. Este é o mesmo valor fornecido para o [PublishProgram](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogram.md) método e identifica exclusivamente o programa que está sendo removido (ou seja, ele é usado como um cookie).  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna um código de erro.  
  
## <a name="remarks"></a>Comentários  
 Para disponibilizar um programa para os mecanismos de depuração e o Gerenciador de sessão de depuração, use o [PublishProgram](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogram.md) método.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugProgramPublisher2](../../../extensibility/debugger/reference/idebugprogrampublisher2.md)   
 [PublishProgram](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogram.md)
