---
title: "CS0738 de erro do compilador | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS0738"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0738"
ms.assetid: 01ce94ee-2435-4326-befc-2b020c441a4f
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# CS0738 de erro do compilador
'type name' não implementa membro de interface 'nome do membro'. 'nome do método' não pode implementar membros de interface porque ele não tem a correspondência de tipo do nome do tipo de retorno.  
  
 O valor de retorno de um método em uma classe de implementação deve corresponder ao valor de retorno do membro da interface que ele implementa.  
  
### Para corrigir este erro  
  
1.  Altere o tipo de retorno do método para coincidir com o membro de interface.  
  
## Exemplo  
 O código a seguir gera CS0738 porque o método da classe retorna `void` e retorna o membro de interface de mesmo nome `int`:  
  
```  
using System; interface ITest { int TestMethod(); } public class Test: ITest { public void TestMethod() { } // CS0738 // Try the following line instead. // public int TestMethod(); }  
```  
  
## Consulte também  
 [Interfaces](/dotnet/csharp/programming-guide/interfaces/index)