---
title: "Restri&#231;&#227;o &#39;Class&#39; e uma restri&#231;&#227;o de tipo de classe espec&#237;fica n&#227;o podem ser combinados | Microsoft Docs"
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
  - "vbc32107"
  - "bc32107"
helpviewer_keywords: 
  - "BC32107"
ms.assetid: 218a7f0c-dd4f-4086-a52c-e8d581377e8b
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Restri&#231;&#227;o &#39;Class&#39; e uma restri&#231;&#227;o de tipo de classe espec&#237;fica n&#227;o podem ser combinados
Uma lista de restrição inclui tanto o [Class \(Visual Basic\)](http://msdn.microsoft.com/pt-br/0777c6e6-46bc-451b-ad70-57b49d4ef4f7) restrição e o nome de uma classe definida.  
  
 Uma lista de restrições impõe exigências no tipo de argumento passado para o parâmetro de tipo. Você pode especificar os seguintes requisitos em qualquer combinação:  
  
-   O argumento de tipo deve implementar uma ou mais interfaces  
  
-   O argumento de tipo deve herdar de no máximo uma classe  
  
-   O argumento de tipo deve expor um construtor sem parâmetros que pode acessar o código de criação \(incluem o `New` restrição\)  
  
 Se você não incluir qualquer interface ou classe específica na lista de restrição, você pode impor uma necessidade geral, especificando um destes procedimentos:  
  
-   O argumento de tipo deve ser um tipo de valor \(inclua a `Structure` restrição\)  
  
-   O argumento de tipo deve ser um tipo de referência \(incluem o `Class` restrição\)  
  
 Não é possível especificar `Structure` e `Class` para o mesmo tipo de parâmetro e você não pode especificar uma mais de uma vez.  
  
 **ID do erro:** BC32107  
  
### Para corrigir este erro  
  
-   Se você quiser permitir que o argumento de tipo seja qualquer tipo de referência, remova o nome da classe da lista de restrições.  
  
-   Se desejar que o argumento de tipo herde o nome da classe especificado, remova o `Class` palavra\-chave da lista de restrições.  
  
## Consulte também  
 [Tipos genéricos no Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)   
 [Tipos de valor e referência](/dotnet/visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types)