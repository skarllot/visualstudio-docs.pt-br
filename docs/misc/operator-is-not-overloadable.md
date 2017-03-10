---
title: "Operador n&#227;o &#233; sobrecarreg&#225;vel | Microsoft Docs"
ms.custom: ""
ms.date: "11/23/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc33002"
  - "bc33002"
helpviewer_keywords: 
  - "BC33002"
ms.assetid: 8628ea42-57d8-41ca-8bdc-5e4c27be543e
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Operador n&#227;o &#233; sobrecarreg&#225;vel
Apenas certos operadores são elegíveis para a sobrecarga. A tabela a seguir lista os operadores que você pode definir.  
  
|Tipo|Operadores|  
|----------|----------------|  
|Unários|`+`, `-`, `IsFalse`, `IsTrue`, `Not`|  
|Binário|`+`, `-`, `*`, `/`, `\`, `&`, `^`, `>>`, `<<`, `=`, `<>`, `>`, `>=`, `<`, `<=`, `And`, `Like`, `Mod`, `Or`, `Xor`|  
|Conversão \(unário\)|`CType`|  
  
 Observe que o `=` operador na lista binária é o operador de comparação, não o operador de atribuição.  
  
 **ID do erro:** BC33002  
  
### Para corrigir este erro  
  
1.  Selecione um operador de conjunto de operadores que pode ser sobrecarregados.  
  
2.  Se você precisar da funcionalidade de sobrecarregar um operador que você não pode sobrecarregar diretamente, crie uma `Function` procedimento que usa os parâmetros apropriados e retorna o valor apropriado.  
  
## Consulte também  
 [Instrução Operator](/dotnet/visual-basic/language-reference/statements/operator-statement)   
 [Procedimentos do operador](/dotnet/visual-basic/programming-guide/language-features/procedures/operator-procedures)   
 [Como definir um operador](../Topic/How%20to:%20Define%20an%20Operator%20\(Visual%20Basic\).md)   
 [Como definir um operador de conversão](../Topic/How%20to:%20Define%20a%20Conversion%20Operator%20\(Visual%20Basic\).md)   
 [Instrução Function](/dotnet/visual-basic/language-reference/statements/function-statement)