---
title: IDebugProperty3::CreateObjectID | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugProperty3::CreateObjectID
helpviewer_keywords:
- IDebugProperty3::CreateObjectID
ms.assetid: f2fa81e7-822f-456e-8729-a96a18eea771
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
ms.openlocfilehash: de8af937ec00abd6551ee68fc6e335ae3d918aee
ms.lasthandoff: 02/22/2017

---
# <a name="idebugproperty3createobjectid"></a>IDebugProperty3::CreateObjectID
Cria uma ID exclusiva para essa propriedade para garantir que ele seja exclusivo entre todas as outras propriedades.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT CreateObjectID(  
   void  
);  
```  
  
```c#  
int CreateObjectID();  
```  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna um código de erro.  
  
## <a name="remarks"></a>Comentários  
 Esse método é chamado quando o Gerenciador de sessão de depuração deseja certificar-se de que esta propriedade é identificada exclusivamente entre todas as outras propriedades. O mecanismo de depuração (DE) oferece suporte a esse método, a menos que as propriedades que ele lida com já exclusivamente são identificadas. Se a DE não oferece suporte a esse método, ele retorna `E_NOTIMPL`.  
  
 Qualquer ID exclusivo criado com `CreateObjectID` é destruído quando o [DestroyObjectID](../../../extensibility/debugger/reference/idebugproperty3-destroyobjectid.md) é chamado de método; isso também sinaliza o término da necessidade para identificar exclusivamente essa propriedade.  
  
> [!NOTE]
>  Não há nenhum método para recuperar essa ID exclusiva, portanto, o DE fazer o que quiser para identificações exclusivas quando o `CreateObjectID` método é chamado.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)   
 [DestroyObjectID](../../../extensibility/debugger/reference/idebugproperty3-destroyobjectid.md)
