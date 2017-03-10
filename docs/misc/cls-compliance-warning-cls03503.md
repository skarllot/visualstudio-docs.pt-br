---
title: "CLS03503 de aviso de conformidade CLS | Microsoft Docs"
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
  - "CLS03503"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CLS03503"
ms.assetid: 2d2e78db-5fcf-47e1-af1e-9545f28a306b
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "douge"
---
# CLS03503 de aviso de conformidade CLS
A CLS não permite modificadores obrigatórios visíveis publicamente \(modreq\), mas permite modificadores opcionais \(modopt\) não entendem  
  
 A CLS não permite modificadores obrigatórios visíveis publicamente \(modreq\), mas permite modificadores opcionais \(modopt\) não entendem.  
  
 Certifique\-se de que os campos não contêm tipos marcados com modificadores obrigatórios visíveis publicamente.  
  
 Para mais informações sobre o subconjunto de linguagem comum \(CLS\) verificação de compatibilidade, consulte [Assemblies compatíveis com CLS](http://msdn.microsoft.com/pt-br/3320b57e-ea55-4697-a17d-f509a36a3c93).  
  
 O exemplo a seguir gera CLS03503:  
  
```  
// CLS03503.cpp // compile with: /clr /LD // CLS03503 expected using namespace System; using namespace System::Reflection; using namespace cli::language; [assembly:CLSCompliant (true)]; [assembly:AssemblyKeyFile("clscompliance.snk")]; public ref class MyClass { public: volatile Int32 param;   // CLS03503 Int32 param2;   // OK };  
```