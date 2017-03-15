---
title: "CLS03506 de aviso de conformidade CLS | Microsoft Docs"
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
  - "CLS03506"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CLS03506"
ms.assetid: baec820c-aabb-44c4-b0cd-043c3ca9c537
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "douge"
---
# CLS03506 de aviso de conformidade CLS
**A CLS não permite modificadores obrigatórios visíveis publicamente \(modreq\), mas permite modificadores opcionais \(modopt\) não entendem**  
  
 A CLS não permite modificadores obrigatórios visíveis publicamente \(modreq\), mas permite modificadores opcionais \(modopt\) não entendem.  
  
 Certifique\-se de que as assinaturas de método não contêm tipos marcados com modificadores obrigatórios visíveis publicamente.  
  
 Para mais informações sobre o subconjunto de linguagem comum \(CLS\) verificação de compatibilidade, consulte [Assemblies compatíveis com CLS](http://msdn.microsoft.com/pt-br/3320b57e-ea55-4697-a17d-f509a36a3c93).  
  
 O exemplo a seguir gera CLS03506:  
  
```  
// CLS03506.cpp // compile with: /clr /LD // CLS03506 expected using namespace System; using namespace System::Reflection; using namespace cli::language; [assembly:CLSCompliant (true)]; [assembly:AssemblyKeyFile("clscompliance.snk")]; public ref class One { public: void F1(volatile Int32 parameter) {}   // CLS03506 void F2( Int32 parameter) {}   // OK };  
```