---
title: "CLS01206 de aviso de conformidade CLS | Microsoft Docs"
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
  - "CLS01206"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CLS01206"
ms.assetid: e72f2293-874b-406c-9f22-92aeb64ac732
caps.latest.revision: 10
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "douge"
---
# CLS01206 de aviso de conformidade CLS
A visibilidade e a acessibilidade de tipos e membros deverão ser desses tipos na assinatura de qualquer membro deverão ser visíveis e acessíveis sempre que o próprio membro estiver visível e acessível. Por exemplo, uma função de membro público que é visível fora do assembly não deve ter um argumento cujo tipo é visível somente dentro do assembly.  
  
 Tipos de assinaturas de método devem ter acessibilidade maior ou igual do método.  Por exemplo, um método público que é visível fora do assembly não terá um argumento cujo tipo é visível somente dentro do assembly.  
  
 Para mais informações sobre conformidade verificação CLS, consulte [Assemblies compatíveis com CLS](http://msdn.microsoft.com/pt-br/3320b57e-ea55-4697-a17d-f509a36a3c93).  
  
 O exemplo a seguir gera CLS01206:  
  
```  
/* CLS01206.cpp */ // compile with: /clr /LD // CLS01206 expected using namespace System; using namespace System::Reflection; [assembly:CLSCompliant (true)]; [assembly:AssemblyKeyFile("clscompliance.snk")]; public ref class PublicLevelType {}; private ref class AssemblyLevelType {}; public ref class One { public: AssemblyLevelType^ Method1() { return gcnew AssemblyLevelType(); } };  
```