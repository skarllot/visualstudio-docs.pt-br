---
title: IDebugDocumentTextEvents2::onUpdateDocumentAttributes | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugDocumentTextEvents2::OnUpdateDocumentAttributes
helpviewer_keywords:
- IDebugDocumentTextEvents2::onUpdateDocumentAttributes
ms.assetid: 31b7d151-9ce2-438e-b405-f8cc46b9f537
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
ms.openlocfilehash: df1d32e5a84b33d9613911e64bdbbdfa956d8b3d
ms.lasthandoff: 02/22/2017

---
# <a name="idebugdocumenttextevents2onupdatedocumentattributes"></a>IDebugDocumentTextEvents2::onUpdateDocumentAttributes
Notifica o receptor do evento que os atributos do documento foram atualizados.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
HRESULT onUpdateDocumentAttributes(   
   TEXT_DOC_ATTR_2 textdocattr  
);  
```  
  
```c#  
int onUpdateDocumentAttributes(   
   enum_TEXT_DOC_ATTR_2 textdocattr  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `textdocattr`  
 [in] Uma combinação de sinalizadores do [TEXT_DOC_ATTR_2](../../../extensibility/debugger/reference/text-doc-attr-2.md) enumeração que especifica os atributos atualizados do documento.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna um código de erro.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugDocumentTextEvents2](../../../extensibility/debugger/reference/idebugdocumenttextevents2.md)   
 [TEXT_DOC_ATTR_2](../../../extensibility/debugger/reference/text-doc-attr-2.md)
