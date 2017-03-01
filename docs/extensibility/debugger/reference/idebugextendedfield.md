---
title: IDebugExtendedField | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- IDebugExtendedField interface
ms.assetid: b491499c-af57-47da-87d6-34b7398f6591
caps.latest.revision: 6
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
ms.openlocfilehash: 8b1eccafe383b4b0c211f3f34846be03acd60d6d
ms.lasthandoff: 02/22/2017

---
# <a name="idebugextendedfield"></a>IDebugExtendedField
Estende os tipos de campos que estão disponíveis para oferecer suporte a genéricos de código gerenciado.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
IDebugExtendedField : IDebugField  
```  
  
## <a name="methods"></a>Métodos  
 Além dos métodos de [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) interface, essa interface implementa os métodos a seguir:  
  
|Método|Descrição|  
|------------|-----------------|  
|[GetExtendedKind](../../../extensibility/debugger/reference/idebugextendedfield-getextendedkind.md)|Recupera o tipo de campo estendido especificado.|  
|[IsClosedType](../../../extensibility/debugger/reference/idebugextendedfield-isclosedtype.md)|Determina se o campo representa um tipo fechado.|  
  
## <a name="requirements"></a>Requisitos  
 Cabeçalho: Sh.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll
