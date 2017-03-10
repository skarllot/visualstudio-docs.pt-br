---
title: "CLS01202 de aviso de conformidade CLS | Microsoft Docs"
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
  - "CLS01202"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CLS01202"
ms.assetid: ab75e9c4-9d87-4bb4-ad8f-3e6ab5559de7
caps.latest.revision: 10
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "douge"
---
# CLS01202 de aviso de conformidade CLS
A visibilidade e a acessibilidade de tipos e membros deverão ser desses tipos na assinatura de qualquer membro deverão ser visíveis e acessíveis sempre que o próprio membro estiver visível e acessível. Por exemplo, um evento público é visível fora do assembly não terá um argumento cujo tipo é visível somente dentro do assembly.  
  
 O tipo de um manipulador de eventos deve ter uma acessibilidade é maior que ou igual a acessibilidade do manipulador de eventos.  
  
 Para mais informações sobre conformidade verificação CLS, consulte [Assemblies compatíveis com CLS](http://msdn.microsoft.com/pt-br/3320b57e-ea55-4697-a17d-f509a36a3c93).  
  
 O exemplo a seguir gera CLS01202:  
  
```  
/* CLS01202.cpp */ // compile with: /clr /LD // CLS01202 expected using namespace System; using namespace System::Reflection; [assembly:CLSCompliant (true)]; [assembly:AssemblyKeyFile("clscompliance.snk")]; public delegate void MyPublicDelegate(); private delegate void MyAssemblyDelegate(); public ref class One { public: event MyAssemblyDelegate^ MyEvent { public: void add(MyAssemblyDelegate^ Addparameter) {}   //  not cls compliant void remove(MyAssemblyDelegate^ Removeparameter) {}   //  not cls compliant void raise() {} } };  
```