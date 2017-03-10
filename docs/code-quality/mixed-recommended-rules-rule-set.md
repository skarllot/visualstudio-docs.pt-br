---
title: "Conjunto de regras recomendadas misto | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c3186b5b-0149-4a75-826e-e3539e4e703f
caps.latest.revision: 3
caps.handback.revision: 3
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Conjunto de regras recomendadas misto
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Microsoft misturado as regras para o mouse em na maioria dos problemas comuns e críticas em seus C\+\+ projeto que dão suporte a Common Language Runtime, incluindo buracos na segurança em potencial, o aplicativo falhará, e outros erros importantes de lógica e de design.  Você deve incluir esta regra definida em qualquer regra personalizada e cria C\+\+ para seus projetos que dão suporte a Common Language Runtime.  Este ruleset é criado para ser configurado com a edição do Visual Studio Professional ou superior.  
  
|Regra|Descrição|  
|-----------|---------------|  
|[C6001](../code-quality/c6001.md)|Usando a memória não inicializada|  
|[C6011](../code-quality/c6011.md)|Desreferenciando o ponteiro nulo|  
|[C6029](../code-quality/c6029.md)|Uso do valor desmarcado|  
|[C6031](../code-quality/c6031.md)|Valor de retorno ignorado|  
|[C6053](../code-quality/c6053.md)|Terminação nula de chamada|  
|[C6054](../code-quality/c6054.md)|Ausentes zero de término|  
|[C6059](../code-quality/c6059.md)|Concatenação incorreto|  
|[C6063](../code-quality/c6063.md)|Argumento ausente de cadeia de caracteres para formatar a função|  
|[C6064](../code-quality/c6064.md)|Argumento ausente de inteiro para formatar a função|  
|[C6066](../code-quality/c6066.md)|Argumento ausente do ponteiro para formatar a função|  
|[C6067](../code-quality/c6067.md)|Argumento ausente do ponteiro de cadeia de caracteres para formatar a função|  
|[C6101](../code-quality/c6101.md)|Retornando a memória não inicializada|  
|[C6200](../code-quality/c6200.md)|O índice exceder o máximo de buffer|  
|[C6201](../code-quality/c6201.md)|O índice exceder o máximo do buffer de pilha|  
|[C6214](../code-quality/c6214.md)|Conversão inválido HRESULT a BOOL|  
|[C6215](../code-quality/c6215.md)|Conversão inválido BOOL a HRESULT|  
|[C6216](../code-quality/c6216.md)|Conversão completo inserida inválido BOOL a HRESULT|  
|[C6217](../code-quality/c6217.md)|Teste inválido de HRESULT com NOT|  
|[C6220](../code-quality/c6220.md)|HRESULT inválidos comparam a \-1|  
|[C6226](../code-quality/c6226.md)|Atribuição inválido de HRESULT a \-1|  
|[C6230](../code-quality/c6230.md)|Uso inválido de HRESULT como booliano|  
|[C6235](../code-quality/c6235.md)|Constante diferente de zero com ou realização|  
|[C6236](../code-quality/c6236.md)|Realização ou com constante diferente de zero|  
|[C6237](../code-quality/c6237.md)|Realização de zero com e perder efeitos colaterais|  
|[C6242](../code-quality/c6242.md)|O local desenrola forçado|  
|[C6248](../code-quality/c6248.md)|Criando uma DACL nulo|  
|[C6250](../code-quality/c6250.md)|Descritores de endereço não\-editados|  
|[C6255](../code-quality/c6255.md)|Uso de Alloca desprotegido|  
|[C6258](../code-quality/c6258.md)|Usar encerra o thread|  
|[C6259](../code-quality/c6259.md)|Código inoperante em Bit a bit ou alternar limitado|  
|[C6260](../code-quality/c6260.md)|Uso de aritmética de byte|  
|[C6262](../code-quality/c6262.md)|Uso excessivo da pilha|  
|[C6263](../code-quality/c6263.md)|Usando Alloca no loop|  
|[C6268](../code-quality/c6268.md)|Parênteses ausentes em conversão|  
|[C6269](../code-quality/c6269.md)|O ponteiro cancelará ignorado|  
|[C6270](../code-quality/c6270.md)|Argumento ausente flutuante para formatar a função|  
|[C6271](../code-quality/c6271.md)|Argumento adicional para formatar a função|  
|[C6272](../code-quality/c6272.md)|Argumento de não float para formatar a função|  
|[C6273](../code-quality/c6273.md)|Não inteiro Argumen para formatar a função|  
|[C6274](../code-quality/c6274.md)|Argumento de não caracteres para formatar a função|  
|[C6276](../code-quality/c6276.md)|Conversão de cadeia de caracteres inválido|  
|[C6277](../code-quality/c6277.md)|Chame inválido de CreateProcess|  
|[C6278](../code-quality/c6278.md)|Matriz\- novo incompatibilidade de escalar DELETE|  
|[C6279](../code-quality/c6279.md)|Escalar novo incompatibilidade de Matriz\- DELETE|  
|[C6280](../code-quality/c6280.md)|Incompatibilidade de Alocação\- desalocação de memória|  
|[C6281](../code-quality/c6281.md)|Precedência de bit a bit da relação|  
|[C6282](../code-quality/c6282.md)|A atribuição substitui o teste|  
|[C6283](../code-quality/c6283.md)|Matriz\- novo incompatibilidade primitiva de escalar DELETE|  
|[C6284](../code-quality/c6284.md)|Argumento inválido de objeto para a função format|  
|[C6285](../code-quality/c6285.md)|Realização ou de constantes|  
|[C6286](../code-quality/c6286.md)|Efeitos colaterais diferentes de zero ou perder realização|  
|[C6287](../code-quality/c6287.md)|Teste redundante|  
|[C6288](../code-quality/c6288.md)|A inclusão mútua sobre for falsa e realização|  
|[C6289](../code-quality/c6289.md)|A exclusão mútua sobre for verdadeira ou realização|  
|[C6290](../code-quality/c6290.md)|\- Não lógico Bit a bit e precedência|  
|[C6291](../code-quality/c6291.md)|\- Não lógico Bit a bit ou precedência|  
|[C6292](../code-quality/c6292.md)|O loop conta acima do máximo|  
|[C6293](../code-quality/c6293.md)|O loop conta para baixo do mínimo|  
|[C6294](../code-quality/c6294.md)|O corpo de loop nunca executado|  
|[C6295](../code-quality/c6295.md)|Loop infinito|  
|[C6296](../code-quality/c6296.md)|Loop executado apenas uma vez|  
|[C6297](../code-quality/c6297.md)|Resultado da conversão do turno para o maior tamanho|  
|[C6299](../code-quality/c6299.md)|Bitfield a comparação booliana|  
|[C6302](../code-quality/c6302.md)|Argumento inválido de cadeia de caracteres para formatar a função|  
|[C6303](../code-quality/c6303.md)|Todo o argumento inválido de cadeia de caracteres para formatar a função|  
|[C6305](../code-quality/c6305.md)|Use incompatível de tamanho e de contagem|  
|[C6306](../code-quality/c6306.md)|Chamada de função incorreta argumento de variável|  
|[C6308](../code-quality/c6308.md)|Escape de Realloc|  
|[C6310](../code-quality/c6310.md)|Constante ilegal de filtro de exceção|  
|[C6312](../code-quality/c6312.md)|A exceção continua o loop de execução|  
|[C6314](../code-quality/c6314.md)|Bit a bit ou precedência|  
|[C6317](../code-quality/c6317.md)|Não complemento|  
|[C6318](../code-quality/c6318.md)|A exceção continua Pesquisa|  
|[C6319](../code-quality/c6319.md)|Ignorado por vírgula|  
|[C6324](../code-quality/c6324.md)|A cópia da cadeia de caracteres em vez de cadeia de caracteres compara|  
|[C6328](../code-quality/c6328.md)|Tipos incompatíveis potenciais de argumento|  
|[C6331](../code-quality/c6331.md)|Sinalizadores de VirtualFree inválidos|  
|[C6332](../code-quality/c6332.md)|Parâmetro inválido de VirtualFree|  
|[C6333](../code-quality/c6333.md)|Tamanho de VirtualFree inválido|  
|[C6335](../code-quality/c6335.md)|Identificador de escape do processo|  
|[C6381](../code-quality/c6381.md)|Ausentes de informações de desligamento|  
|[C6383](../code-quality/c6383.md)|Excesso de buffer de Byte\- contagem de elementos contagem|  
|[C6384](../code-quality/c6384.md)|Divisão do tamanho do ponteiro|  
|[C6385](../code-quality/c6385.md)|Excesso de leitura|  
|[C6386](../code-quality/c6386.md)|Excesso de gravação|  
|[C6387](../code-quality/c6387.md)|Valor de parâmetro inválido|  
|[C6388](../code-quality/c6388.md)|Valor de parâmetro inválido|  
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
|[C6995](../code-quality/c6995.md)|Falha ao salvar o arquivo de log de XML|  
|[C26100](../code-quality/c26100.md)|Condição de corrida|  
|[C26101](../code-quality/c26101.md)|Falha ao usar corretamente a operação bloqueada|  
|[C26110](../code-quality/c26110.md)|O chamador não mantém o bloqueio|  
|[C26111](../code-quality/c26111.md)|O chamador não liberar o bloqueio|  
|[C26112](../code-quality/c26112.md)|O chamador não pode conter nenhum bloqueio|  
|[C26115](../code-quality/c26115.md)|Falha ao liberar o bloqueio|  
|[C26116](../code-quality/c26116.md)|Falha ao adquirir ou mantendo o bloqueio|  
|[C26117](../code-quality/c26117.md)|Liberando o bloqueio de unheld|  
|[C26140](../code-quality/c26140.md)|Erro de anotação de SAL de simultaneidade|  
|[C28020](../code-quality/c28020.md)|A expressão não for verdadeira nessa chamada|  
|[C28021](../code-quality/c28021.md)|O parâmetro que está sendo anotado deve ser um ponteiro|  
|[C28022](../code-quality/c28022.md)|As classes da função nessa função não correspondem a classe da função no typedef usado para defini\-lo.|  
|[C28023](../code-quality/c28023.md)|A função que está sendo atribuído ou transmitidas deve ter uma anotação no mínimo uma de \_Function\_class\_ da classe|  
|[C28024](../code-quality/c28024.md)|O ponteiro de função que está sendo atribuído a for anotado com a classe da função, que não está presente na lista de classe da função.|  
|[C28039](../code-quality/c28039.md)|O tipo de parâmetro real deve corresponder exatamente ao tipo|  
|[C28112](../code-quality/c28112.md)|Uma variável que é acessado através de uma função bloqueada sempre deve ser acessado através de uma função bloqueada.|  
|[C28113](../code-quality/c28113.md)|Acessando uma variável local por uma função bloqueada|  
|[C28125](../code-quality/c28125.md)|A função deve ser chamada de uma exceto o bloco try\/catch|  
|[C28137](../code-quality/c28137.md)|O argumento de variável deve ser em vez de literal constante \(\)|  
|[C28138](../code-quality/c28138.md)|O argumento deve ser constante em vez de variável|  
|[C28159](../code-quality/c28159.md)|Considere usar outra função em seu lugar.|  
|[C28160](../code-quality/c28160.md)|Anotação de erro|  
|[C28163](../code-quality/c28163.md)|A função nunca deve ser chamado de dentro de uma exceto o bloco try\/catch|  
|[C28164](../code-quality/c28164.md)|O argumento está sendo passado a uma função que espera um ponteiro para um objeto \(não um ponteiro para um ponteiro\)|  
|[C28182](../code-quality/c28182.md)|Desreferenciando o ponteiro NULL.  O ponteiro contém o mesmo valor NULO que outro ponteiro fez.|  
|[C28183](../code-quality/c28183.md)|O argumento pode ser um valor, e é uma cópia do valor localizado no ponteiro|  
|[C28193](../code-quality/c28193.md)|A variável contém um valor que deve ser verificado|  
|[C28196](../code-quality/c28196.md)|O requisito não estiver satisfeito. \(A expressão não é avaliada como true.\)|  
|[C28202](../code-quality/c28202.md)|Referência ilegal do membro não estático|  
|[C28203](../code-quality/c28203.md)|Referência ambígua ao membro da classe.|  
|[C28205](../code-quality/c28205.md)|\_Success\_ ou \_On\_failure\_ usado em um contexto ilegal|  
|[C28206](../code-quality/c28206.md)|Pontos à esquerda do operando a uma estrutura, use “\-\>”|  
|[C28207](../code-quality/c28207.md)|O operando esquerdo é uma estrutura, use “.”|  
|[C28209](../code-quality/c28209.md)|A declaração do símbolo tem uma declaração conflitante|  
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
|[C28244](../code-quality/c28244.md)|A anotação para a função tem um parâmetro unparseable\/anotação externo|  
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
|[C28306](../code-quality/c28306.md)|A anotação no parâmetro é obsoleto|  
|[C28307](../code-quality/c28307.md)|A anotação no parâmetro é obsoleto|  
|[C28350](../code-quality/c28350.md)|A anotação descreve uma situação que não é condicional aplicável.|  
|[C28351](../code-quality/c28351.md)|A anotação descreve onde um valor dinâmico uma variável \(\) não pode ser usado na condição.|  
|[CA1001](../Topic/CA1001:%20Types%20that%20own%20disposable%20fields%20should%20be%20disposable.md)|Tipos que possui campos descartáveis deve ser descartável|  
|[CA1009](../code-quality/ca1009-declare-event-handlers-correctly.md)|Declare manipuladores de eventos corretamente|  
|[CA1016](../code-quality/ca1016-mark-assemblies-with-assemblyversionattribute.md)|Marcar os assemblies com AssemblyVersionAttribute|  
|[CA1033](../Topic/CA1033:%20Interface%20methods%20should%20be%20callable%20by%20child%20types.md)|Os métodos da interface devem estar acessíveis por tipos de filho|  
|[CA1049](../code-quality/ca1049-types-that-own-native-resources-should-be-disposable.md)|Tipos que possui recursos nativos deve ser descartável|  
|[CA1060](../code-quality/ca1060-move-p-invokes-to-nativemethods-class.md)|Mover P\/Invokes à classe de NativeMethods|  
|[CA1061](../code-quality/ca1061-do-not-hide-base-class-methods.md)|Não ocultar métodos da classe base|  
|[CA1063](../code-quality/ca1063-implement-idisposable-correctly.md)|Implemente corretamente IDisposable|  
|[CA1065](../code-quality/ca1065-do-not-raise-exceptions-in-unexpected-locations.md)|Não digite as exceções em locais inesperados|  
|[CA1301](../Topic/CA1301:%20Avoid%20duplicate%20accelerators.md)|Evite aceleradores duplicados|  
|[CA1400](../Topic/CA1400:%20P-Invoke%20entry%20points%20should%20exist.md)|Os pontos de entrada de P\/Invoke devem existir|  
|[CA1401](../Topic/CA1401:%20P-Invokes%20should%20not%20be%20visible.md)|P\/Invokes não deve ser visível|  
|[CA1403](../code-quality/ca1403-auto-layout-types-should-not-be-com-visible.md)|Os tipos de layout automático não deve ser visível COM|  
|[CA1404](../code-quality/ca1404-call-getlasterror-immediately-after-p-invoke.md)|Chame GetLastError imediatamente depois de P\/Invoke|  
|[CA1405](../code-quality/ca1405-com-visible-type-base-types-should-be-com-visible.md)|Os tipos de base visíveis de tipo COM o devem ser visível COM|  
|[CA1410](../code-quality/ca1410-com-registration-methods-should-be-matched.md)|Os métodos de registro COM o devem ser correspondidos|  
|[CA1415](../code-quality/ca1415-declare-p-invokes-correctly.md)|Declare P\/Invokes corretamente|  
|[CA1821](../code-quality/ca1821-remove-empty-finalizers.md)|Remova os finalizers vazias|  
|[CA1900](../code-quality/ca1900-value-type-fields-should-be-portable.md)|Os campos do tipo de valor devem ser portáteis|  
|[CA1901](../code-quality/ca1901-p-invoke-declarations-should-be-portable.md)|As declarações de P\/Invoke devem ser portáteis|  
|[CA2002](../Topic/CA2002:%20Do%20not%20lock%20on%20objects%20with%20weak%20identity.md)|Não bloqueie em objetos de identidade fraco|  
|[CA2100](../code-quality/ca2100-review-sql-queries-for-security-vulnerabilities.md)|Revise consultas SQL para vulnerabilidades de segurança|  
|[CA2101](../code-quality/ca2101-specify-marshaling-for-p-invoke-string-arguments.md)|Especifique que o marshaling para argumentos de cadeia de caracteres de P\/Invoke|  
|[CA2108](../code-quality/ca2108-review-declarative-security-on-value-types.md)|Segurança declarativa revisão em tipos de valor|  
|[CA2111](../code-quality/ca2111-pointers-should-not-be-visible.md)|Os ponteiros não devem ser visíveis|  
|[CA2112](../code-quality/ca2112-secured-types-should-not-expose-fields.md)|Os tipos não seguros deve expor campos|  
|[CA2114](../code-quality/ca2114-method-security-should-be-a-superset-of-type.md)|A segurança do método deve ser um superconjunto do tipo|  
|[CA2116](../Topic/CA2116:%20APTCA%20methods%20should%20only%20call%20APTCA%20methods.md)|Os métodos de APTCA só devem chamar métodos de APTCA|  
|[CA2117](../code-quality/ca2117-aptca-types-should-only-extend-aptca-base-types.md)|Os tipos de APTCA só devem estender tipos de base de APTCA|  
|[CA2122](../code-quality/ca2122-do-not-indirectly-expose-methods-with-link-demands.md)|Não expõe métodos indiretamente com as demandas de link|  
|[CA2123](../code-quality/ca2123-override-link-demands-should-be-identical-to-base.md)|As demandas do link de substituição devem ser idênticas com base|  
|[CA2124](../code-quality/ca2124-wrap-vulnerable-finally-clauses-in-outer-try.md)|Cláusulas vulneráveis de quebra automática finalmente tente externa|  
|[CA2126](../Topic/CA2126:%20Type%20link%20demands%20require%20inheritance%20demands.md)|As demandas do link do tipo exigem demandas de herança|  
|[CA2131](../code-quality/ca2131-security-critical-types-may-not-participate-in-type-equivalence.md)|Os tipos críticos de segurança não podem participar da equivalência do tipo|  
|[CA2132](../code-quality/ca2132-default-constructors-must-be-at-least-as-critical-as-base-type-default-constructors.md)|Os construtores padrão devem ser pelo menos críticos quanto construtores padrão do tipo de base|  
|[CA2133](../code-quality/ca2133-delegates-must-bind-to-methods-with-consistent-transparency.md)|O delega devem associar a transparência consistente com métodos|  
|[CA2134](../code-quality/ca2134-methods-must-keep-consistent-transparency-when-overriding-base-methods.md)|Os métodos devem manter a transparência consistente ao substituir métodos de base|  
|[CA2137](../Topic/CA2137:%20Transparent%20methods%20must%20contain%20only%20verifiable%20IL.md)|Os métodos transparentes devem conter apenas o IL verificável|  
|[CA2138](../code-quality/ca2138-transparent-methods-must-not-call-methods-with-the-suppressunmanagedcodesecurity-attribute.md)|Os métodos transparentes não devem chamar métodos com o atributo de SuppressUnmanagedCodeSecurity|  
|[CA2140](../code-quality/ca2140-transparent-code-must-not-reference-security-critical-items.md)|O código transparente não deve referenciar itens críticos de segurança|  
|[CA2141](../code-quality/ca2141-transparent-methods-must-not-satisfy-linkdemands.md)|Os métodos transparentes não devem satisfazer LinkDemands|  
|[CA2146](../code-quality/ca2146-types-must-be-at-least-as-critical-as-their-base-types-and-interfaces.md)|Os tipos devem ser pelo menos críticos quanto os tipos de base e interfaces|  
|[CA2147](../code-quality/ca2147-transparent-methods-may-not-use-security-asserts.md)|Os métodos transparentes não podem usar segurança afirmam|  
|[CA2149](../code-quality/ca2149-transparent-methods-must-not-call-into-native-code.md)|Os métodos transparentes não devem chamar em código nativo|  
|[CA2200](../code-quality/ca2200-rethrow-to-preserve-stack-details.md)|Lançar novamente para preservar detalhes da pilha|  
|[CA2202](../code-quality/ca2202-do-not-dispose-objects-multiple-times.md)|Não remove objetos várias vezes|  
|[CA2207](../code-quality/ca2207-initialize-value-type-static-fields-inline.md)|Inicializar os campos estáticos de tipo de valor de tabela embutida|  
|[CA2212](../code-quality/ca2212-do-not-mark-serviced-components-with-webmethod.md)|Não marque componentes atendidos com WebMethod|  
|[CA2213](../code-quality/ca2213-disposable-fields-should-be-disposed.md)|Os campos descartáveis devem ser removidos|  
|[CA2214](../Topic/CA2214:%20Do%20not%20call%20overridable%20methods%20in%20constructors.md)|Não chame métodos overridable nos construtores|  
|[CA2216](../code-quality/ca2216-disposable-types-should-declare-finalizer.md)|Os tipos descartáveis devem declarar o finalizador|  
|[CA2220](../code-quality/ca2220-finalizers-should-call-base-class-finalizer.md)|Finalizers deve chamar o finalizador da classe base|  
|[CA2229](../code-quality/ca2229-implement-serialization-constructors.md)|Construtores de serialização de ferramentas|  
|[CA2231](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)|Operador de igual de sobrecarga em substituir ValueType.Equals|  
|[CA2232](../code-quality/ca2232-mark-windows-forms-entry-points-with-stathread.md)|Pontos de entrada do Windows Forms de marca a STAThread|  
|[CA2235](../code-quality/ca2235-mark-all-non-serializable-fields.md)|Marcar todos os campos não serializáveis|  
|[CA2236](../code-quality/ca2236-call-base-class-methods-on-iserializable-types.md)|Chamar métodos da classe base em tipos de ISerializable|  
|[CA2237](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)|Marcar tipos de ISerializable com SerializableAttribute|  
|[CA2238](../code-quality/ca2238-implement-serialization-methods-correctly.md)|Implementar os métodos de serialização corretamente|  
|[CA2240](../Topic/CA2240:%20Implement%20ISerializable%20correctly.md)|Implementar ISerializable corretamente|  
|[CA2241](../code-quality/ca2241-provide-correct-arguments-to-formatting-methods.md)|Forneça argumentos corretos para formatação métodos|  
|[CA2242](../code-quality/ca2242-test-for-nan-correctly.md)|Teste para NaN corretamente|