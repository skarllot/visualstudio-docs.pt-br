---
title: "CS0281 de erro do compilador | Microsoft Docs"
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
  - "CS0281"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0281"
ms.assetid: 3b886510-6e4d-45bc-b885-3ab7f6b6b2c6
caps.latest.revision: 18
caps.handback.revision: 18
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# CS0281 de erro do compilador
Foi concedido acesso de amigo para 'AssemblyName1', mas o assembly de saída é chamado 'AssemblyName2'. Tente adicionar uma referência a 'AssemblyName1' ou alterar o nome do assembly de saída para corresponder.  
  
 Acesso de amigo é um novo recurso common language runtime \(CLR\) que permite que um assembly ver tipos não públicos de outro conjunto. Esse erro ocorre quando o conceder acesso de amigo do assembly Especifica o nome errado para o assembly de usuário autorizado. Para obter mais informações, consulte [Assemblies amigáveis](../Topic/Friend%20Assemblies%20\(C%23%20and%20Visual%20Basic\).md).  
  
## Exemplo  
 A sequência de exemplos de código a seguir irá gerar CS0281.  
  
 Os arquivos usados para criar os conjuntos de alta segurança são gerados da seguinte maneira:  
  
-   sn \-d CS0281.snk  
  
-   sn \-k CS0281.snk  
  
-   sn \-i CS0281.snk CS0281.snk  
  
-   sn \-pc CS0281.snk key.publickey  
  
-   sn \- tp key.publickey  
  
```  
// CS0281.cs // compile with: /target:library /keyfile:CS0281.snk public class A {}  
```  
  
## Exemplo  
  
```  
// CS0281_b.cs // compile with: /target:library /keyfile:CS0281.snk /reference:CS0281.dll [assembly:System.Runtime.CompilerServices.InternalsVisibleTo("CS0281 , PublicKey=00240000048000009400000006020000002400005253413100040000010001004b2d4d56af7c50be2fcbbf97cb880b9e73ad84467a587191fef63aadc118a96cecf9d508cd679c907b6e20f71684300bdc2c0a851019af0c96b29bf8f1339753276041aefd67db46139e6348b3a12f29537b4dc6c2c19829df2c9ed6803f3c63c3b84cfa2728849386aea575c543a5f70fa85793d2946f15f7fe1ccb0c5e8fe0")] class B : A {}  
```  
  
## Exemplo  
 O exemplo a seguir gera CS0281.  
  
 Observe que este exemplo cria um arquivo de saída com o mesmo nome que o arquivo de saída no primeiro exemplo. Para resolver, não altere os atributos de assembly do componente e adicionar classe C.  
  
```  
// CS0281_c.cs // compile with: /target:library /out:CS0281.dll /keyfile:CS0281.snk /reference:CS0281_b.dll // CS0281 expected [assembly:System.Reflection.AssemblyVersion("3")] [assembly:System.Reflection.AssemblyCulture("en-us")] class C : B {} public class A {}  
```