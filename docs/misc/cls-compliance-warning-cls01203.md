---
title: "CLS01203 de aviso de conformidade CLS | Microsoft Docs"
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
  - "CLS01203"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CLS01203"
ms.assetid: fe27463a-27df-473b-985a-b04c3bfac4d3
caps.latest.revision: 10
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "douge"
---
# CLS01203 de aviso de conformidade CLS
A visibilidade e a acessibilidade de tipos e membros deverão ser desses tipos na assinatura de qualquer membro deverão ser visíveis e acessíveis sempre que o próprio membro estiver visível e acessível. Por exemplo, um campo público que é visível fora do assembly não deve ser de um tipo que é visível somente dentro do assembly.  
  
 A visibilidade e a acessibilidade de tipos e membros deverão ser desses tipos na assinatura de qualquer membro deverão ser visíveis e acessíveis sempre que o próprio membro estiver visível e acessível. Por exemplo, um campo público que é visível fora do assembly não deve ser de um tipo que é visível somente dentro do assembly.  
  
 Para mais informações sobre conformidade verificação CLS, consulte [Assemblies compatíveis com CLS](http://msdn.microsoft.com/pt-br/3320b57e-ea55-4697-a17d-f509a36a3c93).  
  
 O exemplo a seguir gera CLS01203:  
  
```  
/* CLS01203.cpp */ // compile with: /clr /LD // CLS01203 expected using namespace System; using namespace System::Reflection; [assembly:CLSCompliant (true)]; [assembly:AssemblyKeyFile("clscompliance.snk")]; public ref class PublicLevelType {}; private ref class AssemblyLevelType {}; public ref class One { public: AssemblyLevelType^ Member1;   // not cls compliant PublicLevelType^ Member2;   // cls compliant };  
```