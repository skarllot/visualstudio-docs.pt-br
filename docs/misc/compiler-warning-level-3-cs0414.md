---
title: "Compilador CS0414 de aviso (n&#237;vel 3) | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS0414"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0414"
ms.assetid: 6a0a80be-799b-4d9c-a7e0-6b91e9ce7be0
caps.latest.revision: 11
caps.handback.revision: 11
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilador CS0414 de aviso (n&#237;vel 3)
Campo particular 'field' é atribuído, mas seu valor nunca é usado  
  
 Esse aviso pode ocorrer em vários cenários em que o compilador possa verificar que uma variável não é referenciada:  
  
-   Um campo privado é atribuído um valor constante, mas nunca subsequentemente é lido. A atribuição desnecessária pode afetar a velocidade. Considere a remoção do campo.  
  
-   Um campo estático privado ou interno é atribuído um valor constante apenas no inicializador. Considere alterar o campo para uma constante.  
  
-   Um campo privado ou interno é atribuído a valores constantes e somente usado em blocos que são excluídos por diretivas \#ifdef. Considere colocar o campo dentro do bloco \#ifdef.  
  
-   Um campo privado ou interno é atribuído valores constantes em vários locais, mas não for acessado. Se o campo não é necessário, considere removê\-la. Caso contrário, usá\-lo de alguma maneira apropriada.  
  
 Em outras situações, ou em que a solução alternativa sugerida não é aceitável, use \#pragma 0414.  
  
 O exemplo a seguir mostra uma maneira na qual CS0414 serão gerados:  
  
```  
// CS0414 // compile with: /W3 class C { private int i = 1;  // CS0414 public static void Main() { } }  
```  
  
 **Observação** se a variável `i` é declarado como `protected or public`, nenhum erro será gerado porque o compilador não sabe se uma classe derivada pode usá\-lo ou algum outro código de cliente pode instanciar a classe e fazer referência à variável  
  
## Consulte também  
 [C\# Compiler Errors](/dotnet/csharp/language-reference/compiler-messages/index)   
 [C\# Compiler Options](/dotnet/csharp/language-reference/compiler-options/index)