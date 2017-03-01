---
title: "Common Language Runtime e a avaliação da expressão | Documentos do Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- debugging [Debugging SDK], expression evaluation
- expression evaluation, and common language runtime
ms.assetid: b36c1eb5-1aaf-48a6-b287-ee7a273d2b1c
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
ms.openlocfilehash: 06f8ed46afbf71b190e3384b321a84c67c2478d4
ms.lasthandoff: 02/22/2017

---
# <a name="common-language-runtime-and-expression-evaluation"></a>Common Language Runtime e avaliação de expressão
> [!IMPORTANT]
>  No Visual Studio 2015, essa forma de implementar os avaliadores de expressão foi preterida. Para obter informações sobre como implementar os avaliadores de expressão do CLR, consulte [avaliadores de expressão de CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) e [amostra do avaliador de expressão gerenciado](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Compiladores, como Visual Basic e c# (pronuncia-se C-sharp), voltados para o tempo de execução do CLR (Common Language), produzem MSIL Microsoft Intermediate Language (), que mais tarde é compilado para código nativo. O CLR fornece um mecanismo de depuração (DE) para depurar o código resultante. Se você pretende integrar sua linguagem de programação proprietária no IDE do Visual Studio, você pode optar por compilar para MSIL e, portanto, não precisa escrever seu próprio DE. No entanto, você precisará escrever um avaliador de expressão (EE) que é capaz de avaliar expressões dentro do contexto de sua linguagem de programação.  
  
## <a name="discussion"></a>Discussão  
 Expressões de linguagem de computador geralmente são analisadas para produzir um conjunto de objetos de dados e um conjunto de operadores usados para manipulá-los. Por exemplo, a expressão "A + B" pode ser analisada para aplicar o operador de adição (+) para os dados de objetos "A" e "B", possivelmente, resultando em outro objeto de dados. O conjunto total de objetos de dados, operadores e suas associações geralmente são representados em um programa como uma árvore, com os operadores em nós da árvore e os objetos de dados nas ramificações. Uma expressão que é dividida em forma de árvore geralmente é chamada de árvore analisada.  
  
 Depois que uma expressão foi analisada, um provedor de símbolo (SP) é chamado para avaliar cada objeto de dados. Por exemplo, se "A" é definida em mais de um método e, em seguida, a pergunta "Qual A?" deve ser atendida antes que o valor de um pode ser determinado. A resposta retornada pelo SP é algo como "O terceiro item na estrutura de pilhas quinta" ou "A 50 bytes além do início da memória estática alocada para esse método."  
  
 Além de produzir MSIL para o próprio programa, os compiladores do CLR também podem produzir as informações de depuração muito descritivas que são gravadas em um arquivo de banco de dados do programa (. PDB). Desde que um compilador de linguagem proprietário gera informações de depuração no mesmo formato que os compiladores do CLR, SP do CLR é capaz de identificar da linguagem chamado objetos de dados. Depois que um objeto de dados chamado tiver sido identificado, o EE usa um objeto de fichário para associar (ou ligar-se) o objeto de dados para a área de memória que contém o valor do objeto. O DE, em seguida, pode obter ou definir um novo valor para o objeto de dados.  
  
 Um compilador proprietário pode fornecer informações de depuração chamando de CLR de `ISymbolWriter` interface (que é definida no .NET Framework no namespace `System.Diagnostics.SymbolStore`). Compilação para MSIL e gravando informações de depuração através dessas interfaces, um compilador proprietário pode usar os campos DE CLR e SP. Isso simplifica bastante integrar uma linguagem proprietária de IDE do Visual Studio.  
  
 Quando o CLR DE chama o EE proprietário para avaliar uma expressão, o DE fornece EE com interfaces um SP e um objeto de fichário. Assim, escrever um meio de mecanismo de depuração com base em CLR é necessário apenas implementar as interfaces do avaliador de expressão apropriada; o CLR se encarrega de associação e o símbolo de tratamento para você.  
  
## <a name="see-also"></a>Consulte também  
 [Escrevendo um avaliador de expressão de CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)
