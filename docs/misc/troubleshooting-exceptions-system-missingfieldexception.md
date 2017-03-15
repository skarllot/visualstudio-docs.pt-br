---
title: "Exce&#231;&#245;es de solu&#231;&#227;o de problemas: System.MissingFieldException | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
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
  - "Classe MissingFieldException"
ms.assetid: afa4d669-7d08-4b14-8341-36717a5054d6
caps.latest.revision: 12
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Exce&#231;&#245;es de solu&#231;&#227;o de problemas: System.MissingFieldException
Um <xref:System.MissingFieldException> exceção é lançada quando há uma tentativa de acessar dinamicamente um campo que não existe.  
  
## Dicas associadas  
 **Se um campo em uma biblioteca de classes foi removido ou renomeado, recompile todos os assemblies que fazem referência a essa biblioteca.**  
 Essa exceção é gerada quando é feita uma tentativa para acessar dinamicamente um campo excluído ou renomeado de um assembly que não é referenciado por seu nome forte.  
  
## Consulte também  
 <xref:System.MissingFieldException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)