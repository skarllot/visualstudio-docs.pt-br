---
title: "N&#227;o acess&#237;vel &#39;&lt; procedurename &gt;&#39; &#233; o mais espec&#237;fico: &lt; signaturelist &gt; | Microsoft Docs"
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
  - "vbc30794"
  - "BC30794"
helpviewer_keywords: 
  - "BC30794"
ms.assetid: 51d54cbb-b530-4661-9952-5ccc17e4220b
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# N&#227;o acess&#237;vel &#39;&lt; procedurename &gt;&#39; &#233; o mais espec&#237;fico: &lt; signaturelist &gt;
Uma instrução de atribuição atribui o endereço de um procedimento sobrecarregado a uma variável do delegado, mas o compilador não pode resolver entre as versões sobrecarregadas.  
  
 Quando o código usa o endereço de um procedimento que é definido em várias versões sobrecarregadas, o compilador deve decidir quais versões usar. Ele tenta encontrar uma versão única com uma lista de parâmetros que corresponde ao delegado a lista de parâmetros. Para obter mais informações, consulte [Resolução de sobrecarga](/dotnet/visual-basic/programming-guide/language-features/procedures/overload-resolution).  
  
 Se o compilador encontrar mais de uma versão do procedimento com uma assinatura correspondente, ele gera esse erro. Isso pode acontecer, por exemplo, se uma das sobrecargas é genérica e um argumento de tipo é passado para ela que concede a ele uma assinatura idêntica a da outra versão.  
  
 **ID do erro:** BC30794  
  
### Para corrigir este erro  
  
-   Se o conflito é causado por uma sobrecarga genérica tendo a mesma assinatura de outra sobrecarga, altere o argumento passado para essa sobrecarga genérica.  
  
## Consulte também  
 [Operador AddressOf](/dotnet/visual-basic/language-reference/operators/addressof-operator)   
 [Instrução Delegate](/dotnet/visual-basic/language-reference/statements/delegate-statement)   
 [NÃO está em compilação: Delegados e o operador AddressOf](http://msdn.microsoft.com/pt-br/7b2ed932-8598-4355-b2f7-5cedb23ee86f)   
 [Resolução de sobrecarga](/dotnet/visual-basic/programming-guide/language-features/procedures/overload-resolution)   
 [Tipos genéricos no Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)