---
title: "Suporte do serviço de linguagem para depuração | Documentos do Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- debugger, language support
- language services, debugging support
ms.assetid: 7a44067f-a410-4a6a-84d2-bda5184140bc
caps.latest.revision: 15
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
ms.openlocfilehash: 0edae6a36daff365c3c9d01b99206ba73242edc0
ms.lasthandoff: 02/22/2017

---
# <a name="language-service-support-for-debugging"></a>Suporte do serviço de linguagem para depuração
Um serviço de linguagem pode fornecer recursos que oferecem suporte a um depurador a <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageDebugInfo>interface.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageDebugInfo> Esses recursos incluem validação de pontos de interrupção e fornecer uma lista de expressões para o **Autos** janela.  
  
 No entanto, você precisa ter um avaliador de expressão para depurar seu idioma. O avaliador de expressão é responsável por avaliar expressões para gerar valores durante a depuração. Para obter informações sobre como implementar os avaliadores de expressão do CLR, consulte:  
  
-   [Avaliadores de expressão de CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators)  
  
-   [Amostra do avaliador de expressão gerenciado](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)  
  
## <a name="compiler-output"></a>Saída do Compilador  
 O tipo do compilador determina o que você precisa fazer para implementar a depuração para seu idioma. Se o compilador tem como alvo o sistema operacional Windows e grava um arquivo. PDB, você pode depurar programas com o mecanismo que é integrado ao Visual Studio de depuração de código nativo. Se o compilador produz Microsoft intermediate language (MSIL), você pode depurar programas com o código gerenciado, depuração engine, que também é integrado ao Visual Studio. Se o compilador tem como alvo um sistema operacional proprietário ou um ambiente de tempo de execução diferente, você precisa escrever seu próprio mecanismo de depuração.  
  
 Para obter mais informações sobre a implementação de depuração para seu idioma, consulte [Introdução](../../extensibility/debugger/getting-started-with-debugger-extensibility.md) no SDK do Visual Studio de depuração.
