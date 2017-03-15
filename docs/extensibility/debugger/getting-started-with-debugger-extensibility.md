---
title: "Introdução à extensibilidade do depurador | Documentos do Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- getting started, Debugging SDK
- debugging [Debugging SDK], getting started
- Debugging SDK, getting started
ms.assetid: d6ce6f43-1409-4bf7-93cd-f3464ca23504
caps.latest.revision: 17
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
ms.openlocfilehash: 258fcfcc97d0a6b1455ec60201527cde3e87f9b8
ms.lasthandoff: 02/22/2017

---
# <a name="getting-started-with-debugger-extensibility"></a>Introdução à extensibilidade do depurador
O [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] fornece as informações necessárias para criar e personalizar componentes do depurador usados para depurar programas de dentro do [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ambiente.  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]depuração adicionou melhorias derivadas a usabilidade ampla teste realizado na anterior [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] depuradores. Você pode usar [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] depuração passar por um aplicativo de vários idioma, ou você pode implementar em interrupções de edição de variáveis durante a depuração de aplicativos e soluções de vários idiomas.  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]depuração é executada fora do processo com o programa que está sendo depurado e, portanto, é menos intrusiva no espaço de processo do aplicativo. Consequentemente, é mais fácil escrever componentes que interagem com o depurador sem afetar seu programa de depuração.  
  
 Usar melhor o [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)], você deve estar familiarizado com o seguinte:  
  
-   O [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ambiente de desenvolvimento integrado (IDE)  
  
-   A linguagem de programação do C++  
  
-   COM ATL  
  
## <a name="in-this-section"></a>Nesta seção  
 [Roteiro para estender o depurador](../../extensibility/debugger/roadmap-for-extending-the-debugger.md)  
 Descreve o processo de implementação de depuração em seu produto, dependendo do seu compilador e sua saída.  
  
 [Componentes do depurador](../../extensibility/debugger/debugger-components.md)  
 Fornece uma visão geral de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] depuração componentes, que incluem o mecanismo de depuração (DE), o avaliador de expressão (EE) e o manipulador de símbolo (SH).  
  
 [Conceitos do depurador](../../extensibility/debugger/debugger-concepts.md)  
 Descreve os principais conceitos de arquiteturas de depuração.  
  
 [Contextos de depurador](../../extensibility/debugger/debugger-contexts.md)  
 Explica como o mecanismo de depuração (DE) opera simultaneamente no código, documentação e contextos de avaliação de expressão. Descreve, para cada um dos três contextos, o local, posição ou avaliação relevante para ele.  
  
 [Tarefas de depuração](../../extensibility/debugger/debugging-tasks.md)  
 Contém links para várias tarefas de depuração, como iniciar um programa e avaliar expressões.
