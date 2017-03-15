---
title: "Infer&#234;ncia de argumento de tipo falhou para o par&#226;metro de tipo &#39;&lt; typeparametername &gt;&#39; de &#39;&lt; genericproceduresignature &gt;&#39; | Microsoft Docs"
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
  - "vbc32051"
  - "bc32051"
helpviewer_keywords: 
  - "BC32051"
ms.assetid: a9c2a0ce-e225-4549-bfd8-d42df5d16bfd
caps.latest.revision: 12
caps.handback.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Infer&#234;ncia de argumento de tipo falhou para o par&#226;metro de tipo &#39;&lt; typeparametername &gt;&#39; de &#39;&lt; genericproceduresignature &gt;&#39;
Inferência de argumento de tipo falhou para o parâmetro de tipo '\< typeparametername \>' de '\< genericproceduresignature \>'. Não foi possível inferir o argumento de tipo do argumento passado ao parâmetro '\< parametername \>'.  
  
 Um procedimento genérico é chamado sem fornecer quaisquer argumentos de tipo, e o compilador não pode inferir o tipo para passar para um dos parâmetros.  
  
 Normalmente, quando você chama um procedimento genérico, você fornece um argumento de tipo para cada parâmetro de tipo que define o procedimento genérico. Se você não fornecer nenhum argumento de tipo, o compilador tenta inferir os tipos a serem passados para os parâmetros de tipo. Se o contexto da chamada fornece conflitantes informações tipo de dados para um parâmetro de tipo, a inferência de tipo falhará.  
  
 O código a seguir pode gerar esse erro.  
  
```  
Public Sub doSomething(Of t)(ByVal arg1 As t(), ByVal arg2 As t) End Sub Call doSomething(6, 42)  
```  
  
 No exemplo anterior, o compilador infere o tipo `Integer` para `t` com base no valor de 42 passado para `arg2`. No entanto, essa inferência exigiria `arg1` para ser do tipo `Integer()`, ou seja, uma matriz de `Integer`, e o valor 6 passado para `arg1` não corresponde a esse tipo.  
  
 **ID do erro:** BC32051  
  
### Para corrigir este erro  
  
-   Forneça os argumentos de tipo ao procedimento genérico, de modo que o compilador não precise inferi\-los.  
  
-   Fornece argumentos normais com tipos que correspondam aos argumentos de tipo.  
  
## Consulte também  
 [Tipos genéricos no Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)   
 [Procedimentos genéricos no Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-procedures)   
 [Lista de tipos](/dotnet/visual-basic/language-reference/statements/type-list)