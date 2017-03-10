---
title: "Solucionando problemas de exce&#231;&#245;es: System.Exception | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Exceção System.Exception"
  - "classes base, exceções"
  - "exceções de classe base"
ms.assetid: fc15931a-9323-47c6-a42f-55d0534b939a
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Solucionando problemas de exce&#231;&#245;es: System.Exception
Representa erros que ocorrem durante a execução do aplicativo. Esta é a classe base para todas as exceções.  
  
## Dicas associadas  
 **Verifique a propriedade InnerException para obter mais informações.**  
 Para corrigir o erro, talvez seja necessário obter informações sobre a exceção interna \(ou anterior\) que conduziram à exceção atual. A exceção atual <xref:System.Exception.InnerException%2A> propriedade contém a exceção interna. Você pode usar o **Exibir detalhes** link no **Assistente de exceção** caixa de diálogo para acessar o <xref:System.Exception.InnerException%2A> propriedade.  
  
 **Desative temporariamente a depuração Just My Code.**  
 A exceção pode ter ocorrido no código que você não escreveu. Para depurar o código, você precisará desativar a depuração Just My Code. Para obter mais informações, consulte [Caixa de diálogo Geral, Depuração, Opções](../debugger/general-debugging-options-dialog-box.md).  
  
## Consulte também  
 <xref:System.Exception>   
 <xref:System.Exception.InnerException%2A>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)   
 [Como interromper quando uma exceção é lançada](../misc/how-to-break-when-an-exception-is-thrown.md)   
 [Caixa de diálogo Geral, Depuração, Opções](../debugger/general-debugging-options-dialog-box.md)