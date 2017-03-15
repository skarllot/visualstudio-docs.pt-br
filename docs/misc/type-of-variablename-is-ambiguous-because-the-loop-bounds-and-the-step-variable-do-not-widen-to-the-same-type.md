---
title: "Tipo de &#39;&lt; variablename &gt;&#39; &#233; amb&#237;guo porque os limites do loop e a vari&#225;vel step n&#227;o se estendem ao mesmo tipo | Microsoft Docs"
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
  - "vbc30983"
  - "bc30983"
helpviewer_keywords: 
  - "BC30983"
ms.assetid: 6b97153c-dee3-4429-b92a-2e5a212c864b
caps.latest.revision: 14
caps.handback.revision: 14
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Tipo de &#39;&lt; variablename &gt;&#39; &#233; amb&#237;guo porque os limites do loop e a vari&#225;vel step n&#227;o se estendem ao mesmo tipo
Seu código contém um `For...Next` loop em que o compilador não pode inferir um tipo de dados para a variável de controle de loop porque as condições a seguir for verdadeira:  
  
-   O tipo de dados da variável de controle de loop não é especificado com um `As` cláusula.  
  
-   Os limites do loop e a variável step contêm pelo menos dois tipos de dados.  
  
-   Existe mais de uma conversão possível entre os tipos de dados.  
  
-   Há um melhor tipo entre os candidatos, para que a escolha do tipo para a variável de controle de loop é ambígua.  
  
 Por exemplo, o seguinte loop possui um limite de tipo `Integer` e um loop associado do tipo `UInteger`:  
  
```vb#  
Dim m As Integer = 1 Dim n As UInteger = 10 ' Not valid. ' For i = m To n ' Loop processing. ' Next  
```  
  
 Há uma conversão possível entre `Integer` e `UInteger`, e uma conversão possível entre `UInteger` e `Integer`, mas ambos são conversões de estreitamento então não é a melhor opção.  
  
 No próximo exemplo, uma terceira variável do tipo `Double` é adicionado. Ambos `Integer` e `UInteger` possuem conversões de expansão padrão para `Double`, que faz a conversão para `Double` a melhor opção. Inferência de tipo atribui à variável de controle de loop `i` o tipo de dados `Double`.  
  
```vb#  
Dim stepVar As Double = 1 ' Valid. For i = m To n Step stepVar ' Loop processing. Next  
```  
  
 **ID do erro:** BC30983  
  
### Para corrigir este erro  
  
-   Converta uma das variáveis explicitamente a um tipo que os outros possuem uma conversão de ampliação, por exemplo:  
  
    ```  
    For i = m To CLng(n)  
    ```  
  
-   Use um `As` cláusula para especificar o tipo da variável de controle:  
  
    ```  
    For i As Double = m To n   
    ```  
  
## Consulte também  
 [Instrução For...Next](/dotnet/visual-basic/language-reference/statements/for-next-statement)   
 [Conversões implícitas e explícitas](/dotnet/visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions)   
 [Inferência de tipo local](/dotnet/visual-basic/programming-guide/language-features/variables/local-type-inference)   
 [Instrução Option Infer](/dotnet/visual-basic/language-reference/statements/option-infer-statement)   
 [Conversões de Widening e Narrowing](/dotnet/visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions)