---
title: Contextos de depurador | Documentos do Microsoft
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
ms.assetid: 79808036-b680-4e4c-9c61-4ed43aa11323
caps.latest.revision: 9
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
ms.openlocfilehash: 5b07a93d36c0301a43ed4e707a5663fd5e950f8a
ms.lasthandoff: 02/22/2017

---
# <a name="debugger-contexts"></a>Contextos de depurador
Em [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] de depuração, o mecanismo de depuração (DE) opera simultaneamente em vários contextos diferentes, da seguinte maneira:  
  
-   O contexto de código, que descreve o local atual no fluxo de execução do programa.  
  
-   O contexto de documentação ou posição, que descreve a posição atual em um documento de origem.  
  
-   O contexto de avaliação de expressão, que descreve o contexto no qual expressão avaliação ocorrerá.  
  
## <a name="in-this-section"></a>Nesta seção  
 [Contexto de código](../../extensibility/debugger/code-context.md)  
 Discute o contexto de código como um endereço no fluxo de instruções do programa em arquiteturas de tempo de execução de hoje versus idiomas não tradicionais, onde código não pode ser representado por instruções, mas outros meios.  
  
 [Posição do documento](../../extensibility/debugger/document-position.md)  
 Define a posição do documento na depuração por meio de uma abstração de uma posição em um arquivo de origem conhecida para o IDE do Visual Studio.  
  
 [Contexto de documento](../../extensibility/debugger/document-context.md)  
 Discute representa o contexto de documento no Visual Studio de depuração em relação a um arquivo de origem. Também discute como o manipulador de símbolo mapeia um contexto de código ao contexto da documentação.  
  
 [Contexto de avaliação de expressão](../../extensibility/debugger/expression-evaluation-context.md)  
 Fornece informações sobre um contexto de avaliação de expressão no Visual Studio. Por exemplo, um contexto de avaliação de expressão associado a um quadro de pilha fornece o contexto para avaliar as variáveis locais, parâmetros de método e membros de classe.  
  
## <a name="related-sections"></a>Seções relacionadas  
 [Conceitos de depuração](../../extensibility/debugger/debugger-concepts.md)  
 Descreve os principais conceitos de arquiteturas de depuração.  
  
 [Componentes de depuração](../../extensibility/debugger/debugger-components.md)  
 Fornece uma visão geral sobre os componentes de depuração do Visual Studio, que incluem o mecanismo de depuração (DE), o avaliador de expressão (EE) e o manipulador de símbolo (SH).  
  
 [Tarefas de depuração](../../extensibility/debugger/debugging-tasks.md)  
 Contém links para várias tarefas de depuração, como iniciar um programa e avaliar expressões.
