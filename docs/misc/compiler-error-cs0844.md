---
title: "CS0844 de erro do compilador | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS0844"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0844"
ms.assetid: ccf74e01-292a-42d0-897c-8add7aee2118
caps.latest.revision: 5
caps.handback.revision: 5
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# CS0844 de erro do compilador
Não é possível usar a variável local 'name' antes de ser declarada. A declaração da variável local oculta o campo 'nome'.  
  
 Um identificador pode ter apenas um significado em um determinado bloco. Variáveis locais que têm o mesmo nome como campos de classe podem ocultar o campo introduzindo um segundo significado para o identificador. Portanto, o compilador gera um erro quando você se referir a um campo de classe em um método e, em seguida, declara uma variável local com o mesmo nome.  
  
### Para corrigir este erro  
  
-   Use `this.num` para fazer referência ao campo de classe.  
  
-   Dê à variável local com um nome diferente do campo da classe.  
  
## Exemplo  
 O código a seguir gera CS0844:  
  
```  
class Test { int num; public void TestMethod() { num = 5; // CS0844 int num = 6;        } public static int Main() { return 1; } }  
```