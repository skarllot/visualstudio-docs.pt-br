---
title: "CLS01211 de aviso de conformidade CLS | Microsoft Docs"
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
  - "CLS01211"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CLS01211"
ms.assetid: a6df4b7a-81e8-4e77-90d1-ec1cc3a759f5
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "douge"
---
# CLS01211 de aviso de conformidade CLS
A visibilidade e a acessibilidade de tipos e membros deverão ser desses tipos na assinatura de qualquer membro deverão ser visíveis e acessíveis sempre que o próprio membro estiver visível e acessível. Por exemplo, um tipo que é visível fora do assembly não deve ter um tipo base que é visível somente dentro do assembly.  
  
 Tipos e interfaces herdadas ou implementado por um tipo \(A\) deve ter acessibilidade maior ou igual do tipo.  Por exemplo, um método público que é visível fora do assembly não terá um argumento cujo tipo é visível somente dentro do assembly.  
  
 Para mais informações sobre conformidade verificação CLS, consulte [Assemblies compatíveis com CLS](http://msdn.microsoft.com/pt-br/3320b57e-ea55-4697-a17d-f509a36a3c93).  
  
 O exemplo a seguir gera CLS01211:  
  
```  
// CLS01211.cpp // compile with: /clr /LD // CLS01211 expected using namespace System; using namespace System::Reflection; [assembly:CLSCompliant (true)]; [assembly:AssemblyKeyFile("clscompliance.snk")]; private interface class I {}; public interface class I2 : public I {};  
```