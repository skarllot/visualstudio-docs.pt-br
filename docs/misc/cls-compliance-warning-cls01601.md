---
title: "CLS01601 de aviso de conformidade CLS | Microsoft Docs"
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
  - "CLS01601"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CLS01601"
ms.assetid: fa162fc6-a0fd-4a0f-a201-4f166304d057
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "douge"
---
# CLS01601 de aviso de conformidade CLS
As matrizes deverão ter elementos com um tipo compatível com CLS e todas as dimensões da matriz devem ter o limite inferior de zero  
  
 As matrizes deverão ter elementos com um tipo compatível com CLS e todas as dimensões da matriz devem ter o limite inferior de zero. Somente o fato de que um item é uma matriz e o tipo de elemento da matriz será necessário para diferenciar sobrecargas. Quando a sobrecarga se baseia em dois ou mais tipos de matriz de tipos de elemento deverão ser chamados de tipos.  
  
 Para mais informações sobre conformidade verificação CLS, consulte [Assemblies compatíveis com CLS](http://msdn.microsoft.com/pt-br/3320b57e-ea55-4697-a17d-f509a36a3c93).  
  
 O exemplo a seguir gera CLS01601:  
  
```  
// CLS01601.cpp // compile with: /clr /LD // CLS01601 expected using namespace System; using namespace System::Reflection; using namespace cli::language; [assembly:CLSCompliant (true)]; [assembly:AssemblyKeyFile("clscompliance.snk")]; [CLSCompliant(true)] public ref class CompliantType {}; [CLSCompliant(false)] public ref class NotCompliantType {}; public ref class One { public: // CLS01601 One(array<NotCompliantType^>^ param) {} // OK One(array<CompliantType^>^ param) {} };  
```