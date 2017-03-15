---
title: "N&#227;o &#233; poss&#237;vel implementar &#39; &lt; interfacename1 &gt;. &lt; nome &gt;&#39; porque sua implementa&#231;&#227;o poderia entrar em conflito com a implementa&#231;&#227;o para &#39; &lt; interfacename2 &gt;. &lt; nome &gt;&#39; para alguns argumentos de tipo | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc32125"
  - "vbc32125"
helpviewer_keywords: 
  - "BC32125"
ms.assetid: 74321d27-4ff8-440c-b5de-d67e98fff274
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# N&#227;o &#233; poss&#237;vel implementar &#39; &lt; interfacename1 &gt;. &lt; nome &gt;&#39; porque sua implementa&#231;&#227;o poderia entrar em conflito com a implementa&#231;&#227;o para &#39; &lt; interfacename2 &gt;. &lt; nome &gt;&#39; para alguns argumentos de tipo
Uma classe implementa mais de uma interface genérica, uma que herda de outra, e duas implementações de um membro de interface poderia entrar em conflito para certos valores de argumentos de tipo.  
  
 As instruções a seguir podem gerar esse erro.  
  
```  
Public Interface iFace1(Of t) Sub testSub() End Interface Public Interface iFace2(Of u) Inherits iFace1(Of u) End Interface Public Class testClass(Of y, z) Implements iFace1(Of y), iFace2(Of z) Public Sub testSuby() Implements iFace1(Of y).testSub End Sub Public Sub testSubz() Implements iFace1(Of z).testSub End Sub End Class  
```  
  
 Porque `iFace2` herda de `iFace1` usando seu próprio parâmetro de tipo \(`u`\), `testClass` implementaria duas versões de `iFace1.testSub` com assinaturas idênticas se o mesmo argumento de tipo foi passado para `y` e `z`. Isso produziria uma ambigüidade sobre qual versão acessar.  
  
 **ID do erro:** BC32125  
  
### Para corrigir este erro  
  
-   Alterar a estrutura de herança das interfaces de modo que `iFace1` não pode ser implementado com dois argumentos de tipo diferente.  
  
     \- ou \-  
  
-   Remova o `Implements` instrução das interfaces que resulta no conflito de implementação.  
  
## Consulte também  
 [Instrução Class](/dotnet/visual-basic/language-reference/statements/class-statement)   
 [Instrução Interface](/dotnet/visual-basic/language-reference/statements/interface-statement)   
 [Instrução Implements](/dotnet/visual-basic/language-reference/statements/implements-statement)   
 [NÃO está em compilação: Palavra\-chave Implements e a instrução Implements](http://msdn.microsoft.com/pt-br/b96560f7-6413-480f-a1e2-f80253bab5be)   
 [Tipos genéricos no Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)