---
title: "CLS03411 de aviso de conformidade CLS | Microsoft Docs"
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
  - "CLS03411"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CLS03411"
ms.assetid: 79b0955a-5a86-46a8-90e9-4419c9068bbe
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "douge"
---
# CLS03411 de aviso de conformidade CLS
A CLS permite apenas um subconjunto das codificações de atributos personalizados  
  
 A CLS permite apenas um subconjunto de tipos como parâmetros para o construtor de um atributos personalizados ou como o tipo de dados de membros de um atributo personalizado. Os únicos tipos que deverão ser exibidos são:  
  
-   System. Type  
  
-   System. String  
  
-   Char  
  
-   System. Boolean  
  
-   Byte  
  
-   Int16  
  
-   System. Int32  
  
-   Int64  
  
-   System. Single  
  
-   System. Double  
  
-   qualquer tipo de enumeração baseado em um tipo base inteiro compatível com CLS.  
  
 Para mais informações sobre o subconjunto de linguagem comum \(CLS\) verificação de compatibilidade, consulte [Assemblies compatíveis com CLS](http://msdn.microsoft.com/pt-br/3320b57e-ea55-4697-a17d-f509a36a3c93).  
  
 O exemplo a seguir gera CLS03411:  
  
```  
// CLS03411.cpp // compile with: /clr /LD // CLS03411 expected using namespace System; using namespace System::Reflection; using namespace cli::language; [assembly:CLSCompliant (true)]; [assembly:AssemblyKeyFile("clscompliance.snk")]; // CLS03411 [AttributeUsage(AttributeTargets::All, AllowMultiple=true)] public ref class MyAttribute1 : public Attribute { public: MyAttribute1(Object^ parameter) {} }; // OK [AttributeUsage(AttributeTargets::All, AllowMultiple=true)] public ref class MyAttribute3 : public Attribute { public: MyAttribute3(Char parameter) {} };  
```