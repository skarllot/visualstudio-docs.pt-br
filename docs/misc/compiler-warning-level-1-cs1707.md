---
title: "Compilador CS1707 de aviso (n&#237;vel 1) | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS1707"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1707"
ms.assetid: 47b6096e-4e4b-4057-b9d7-4a096139267a
caps.latest.revision: 9
caps.handback.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilador CS1707 de aviso (n&#237;vel 1)
Delegado 'DelegateName' associado a 'MethodName1' em vez de 'MethodName2' devido a novas regras de idioma  
  
 C\# 2.0 implementa novas regras para associar um delegado para um método. Informações adicionais são consideradas que não foi examinou no passado. Esse aviso indica que o delegado agora está vinculado a uma outra sobrecarga do método que estava anteriormente vinculado a. Talvez você queira verificar se o delegado realmente deve ser vinculado ao 'MethodName1' em vez de 'MethodName2'.  
  
 Para obter uma descrição de como o compilador determina qual método de associar um delegado, consulte [Usando variação em delegações](../Topic/Using%20Variance%20in%20Delegates%20\(C%23%20and%20Visual%20Basic\).md).