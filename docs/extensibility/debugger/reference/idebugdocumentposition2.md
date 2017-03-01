---
title: IDebugDocumentPosition2 | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugDocumentPosition2
helpviewer_keywords:
- IDebugDocumentPosition2 interface
ms.assetid: 0e838ced-12bb-4efc-b811-2b7c034b77b0
caps.latest.revision: 13
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
ms.openlocfilehash: 3e683359902cec05e24725df84dc590ff966a1f2
ms.lasthandoff: 02/22/2017

---
# <a name="idebugdocumentposition2"></a>IDebugDocumentPosition2
Essa interface representa uma posição abstrata em um arquivo de origem.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
IDebugDocumentPosition2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Observações para implementadores  
 Normalmente, o Visual Studio implementa essa interface. Um mecanismo de depuração (DE) também deve implementar essa interface se ele deve fornecer seu próprio código-fonte (como quando o DE implementa o [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md) interface).  
  
## <a name="notes-for-callers"></a>Observações para chamadores  
 Essa interface é passada como um argumento para [EnumCodeContexts](../../../extensibility/debugger/reference/idebugprogram2-enumcodecontexts.md). Ele também é fornecido como parte de um [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md) union (especificamente, uma [BP_LOCATION_CODE_FILE_LINE](../../../extensibility/debugger/reference/bp-location-code-file-line.md) estrutura) que por sua vez é parte do [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) estrutura, que é usada na criação de um ponto de interrupção pendente.  
  
## <a name="methods-in-vtable-order"></a>Métodos na ordem Vtable  
 A tabela a seguir mostra os métodos de `IDebugDocumentPosition2`.  
  
|Método|Descrição|  
|------------|-----------------|  
|[GetFileName](../../../extensibility/debugger/reference/idebugdocumentposition2-getfilename.md)|Obtém o nome do arquivo do arquivo de origem que contém essa posição do documento.|  
|[GetDocument](../../../extensibility/debugger/reference/idebugdocumentposition2-getdocument.md)|Obtém o que contém o documento.|  
|[IsPositionInDocument](../../../extensibility/debugger/reference/idebugdocumentposition2-ispositionindocument.md)|Determina se essa posição está contida em um determinado documento.|  
|[GetRange](../../../extensibility/debugger/reference/idebugdocumentposition2-getrange.md)|Obtém o intervalo para essa posição de documento.|  
  
## <a name="requirements"></a>Requisitos  
 Cabeçalho: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Consulte também  
 [EnumCodeContexts](../../../extensibility/debugger/reference/idebugprogram2-enumcodecontexts.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [BP_LOCATION_CODE_FILE_LINE](../../../extensibility/debugger/reference/bp-location-code-file-line.md)
