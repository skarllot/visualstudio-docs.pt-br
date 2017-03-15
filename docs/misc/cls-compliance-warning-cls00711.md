---
title: "CLS00711 de aviso de conformidade CLS | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CLS00711"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CLS00711"
ms.assetid: 76481641-bda1-4128-8da8-ccba577b7ba1
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "douge"
---
# CLS00711 de aviso de conformidade CLS
O tipo subjacente de um enum deve ser um tipo de inteiro CLS interno  
  
 Se você especificar o tipo subjacente de uma enumeração, e se você quiser um assembly compatível com CLS, o tipo subjacente da enumeração deve ser um tipo de inteiro compatível, o subconjunto de linguagem comum \(CLS\).  
  
 Para obter mais informações sobre enums CLR, consulte [classe enum](/visual-cpp/windows/enum-class-cpp-component-extensions).  
  
 Para mais informações sobre conformidade verificação CLS, consulte [Assemblies compatíveis com CLS](http://msdn.microsoft.com/pt-br/3320b57e-ea55-4697-a17d-f509a36a3c93).  
  
 O exemplo a seguir gera CLS00711:  
  
```  
// CLS00711.cpp // compile with: /clr /LD // CLS00711 expected using namespace System; using namespace System::Reflection; [assembly:CLSCompliant (true)]; [assembly:AssemblyKeyFile("clscompliance.snk")]; public ref class One { public: enum class MyEnum_cls_bad : Char { bad_one = 1, bad_two = 2, bad_three = 3 }; enum class MyEnum_cls_good : Int32 { good_one = 1, good_two = 2, good_three = 3 }; };  
```