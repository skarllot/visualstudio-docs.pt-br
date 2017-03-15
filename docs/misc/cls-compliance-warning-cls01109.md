---
title: "CLS01109 de aviso de conformidade CLS | Microsoft Docs"
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
  - "CLS01109"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CLS01109"
ms.assetid: 5bfd6fcf-95bb-4f13-8090-5303eebb3c06
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "douge"
---
# CLS01109 de aviso de conformidade CLS
Todos os tipos que aparecem em uma assinatura deverão ser compatível com CLS  
  
 Certifique\-se de que todos os tipos que aparecem em uma assinatura de função de membro são compatíveis com CLS.  
  
 O exemplo a seguir gera CLS01109:  
  
```  
// CLS01109.cpp // compile with: /clr /c [assembly:System::CLSCompliant(true)]; [System::CLSCompliant(false)] public ref class NotCompliantType {}; public ref class MyClass { public: property array< NotCompliantType^ >^ SomeProperty {   // CLS01109 array< NotCompliantType^ >^ get() { return nullptr; } void set(array< NotCompliantType^ >^ v ) { } } };  
```  
  
 Resolução possível:  
  
```  
// CLS01109b.cpp // compile with: /clr /LD [assembly:System::CLSCompliant(true)]; public ref class CompliantType {}; public ref class MyClass { public: property array< CompliantType^ >^ SomeProperty { array< CompliantType^ >^ get() { return nullptr; } void set(array< CompliantType^ >^ v ) { } } };  
```