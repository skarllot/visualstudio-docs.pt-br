---
title: "CLS03514 de aviso de conformidade CLS | Microsoft Docs"
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
  - "CLS03514"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CLS03514"
ms.assetid: b2d326ce-8c1b-4351-80d1-ccd1818b1ea3
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "douge"
---
# CLS03514 de aviso de conformidade CLS
A CLS não permite modificadores obrigatórios visíveis publicamente \(modreq\), mas permite modificadores opcionais \(modopt\) não entendem  
  
 A CLS não permite modificadores obrigatórios visíveis publicamente \(modreq\), mas permite modificadores opcionais \(modopt\) não entendem.  
  
 Certifique\-se de que as assinaturas de delegado não contêm tipos marcados com modificadores obrigatórios visíveis publicamente.  
  
 Para mais informações sobre o subconjunto de linguagem comum \(CLS\) verificação de compatibilidade, consulte [Assemblies compatíveis com CLS](http://msdn.microsoft.com/pt-br/3320b57e-ea55-4697-a17d-f509a36a3c93).  
  
 O exemplo a seguir gera CLS03514:  
  
```  
// CLS03514.cpp // compile with: /clr /LD // CLS03514 expected using namespace System; using namespace System::Reflection; using namespace cli::language; [assembly:CLSCompliant (true)]; [assembly:AssemblyKeyFile("clscompliance.snk")]; public delegate void MyDel(volatile Int32 param);   // CLS03514 public delegate void MyDel2(Int32 param);   // OK  
```