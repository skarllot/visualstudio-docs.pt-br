---
title: "Como retornar &#224; fun&#231;&#227;o que chamou MFC em caso de parada | Microsoft Docs"
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
  - "vs.debug.mfc"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "C++"
helpviewer_keywords: 
  - "comando Interromper"
  - "depuração [MFC], Funções "
  - "depuração [MFC], retornando para a função de chamada"
  - "chamadas de função, retornando para a função de chamada"
  - "funções [C++], depuração"
  - "funções [depurador]"
  - "programas, parando"
ms.assetid: d254a5a9-afbd-4923-9d7a-7422d824cabf
caps.latest.revision: 18
caps.handback.revision: 18
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Como retornar &#224; fun&#231;&#227;o que chamou MFC em caso de parada
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

> [!NOTE]
>  As caixas de diálogo e os comandos de menu que você vê podem ser diferentes dos descritos na Ajuda, dependendo da sua edição ou das configurações ativas.  Para alterar as configurações, escolha Importar e Exportar Configurações no menu Ferramentas.  Para obter mais informações, consulte [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/pt-br/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
 Se você usou o comando **Interromper** no menu **Depurar** para interromper o programa e terminou no MFC, e se você tiver certeza de que o problema está em seu código, poderá usar a janela Pilha de Chamadas para navegar de volta para a função.  Para obter mais informações, consulte [Como usar a janela Pilha de Chamadas](../debugger/how-to-use-the-call-stack-window.md).  
  
 Às vezes seu código pode ser interrompido na bomba da mensagem.  Nesse caso, não há nenhum código de usuário na pilha de chamadas.  Para evitar esse problema, você poderá usar pontos de interrupção \(possivelmente com condições e contagens de ocorrências\) em vez do comando **Interromper**.  Para obter mais informações, consulte [Breakpoints and Tracepoints](http://msdn.microsoft.com/pt-br/fe4eedc1-71aa-4928-962f-0912c334d583).  
  
### Para navegar até a função da qual o MFC foi chamado  
  
-   Use a janela **Pilha de Chamadas**.  
  
## Consulte também  
 [Perguntas frequentes de depuração do código nativo](../debugger/debugging-native-code-faqs.md)   
 [Depurando código nativo](../debugger/debugging-native-code.md)