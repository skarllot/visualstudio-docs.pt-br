---
title: "Este aplicativo de inst&#226;ncia &#250;nica n&#227;o p&#244;de se conectar &#224; inst&#226;ncia original | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbrAppModel_SingleInstanceCantConnect"
ms.assetid: 7c2c0cee-02a1-4157-be03-39d18e18408f
caps.latest.revision: 12
caps.handback.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Este aplicativo de inst&#226;ncia &#250;nica n&#227;o p&#244;de se conectar &#224; inst&#226;ncia original
Este aplicativo de instância única não pôde se conectar à instância original. Algumas das possíveis causas para esse problema são as seguintes:  
  
-   A instância original parou de responder.  
  
-   O aplicativo não tem permissões para criar objetos kernel. Para obter mais informações sobre objetos kernel, consulte [Mutexes](../Topic/Mutexes.md).  
  
     O nome de base para os objetos kernel vem da concatenação GUID, número de versão principal e número da versão secundária do assembly. Por exemplo, o nome de base poderia ser `3639f15d-9547-43da-8145-60da347829915.1`.  
  
### Para corrigir esse erro ao desenvolver o aplicativo  
  
1.  Verifique se o aplicativo não entra em um estado sem resposta.  
  
2.  Verifique se o aplicativo tem permissões suficientes para criar objetos kernel.  
  
3.  Reinicie a instância original do aplicativo.  
  
4.  Reinicie o computador para limpar qualquer processo que possa estar usando o recurso que é necessário para se conectar ao aplicativo da instância original.  
  
5.  Observe as circunstâncias nas quais o erro ocorreu e telefone o Atendimento Microsoft.  
  
## Consulte também  
 [NIB: Como: Especificar comportamento de instâncias para um aplicativo \(Visual Basic\)](http://msdn.microsoft.com/pt-br/48539ad8-d960-4210-beab-ee65f6c6dc6e)   
 [Noções básicas do depurador](../debugger/debugger-basics.md)   
 [Acessibilidade e suporte a produtos PAVEOVER](http://msdn.microsoft.com/pt-br/14e1d293-7b6d-40a6-bf3e-a92f8ee6c88c)