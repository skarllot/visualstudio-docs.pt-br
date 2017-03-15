---
title: "Exce&#231;&#245;es de solu&#231;&#227;o de problemas: System.FieldAccessException | Microsoft Docs"
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
  - "Classe FieldAccessException"
ms.assetid: 47a72daf-500e-494c-b2fe-374edad2e9cd
caps.latest.revision: 15
caps.handback.revision: 15
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Exce&#231;&#245;es de solu&#231;&#227;o de problemas: System.FieldAccessException
Um <xref:System.FieldAccessException> exceção é lançada quando houver uma tentativa inválida de acessar um campo particular ou protegido dentro de uma classe.  
  
## Dicas associadas  
 **Se o nível de acesso de um campo em uma biblioteca de classes for alterado, recompile todos os assemblies que fazem referência a essa biblioteca.**  
 Essa exceção geralmente é lançada quando o nível de acesso \(`Public`, `Private`, etc\) de um campo em uma classe de biblioteca é alterada, e um ou mais assemblies que fazem referência à biblioteca não foram recompilados.  
  
## Consulte também  
 <xref:System.FieldAccessException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)