---
title: IDebugDocumentText2 | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugDocumentText2
helpviewer_keywords:
- IDebugDocumentText2 interface
ms.assetid: e85f50a3-211c-4220-a9f4-789950ba2782
caps.latest.revision: 12
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
ms.openlocfilehash: c07e63076b13943fceb00c48675307dd28cc9eaf
ms.lasthandoff: 02/22/2017

---
# <a name="idebugdocumenttext2"></a>IDebugDocumentText2
Essa interface representa um documento de texto.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
IDebugDocumentText2 : IDebugDocument2  
```  
  
## <a name="notes-for-implementers"></a>Observações para implementadores  
 Um mecanismo de depuração (DE) implementa essa interface quando ele precisa fornecer o código-fonte está em formato de texto. Como esse é o caso mais comum, se a DE implementar o [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md) interface, ele também deve implementar o `IDebugDocumentText2` interface.  
  
## <a name="notes-for-callers"></a>Observações para chamadores  
 Use o `QueryInterface` método para obter essa interface de um `IDebugDocument2` interface.  
  
## <a name="methods-in-vtable-order"></a>Métodos na ordem Vtable  
 Além dos métodos de `IDebugDocument2` interface, essa interface implementa os métodos a seguir:  
  
|Método|Descrição|  
|------------|-----------------|  
|[GetSize](../../../extensibility/debugger/reference/idebugdocumenttext2-getsize.md)|Recupera o tamanho do texto nessa posição no documento.|  
|[GetText](../../../extensibility/debugger/reference/idebugdocumenttext2-gettext.md)|Recupera o texto da posição especificada no documento.|  
  
## <a name="remarks"></a>Comentários  
 Um objeto que implementa essa interface também deve implementar o <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer>da interface, que fornece o <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint>interface para um [IDebugDocumentTextEvents2](../../../extensibility/debugger/reference/idebugdocumenttextevents2.md) objeto.</xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint> </xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer>  
  
## <a name="requirements"></a>Requisitos  
 Cabeçalho: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Consulte também  
 [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)   
 [IDebugDocumentTextEvents2](../../../extensibility/debugger/reference/idebugdocumenttextevents2.md)
