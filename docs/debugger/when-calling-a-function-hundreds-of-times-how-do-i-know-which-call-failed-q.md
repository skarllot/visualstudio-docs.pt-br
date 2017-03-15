---
title: "Durante a chamada de uma fun&#231;&#227;o centenas de vezes, como sei qual chamada falhou? | Microsoft Docs"
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
  - "vs.debug.functions"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "C++"
helpviewer_keywords: 
  - "pontos de interrupção, solucionando problemas"
  - "pontos de interrupção condicionais"
  - "erros [depurador], localizando qual chamada de função falhou"
  - "erros [depurador], chamadas de função"
  - "erros [Visual Studio], chamadas de função"
  - "falhas"
  - "chamadas de função, falha"
  - "funções [depurador]"
  - "contagem de ocorrências"
  - "falhas de chamada de ponto de interrupção de local"
  - "Ignorar Contagem"
ms.assetid: 66cfac86-f5be-4d3a-9329-d44cd74bc586
caps.latest.revision: 17
caps.handback.revision: 17
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Durante a chamada de uma fun&#231;&#227;o centenas de vezes, como sei qual chamada falhou?
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

## Descrição do problema  
 Meu programa falha em uma chamada para uma determinada função, `CnvtV`.  O programa provavelmente chama essa função algumas centenas de vezes antes de falhar.  Se eu definir um ponto de interrupção de local em `CnvtV`, o programa parará em cada chamada a essa função, e eu não quero isso.  Eu não sei quais condições causam a falha na chamada, portanto, não consigo definir um ponto de interrupção condicional.  O que posso fazer?  
  
## Solução  
 Você pode definir um ponto de interrupção na função com o campo **Contagem de Ocorrências** com um valor mais alto que nunca será atingido.  Nesse caso, como você acredita que a função `CnvtV` é chamada algumas centenas de vezes, pode definir **Contagem de Ocorrências** como 1000 ou mais.  Execute o programa e aguarde a chamada falhar.  Quando falhar, abra a janela Pontos de Interrupção e verifique a lista de pontos de interrupção.  O ponto de interrupção definido em `CnvtV` aparece, seguido pela contagem de ocorrências e o número de iterações restantes:  
  
```  
CnvtV(int) (no condition) when hit count is equal to 1000 (currently 101)  
```  
  
 Agora você sabe que a função falha na 101a chamada.  Se você redefinir o ponto de interrupção com uma contagem de ocorrências de 101 e executar o programa novamente, o programa de chamada parará na chamada para `CnvtV` que causou a falha.  
  
## Consulte também  
 [Perguntas frequentes de depuração do código nativo](../debugger/debugging-native-code-faqs.md)   
 [Setting Breakpoints](http://msdn.microsoft.com/pt-br/fe4eedc1-71aa-4928-962f-0912c334d583)   
 [Depurando código nativo](../debugger/debugging-native-code.md)