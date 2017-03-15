---
title: "&#39;&lt; elementname &gt;&#39; para Imports alias &#39;&lt; qualifiedelementname &gt;&#39; n&#227;o faz refer&#234;ncia a um Namespace, classe, estrutura, Interface, Enum ou m&#243;dulo | Microsoft Docs"
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
  - "bc30798"
  - "vbc30798"
helpviewer_keywords: 
  - "BC30798"
ms.assetid: bfa66627-516a-4955-977d-92372bcea090
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt; elementname &gt;&#39; para Imports alias &#39;&lt; qualifiedelementname &gt;&#39; n&#227;o faz refer&#234;ncia a um Namespace, classe, estrutura, Interface, Enum ou m&#243;dulo
Um [Instrução Imports \(tipo e namespace .NET\)](/dotnet/visual-basic/language-reference/statements/imports-statement-net-namespace-and-type) Especifica um elemento de programação que não pode ser importado.  
  
 O `Imports` instrução é usada para reduzir ou eliminar a necessidade de uma cadeia de caracteres de qualificação na frente de um nome de elemento. Qualificar o elemento de `Imports` própria para fornecer um caminho não ambíguo para uma única declaração do elemento de instrução. Depois disso, você não precisa qualificar referências ao elemento.  
  
 `Imports` é mais comumente usado para namespaces, mas você também pode importar classe, módulo, estrutura, interface ou enumeração para permitir que a referência a seus elementos sem uma cadeia de caracteres longa qualificado.  
  
 Para obter mais informações, consulte "Importing Containing Elements" [NOTINBUILD: Resolvendo uma referência quando várias variáveis têm o mesmo nome](http://msdn.microsoft.com/pt-br/9601e39f-1911-44e1-ace5-3f6e090408b9).  
  
 **ID do erro:** BC30798  
  
### Para corrigir este erro  
  
1.  Verifique a ortografia dos elementos na cadeia de qualificação no `Imports` instrução, especialmente o último elemento na cadeia de caracteres, que é o elemento são qualificados.  
  
2.  Verifique se o elemento que são qualificadas de um tipo qualificado \(namespace, classe, módulo, estrutura, interface ou enumeração\). Se não estiver, remova o `Imports` instrução.  
  
## Consulte também  
 [Referências e a instrução Imports](/dotnet/visual-basic/programming-guide/program-structure/references-and-the-imports-statement)