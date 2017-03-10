---
title: "DA0007: evitar usar exce&#231;&#245;es no fluxo de controle | Microsoft Docs"
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
  - "vs.performance.rules.DAExceptionsThrown"
  - "vs.performance.7"
  - "vs.performance.rules.DA0007"
  - "vs.performance.DA0007"
ms.assetid: ee8ba8b5-2313-46c9-b129-3f3a2a232898
caps.latest.revision: 13
caps.handback.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# DA0007: evitar usar exce&#231;&#245;es no fluxo de controle
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|Identificação da Regra|DA0007|  
|Categoria|uso do .NET Framework|  
|Analisando métodos|Todos|  
|Message \(Mensagem\)|Um número alto de exceções está sendo gerado consistentemente.  Considere a redução do uso de exceções na lógica do programa.|  
|Tipo de mensagem|Aviso|  
  
 Quando você analisa usando a amostragem, a memória .NET ou os métodos de contenção de recurso, você deve coletar pelo menos 25 amostras para disparar esta regra.  
  
## Causa  
 Uma taxa alta de manipuladores de exceção do .NET Framework foi chamada na criação de perfis de dados.  Considere usar outra lógica de fluxo de controle para reduzir o número de exceções emitidas.  
  
## Descrição da Regra  
 Quando o uso de manipuladores de exceção capturar erros e os outros eventos que interrompem a execução do programa é uma boa prática, o uso do manipulador de exceção como parte da lógica normal de execução do programa pode ser dispendiosa e deve ser evitado.  Na maioria dos casos, as exceções devem ser usadas apenas para as condições que raramente ocorrem e não são previstas.  As exceções não devem ser usadas para retornar valores como parte do fluxo de programa típico.  Em muitos casos, você pode aumentar evitar exceções validando valores e usando a lógica condicional para interromper a execução de instruções que fazem com que o problema.  
  
 Para obter mais informações consulte [Gerenciamento de exceção](http://go.microsoft.com/fwlink/?LinkID=177825) a seção de **Chapter 5 — Improving Managed Code Performance** no volume de **Improving .NET Application Performance and Scalability** de biblioteca de **Microsoft Patterns and Practices** no MSDN.  
  
## Como investigar um aviso  
 Clique duas vezes na mensagem na janela de lista de erros para navegar para modo Marcas.  Localize a coluna que contém as medidas de **.NET \(CLR\) exceção de @ProcessInstance \\ \# de Exceps gerado\/sec** .  Determine se há etapas específicas de execução do programa onde a manipulação de exceção é mais frequente do que outros.  Usando um perfil de amostragem, tente identificar as instruções do lançamento e tentar blocos de try\/catch que gerencia exceções frequentes.  Se necessário, adicionar lógica em blocos de try\/catch para ajudá\-lo a compreender quais exceções são tratados com mais frequência.  Sempre que possível, substituir instruções executadas frequentemente de lançamento ou captura blocos com lógica de controle de fluxo ou código simples de validação.  
  
 Por exemplo, se você retomasse descobrir que seu aplicativo tratava exceções frequentes de DivideByZeroException, adicionar lógica em seu programa à verificação de denominadores com valores zero melhorará o desempenho do aplicativo.