---
title: "Contexto de código | Documentos do Microsoft"
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
ms.assetid: 65e4d37a-086b-426e-9394-a3534967fd59
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
ms.openlocfilehash: 352038caf276c3cf0c70e78d158a8856d810bf48
ms.lasthandoff: 02/22/2017

---
# <a name="code-context"></a>Contexto de Código
Em [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] depuração, uma **o contexto de código**:  
  
-   Fornece uma abstração de uma posição no código como conhecido para o mecanismo de depuração (DE). A maioria das arquiteturas de tempo de execução de hoje, um contexto de código pode ser pensado como um endereço no fluxo de instruções do programa. Para idiomas não tradicionais, onde o código não pode ser representado por instruções, um contexto de código pode ser representado por outros meios.  
  
-   Descreve a posição atual no fluxo de execução do programa que está sendo depurado.  
  
-   Existe somente quando um programa foi interrompido no ponto de interrupção.  
  
-   Tem um contexto de documento associado.  
  
-   É implementada por um [IDebugCodeContext2](../../extensibility/debugger/reference/idebugcodecontext2.md) interface.  
  
## <a name="see-also"></a>Consulte também  
 [Contexto de documento](../../extensibility/debugger/document-context.md)   
 [Contextos de depurador](../../extensibility/debugger/debugger-contexts.md)
