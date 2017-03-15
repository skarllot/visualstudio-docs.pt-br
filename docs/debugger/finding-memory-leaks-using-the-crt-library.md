---
title: "Localizando perdas de mem&#243;ria usando a biblioteca CRT | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
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
  - "C++"
helpviewer_keywords: 
  - "_crtBreakAlloc"
  - "_CRTDBG_MAP_ALLOC"
  - "_CrtDumpMemoryLeaks"
  - "_CrtMemCheckpoint"
  - "_CrtMemDifference"
  - "_CrtMemDumpStatistics"
  - "_CrtMemState"
  - "_CrtSetBreakAlloc"
  - "_CrtSetDbgFlag"
  - "_CrtSetReportMode"
  - "pontos de interrupção, na alocação de memória"
  - "depurando perdas de memória"
  - "perdas de memória"
  - "perdas de memória, detectando e isolando"
  - "memória, depuração"
ms.assetid: cf6dc7a6-cd12-4283-b1b6-ea53915f7ed1
caps.latest.revision: 28
caps.handback.revision: 28
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Localizando perdas de mem&#243;ria usando a biblioteca CRT
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Vazamentos de memória, definidos como a falha em desalocar corretamente a memória anteriormente alocada, estão entre os bugs mais sutis e difíceis de detectar em aplicativos C\/C\+\+. Um pequeno vazamento de memória não pode ser observado em primeiro lugar, mas ao longo do tempo, um vazamento de memória progressivo pode causar os sintomas que variam de desempenho reduzido a falhar quando o aplicativo é executado sem memória. Pior ainda, um aplicativo de escape que usa toda a memória disponível pode causar outro aplicativo falhe, criando a confusão em relação ao que o aplicativo é responsável. Até mesmo aparentemente vazamentos de memória inofensivos podem ser sintomáticos de outros problemas que devem ser corrigidos.  
  
 O [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] depurador e bibliotecas C Runtime \(CRT\) fornecem os meios para detectar e identificar vazamentos de memória.  
  
## Habilitar detecção de vazamento de memória  
 As principais ferramentas para detectar vazamentos de memória são o depurador e as bibliotecas de tempo de execução C \(CRT\) funções de heap de depuração.  
  
 Para habilitar as funções de heap de depuração, inclua as seguintes instruções em seu programa:  
  
```  
#define _CRTDBG_MAP_ALLOC #include <stdlib.h> #include <crtdbg.h>  
```  
  
 Para as funções de CRT funcionem corretamente, o `#include` instruções devem seguir a ordem mostrada aqui.  
  
 Incluindo crtdbg. h mapeia o `malloc` e o [livre](/visual-cpp/c-runtime-library/reference/free) funções às versões de depuração, [malloc\_dbg](/visual-cpp/c-runtime-library/reference/malloc-dbg) e `free`, que acompanham a alocação de memória e desalocação. Esse mapeamento ocorre apenas em compilações de depuração, que têm `_DEBUG`. Compilações lançadas usam as `malloc` e `free` funções.  
  
 O `#define` instrução mapeia uma versão de base das funções de heap de CRT para a versão de depuração correspondente. Se você omitir o `#define` instrução, o despejo de vazamento de memória será menos detalhado.  
  
 Depois que você habilitou as funções de heap de depuração usando estas instruções, você pode colocar uma chamada para `_CrtDumpMemoryLeaks` antes de um ponto de saída do aplicativo para exibir um relatório de vazamento de memória quando seu aplicativo for encerrado:  
  
```  
_CrtDumpMemoryLeaks();  
```  
  
 Se seu aplicativo tiver várias saídas, você não será necessário posicionar manualmente uma chamada para [crtdumpmemoryleaks](/visual-cpp/c-runtime-library/reference/crtdumpmemoryleaks) em cada ponto de saída. Uma chamada para `_CrtSetDbgFlag` no início de seu aplicativo causará uma chamada automática para `_CrtDumpMemoryLeaks` em cada ponto de saída. Você deve definir os dois campos de bits mostrados aqui:  
  
```  
_CrtSetDbgFlag ( _CRTDBG_ALLOC_MEM_DF | _CRTDBG_LEAK_CHECK_DF );  
```  
  
 Por padrão, `_CrtDumpMemoryLeaks` gera o relatório de vazamento de memória para o **Depurar** painel do **saída** janela. Você pode usar `_CrtSetReportMode` para redirecionar o relatório para outro local.  
  
 Se você usar uma biblioteca, a biblioteca poderá redefinir a saída para outro local. Nesse caso, você pode definir o local de saída para o **saída** janela, conforme mostrado aqui:  
  
```  
_CrtSetReportMode( _CRT_ERROR, _CRTDBG_MODE_DEBUG );  
```  
  
## Interpretando o relatório de vazamento de memória  
 Se seu aplicativo não definir `_CRTDBG_MAP_ALLOC`, [crtdumpmemoryleaks](/visual-cpp/c-runtime-library/reference/crtdumpmemoryleaks) exibe um relatório de vazamento de memória que é semelhante ao seguinte:  
  
```  
Detected memory leaks! Dumping objects -> {18} normal block at 0x00780E80, 64 bytes long. Data: <                > CD CD CD CD CD CD CD CD CD CD CD CD CD CD CD CD Object dump complete.  
```  
  
 Se seu aplicativo define `_CRTDBG_MAP_ALLOC`, o relatório de vazamento de memória tem esta aparência:  
  
```  
Detected memory leaks! Dumping objects -> C:\PROGRAM FILES\VISUAL STUDIO\MyProjects\leaktest\leaktest.cpp(20) : {18} normal block at 0x00780E80, 64 bytes long. Data: <                > CD CD CD CD CD CD CD CD CD CD CD CD CD CD CD CD Object dump complete.  
```  
  
 A diferença é que o segundo relatório mostra o nome do arquivo e o número da linha onde a memória vazada é atribuída primeiro.  
  
 Se você definir `_CRTDBG_MAP_ALLOC` ou não, o vazamento de memória relatório exibirá as seguintes informações:  
  
-   O número de alocação de memória, que é `18` neste exemplo  
  
-   O [tipo de bloco](http://msdn.microsoft.com/pt-br/e2f42faf-0687-49e7-aa1f-916038354f97), que é `normal` neste exemplo.  
  
-   O local da memória hexadecimal, que é `0x00780E80` neste exemplo.  
  
-   O tamanho do bloco, `64 bytes` neste exemplo.  
  
-   Os primeiros 16 bytes de dados em bloco, em formato hexadecimal.  
  
 O relatório de vazamento de memória identifica um bloco de memória como normal, cliente ou CRT. Um *bloco normal* é a memória comum atribuída pelo seu programa. Um *Bloco de cliente* é um tipo especial de bloco de memória usado por programas MFC para objetos que exigem um destruidor. O MFC `new` operador cria um bloco normal ou um bloco de cliente, conforme apropriado para o objeto que está sendo criado. Um *Bloco de CRT* é alocada pela biblioteca de CRT para seu próprio uso. A biblioteca de CRT trata a desalocação desses blocos. Portanto, é improvável que você verá no relatório de vazamento de memória, a menos que algo esteja significativamente errado, por exemplo, a biblioteca de CRT está corrompida.  
  
 Há dois outros tipos de blocos de memória que nunca aparecem nos relatórios de vazamento de memória. Um *bloco livre* é a memória que foi liberada. Isso significa que ele não é vazado, por definição. Um *bloco ignorar* é a memória que você marcou explicitamente para excluí\-la do relatório de vazamento de memória.  
  
 Essas técnicas funcionam para a memória alocada usando o CRT padrão `malloc` função. Se seu programa aloca memória usando o C\+\+ `new` operador, no entanto, você precisará redefinir `new` se você deseja ver os arquivo e números de linha no relatório de vazamento de memória. Você pode fazer isso com um bloco de código que tem esta aparência:  
  
```  
#ifdef _DEBUG #ifndef DBG_NEW #define DBG_NEW new ( _NORMAL_BLOCK , __FILE__ , __LINE__ ) #define new DBG_NEW #endif #endif  // _DEBUG  
```  
  
## Definir pontos de interrupção em um número de alocação de memória  
 O número de alocação de memória informa quando um bloco de perda de memória foi alocado. Um bloco com um número de alocação de memória de 18, por exemplo, é o 18º bloco de memória alocada durante a execução do aplicativo. O relatório de CRT conta todas as alocações de bloco de memória durante a execução. Isso inclui as alocações pela biblioteca do CRT e outras bibliotecas, como o MFC. Portanto, um bloco com um número de alocação de memória de 18 não pode ser o 18º bloco de memória alocado pelo seu código. Normalmente, não será.  
  
 Você pode usar o número de alocação para definir um ponto de interrupção na alocação de memória.  
  
#### Para definir um ponto de interrupção de alocação de memória usando a janela Inspeção  
  
1.  Definir um ponto de interrupção no início do seu aplicativo e, em seguida, inicie o aplicativo.  
  
2.  Quando o aplicativo for interrompido no ponto de interrupção, o **inspeção** janela.  
  
3.  No **inspeção** janela, digite `_crtBreakAlloc` no **nome** coluna.  
  
     Se você estiver usando a versão DLL multithread da biblioteca CRT \(a opção \/MD\), inclua o operador de contexto: `{,,ucrtbased.dll}_crtBreakAlloc`  
  
4.  Pressione **retornar**.  
  
     O depurador avalia a chamada e coloca o resultado no **valor** coluna. Esse valor será \-1 se você não definir nenhum ponto de interrupção nas alocações de memória.  
  
5.  No **valor** coluna, substitua o valor mostrado com o número de alocação da alocação de memória onde você deseja interromper.  
  
 Depois de definir um ponto de interrupção em um número de alocação de memória, você pode continuar a depuração. Tenha cuidado ao executar o programa nas mesmas condições que a execução anterior para que não altera a ordem de alocação de memória. Quando o programa interrompe a alocação de memória especificado, você pode usar o **pilha de chamadas** janela e outras janelas do depurador para determinar as condições sob as quais a memória foi alocada. Em seguida, você pode continuar a execução para observar o que acontece ao objeto e determinar por que ele não ser deslocado corretamente.  
  
 Definindo um ponto de interrupção de dados no objeto também pode ser útil. Para obter mais informações, consulte [Usando pontos de interrupção](../debugger/using-breakpoints.md).  
  
 Você também pode definir pontos de interrupção de alocação de memória no código. Há duas maneiras de fazer isso:  
  
```  
_crtBreakAlloc = 18;  
```  
  
 ou:  
  
```  
_CrtSetBreakAlloc(18);  
```  
  
## Comparando estados de memória  
 Outra técnica para localizar vazamentos de memória envolve pegar instantâneos do estado da memória do aplicativo nos pontos\-chave. Para obter um instantâneo do estado da memória em um determinado ponto no seu aplicativo, criar um **crtmemstate** estrutura e passá\-lo para o `_CrtMemCheckpoint` função. Esta função preenche a estrutura com um instantâneo do estado da memória atual:  
  
```  
_CrtMemState s1; _CrtMemCheckpoint( &s1 );  
  
```  
  
 `_CrtMemCheckpoint` preenche a estrutura com um instantâneo do estado atual de memória.  
  
 Para exibir o conteúdo de um **crtmemstate** estrutura, passe a estrutura para o `_ CrtMemDumpStatistics` função:  
  
```  
_CrtMemDumpStatistics( &s1 );  
  
```  
  
 `_ CrtMemDumpStatistics` gera um despejo do estado de memória tem esta aparência:  
  
```  
0 bytes in 0 Free Blocks. 0 bytes in 0 Normal Blocks. 3071 bytes in 16 CRT Blocks. 0 bytes in 0 Ignore Blocks. 0 bytes in 0 Client Blocks. Largest number used: 3071 bytes. Total allocations: 3764 bytes.  
  
```  
  
 Para determinar se um vazamento de memória ocorreu em uma seção de código, você pode tirar instantâneos do estado da memória antes e após a seção e, em seguida, use `_ CrtMemDifference` para comparar os dois estados:  
  
```  
_CrtMemCheckpoint( &s1 ); // memory allocations take place here _CrtMemCheckpoint( &s2 ); if ( _CrtMemDifference( &s3, &s1, &s2) ) _CrtMemDumpStatistics( &s3 );  
```  
  
 `_CrtMemDifference` compara os estados de memória `s1` e `s2` e retorna um resultado em \(`s3`\) que é a diferença de `s1` e `s2`.  
  
 Uma técnica para localizar vazamentos de memória começa colocando `_CrtMemCheckpoint` chamadas no início e no final do seu aplicativo, em seguida, usando `_CrtMemDifference` para comparar os resultados. Se `_CrtMemDifference` mostra um vazamento de memória, você pode adicionar mais `_CrtMemCheckpoint` chamadas para dividir seu programa usando uma pesquisa binária até ter isolado a fonte do vazamento.  
  
## Falsos positivos  
 Em alguns casos, `_CrtDumpMemoryLeaks` poderá dar falsas indicações de vazamentos de memória. Isso pode ocorrer se você usar uma biblioteca que marca alocações internas como normal\_blocks em vez de `_CRT_BLOCK`s ou `_CLIENT_BLOCK`s. Nesse caso, `_CrtDumpMemoryLeaks` é capaz de reconhecer a diferença entre alocações de usuário e alocações internas de biblioteca. Se os destruidores globais para as alocações de biblioteca executado após o ponto onde você chamar `_CrtDumpMemoryLeaks`, cada alocação interna da biblioteca é relatada como um vazamento de memória. Versões mais antigas do Standard Template Library, anteriores ao Visual Studio .NET, causaram `_CrtDumpMemoryLeaks` para relatar falsos positivos, mas isso foi corrigido em versões recentes.  
  
## Consulte também  
 [Detalhes da pilha de depuração CRT](../debugger/crt-debug-heap-details.md)   
 [Segurança do depurador](../debugger/debugger-security.md)   
 [Depurando código nativo](../debugger/debugging-native-code.md)