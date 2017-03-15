---
title: Roteiro para estender o depurador | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- debugging [Debugging SDK], roadmap
- Debugging SDK, roadmap
ms.assetid: 1f4096a8-f7aa-4dfa-84e1-6d59263e70bb
caps.latest.revision: 16
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
ms.openlocfilehash: 49df627aa42cd6cc6ac1430e4e68694fa51a2fc1
ms.lasthandoff: 02/22/2017

---
# <a name="roadmap-for-extending-the-debugger"></a>Roteiro para estender o depurador
Esta documentação fornece informações de referência e guia para estender o [!INCLUDE[vs_current_short](../../code-quality/includes/vs_current_short_md.md)] do depurador com o [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)].  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]depuração de documentação inclui exemplos, uma referência abrangente e vários cenários representantes que demonstram as maneiras comuns de personalizar o depurador.  
  
 O compilador e sua saída determinam o que você precisa fazer para implementar a depuração em seu produto. Se o compilador:  
  
-   Tem como alvo o sistema operacional nativo do Windows e grava um. Arquivo PDB, você pode depurar programas com o mecanismo de depuração de código nativo (DE), que é integrado ao [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Você não precisa implementar um avaliador de expressão ou DE. O avaliador de expressão foi escrito para a sintaxe da linguagem de programação C++.  
  
-   Produz Microsoft intermediate language (MSIL) de saída, você pode depurar programas com o mecanismo de depuração de código gerenciado DE, que também está integrado a [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Portanto, você só precisa implementar um avaliador de expressão. Um avaliador de expressão de exemplo é fornecido para você. Para mais informações, consulte os seguintes tópicos:  
  
     [Avaliação de expressão](../../extensibility/debugger/expression-evaluation-visual-studio-debugging-sdk.md)  
  
     [Avaliando expressões](../../extensibility/debugger/evaluating-expressions.md)  
  
     [Contexto de avaliação de expressão](../../extensibility/debugger/expression-evaluation-context.md)  
  
     [Avaliação da expressão no modo de interrupção](../../extensibility/debugger/expression-evaluation-in-break-mode.md)  
  
     [Escrevendo um avaliador de expressão de tempo de execução linguagem comum](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)  
  
-   Destinos de um sistema operacional ou algum outro ambiente de tempo de execução do proprietário, você precisa escrever seu próprio DE. Um tutorial que cria um simples DE usar COM da ATL é fornecido. Para mais informações, consulte os seguintes tópicos:  
  
     [Criando um mecanismo de depuração personalizado](../../extensibility/debugger/creating-a-custom-debug-engine.md)  
  
     [Tutorial: Criando um mecanismo de depuração usando COM ATL](http://msdn.microsoft.com/en-us/9097b71e-1fe7-48f7-bc00-009e25940c24)  
  
     [Implementando um fornecedor de porta](../../extensibility/debugger/implementing-a-port-supplier.md)  
  
     [Exemplos](../../extensibility/debugger/visual-studio-debugging-samples.md)  
  
## <a name="see-also"></a>Consulte também  
 [Introdução](../../extensibility/debugger/getting-started-with-debugger-extensibility.md)
