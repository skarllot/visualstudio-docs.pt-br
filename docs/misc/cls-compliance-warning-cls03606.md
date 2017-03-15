---
title: "CLS03606 de aviso de conformidade CLS | Microsoft Docs"
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
  - "CLS03606"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CLS03606"
ms.assetid: 567b0b18-7487-4f48-a9ae-a4a4db53a409
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "douge"
---
# CLS03606 de aviso de conformidade CLS
Métodos estáticos globais não são compatíveis com CLS  
  
 Métodos e campos estáticos globais não são compatíveis com CLS.  
  
 Para mais informações sobre o subconjunto de linguagem comum \(CLS\) verificação de compatibilidade, consulte [Assemblies compatíveis com CLS](http://msdn.microsoft.com/pt-br/3320b57e-ea55-4697-a17d-f509a36a3c93).  
  
 O exemplo a seguir gera CLS03606:  
  
```  
// CLS03606.cpp // compile with: /clr /LD // CLS03606 expected using namespace System; using namespace System::Reflection; [assembly:CLSCompliant (true)]; [assembly:AssemblyKeyFile("clscompliance.snk")]; void MyGlobalFunction1() {}   // CLS03606 public ref class MyClass { public: void MemberFunction() {}   // OK };  
```