---
title: "CS0021 de erro do compilador | Microsoft Docs"
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
  - "CS0021"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0021"
ms.assetid: 4eb5fa24-8261-4962-b36a-224be5074217
caps.latest.revision: 14
caps.handback.revision: 14
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# CS0021 de erro do compilador
Não é possível aplicar a indexação com \[\] a uma expressão do tipo 'type'  
  
 Foi feita uma tentativa para acessar um valor por meio de um indexador em um tipo de dados que não oferece suporte a [Indexadores](/dotnet/csharp/programming-guide/indexers/index).  
  
 Você pode receber CS0021 ao tentar usar um indexador em um assembly de C\+\+. Nesse caso, decore a classe do C\+\+ com o `DefaultMember` atributo para que o compilador c\# saiba qual indexador é o padrão. O exemplo a seguir gera CS0021.  
  
## Exemplo  
 Esse arquivo é compilado em um arquivo. dll — com o `DefaultMember` atributo comentadas — para gerar o erro.  
  
```  
// CPP0021.cpp // compile with: /clr /LD using namespace System::Reflection; // Uncomment the following line to resolve //[DefaultMember("myItem")] public ref class MyClassMC { public: property int myItem[int] { int get(int i){  return 5; } void set(int i, int value) {} } };  
```  
  
## Exemplo  
 A seguir está o arquivo c\# que chama o arquivo. dll. Esse arquivo tenta acessar a classe por meio de um indexador, mas porque nenhum membro foi declarado como o indexador padrão a ser usado, o erro é gerado.  
  
```  
// CS0021.cs // compile with: /reference:CPP0021.dll public class MyClass { public static void Main() { MyClassMC myMC = new MyClassMC(); int j = myMC[1]; // CS0021 } }  
```