---
title: "No&#231;&#245;es b&#225;sicas sobre depura&#231;&#227;o: janela Registros | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "JScript"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "depurando [Visual Studio], Janela Registros"
  - "Janela Registros, sobre janela Registros"
ms.assetid: ab354047-053e-4f94-8ac1-26e761442b6f
caps.latest.revision: 22
caps.handback.revision: 22
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# No&#231;&#245;es b&#225;sicas sobre depura&#231;&#227;o: janela Registros
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

A janela **Registros** estará disponível apenas se a depuração do nível de endereços estiver habilitada na caixa de diálogo **Opções**, nó **Depuração**.  
  
 Os registros são locais especiais dentro de um processador \(CPU\) que são usados para armazenar partes pequenas de dados em que o processador está trabalhando ativamente.  Compilar ou interpretar o código\-fonte gera instruções que movem dados da memória para os registros e de volta, conforme o necessário.  Acessar dados em registros é muito rápido comparado a acessar dados na memória. Sendo assim, o código que permite que o processador mantenha dados em um registro e os acesse repetidamente tende a ser executado mais rápido do que o código que requer que o processador carregue e descarregue registros constantemente.  Para que o compilador possa manter os dados nos registros e executar outras otimizações, evite usar variáveis globais e confie em variáveis locais o máximo possível.  O código escrito dessa maneira tem boa a localidade de referência.  Em algumas linguagens, por exemplo, C\/C\+\+, o desenvolvedor pode declarar uma variável do registro, que diz ao compilador para tentar o melhor possível para manter a variável em um registro constantemente.  Para obter mais informações, consulte [Registrar Palavra\-Chave](http://msdn.microsoft.com/pt-br/5b66905a-2f7f-4918-bb55-5e66d4bc50f9)  
  
 Os registros podem ser divididos em dois tipos: uso geral e finalidade especial.  Os registros de uso geral mantêm dados para operações gerais, por exemplo, adicionar dois números ou referenciar um elemento em uma matriz.  Os registros de finalidade especial têm finalidades específicas e significado especializado.  Um bom exemplo é o registro do ponteiro de pilha, que o processador usa para manter controle da pilha de chamadas do programa.  Como programador, você provavelmente não manipulará o ponteiro de pilhas diretamente.  No entanto, é essencial para o funcionamento correto do programa porque, sem o ponteiro de pilha, o processador não saberia para onde retornar ao término de uma chamada de função.  
  
 A maioria de registros de uso geral contém apenas um elemento de dados.  Por exemplo, um único inteiro, número de ponto flutuante ou elemento de uma matriz.  Alguns processadores mais novos têm registros maiores, chamados de registros de vetor, que podem manter uma matriz de dados pequena.  Como eles contêm tantos dados, os registros de vetor permitem que as operações que envolvem as matrizes sejam executadas muito rapidamente.  Os registros de vetor foram usados primeiro em supercomputadores caros de alto desempenho, mas agora estão se tornando disponíveis em microprocessadores onde estão acostumados a grande vantagem em operações gráficas intensivas.  
  
 Um processador normalmente tem dois conjuntos de registros de uso geral, um otimizado para operações de ponto flutuante e o outro para operações de inteiros.  Não é surpresa eles serem chamados de registros de pontos flutuante e inteiros.  
  
 O código gerenciado é compilado em tempo de execução para o código nativo que acessa os registros físicos do microprocessador.  A janela **Registros** exibe físicos esses registros físicos para Common Language Runtime ou código nativo.  A janela **Registros** não exibe informações de registro para o script ou aplicativo SQL, porque o script e SQL são linguagens que não dão suporte ao conceito de registros.  
  
 Para obter mais informações sobre como exibir a janela **Registros**, consulte [Usando a janela de registros](../debugger/how-to-use-the-registers-window.md).  
  
 Quando você examina a janela **Registros**, verá entradas como este exemplo:  
  
```  
EAX = 003110D8  
```  
  
 O símbolo à esquerda do sinal \= é o nome do registro, EAX, nesse caso.  O número à direita do sinal \= representa o conteúdo do registro.  
  
 A janela **Registros** permite fazer mais do que apenas exibir o conteúdo de um registro.  Quando você está no modo de interrupção em código nativo, pode clicar no conteúdo de um registro e editar o valor.  Isso não é algo que você deve fazer aleatoriamente.  A menos que você compreenda o registro que está editando, e os dados que ele contém, o resultado de uma edição descuidada provavelmente será uma falha de programa ou alguma outra consequência indesejada.  Infelizmente, uma explicação detalhada dos conjuntos de registro dos vários processadores Intel e compatíveis com Intel vai além do escopo dessa breve introdução.  
  
## Registrar grupos  
 Para reduzir a confusão, a janela **Registros** organiza os registros em grupos.  Se você clicar com o botão direito na janela **Registros**, verá um menu de atalho contendo uma lista de grupos, que você pode exibir ou ocultar como achar melhor.  
  
## Consulte também  
 [Como usar a janela Registros](../debugger/how-to-use-the-registers-window.md)   
 [Noções básicas do depurador](../debugger/debugger-basics.md)