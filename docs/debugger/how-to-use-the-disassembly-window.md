---
title: "Como usar a janela Desmontagem | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.disassembly"
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
  - "linguagem de assembly, depurando código de assembly embutido"
  - "pontos de interrupção, janela de Desmontagem"
  - "janela de Desmontagem"
  - "código de máquina"
ms.assetid: eaf84dd0-c82d-481b-af51-690b74e7794c
caps.latest.revision: 29
caps.handback.revision: 29
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Como usar a janela Desmontagem
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Esse recurso estará disponível apenas se a depuração do nível de endereços estiver habilitada na caixa de diálogo **Opções**, nó **Depuração**.  Não está disponível para depuração de Script ou SQL.  
  
 A janela **Desmontagem** mostra o código assembly correspondente às instruções criadas pelo compilador.  Se você estiver depurando código gerenciado, essas instruções de assembly correspondem ao código nativo criado pelo compilador JIT \(Just\-in\-Time\), não a linguagem intermediária da Microsoft \(MSIL\) gerada pelo compilador do Visual Studio.  
  
 Além das instruções de assembly, a janela **Desmontagem** pode mostrar as seguintes informações opcionais:  
  
-   Endereço de memória onde cada instrução está localizada.  Para aplicativos nativos, este é o endereço de memória real.  Para o Visual Basic, C\# ou código gerenciado, é um deslocamento do início da função.  
  
-   O código\-fonte do qual o código do assembly deriva.  
  
-   As representações byte a byte de código do computador real ou instruções de MSIL.  
  
-   Nomes do símbolo para os endereços de memória.  
  
-   Números de linha que correspondem ao código\-fonte.  
  
 As instruções da linguagem de assembly consistem em mnemônica, que são abreviações para nomes de instrução e símbolos que representam variáveis, registros e constantes.  Cada instrução de linguagem de máquina é representada por um mnemônico de assembly da linguagem, geralmente seguido por uma ou mais variáveis, registros ou constantes.  
  
 Se você não puder ler a linguagem assembly e quiser aproveitar a janela Desmontagem, consulte um bom livro sobre programação da linguagem de assembly.  A programação da linguagem de assembly está além do escopo do que podemos abordar nesta breve introdução à janela Desmontagem.  
  
 Como o código do assembly depende intensamente dos registros do processador ou, no caso do código gerenciado, os registros do Common Language Runtime, você normalmente achará útil usar a janela Desmontagem junto com a janela Registros, o que permite examinar o conteúdo do registro.  
  
 Você provavelmente jamais desejará ou precisará exibir instruções de código de máquina em seu formato bruto e numérico, em vez da linguagem de assembly.  No entanto, se quiser fazer isso, poderá usar a janela Memória para essa finalidade ou escolher Bytes de Código no menu de atalho na janela Desmontagem.  
  
> [!NOTE]
>  As caixas de diálogo e os comandos de menu que você vê podem ser diferentes dos descritos na Ajuda, dependendo da sua edição ou das configurações ativas.  Para alterar as configurações, escolha **Importar e Exportar Configurações** no menu **Ferramentas**.  Para obter mais informações, consulte [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/pt-br/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### Para exibir a janela Desmontagem  
  
-   No menu **Depurar**, escolha **Janelas** e clique em **Desmontagem**.  
  
     O depurador deve estar em execução ou no modo de interrupção.  
  
### Para ativar ou desativar as informações opcionais  
  
-   Clique com o botão direito na janela **Desmontagem** e defina ou desmarque as opções desejadas no menu de atalho.  
  
     Uma seta amarela na margem esquerda marca o local do ponto de execução atual.  Para o código nativo, isso corresponde ao contador do programa da CPU.  Este local mostra a próxima instrução que será executada em seu programa.  
  
     Para obter mais informações, consulte [Paginação para cima ou para baixo na memória](../debugger/how-to-page-up-or-down-in-memory.md).  
  
## Consulte também  
 [Exibindo dados no depurador](../debugger/viewing-data-in-the-debugger.md)   
 [Como usar a janela Registros](../debugger/how-to-use-the-registers-window.md)