---
title: "Exce&#231;&#245;es de solu&#231;&#227;o de problemas: System.StackOverflowException | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "JScript"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "Classe StackOverflowException"
ms.assetid: 51b71217-c507-4f5b-bc35-0236180d7968
caps.latest.revision: 20
caps.handback.revision: 20
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Exce&#231;&#245;es de solu&#231;&#227;o de problemas: System.StackOverflowException
Um <xref:System.StackOverflowException> exceção é lançada quando a pilha de execução excede por ter muitas chamadas de método aninhadas.  
  
## Dicas associadas  
 Verifique se que você não tem um loop infinito ou recursão infinita.  
 Muitas chamadas de método são geralmente indicativos de recursão profunda ou irrestrita.  
  
## Comentários  
 Você não pode capturar exceções de estouro de pilha, porque o código de tratamento de exceções pode exigir a pilha. Em vez disso, quando um estouro de pilha ocorre em um aplicativo normal, o tempo de execução do CLR \(Common Language\) encerra o processo.  
  
 Um aplicativo que hospeda o CLR pode alterar o comportamento padrão e especificar que o CLR descarregue o domínio do aplicativo onde a exceção ocorre, mas permite que o processo continue. Para obter mais informações, consulte [Interface ICLRPolicyManager](../Topic/ICLRPolicyManager%20Interface.md).  
  
## Consulte também  
 <xref:System.StackOverflowException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)   
 [Estruturas de loop](/dotnet/visual-basic/programming-guide/language-features/control-flow/loop-structures)