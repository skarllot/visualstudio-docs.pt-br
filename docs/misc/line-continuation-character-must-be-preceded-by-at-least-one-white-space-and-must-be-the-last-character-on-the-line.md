---
title: "Caractere de continua&#231;&#227;o de linha &#39;_&#39; deve ser precedido pelo menos um espa&#231;o em branco e deve ser o &#250;ltimo caractere na linha | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc30999"
  - "bc30999"
helpviewer_keywords: 
  - "BC30999"
ms.assetid: 32caf62f-52e4-4acd-b40f-5af65e42e643
caps.latest.revision: 4
caps.handback.revision: 4
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Caractere de continua&#231;&#227;o de linha &#39;_&#39; deve ser precedido pelo menos um espa&#231;o em branco e deve ser o &#250;ltimo caractere na linha
Você pode usar o caractere de continuação de linha, que é um caractere de sublinhado \(\_\), para interromper uma longa linha de código em várias linhas no arquivo. O sublinhado deve ser imediatamente precedido por um espaço e seguido imediatamente por um terminador de linha \(retorno de carro\). Por exemplo:  
  
```  
Dim books As XDocument = _ XDocument.Load(My.Application.Info.DirectoryPath & _ "\..\..\Data\books.xml")  
```  
  
 **ID do erro:** BC30999  
  
### Para corrigir este erro  
  
1.  Certifique\-se de que o caractere de continuação de linha \(\_\) é o último caractere em uma linha de código.  
  
2.  Verifique se há um espaço antes do caractere de continuação de linha, separando\-o de qualquer outro código na linha.  
  
## Consulte também  
 [Como quebrar e combinar instruções no código](../Topic/How%20to:%20Break%20and%20Combine%20Statements%20in%20Code%20\(Visual%20Basic\).md)