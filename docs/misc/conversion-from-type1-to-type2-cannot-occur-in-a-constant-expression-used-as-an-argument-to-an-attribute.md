---
title: "Convers&#227;o de &#39;&lt; type1 &gt;&#39; para &#39;&lt; type2 &gt;&#39; n&#227;o pode ocorrer em uma express&#227;o constante usada como um argumento para um atributo | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc30934"
  - "vbc30934"
helpviewer_keywords: 
  - "BC30934"
ms.assetid: 120e05f9-1d0e-4800-b05c-a8373e286b9b
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Convers&#227;o de &#39;&lt; type1 &gt;&#39; para &#39;&lt; type2 &gt;&#39; n&#227;o pode ocorrer em uma express&#227;o constante usada como um argumento para um atributo
Uma expressão usada para um argumento de atributo avalia para um tipo de dados diferente do parâmetro de atributo correspondente, e [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] não permite a conversão de tipos necessária para argumentos de atributo.  
  
 Um atributo fornece metadados para o elemento para que é aplicado, e o compilador deve ser capaz de construir todos os metadados em tempo de compilação. Por esse motivo, cada atributo deve usar valores que são constantes no tempo de compilação e, portanto, cada argumento de atributo deve ser avaliada como um valor constante de tempo de compilação.  
  
 Determinadas conversões de tipos não podem produzir valores que são constantes no tempo de compilação. Por exemplo, converter um `String` para um `Double` ou um `Date` depende da configuração de localidade no tempo de execução. Outras conversões, como uma matriz de um tipo derivado para uma matriz de `Object`, apresentam uma variedade de problemas que não permitem que o compilador as permita em argumentos de atributo.  
  
 **ID do erro:** BC30934  
  
### Para corrigir este erro  
  
-   Use uma expressão que avalia para o mesmo tipo de dados como o parâmetro correspondente, conforme definido pelo atributo.  
  
## Consulte também  
 [NÃO está em compilação: Atributos no Visual Basic](http://msdn.microsoft.com/pt-br/620bfc0e-4582-4c8b-8432-ebc5c3dccc22)   
 [NÃO está em compilação: Aplicação de atributos](http://msdn.microsoft.com/pt-br/2b1703ed-4437-49b3-bc0b-568094324f47)   
 [Instrução Const](/dotnet/visual-basic/language-reference/statements/const-statement)   
 [Conversões de tipo no Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/type-conversions)