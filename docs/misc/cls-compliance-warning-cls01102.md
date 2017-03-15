---
title: "CLS01102 de aviso de conformidade CLS | Microsoft Docs"
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
  - "CLS01102"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CLS01102"
ms.assetid: 49426c42-9d01-49ba-b061-ca0e8bd6782d
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "douge"
---
# CLS01102 de aviso de conformidade CLS
Todos os tipos que aparecem em uma assinatura deverão ser compatível com CLS  
  
 Se um evento é compatível com CLS, todos os tipos usados no caso de funções de acesso, a menos que marcar não CLS, devem ser tipos compatíveis com CLS.  
  
 Para mais informações sobre conformidade verificação CLS, consulte [Assemblies compatíveis com CLS](http://msdn.microsoft.com/pt-br/3320b57e-ea55-4697-a17d-f509a36a3c93).  
  
```  
// CLS01102.cpp // compile with: /clr /LD // CLS01102 expected using namespace System; using namespace System::Reflection; [assembly:CLSCompliant (true)]; [assembly:AssemblyKeyFile("clscompliance.snk")]; // Test types [CLSCompliant(true)] public delegate void CompliantType([parameter:CLSCompliant(true)] int parameter); [CLSCompliant(false)] public delegate void NotCompliantType([parameter:CLSCompliant(false)] int parameter); public ref class One { public: event NotCompliantType^ MyEvent { public: void add(NotCompliantType^ Addparameter) {} void remove(NotCompliantType^ Removeparameter) {} void raise([parameter:CLSCompliant(false)] int parameter) {} } };  
```