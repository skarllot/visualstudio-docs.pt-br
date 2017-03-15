---
title: "Nenhum m&#233;todo acess&#237;vel &#39;&lt; procedurename &gt;&#39; tem uma assinatura compat&#237;vel com delegado &#39;&lt; nomedelegado &gt;&#39;: &lt; suberrorlist &gt; | Microsoft Docs"
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
  - "bc30950"
  - "vbc30950"
helpviewer_keywords: 
  - "BC30950"
ms.assetid: c1938099-2c03-491e-b599-d0c43bf94baf
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Nenhum m&#233;todo acess&#237;vel &#39;&lt; procedurename &gt;&#39; tem uma assinatura compat&#237;vel com delegado &#39;&lt; nomedelegado &gt;&#39;: &lt; suberrorlist &gt;
Uma instrução de atribuição atribui o endereço de um procedimento para uma variável do delegado, mas o compilador não pode localizar uma versão do procedimento com uma assinatura correspondente.  
  
 Quando o código usa o endereço de um procedimento, o compilador tenta encontrar uma versão do procedimento com uma lista de parâmetros que corresponde do delegado. Se o procedimento é definido em várias versões sobrecarregadas, o compilador tenta encontrar uma versão única com uma assinatura correspondente. Para obter mais informações, consulte [Resolução de sobrecarga](/dotnet/visual-basic/programming-guide/language-features/procedures/overload-resolution).  
  
 Se o compilador não pode localizar qualquer versão do procedimento com uma assinatura correspondente, ele gera esse erro. Isso pode acontecer, por exemplo, se o procedimento ou o delegado é genérico e um argumento de tipo passado para ele que dá uma assinatura que não corresponde a outra assinatura.  
  
 **ID do erro:** BC30950  
  
### Para corrigir este erro  
  
1.  Redefina o procedimento ou o delegado para que eles tenham correspondência listas de parâmetros.  
  
     \- ou \-  
  
     Definir um novo delegado com uma lista de parâmetros correspondentes que o procedimento ou definir um novo procedimento com uma lista de parâmetros correspondentes do delegado.  
  
2.  Se o procedimento ou o delegado for genérico, em seguida, passe um argumento de tipo que faz com que a sua assinatura coincidir com a outra assinatura.  
  
## Consulte também  
 [Operador AddressOf](/dotnet/visual-basic/language-reference/operators/addressof-operator)   
 [Instrução Delegate](/dotnet/visual-basic/language-reference/statements/delegate-statement)   
 [NÃO está em compilação: Delegados e o operador AddressOf](http://msdn.microsoft.com/pt-br/7b2ed932-8598-4355-b2f7-5cedb23ee86f)   
 [Resolução de sobrecarga](/dotnet/visual-basic/programming-guide/language-features/procedures/overload-resolution)   
 [Tipos genéricos no Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)