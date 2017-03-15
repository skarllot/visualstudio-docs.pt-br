---
title: "Infer&#234;ncia de argumento de tipo falhou para o par&#226;metro de tipo &#39;&lt; typeparametername1 &gt;&#39; de &#39;&lt; genericproceduresignature &gt;&#39; | Microsoft Docs"
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
  - "vbc32116"
  - "bc32116"
helpviewer_keywords: 
  - "BC32116"
ms.assetid: 6bfb02ec-814a-4b1f-a585-6d902a861d00
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Infer&#234;ncia de argumento de tipo falhou para o par&#226;metro de tipo &#39;&lt; typeparametername1 &gt;&#39; de &#39;&lt; genericproceduresignature &gt;&#39;
Inferência de argumento de tipo falhou para o parâmetro de tipo '\< typeparametername1 \>' de '\< genericproceduresignature \>'. Argumento de tipo inferido do argumento passado ao parâmetro '\< parametername1 \>' está em conflito com o argumento de tipo inferido do argumento passado ao parâmetro '\< parametername2 \>'.  
  
 Um procedimento genérico é chamado sem nenhum argumento de tipo, e a inferência de tipo tentadas produziram um conflito de tipo de dados entre os parâmetros de tipo.  
  
 Normalmente, quando você chama um procedimento genérico, você fornece um argumento de tipo para cada parâmetro de tipo que define o procedimento genérico. Se você não fornecer nenhum argumento de tipo, o compilador tenta inferir os tipos a serem passados para os parâmetros de tipo. Se o contexto da chamada fornece conflitantes informações tipo de dados para um parâmetro de tipo, a inferência de tipo falhará.  
  
 O código a seguir pode gerar esse erro.  
  
```  
Public Sub takeTwoValues(Of t)(ByVal x As t, ByVal y As t) End Sub Call takeTwoValues(4, 2.5)  
```  
  
 Como o primeiro argumento faz com que o compilador inferir `Integer` para o parâmetro de tipo `t`, enquanto o segundo argumento o leva a inferir `Double` para o mesmo parâmetro de tipo, há um conflito sobre qual tipo de dados para passar para `t`.  
  
 **ID do erro:** BC32116  
  
### Para corrigir este erro  
  
-   Forneça os argumentos de tipo para o tipo genérico, de modo que o compilador não precise inferi\-los.  
  
    ```  
    Call takeTwoValues(Of Double)(4, 2.5)  
    ```  
  
     Observe que neste caso, quando dois argumentos normais são tipos de dados diferentes, o código de chamada deve passar um argumento de tipo que possa acomodar ambos os tipos de dados. Nesse caso, `Integer` amplia a `Double`.  
  
     \- ou \-  
  
-   Redefina o procedimento genérico para especificar parâmetros de tipo diferente para os parâmetros normais, para que não haja conflitos inferindo os tipos.  
  
    ```  
    Public Sub takeTwoValues(Of t1, t2)(ByVal x As t1, ByVal y As t2)  
    ```  
  
## Consulte também  
 [Tipos genéricos no Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)   
 [Procedimentos genéricos no Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-procedures)   
 [Lista de tipos](/dotnet/visual-basic/language-reference/statements/type-list)