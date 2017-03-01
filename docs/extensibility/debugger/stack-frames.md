---
title: Quadros de pilha | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- stack frames, debugging
- debugging [Debugging SDK], stack frames
- stack frames
ms.assetid: b5e439d4-1e9d-4e13-9cad-bb8b136d4ca8
caps.latest.revision: 11
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
ms.openlocfilehash: b377d70a5b49786ef5494452ae7e58913906bb2b
ms.lasthandoff: 02/22/2017

---
# <a name="stack-frames"></a>Registros de Ativação
Em termos de arquitetura do depurador, uma **quadro de pilha**:  
  
-   É uma abstração de uma pilha que fornece o contexto de execução de um thread. Um thread sempre executado dentro de uma função. Um quadro de pilha mantém as variáveis locais da função e os argumentos para ele. Para depurar com o Visual Studio, o idioma ou o ambiente está sendo depurado deve dar suporte a quadros de pilha.  
  
-   Pode identificar se descreva e pode retornar o thread associado. Um quadro de pilha também pode retornar o contexto do código que representa o ponteiro de instrução atual, bem como a documentação associada e contextos de avaliação de expressão.  
  
-   Tem propriedades que descrevem o nome, tipo e valor de argumentos e variáveis locais e que aparecem em várias janelas de depuração do IDE.  
  
-   É representado por um [IDebugStackFrame2](../../extensibility/debugger/reference/idebugstackframe2.md) interface, geralmente criado por um mecanismo de depuração (DE) ou a máquina virtual como consequência executando um thread.  
  
## <a name="see-also"></a>Consulte também  
 [Contextos de depurador](../../extensibility/debugger/debugger-contexts.md)   
 [Conceitos do depurador](../../extensibility/debugger/debugger-concepts.md)   
 [Mecanismo de depuração](../../extensibility/debugger/debug-engine.md)   
 [IDebugStackFrame2](../../extensibility/debugger/reference/idebugstackframe2.md)
