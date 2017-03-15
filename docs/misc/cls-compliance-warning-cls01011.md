---
title: "CLS01011 de aviso de conformidade CLS | Microsoft Docs"
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
  - "CLS01011"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CLS01011"
ms.assetid: e4141e15-14fd-491c-9639-f3f3a47d7865
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "douge"
---
# CLS01011 de aviso de conformidade CLS
Acessibilidade não deverá ser alterada quando substituir métodos herdados  
  
 Certifique\-se de que o método de substituição tem a mesma visibilidade que o método que ele substitui.  Acessibilidade não deverá ser alterada quando substituindo métodos, exceto quando substituir um método herdado de um assembly diferente com acessibilidade família ou Assembly herdados. Nesse caso, a substituição deverá ter acessibilidade da família.  
  
 Para mais informações sobre conformidade verificação CLS, consulte [Assemblies compatíveis com CLS](http://msdn.microsoft.com/pt-br/3320b57e-ea55-4697-a17d-f509a36a3c93).  
  
 O exemplo a seguir gera CLS01011:  
  
```  
// CLS01011.cpp // compile with: /clr /LD // CLS01011 expected using namespace System; using namespace System::Reflection; using namespace cli::language; [assembly:CLSCompliant (true)]; [assembly:AssemblyKeyFile("clscompliance.snk")]; public ref class BaseType { public protected: virtual void BaseTypeMethod() {} }; public ref class One : public BaseType { public: void BaseTypeMethod() {}   // CLS01011 // OK // public protected: //    void BaseTypeMethod() {} };  
```