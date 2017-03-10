---
title: "Anotando o comportamento de bloqueio | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "_Releases_nonreentrant_lock_"
  - "_Lock_kind_mutex_"
  - "_Lock_kind_critical_section_"
  - "_Acquires_lock_"
  - "_Releases_lock_"
  - "_Has_lock_kind_"
  - "_Releases_exclusive_lock_"
  - "_Post_same_lock_"
  - "_Requires_exclusive_lock_held_"
  - "_Requires_shared_lock_held_"
  - "_Lock_kind_semaphore_"
  - "_Requires_lock_held_"
  - "_Acquires_exclusive_lock_"
  - "_Create_lock_level_"
  - "_Acquires_nonreentrant_lock_"
  - "_Releases_shared_lock_"
  - "_Has_lock_level_"
  - "_Lock_kind_spin_lock_"
  - "_Requires_lock_not_held_"
  - "_Acquires_shared_lock_"
  - "_Requires_no_locks_held_"
  - "_Lock_level_order_"
  - "_Lock_kind_event_"
ms.assetid: 07769c25-9b97-4ab7-b175-d1c450308d7a
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Anotando o comportamento de bloqueio
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Para evitar bug de simultaneidade em seu programa multi\-threaded, sempre siga uma disciplina apropriado de bloqueio e usar anotações de SAL.  
  
 Os bug de simultaneidade são difíceis de notòria reproduzir, diagnosticar, e depurar porque não são determinísticas.  Raciocinar sobre a intercalação de thread é difícil o melhor forma, e se torna impraticável quando você estiver criando um corpo de código que tem mais do que alguns threads.  Consequentemente, é uma prática recomendada e uma disciplina de bloqueio em seus programas multi\-threaded.  Por exemplo, obedecendo um bloqueio ordenar ao adquirir vários bloqueios que ajuda a evitar deadlocks, e a aquisição do bloqueio apropriado de guarda antes de acessar ajuda compartilhadas de um recurso evitar situações de competição.  
  
 Infelizmente, as regras aparentemente simples de bloqueio podem ser surpreendentemente duras de e na prática.  Uma limitação fundamental nas linguagens de programação de hoje e em compiladores é que eles não suportam diretamente a especificação e análise de requisitos de simultaneidade.  Os programadores precisam confiar em comentários informais de código para expressar suas intenções sobre como usam bloqueios.  
  
 As anotações de SAL de simultaneidade são criadas para ajudá\-lo a especificar efeitos colaterais de bloqueio, responsabilidade de bloqueio, tutela de dados, a hierarquia de pedido de bloqueio, e outro comportamento de bloqueio esperado.  Fazendo regras implícitas explícitas, as anotações de simultaneidade de SAL fornecem uma maneira consistente para que você documente como o código usa regras de bloqueio.  As anotações de simultaneidade também aprimoram a capacidade de ferramentas de análise de código de localizar situações de competição, deadlock, operações incompatíveis de sincronização, e outros erros suteis de simultaneidade.  
  
## Diretrizes gerais  
 Usando anotações, você poderá indicar os contratos que são implícitos por definições de funções entre implementações callees \(\) e clientes chamadores \(\), e express invariants e outras propriedades de programa que pode mais melhorar a análise.  
  
 O SAL oferece suporte a diversos tipos de bloqueio primitivo\- por exemplo, seções críticas, mutexes, bloqueios de rotação, entre outros objetos do recurso.  Muitas anotações de simultaneidade têm uma expressão de bloqueio como um parâmetro.  Por convenção, um bloqueio é denotado pela expressão de caminho do objeto de bloqueio subjacente.  
  
 Alguns thread regras de propriedade para serem considerados:  
  
-   Os bloqueios de rotação são os bloqueios uncounted com propriedade leve do thread.  
  
-   Mutexes e seções críticos os bloqueios são contados com propriedade leve do thread.  
  
-   Semáforos e os eventos são contados os bloqueios que não têm a propriedade leve do thread.  
  
## Anotações de Bloqueio  
 A tabela a seguir lista as anotações de bloqueio.  
  
|Anotação|Descrição|  
|--------------|---------------|  
|`_Acquires_exclusive_lock_(expr)`|Anota uma função e indica que o estado da postagem os incrementos de função por um a contagem exclusiva de bloqueio do objeto de bloqueio que é nomeada por `expr`.|  
|`_Acquires_lock_(expr)`|Anota uma função e indica que o estado da postagem os incrementos de função por um a contagem de bloqueio do objeto de bloqueio que é nomeada por `expr`.|  
|`_Acquires_nonreentrant_lock_(expr)`|O bloqueio que é nomeada por `expr` é adquirido.  Um erro é informado se o bloqueio for mantido nele.|  
|`_Acquires_shared_lock_(expr)`|Anota uma função e indica que o estado da postagem os incrementos de função por um a contagem compartilhada de bloqueio do objeto de bloqueio que é nomeada por `expr`.|  
|`_Create_lock_level_(name)`|Uma instrução que declara o símbolo `name` para ser um nível de bloqueio de forma que pode ser usado nas anotações `_Has_Lock_level_` e `_Lock_level_order_`.|  
|`_Has_lock_kind_(kind)`|Anota qualquer objeto para refinar a informação de tipo de um objeto de recurso.  Às vezes, um tipo comum é usado para tipos diferentes de recursos e o tipo sobrecarregado não é suficiente para distinguir os requisitos de semântica entre vários recursos.  Eis uma lista de parâmetros predefinidos de `kind` :<br /><br /> `_Lock_kind_mutex_`<br /> Identificação do tipo de bloqueio para mutexes.<br /><br /> `_Lock_kind_event_`<br /> Identificação do tipo de bloqueio para eventos.<br /><br /> `_Lock_kind_semaphore_`<br /> Identificação do tipo de bloqueio para semáforos.<br /><br /> `_Lock_kind_spin_lock_`<br /> Identificação do tipo de bloqueio para bloqueios de rotação.<br /><br /> `_Lock_kind_critical_section_`<br /> Identificação do tipo de bloqueio para seções críticas.|  
|`_Has_lock_level_(name)`|Anota um objeto de bloqueio e permite bloqueio em nível de `name`.|  
|`_Lock_level_order_(name1, name2)`|Uma declaração que dá a ordenação de bloqueio entre `name1` e `name2`.|  
|`_Post_same_lock_(expr1, expr2)`|Anota uma função e indica que o estado da postagem os dois bloqueios, `expr1` e `expr2`, será tratado como se forem o mesmo objeto de bloqueio.|  
|`_Releases_exclusive_lock_(expr)`|Anota uma função e indica que o estado da postagem reduz a função por uma contagem exclusiva de bloqueio do objeto de bloqueio que é nomeada por `expr`.|  
|`_Releases_lock_(expr)`|Anota uma função e indica que o estado da postagem do diminuirá a contagem por uma função de bloqueio do objeto de bloqueio que é nomeada por `expr`.|  
|`_Releases_nonreentrant_lock_(expr)`|O bloqueio que é nomeada por `expr` é liberado.  Um erro é informado se o bloqueio não é mantido no momento.|  
|`_Releases_shared_lock_(expr)`|Anota uma função e indica que o estado da postagem reduz a função por uma contagem compartilhada de bloqueio do objeto de bloqueio que é nomeada por `expr`.|  
|`_Requires_lock_held_(expr)`|Anota uma função e indica\-a que indica pre em que a contagem de bloqueio do objeto que é nomeada por `expr` é pelo menos um.|  
|`_Requires_lock_not_held_(expr)`|Anota uma função e indica\-a que indica pre em que a contagem de bloqueio do objeto que é nomeada por `expr` são zero.|  
|`_Requires_no_locks_held_`|Anota uma função e indica que as contagens de bloqueio de todos os bloqueios que são conhecidos ao verificador são zero.|  
|`_Requires_shared_lock_held_(expr)`|Anota uma função e indica\-a que indica pre em que a conta compartilhada de bloqueio do objeto que é nomeada por `expr` é pelo menos um.|  
|`_Requires_exclusive_lock_held_(expr)`|Anota uma função e indica\-a que indica pre em que a contagem exclusiva de bloqueio do objeto que é nomeada por `expr` é pelo menos um.|  
  
## Intrinsics de SAL para objetos não expostos de bloqueio  
 Certos objetos de bloqueio não são expostos pela implementação das funções de bloqueio associadas.  A tabela a seguir lista as variáveis intrínsecos de SAL que habilitam anotações em funções que operam nesses objetos não expostos de bloqueio.  
  
|Anotação|Descrição|  
|--------------|---------------|  
|`_Global_cancel_spin_lock_`|Descreve o bloqueio de rotação de cancelamento.|  
|`_Global_critical_region_`|Descreve a região crítico.|  
|`_Global_interlock_`|Descreve bloqueado operações.|  
|`_Global_priority_region_`|Descreve a região de prioridade.|  
  
## Anotações de Acesso a Dados Compartilhados  
 A tabela a seguir lista as anotações para o acesso a dados compartilhado.  
  
|Anotação|Descrição|  
|--------------|---------------|  
|`_Guarded_by_(expr)`|Anota uma variável e indica que sempre que a variável é acessado, a contagem de bloqueio do objeto de bloqueio que é nomeada por `expr` é pelo menos um.|  
|`_Interlocked_`|Anota uma variável e é equivalente a `_Guarded_by_(_Global_interlock_)`.|  
|`_Interlocked_operand_`|O parâmetro de função anotado é o operando de destino de uma das várias funções interconectadas.  Esses operandos devem ter propriedades adicionais específicas.|  
|`_Write_guarded_by_(expr)`|Anota uma variável e indica que sempre que a variável é alterado, a contagem de bloqueio do objeto de bloqueio que é nomeada por `expr` é pelo menos um.|  
  
## Consulte também  
 [Usando anotações de SAL para reduzir defeitos de código do C\/C\+\+](../code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects.md)   
 [Noções básicas de SAL](../code-quality/understanding-sal.md)   
 [Anotando parâmetros de função e valores de retorno](../code-quality/annotating-function-parameters-and-return-values.md)   
 [Anotando o comportamento da função](../code-quality/annotating-function-behavior.md)   
 [Anotando estruturas e classes](../code-quality/annotating-structs-and-classes.md)   
 [Especificando quando e onde uma anotação se aplica](../code-quality/specifying-when-and-where-an-annotation-applies.md)   
 [Funções intrínsecas](../code-quality/intrinsic-functions.md)   
 [Práticas recomendadas e exemplos](../code-quality/best-practices-and-examples-sal.md)   
 [Blog da equipe de análise de código](http://go.microsoft.com/fwlink/p/?LinkId=251197)