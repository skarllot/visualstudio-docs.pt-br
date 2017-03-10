---
title: "Vari&#225;vel est&#225;tica &#39;&lt; variablename &gt;&#39; declarada sem uma cl&#225;usula &#39;As&#39;; tipo de &#39;Object&#39; assumido | Microsoft Docs"
ms.custom: ""
ms.date: "11/23/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc42111"
  - "bc42111"
helpviewer_keywords: 
  - "BC42111"
ms.assetid: ca6b625c-21a5-45f7-ac67-282f6993a724
caps.latest.revision: 15
caps.handback.revision: 15
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Vari&#225;vel est&#225;tica &#39;&lt; variablename &gt;&#39; declarada sem uma cl&#225;usula &#39;As&#39;; tipo de &#39;Object&#39; assumido
O compilador não inferir o tipo de dados de variáveis locais estáticas. No exemplo a seguir, com `Option Strict` definido como `Off`, o tipo de `m` será `Object`, independentemente de `Option Infer` é definido como `On` ou `Off`. Não se aplicam a inferência de tipo local.  
  
```  
Sub Main() Static m = 10 End Sub  
```  
  
 Por padrão, essa mensagem é um aviso. Para obter informações sobre como ocultar avisos ou tratar avisos como erros, consulte [Configurando avisos no Visual Basic](../ide/configuring-warnings-in-visual-basic.md).  
  
 **ID do erro:** BC42111  
  
### Para resolver este aviso  
  
-   Especifique o tipo de dados para as variáveis locais estáticas.  
  
     Por exemplo, se você quiser `m` no exemplo anterior para ser do tipo `Integer`, especifique o tipo na declaração.  
  
    ```  
    Sub Main() Static m As Integer = 10 End Sub  
  
    ```  
  
## Consulte também  
 [Instrução Dim](/dotnet/visual-basic/language-reference/statements/dim-statement)   
 [NOTINBUILD como: aumentar o tempo de vida da variável](http://msdn.microsoft.com/pt-br/04e7c56c-1db0-4fe5-a678-859a39ec654b)   
 [Inferência de tipo local](/dotnet/visual-basic/programming-guide/language-features/variables/local-type-inference)   
 [Instrução Option Infer](/dotnet/visual-basic/language-reference/statements/option-infer-statement)   
 [Estático](/dotnet/visual-basic/language-reference/modifiers/static)