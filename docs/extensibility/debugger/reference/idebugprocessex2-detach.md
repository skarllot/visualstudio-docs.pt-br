---
title: IDebugProcessEx2::Detach | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugProcessEx2::Detach
helpviewer_keywords:
- IDebugProcessEx2::Detach method
ms.assetid: 66d54c2c-9302-47c8-9975-f30ed988ab29
caps.latest.revision: 15
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
ms.openlocfilehash: 579b8a5aaf4aff6c2629a7bcc2cc92d66b208870
ms.lasthandoff: 02/22/2017

---
# <a name="idebugprocessex2detach"></a>IDebugProcessEx2::Detach
Esse método informa o processo que uma sessão não está depurando o processo.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
HRESULT Detach(   
   IDebugSession2* pSession  
);  
```  
  
```c#  
int Detach(  
   IDebugSession2 pSession  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pSession`  
 [in] Um valor que identifica exclusivamente a sessão para desanexar este processo de.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna um código de erro.  
  
## <a name="remarks"></a>Comentários  
 A interface passado `pSession` é deve ser tratada apenas como um cookie, um valor que identifica exclusivamente o Gerenciador de sessão de depuração que originalmente anexado a esse processo; nenhum dos métodos na interface fornecida é funcional.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugProcessEx2](../../../extensibility/debugger/reference/idebugprocessex2.md)
