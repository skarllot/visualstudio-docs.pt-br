---
title: IDebugPortSupplierDescription2 | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- IDebugPortSupplierDescription2 interface
ms.assetid: dd19b9d6-0703-44b3-9498-cedffa0ce5b7
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
ms.openlocfilehash: b12bc5a819c709fb403d545b1f48c0bd4803c865
ms.lasthandoff: 02/22/2017

---
# <a name="idebugportsupplierdescription2"></a>IDebugPortSupplierDescription2
Permite que o [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] interface do usuário para exibir o texto dentro de **transportar informações** seção o **anexar ao processo** caixa de diálogo.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
IDebugPortSupplierDescription2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Observações para implementadores  
 Essa interface é implementada por fornecedores de porta.  
  
## <a name="methods"></a>Métodos  
 A tabela a seguir mostra os métodos de `IDebugPortSupplierDescription2`.  
  
|Método|Descrição|  
|------------|-----------------|  
|[GetDescription](../../../extensibility/debugger/reference/idebugportsupplierdescription2-getdescription.md)|Recupera a descrição e a descrição de metadados para o fornecedor de porta.|  
  
## <a name="requirements"></a>Requisitos  
 Cabeçalho: Msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll
