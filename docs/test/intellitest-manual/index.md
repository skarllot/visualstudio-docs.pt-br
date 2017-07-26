---
title: "Manual de referência de IntelliTest | Ferramentas de teste do Microsoft Developer | Microsoft Docs"
ms.custom: 
ms.date: 05/02/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- IntelliTest Reference Manual, IntelliTest
ms.assetid: C5FA1C59-BB82-43B6-BF96-D0D85E033DAE
caps.latest.revision: 56
ms.author: douge
manager: douge
translation.priority.ht:
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
ms.translationtype: Human Translation
ms.sourcegitcommit: 45d36934cf1c46902cac566203cddf4a118b7fe4
ms.openlocfilehash: 1f37379b77701a969cc6667abc0778dbbb95202f
ms.contentlocale: pt-br
ms.lasthandoff: 06/02/2017

---
# <a name="intellitest-reference-manual"></a>Manual de referência do IntelliTest

## <a name="contents"></a>Conteúdo

* **[Visão geral do IntelliTest](introduction.md)**
  - [O Olá, Mundo do IntelliTest](introduction.md#hello-world)
  - [Limitações](introduction.md#limitations)
    * [Não determinismo](introduction.md#nondeterminism)
    * [Simultaneidade](introduction.md#concurrency)
    * [Código nativo](introduction.md#native-code)
    * [Plataforma](introduction.md#platform)
    * [Linguagem](introduction.md#language)
    * [Raciocínio simbólico](introduction.md#symbolic-reasoning)
    * [Rastreamentos de pilha incorretos](introduction.md#incorrect-stack)
  - [Leitura adicional](introduction.md#further-reading)<p>&nbsp;</p>

* **[Introdução ao IntelliTest](getting-started.md)**
  - [Atributos importantes](getting-started.md#important-attributes)
  - [Classes auxiliares estáticas importantes](getting-started.md#helper-classes)<p>&nbsp;</p>
 
* **[Geração de teste](test-generation.md)**
  - [Geradores de teste](test-generation.md#test-generators)
  - [Teste de unidade parametrizado](test-generation.md#parameterized-unit-testing)
  - [Teste de unidade parametrizado genérico](test-generation.md#generic-parameterized)
  - [Permissão de exceções](test-generation.md#allowing-exceptions)
  - [Teste de tipos internos](test-generation.md#internal-types)
  - [Suposições e declarações](test-generation.md#assumptions-and-assertions)
  - [Pré-condição](test-generation.md#precondition)
  - [Pós-condição](test-generation.md#postcondition)
  - [Falhas de teste](test-generation.md#test-failures)
  - [Configuração e desmontagem](test-generation.md#setup-teardown)
  - [Leitura adicional](test-generation.md#further-reading)<p>&nbsp;</p>

* **[Geração de entrada](input-generation.md)**
  - [Solver de restrição](input-generation.md#constraint-solver)
  - [Cobertura de código dinâmico](input-generation.md#dynamic-code-coverage)
  - [Números inteiros e flutuações](input-generation.md#integers-and-floats)
  - [Objetos](input-generation.md#objects)
  - [Instanciação de classes existentes](input-generation.md#existing-classes)
  - [Visibilidade](input-generation.md#visibility)
  - [Simulações parametrizadas](input-generation.md#parameterized-mocks)
  - [Estruturas](input-generation.md#structs)
  - [Matrizes e cadeias de caracteres](input-generation.md#arrays-and-strings)
  - [Obtenção de entradas adicionais](input-generation.md#additional-inputs)
  - [Leitura adicional](input-generation.md#further-reading)<p>&nbsp;</p>

* **[Limites de exploração](exploration-bounds.md)**
  - [MaxConstraintSolverTime](exploration-bounds.md#maxconstraintsolvertime)
  - [MaxConstraintSolverMemory](exploration-bounds.md#maxconstraintsolvermemory)
  - [MaxBranches](exploration-bounds.md#maxbranches)
  - [MaxCalls](exploration-bounds.md#maxcalls)
  - [MaxStack](exploration-bounds.md#maxstack)
  - [MaxConditions](exploration-bounds.md#maxconditions)
  - [MaxRuns](exploration-bounds.md#maxruns)
  - [MaxRunsWithoutNewTests](exploration-bounds.md#maxrunswithoutnewtests)
  - [MaxRunsWithUniquePaths](exploration-bounds.md#maxrunswithuniquepaths)
  - [MaxExceptions](exploration-bounds.md#maxexceptions)
  - [TestExcludePathBoundsExceeded](exploration-bounds.md#testexcludepathboundsexceeded)
  - [TestEmissionFilter](exploration-bounds.md#testemissionfilter)
  - [TestEmissionBranchHits](exploration-bounds.md#testemissionbranchhits)<p>&nbsp;</p>

* **[Glossário do atributo](attribute-glossary.md)**
  - [PexAssumeNotNull](attribute-glossary.md#pexassumenotnull)
  - [PexClass](attribute-glossary.md#pexclass)
  - [PexGenericArguments](attribute-glossary.md#pexgenericarguments)
  - [PexMethod](attribute-glossary.md#pexmethod)
  - [PexExplorationAttributeBase](attribute-glossary.md#pexexplorationattributebase)
  - [PexAssemblySettings](attribute-glossary.md#pexassemblysettings)
  - [PexAssemblyUnderTest](attribute-glossary.md#pexassemblyundertest)
  - [PexInstrumentAssemblyAttribute](attribute-glossary.md#pexinstrumentassemblyattribute)
  - [PexUseType](attribute-glossary.md#pexusetype)
  - [PexAllowedException](attribute-glossary.md#pexallowedexception)
  - [PexAllowedExceptionFromAssembly](attribute-glossary.md#pexallowedexceptionfromassembly)
  - [PexAllowedExceptionFromType](attribute-glossary.md#pexallowedexceptionfromtype)
  - [PexAllowedExceptionFromTypeUnderTest](attribute-glossary.md#pexallowedexceptionfromtypeundertest)<p>&nbsp;</p>

* **[Cascata de configurações](settings-waterfall.md)**

* **[Classes auxiliares estáticas](static-helper-classes.md)**
  - [PexAssume](static-helper-classes.md#pexassume)
  - [PexAssert](static-helper-classes.md#pexassert)
  - [PexChoose](static-helper-classes.md#pexchoose)
  - [PexObserve](static-helper-classes.md#pexobserve)
  - [PexSymbolicValue](static-helper-classes.md#pexsymbolicvalue)<p>&nbsp;</p>

* **[Avisos e erros](warnings-and-errors.md)**
  - [MaxBranches excedido](warnings-and-errors.md#maxbranches-exceeded)
  - [MaxConstraintSolverTime excedido](warnings-and-errors.md#maxconstraintsolvertime-exceeded)
  - [MaxConditions excedido](warnings-and-errors.md#maxconditions-exceeded)
  - [MaxCalls excedido](warnings-and-errors.md#maxcalls-exceeded)
  - [MaxStack excedido](warnings-and-errors.md#maxstack-exceeded)
  - [MaxRuns excedido](warnings-and-errors.md#maxruns-exceeded)
  - [MaxRunsWithoutNewTests excedido](warnings-and-errors.md#maxrunswithoutnewtests-exceeded)
  - [Não é possível concretizar a solução](warnings-and-errors.md#cannot-concretize-solution)
  - [Precisa de ajuda para o objeto do constructo](warnings-and-errors.md#help-construct)
  - [Precisa de ajuda para encontrar tipos](warnings-and-errors.md#help-types)
  - [Tipo utilizável estimado](warnings-and-errors.md#usable-type-guessed)
  - [Falha inesperada durante a exploração](warnings-and-errors.md#unexpected-exploration)
  - [TargetInvocationException](warnings-and-errors.md#targetinvocationexception)
  - [Método não instrumentado chamado](warnings-and-errors.md#uninstrumented-method-called)
  - [Método externo chamado](warnings-and-errors.md#external-method-called)
  - [Método não instrumentável chamado](warnings-and-errors.md#uninstrumentable-method-called)
  - [Problema de capacidade de teste](warnings-and-errors.md#testability-issue)
  - [Limitação](warnings-and-errors.md#limitation)
  - [Incompatibilidade de chamada observada](warnings-and-errors.md#observed-call-mismatch)
  - [Valor armazenado no campo estático](warnings-and-errors.md#value-static-field)<p>&nbsp;</p>

## <a name="got-feedback"></a>Recebeu comentários?

Poste suas ideias e solicitações de recursos no  **[UserVoice](https://visualstudio.uservoice.com/forums/121579-visual-studio-2015/category/157869-test-tools?query=IntelliTest)**.

