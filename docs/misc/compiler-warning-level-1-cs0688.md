---
title: "Compilador CS0688 de aviso (n&#237;vel 1) | Microsoft Docs"
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
  - "CS0688"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0688"
ms.assetid: 8ce5af36-663e-46e8-87e9-bb32555796ae
caps.latest.revision: 9
caps.handback.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilador CS0688 de aviso (n&#237;vel 1)
'method1' exige um link, mas substitui ou implementa 'method2' que não tem uma demanda de link. Pode haver uma falha de segurança.  
  
 A demanda de link configurar no método da classe derivada pode facilmente ser evitada chamando o método da classe base. Para fechar a brecha de segurança, o método da classe base precisa usar também a demanda de link. Para obter mais informações, consulte [exigem versus LinkDemand](http://msdn.microsoft.com/pt-br/1ab877f2-70f4-4e0d-8116-943999dfe8f5).  
  
## Exemplo  
 O exemplo a seguir gera CS0688. Para resolver o aviso sem modificar a classe base, remova o atributo de segurança substituindo o método. Isso não resolverá o problema de segurança.  
  
```  
// CS0688.cs // compile with: /W:1 using System; using System.Security.Permissions; class Base { //Uncomment the following line to close the security hole //[FileIOPermission(SecurityAction.LinkDemand, All=@"C:\\")] public virtual void DoScaryFileStuff() { } } class Derived: Base { [FileIOPermission(SecurityAction.LinkDemand, All=@"C:\\")] // CS0688 public override void DoScaryFileStuff() { } static void Main() { } }  
```