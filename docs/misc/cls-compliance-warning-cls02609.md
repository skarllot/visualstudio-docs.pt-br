---
title: "CLS02609 de aviso de conformidade CLS | Microsoft Docs"
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
  - "CLS02609"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CLS02609"
ms.assetid: ea1afa9a-03d2-4417-af14-68e3b03a858f
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "douge"
---
# CLS02609 de aviso de conformidade CLS
Uma propriedade e seus acessadores devem ser todos estáticos, virtuais ou instância  
  
 Uma propriedade e seus acessadores deverão não diferem em seu estático, virtual, ou qualificadores de instância.  
  
 Para mais informações sobre conformidade verificação CLS, consulte [Assemblies compatíveis com CLS](http://msdn.microsoft.com/pt-br/3320b57e-ea55-4697-a17d-f509a36a3c93).  
  
 O exemplo a seguir gera CLS02609:  
  
```  
// CLS02609.cpp // compile with: /clr /LD // CLS02609 expected using namespace System; using namespace System::Reflection; [assembly:CLSCompliant (true)]; [assembly:AssemblyKeyFile("clscompliance.snk")]; public ref class One { private: int InstanceMember; static int StaticMember; public: property int MyProperty1 {   // CLS02609 public: void set(int value) {} static int get() { return StaticMember; } } property int MyProperty2 {   // OK public: void set(int value) {} int get() { return StaticMember; } } };  
```