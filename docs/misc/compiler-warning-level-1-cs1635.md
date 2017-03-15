---
title: "Compilador CS1635 de aviso (n&#237;vel 1) | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS1635"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1635"
ms.assetid: e1795880-f7ea-4dca-b15b-4ba549d7ed78
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilador CS1635 de aviso (n&#237;vel 1)
Não é possível restaurar o aviso 'código de aviso' porque ele foi desabilitado globalmente  
  
 Este aviso ocorre se você usar o **\/nowarn** projeto configuração para desabilitar um aviso para a unidade de compilação inteiro ou opção de linha de comando, mas usar `#pragma warning restore` para tentar restaurar esse aviso. Para resolver esse erro, remova a opção de linha de comando \/nowarn ou a configuração de projeto, ou remova o `#pragma warning restore` há avisos que você está desativando por meio da linha de comando ou as configurações do projeto. Para obter mais informações, consulte o [\#pragma aviso](/dotnet/csharp/language-reference/preprocessor-directives/preprocessor-pragma-warning) tópico.  
  
 O exemplo a seguir gera CS1635:  
  
```  
// CS1635.cs // compile with: /w:1 /nowarn:162 enum MyEnum {one=1,two=2,three=3}; class MyClass { public static void Main() { #pragma warning disable 162 if (MyEnum.three == MyEnum.two) System.Console.WriteLine("Duplicate"); #pragma warning restore 162 } }  
```