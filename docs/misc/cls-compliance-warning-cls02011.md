---
title: "CLS02011 de aviso de conformidade CLS | Microsoft Docs"
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
  - "CLS02011"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CLS02011"
ms.assetid: 9466be1e-9558-49e8-9ea4-5cfc54a22066
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "douge"
---
# CLS02011 de aviso de conformidade CLS
Classes compatível com CLS, tipos de valor e interfaces não deverão exigir a implementação das interfaces não compatível com CLS  
  
 Um tipo marcado como compatível com CLS tem um ou mais tipos base que não são compatíveis com CLS.  
  
 Para mais informações sobre conformidade verificação CLS, consulte [Assemblies compatíveis com CLS](http://msdn.microsoft.com/pt-br/3320b57e-ea55-4697-a17d-f509a36a3c93).  
  
 O exemplo a seguir gera CLS02011:  
  
```  
// CLS02011.cpp // compile with: /clr /LD // CLS02011 expected using namespace System; using namespace System::Reflection; [assembly:CLSCompliant (true)]; [assembly:AssemblyKeyFile("clscompliance.snk")]; [CLSCompliant(true)] public interface class CompliantInterface {}; [CLSCompliant(false)] public interface class NotCompliantInterface {}; public ref class One : public NotCompliantInterface {};   // CLS02011 public ref class Two : public CompliantInterface {};   // OK  
```