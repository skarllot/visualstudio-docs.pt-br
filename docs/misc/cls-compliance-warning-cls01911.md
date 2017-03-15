---
title: "CLS01911 de aviso de conformidade CLS | Microsoft Docs"
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
  - "CLS01911"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CLS01911"
ms.assetid: 673a701a-166b-4782-bff4-a198f70becd5
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "douge"
---
# CLS01911 de aviso de conformidade CLS
Interfaces compatíveis com CLS não deverão definir métodos estáticos, nem devem definir campos  
  
 Uma interface compatível com CLS não pode conter campos ou métodos estáticos.  
  
 Para mais informações sobre conformidade verificação CLS, consulte [Assemblies compatíveis com CLS](http://msdn.microsoft.com/pt-br/3320b57e-ea55-4697-a17d-f509a36a3c93).  
  
 O exemplo a seguir gera CLS01911:  
  
```  
// CLS01911.cpp // compile with: /clr /LD // CLS01911 expected using namespace System; using namespace System::Reflection; [assembly:CLSCompliant (true)]; [assembly:AssemblyKeyFile("clscompliance.snk")]; public interface class IOne { static void Method1() {}   // interface static method not cls compliant };  
```