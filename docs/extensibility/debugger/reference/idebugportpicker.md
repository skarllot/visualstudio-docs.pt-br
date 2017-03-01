---
title: IDebugPortPicker | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- IDebugPortPicker interface
ms.assetid: 8b7f6685-a3c5-4355-b706-c1b574f6ff84
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
ms.openlocfilehash: d7df3ffc68ef56a8cced2594705d852d6e4835d8
ms.lasthandoff: 02/22/2017

---
# <a name="idebugportpicker"></a>IDebugPortPicker
Representa uma interface do usuário personalizada para selecionar a porta.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
IDebugPortPicker : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Observações para implementadores  
 Essa interface é implementada por fornecedores de porta. Um fornecedor de porta define seu seletor de porta, expondo-as como um CLSID e apontando a `metricPortPickerCLSID` métrica no CLSID exposto.  
  
## <a name="methods"></a>Métodos  
 A tabela a seguir mostra os métodos de `IDebugPortPicker`.  
  
|Método|Descrição|  
|------------|-----------------|  
|[DisplayPortPicker](../../../extensibility/debugger/reference/idebugportpicker-displayportpicker.md)|Exibe a caixa de diálogo especificada que permite ao usuário selecionar uma porta.|  
|[SetSite](../../../extensibility/debugger/reference/idebugportpicker-setsite.md)|Define o provedor de serviço.|  
  
## <a name="requirements"></a>Requisitos  
 Cabeçalho: Msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll
