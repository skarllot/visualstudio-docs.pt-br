---
title: "Exce&#231;&#245;es de solu&#231;&#227;o de problemas: System.Runtime.InteropServices.SafeArrayRankMismatchException | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "EHSafeArrayRankMismatch"
dev_langs: 
  - "JScript"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "Classe SafeArrayRankMismatchException"
ms.assetid: 6c69355c-8bfd-49bb-acad-b4d7236ae2e7
caps.latest.revision: 13
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Exce&#231;&#245;es de solu&#231;&#227;o de problemas: System.Runtime.InteropServices.SafeArrayRankMismatchException
Um <xref:System.Runtime.InteropServices.SafeArrayRankMismatchException> exceção é lançada quando a classificação de uma entrada SAFEARRAY não corresponde à classificação especificada na assinatura gerenciada.  
  
## Dicas associadas  
 **Verifique se que a matriz tem o número de dimensões necessário.**  
 Como a classificação e os limites de uma matriz segura não podem ser determinados da biblioteca de tipos, a classificação é considerada igual a 1 e o limite inferior é considerado igual a 0. Os limites e a classificação devem ser definidos na assinatura gerenciada produzida pelo [Tlbimp.exe \(Importador de Biblioteca de Tipos\)](../Topic/Tlbimp.exe%20\(Type%20Library%20Importer\).md).  
  
## Consulte também  
 <xref:System.Runtime.InteropServices.SafeArrayRankMismatchException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)   
 [Marshaling padrão para matrizes](../Topic/Default%20Marshaling%20for%20Arrays.md)   
 [Matrizes](/dotnet/visual-basic/programming-guide/language-features/arrays/index)