---
title: "Exce&#231;&#245;es de solu&#231;&#227;o de problemas: System.IO.EndOfStreamException | Microsoft Docs"
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
  - "Classe EndOfStreamException"
ms.assetid: 1271e6f6-3a0d-49f0-9ff4-178d480687be
caps.latest.revision: 14
caps.handback.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Exce&#231;&#245;es de solu&#231;&#227;o de problemas: System.IO.EndOfStreamException
Um <xref:System.IO.EndOfStreamException> exceção é lançada quando há uma tentativa de leitura ultrapassou o fim de um fluxo.  
  
## Dicas associadas  
 **Verifique se o fim do arquivo foi atingido antes da leitura.**  
 Use o <xref:System.IO.StreamReader.Peek%2A> método para verificar o fim do arquivo antes da leitura do fluxo.  
  
## Consulte também  
 <xref:System.IO.EndOfStreamException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)   
 [Como ler e gravar em um arquivo de dados recém\-criado](../Topic/How%20to:%20Read%20and%20Write%20to%20a%20Newly%20Created%20Data%20File.md)   
 [Como abrir um arquivo de log e acrescentar dados a ele](../Topic/How%20to:%20Open%20and%20Append%20to%20a%20Log%20File.md)