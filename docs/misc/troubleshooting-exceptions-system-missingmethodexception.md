---
title: "Exce&#231;&#245;es de solu&#231;&#227;o de problemas: System.MissingMethodException | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
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
  - "Classe MissingMethodException"
ms.assetid: 1ca4c351-ca26-4a6d-a5a1-c484ac193e2e
caps.latest.revision: 13
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Exce&#231;&#245;es de solu&#231;&#227;o de problemas: System.MissingMethodException
Um <xref:System.MissingMethodException> exceção é lançada quando há uma tentativa de acessar dinamicamente um método que não existe.  
  
## Dicas associadas  
 **Se um método em uma biblioteca de classes foi removido ou renomeado, recompile todos os assemblies que fazem referência a esse método.**  
 Essa exceção geralmente é lançada quando é feita uma tentativa para acessar dinamicamente um método excluído ou renomeado de um assembly que não é referenciado por seu nome forte.  
  
## Comentários  
 Se você estiver chamando uma função não gerenciada, essa exceção é lançada se o CLR não é possível localizar o módulo ou função.  
  
## Consulte também  
 <xref:System.MissingMethodException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)   
 [Solucionando problemas de interoperabilidade](/dotnet/visual-basic/programming-guide/com-interop/troubleshooting-interoperability)