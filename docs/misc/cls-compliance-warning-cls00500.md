---
title: "CLS00500 de aviso de conformidade CLS | Microsoft Docs"
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
  - "CLS00500"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CLS00500"
ms.assetid: faaf377e-3738-4c0d-9a51-09db4073564e
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "douge"
---
# CLS00500 de aviso de conformidade CLS
Todos os nomes em um escopo compatível com CLS deverão ser independentes distintos de tipo  
  
 Todos os nomes introduzidos em um escopo compatível com CLS deverão ser distinto independente do tipo, exceto onde os nomes são idênticos e resolvidos por meio da sobrecarga. Para fins CLS, dois nomes são os mesmos se os mapeamentos em minúsculas forem iguais. Somente as funções e propriedades podem ser sobrecarregadas. Quando sobrecarregado, funções e propriedades devem ser sobrecarregadas com base apenas no número e tipos de seus parâmetros, exceto os operadores de conversão, que também podem ser sobrecarregados com base no tipo de retorno; consulte [Conversões definidas pelo usuário](/visual-cpp/dotnet/user-defined-conversions-cpp-cli) para obter mais informações.  
  
 Para mais informações sobre conformidade verificação CLS, consulte [Assemblies compatíveis com CLS](http://msdn.microsoft.com/pt-br/3320b57e-ea55-4697-a17d-f509a36a3c93).  
  
 O exemplo a seguir gera CLS00500:  
  
```  
// CLS00500.cpp // compile with: /clr /LD // CLS00500 expected using namespace System; using namespace System::Reflection; [assembly:AssemblyKeyFile("clscompliance.snk")]; [assembly:System::CLSCompliant(true)]; public ref class a {}; public ref class A {};   // CLS00500  
```