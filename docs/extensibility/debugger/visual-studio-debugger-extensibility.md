---
title: Extensibilidade do depurador do Visual Studio | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- debugging [Visual Studio], Debugging SDK
- Debugging SDK
ms.assetid: c088b6a2-c3ad-446b-830d-9c6f41b2934b
caps.latest.revision: 32
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
ms.openlocfilehash: b7baa5ac92cafd2bcb8b106c4bb0168932be262c
ms.lasthandoff: 02/22/2017

---
# <a name="visual-studio-debugger-extensibility"></a>Extensibilidade do depurador do Visual Studio
O Visual Studio inclui um depurador de código fonte totalmente interativas, fornecendo uma ferramenta poderosa e fácil de usar para rastrear bugs em seu programa. O depurador tem suporte completo para Visual Basic, c#, C/C++ e JavaScript. No entanto, com o [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)], que está disponível na [Microsoft Download Center](http://go.microsoft.com/fwlink/?LinkId=214453), outras linguagens de programação podem ter suporte no depurador com os mesmos recursos avançados.  
  
 O [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] depurador é comum front-end (ou seja, a interface do usuário) para os componentes de depuração são, por sua vez, específico do idioma que está sendo depurado. Novos idiomas, tudo o que é necessário para oferecer suporte o [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] depurador é criar os componentes de back-end necessários, como um mecanismo de depuração (DE). É aí que o [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] chega.  
  
 O [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] inclui uma referência completa a todos os [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] elementos necessários para criar um novo DE. Além disso, há exemplos e tutoriais que ajudarão a começar.  
  
 Para um exemplo de ponta a ponta de um sistema de projeto de linguagem com suporte à depuração, consulte o [IronPython exemplo](http://msdn.microsoft.com/en-us/4c41695c-12c1-4670-b43b-d8d84c9e4089).  
  
 As seções a seguir descrevem como estender o depurador usando o [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)].  
  
## <a name="in-this-section"></a>Nesta seção  
 [Introdução](../../extensibility/debugger/getting-started-with-debugger-extensibility.md)  
 Descreve o que [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] depuração ofertas e como instalar o SDK.  
  
 [Criando um mecanismo de depuração personalizado](../../extensibility/debugger/creating-a-custom-debug-engine.md)  
 Documenta o processo DE personalizado, de preparação de seu programa para a da desanexação DE.  
  
 [Escrevendo um avaliador de expressão de CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)  
 Explica se você deve escrever um avaliador de expressão.  
  
 [Escolhendo uma estratégia de implementação do mecanismo de depuração](../../extensibility/debugger/choosing-a-debug-engine-implementation-strategy.md)  
 Discute como implementar seu DE.  
  
 [Referência](../../extensibility/debugger/reference/reference-visual-studio-debugging-apis.md)  
 Documentos de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] API de depuração.  
  
 [Exemplos](../../extensibility/debugger/visual-studio-debugging-samples.md)  
 Contém links para uma amostra do avaliador de expressão comuns language runtime e um exemplo de mecanismo de depuração.
