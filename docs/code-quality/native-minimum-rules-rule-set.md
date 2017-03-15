---
title: "Conjunto de regras m&#237;nimas nativo | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 2d898bc4-fba5-472e-8f09-b0c6b511c5a3
caps.latest.revision: 3
caps.handback.revision: 3
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Conjunto de regras m&#237;nimas nativo
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

As regras mínimas nativos do Microsoft referem\-se aos problemas mais importantes em seu código nativo, incluindo buracos na segurança em potencial e o aplicativo falhará.  Você deve incluir esta regra definida em qualquer regra personalizada e cria para seus projetos nativos.  
  
|Regra|Descrição|  
|-----------|---------------|  
|[C6001](../code-quality/c6001.md)|Usando a memória não inicializada|  
|[C6011](../code-quality/c6011.md)|Desreferenciando o ponteiro nulo|  
|[C6029](../code-quality/c6029.md)|Uso do valor desmarcado|  
|[C6053](../code-quality/c6053.md)|Terminação nula de chamada|  
|[C6059](../code-quality/c6059.md)|Concatenação incorreto|  
|[C6063](../code-quality/c6063.md)|Argumento ausente de cadeia de caracteres para formatar a função|  
|[C6064](../code-quality/c6064.md)|Argumento ausente de inteiro para formatar a função|  
|[C6066](../code-quality/c6066.md)|Argumento ausente do ponteiro para formatar a função|  
|[C6067](../code-quality/c6067.md)|Argumento ausente do ponteiro de cadeia de caracteres para formatar a função|  
|[C6101](../code-quality/c6101.md)|Retornando a memória não inicializada|  
|[C6200](../code-quality/c6200.md)|O índice exceder o máximo de buffer|  
|[C6201](../code-quality/c6201.md)|O índice exceder o máximo do buffer de pilha|  
|[C6270](../code-quality/c6270.md)|Argumento ausente flutuante para formatar a função|  
|[C6271](../code-quality/c6271.md)|Argumento adicional para formatar a função|  
|[C6272](../code-quality/c6272.md)|Argumento de não float para formatar a função|  
|[C6273](../code-quality/c6273.md)|Não inteiro Argumen para formatar a função|  
|[C6274](../code-quality/c6274.md)|Argumento de não caracteres para formatar a função|  
|[C6276](../code-quality/c6276.md)|Conversão de cadeia de caracteres inválido|  
|[C6277](../code-quality/c6277.md)|Chame inválido de CreateProcess|  
|[C6284](../code-quality/c6284.md)|Argumento inválido de objeto para a função format|  
|[C6290](../code-quality/c6290.md)|\- Não lógico Bit a bit e precedência|  
|[C6291](../code-quality/c6291.md)|\- Não lógico Bit a bit ou precedência|  
|[C6302](../code-quality/c6302.md)|Argumento inválido de cadeia de caracteres para formatar a função|  
|[C6303](../code-quality/c6303.md)|Todo o argumento inválido de cadeia de caracteres para formatar a função|  
|[C6305](../code-quality/c6305.md)|Use incompatível de tamanho e de contagem|  
|[C6306](../code-quality/c6306.md)|Chamada de função incorreta argumento de variável|  
|[C6328](../code-quality/c6328.md)|Tipos incompatíveis potenciais de argumento|  
|[C6385](../code-quality/c6385.md)|Excesso de leitura|  
|[C6386](../code-quality/c6386.md)|Excesso de gravação|  
|[C6387](../code-quality/c6387.md)|Valor de parâmetro inválido|  
|[C6500](../code-quality/c6500.md)|Propriedade inválido de atributo|  
|[C6501](../code-quality/c6501.md)|Conflitante valores de propriedade do atributo|  
|[C6503](../code-quality/c6503.md)|As referências não podem ser nulas|  
|[C6504](../code-quality/c6504.md)|Zero não no ponteiro|  
|[C6505](../code-quality/c6505.md)|MustCheck em void|  
|[C6506](../code-quality/c6506.md)|Tamanho do buffer não no ponteiro ou matriz|  
|[C6507](http://msdn.microsoft.com/pt-br/18f88cd1-d035-4403-a6a4-12dd0affcf21)|A incompatibilidade nula em cancelará zero|  
|[C6508](../code-quality/c6508.md)|Acesso de gravação na constante|  
|[C6509](../code-quality/c6509.md)|Retorno usado em pré\-requisito|  
|[C6510](../code-quality/c6510.md)|Zero não terminado no ponteiro|  
|[C6511](../code-quality/c6511.md)|MustCheck deve ser Sim ou não|  
|[C6513](../code-quality/c6513.md)|Tamanho do elemento sem tamanho do buffer|  
|[C6514](../code-quality/c6514.md)|O tamanho do buffer excede o tamanho da matriz|  
|[C6515](../code-quality/c6515.md)|Tamanho do buffer não no ponteiro|  
|[C6516](../code-quality/c6516.md)|Nenhuma propriedade no atributo|  
|[C6517](../code-quality/c6517.md)|Tamanho válido no buffer ilegível|  
|[C6518](../code-quality/c6518.md)|Tamanho gravável no buffer não gravável|  
|[C6519](http://msdn.microsoft.com/pt-br/2b6326b0-0539-4d26-8fb1-720114933232)|Anotação inválido: o valor da propriedade “NeedsRelease” Sim ou não deve ser|  
|[C6521](http://msdn.microsoft.com/pt-br/e98d0ae3-6f13-47b2-9a15-15d4055af9ef)|A cadeia de caracteres inválido de tamanho cancelará|  
|[C6522](../code-quality/c6522.md)|Tipo inválido de cadeia de caracteres de tamanho|  
|[C6523](http://msdn.microsoft.com/pt-br/11397a31-b224-46b0-afb7-d49ca576a3bb)|Parâmetro inválido de cadeia de caracteres de tamanho|  
|[C6525](../code-quality/c6525.md)|Local acessível de cadeia de caracteres inválido de tamanho|  
|[C6526](http://msdn.microsoft.com/pt-br/59c590c7-0098-4166-a1ac-87f324596002)|Tipo de buffer inválido de cadeia de caracteres de tamanho|  
|[C6527](../code-quality/c6527.md)|Anotação inválido: A propriedade “NeedsRelease” não pode ser usada em valores de tipo void|  
|[C6530](../code-quality/c6530.md)|Estilo não reconhecido da cadeia de caracteres de formato|  
|[C6540](../code-quality/c6540.md)|O uso de anotações de atributo nesta função invalidará todas as anotações existentes de \_\_declspec|  
|[C6551](../code-quality/c6551.md)|Especificação inválida de tamanho: expressão não parsable|  
|[C6552](../code-quality/c6552.md)|Deref\= inválido ou Notref\=: expressão não parsable|  
|[C6701](../code-quality/c6701.md)|O valor não é um válido e sim\/não avalia talvez|  
|[C6702](../code-quality/c6702.md)|O valor não é um valor de cadeia de caracteres|  
|[C6703](../code-quality/c6703.md)|O valor não é um número\)|  
|[C6704](../code-quality/c6704.md)|Erro inesperado de expressão de anotação|  
|[C6705](../code-quality/c6705.md)|O número esperado de argumentos da anotação não corresponde ao número real de casos da anotação|  
|[C6706](../code-quality/c6706.md)|Erro inesperado de anotação de anotação|  
|[C28021](../code-quality/c28021.md)|O parâmetro que está sendo anotado deve ser um ponteiro|  
|[C28182](../code-quality/c28182.md)|Desreferenciando o ponteiro NULL.  O ponteiro contém o mesmo valor NULO que outro ponteiro fez.|  
|[C28202](../code-quality/c28202.md)|Referência ilegal do membro não estático|  
|[C28203](../code-quality/c28203.md)|Referência ambígua ao membro da classe.|  
|[C28205](../code-quality/c28205.md)|\_Success\_ ou \_On\_failure\_ usado em um contexto ilegal|  
|[C28206](../code-quality/c28206.md)|Pontos à esquerda do operando a uma estrutura, use “\-\>”|  
|[C28207](../code-quality/c28207.md)|O operando esquerdo é uma estrutura, use “.”|  
|[C28210](../code-quality/c28210.md)|As anotações para o contexto de \_\_on\_failure não devem estar pre no contexto explícita|  
|[C28211](../code-quality/c28211.md)|Nome do contexto estático esperado para SAL\_context|  
|[C28212](../code-quality/c28212.md)|Expressão do ponteiro esperada de anotação|  
|[C28213](../code-quality/c28213.md)|A anotação de \_Use\_decl\_annotations\_ deve ser usada para fazer referência, sem alteração, instrução anterior.|  
|[C28214](../code-quality/c28214.md)|Os nomes de parâmetro de atributo devem ser p1 p9…|  
|[C28215](../code-quality/c28215.md)|O typefix não pode ser aplicado a um parâmetro que já tenha um typefix|  
|[C28216](../code-quality/c28216.md)|A anotação de checkReturn se aplica apenas aos postconditions para o parâmetro da função específica.|  
|[C28217](../code-quality/c28217.md)|Para a função, o número de parâmetros para a anotação não corresponde ao localizado no arquivo|  
|[C28218](../code-quality/c28218.md)|Para o paramteer de função, o parâmetro da anotação não corresponde ao localizado no arquivo|  
|[C28219](../code-quality/c28219.md)|O membro de enumeração esperado para a anotação o parâmetro na anotação|  
|[C28220](../code-quality/c28220.md)|A expressão de inteiro esperado para a anotação o parâmetro na anotação|  
|[C28221](../code-quality/c28221.md)|Expressão de cadeia de caracteres esperada para o parâmetro na anotação|  
|[C28222](../code-quality/c28222.md)|\_\_yes, \_\_no, ou \_\_maybe esperado para a anotação|  
|[C28223](../code-quality/c28223.md)|Não encontrou o token\/identificador esperados da anotação, parâmetro|  
|[C28224](../code-quality/c28224.md)|A anotação requer parâmetros|  
|[C28225](../code-quality/c28225.md)|Não encontrou o número correto de parâmetros requeridos na anotação|  
|[C28226](../code-quality/c28226.md)|A anotação não pode também ser um PrimOp \(na instrução atual\)|  
|[C28227](../code-quality/c28227.md)|A anotação não pode também ser um PrimOp \(consulte a instrução anterior\)|  
|[C28228](../code-quality/c28228.md)|Parâmetro da anotação: não pode ser usado em anotações|  
|[C28229](../code-quality/c28229.md)|A anotação não da suporte a parâmetros|  
|[C28230](../code-quality/c28230.md)|O tipo de parâmetro não tem nenhum membro.|  
|[C28231](../code-quality/c28231.md)|A anotação é válida apenas na matriz|  
|[C28232](../code-quality/c28232.md)|pre, postagem, ou deref não aplicado a qualquer anotação|  
|[C28233](../code-quality/c28233.md)|pre, postagem, ou deref aplicado a um bloco|  
|[C28234](../code-quality/c28234.md)|a expressão de \_\_at não se aplica à função atual|  
|[C28235](../code-quality/c28235.md)|A função pode não estar bem como uma anotação|  
|[C28236](../code-quality/c28236.md)|A anotação não pode ser usada em uma expressão|  
|[C28237](../code-quality/c28237.md)|A anotação no parâmetro não tem mais suporte|  
|[C28238](../code-quality/c28238.md)|A anotação no parâmetro tem mais de um valor de, o stringValue, e de longValue.  Use paramn\=xxx|  
|[C28239](../code-quality/c28239.md)|A anotação no parâmetro tem ambos, avaliar o stringValue, ou o longValue; e paramn\=xxx.  Use somente paramn\=xxx|  
|[C28240](../code-quality/c28240.md)|A anotação no parâmetro não tiver param2 mas nenhum param1|  
|[C28241](../code-quality/c28241.md)|A anotação para a função no parâmetro não é reconhecida|  
|[C28243](../code-quality/c28243.md)|A anotação para a função no parâmetro requer mais cancelará do tipo real anotado reserva|  
|[C28245](../code-quality/c28245.md)|A anotação para a função “anota essa” em uma função não\-membro\-|  
|[C28246](../code-quality/c28246.md)|A anotação do parâmetro da função não corresponde ao tipo do parâmetro|  
|[C28250](../code-quality/c28250.md)|Anotação inconsistente para a função: a instância anterior tem um erro.|  
|[C28251](../code-quality/c28251.md)|Anotação inconsistente para a função: esta instância tiver um erro.|  
|[C28252](../code-quality/c28252.md)|Anotação inconsistente para a função: o parâmetro tem uma outras anotações nesta instância.|  
|[C28253](../code-quality/c28253.md)|Anotação inconsistente para a função: o parâmetro tem uma outras anotações nesta instância.|  
|[C28254](../code-quality/c28254.md)|o dynamic\_cast\<\>\(\) não têm suporte nas anotações|  
|[C28262](../code-quality/c28262.md)|Um erro de sintaxe na anotação foi encontrado na função, para a anotação|  
|[C28263](../code-quality/c28263.md)|Um erro de sintaxe em uma anotação condicional foi localizado para a anotação intrínseca|  
|[C28264](http://msdn.microsoft.com/pt-br/bf6ea983-a06e-4752-a042-747a7dbf338c)|Os valores das listas de resultados devem ser constantes.|  
|[C28267](../code-quality/c28267.md)|Um erro de sintaxe nas anotações anotação foi encontrada na função.|  
|[C28272](../code-quality/c28272.md)|A anotação para a função, revise parâmetro quando for inconsistente com a declaração de função|  
|[C28273](../code-quality/c28273.md)|Para a função, encontrar pistas forem inconsistentes com a declaração de função|  
|[C28275](../code-quality/c28275.md)|O parâmetro para o \_Macro\_value\_ for nulo|  
|[C28279](../code-quality/c28279.md)|Para iniciar o símbolo “,” foi encontrado “sem uma extremidade correspondente”|  
|[C28280](../code-quality/c28280.md)|Para o símbolo, uma “end” não foi encontrada uma correspondência “iniciado”|  
|[C28282](../code-quality/c28282.md)|As cadeias de formato devem estar nas condições anteriores|  
|[C28285](../code-quality/c28285.md)|Para a função, erro de sintaxe do parâmetro|  
|[C28286](../code-quality/c28286.md)|Para a função, erro de sintaxe na extremidade|  
|[C28287](../code-quality/c28287.md)|Para a função, erro de sintaxe na anotação de \_At\_\(\) \(nome do parâmetro não reconhecido\)|  
|[C28288](../code-quality/c28288.md)|Para a função, erro de sintaxe na anotação de \_At\_\(\) \(nome de parâmetro inválido\)|  
|[C28289](../code-quality/c28289.md)|Para a função: ReadableTo ou WritableTo não tinha as especificações associado como um parâmetro.|  
|[C28290](../code-quality/c28290.md)|a anotação para a função Externals contém mais do que o número real de parâmetros|  
|[C28291](../code-quality/c28291.md)|nulo\/notnull de postagem no nível 0 de deref não tem sentido para a função.|  
|[C28300](../code-quality/c28300.md)|Operandos da expressão de tipo incompatíveis para o operador|  
|[C28301](../code-quality/c28301.md)|Nenhuma anotações para a primeira declaração da função.|  
|[C28302](../code-quality/c28302.md)|Um operador adicional de \_Deref\_ foi encontrado na anotação.|  
|[C28303](../code-quality/c28303.md)|Um operador ambíguo de \_Deref\_ foi encontrado na anotação.|  
|[C28304](../code-quality/c28304.md)|Um operador de forma incorreta colocado de \_Notref\_ foi encontrado aplicado ao token.|  
|[C28305](../code-quality/c28305.md)|Um erro quando analisar um token foi descoberta.|  
|[C28350](../code-quality/c28350.md)|A anotação descreve uma situação que não é condicional aplicável.|  
|[C28351](../code-quality/c28351.md)|A anotação descreve onde um valor dinâmico uma variável \(\) não pode ser usado na condição.|