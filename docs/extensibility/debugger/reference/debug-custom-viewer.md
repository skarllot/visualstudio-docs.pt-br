---
title: DEBUG_CUSTOM_VIEWER | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- DEBUG_CUSTOM_VIEWER
helpviewer_keywords:
- DEBUG_CUSTOM_VIEWER structure
ms.assetid: 8e0ef3f0-0107-48e8-a037-6e52b4c4ed9d
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
ms.openlocfilehash: 7d32ca283b82691f4391d069d28b4a634489dffd
ms.lasthandoff: 02/22/2017

---
# <a name="debugcustomviewer"></a>DEBUG_CUSTOM_VIEWER
Uma estrutura que identifica um visualizador personalizado ou digite visualizador.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
typedef struct tagDEBUG_CUSTOM_VIEWER {  
   DWORD dwID;  
   BSTR  bstrMenuName;  
   BSTR  bstrDescription;  
   GUID  guidLang;  
   GUID  guidVendor;  
   BSTR  bstrMetric;  
} DEBUG_CUSTOM_VIEWER;  
```  
  
```c#  
public struct DEBUG_CUSTOM_VIEWER {  
   public uint   dwID;  
   public string bstrMenuName;  
   public string bstrDescription;  
   public Guid   guidLang;  
   public Guid   guidVendor;  
   public string bstrMetric;  
};  
```  
  
## <a name="members"></a>Membros  
 dwID  
 Uma ID para diferenciar vários visualizadores ou visualizadores implementados por um `GUID`.  
  
 bstrMenuName  
 O texto que aparecerá no menu suspenso.  
  
 bstrDescription  
 Uma descrição do visualizador personalizado ou Visualizador de tipo (deve ser um valor nulo se não usado).  
  
 guidLang  
 Idioma do avaliador de expressão fornece.  
  
 guidVendor  
 Fornecedor do avaliador de expressão fornece.  
  
 bstrMetric  
 Métrica sob a qual o visualizador personalizado ou o Visualizador de tipo `CLSID` é armazenada.  
  
## <a name="remarks"></a>Comentários  
 Uma lista dessa estrutura é retornada por uma chamada para o [GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md) método (e, por extensão, o [GetCustomViewerList](../../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewerlist.md) método).  
  
## <a name="requirements"></a>Requisitos  
 Cabeçalho: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Consulte também  
 [Estruturas e uniões](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md)   
 [GetCustomViewerList](../../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewerlist.md)
