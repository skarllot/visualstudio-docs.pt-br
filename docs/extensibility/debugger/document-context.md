---
title: Contexto de documentos | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- debugging [Debugging SDK], contexts
ms.assetid: 8e8b5702-5c16-4988-953d-69dd807d8b84
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
ms.openlocfilehash: 8ed5498961a575d0f9d3f7c64b46bc73a2d510b5
ms.lasthandoff: 02/22/2017

---
# <a name="document-context"></a>Contexto de documento
Em [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] depuração, uma **contexto de documento**:  
  
-   Representa uma posição em um arquivo de origem. Para os idiomas em que o arquivo de origem não pode estar presente, um contexto de documento identifica uma posição em um documento costuma ser gerada pelo ambiente de tempo de execução. Por exemplo, um mecanismo de script pode gerar um documento de script. Para obter mais informações, consulte [posição do documento](../../extensibility/debugger/document-position.md).  
  
-   Descreve uma posição em um documento de origem que corresponde a um contexto de código. O manipulador de símbolo mapeia um contexto de código ao contexto de documentação, usando as informações geradas por um compilador ou intérprete.  
  
-   É implementada por um [IDebugDocumentContext2](../../extensibility/debugger/reference/idebugdocumentcontext2.md) interface.  
  
## <a name="see-also"></a>Consulte também  
 [Contexto de código](../../extensibility/debugger/code-context.md)   
 [Provedor de símbolo](../../extensibility/debugger/symbol-provider.md)   
 [Interfaces de provedor de símbolo](../../extensibility/debugger/reference/symbol-provider-interfaces.md)   
 [Contextos de depurador](../../extensibility/debugger/debugger-contexts.md)
