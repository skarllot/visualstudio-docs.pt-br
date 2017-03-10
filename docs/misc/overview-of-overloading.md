---
title: "Vis&#227;o geral da sobrecarga | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "função sobrecarga sobre sobrecarga de função"
  - "sobrecarga de operador, sobre sobrecarga de operador"
ms.assetid: cd012dd4-607c-4f8e-bd2e-2bd506ac81ea
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Vis&#227;o geral da sobrecarga
Com a linguagem C\+\+, você pode sobrecarregar funções e operadores. Sobrecarga é a prática de fornecer mais de uma definição para um determinado nome de função no mesmo escopo. O compilador é quem escolhe a versão apropriada da função ou operador com base nos argumentos com o qual ele é chamado. Por exemplo, a função max é considerado uma função sobrecarregada. Ele pode ser usado no código como o seguinte:  
  
```  
// overview_overload.cpp  
double max( double d1, double d2 )  
{  
   return ( d1 > d2 ) ? d1 : d2;  
}  
  
int max( int i1, int i2 )  
{  
   return ( i1 > i2 ) ? i1 : i2;  
}  
int main()  
{  
   int    i = max( 12, 8 );  
   double d = max( 32.9, 17.4 );  
}  
```  
  
 Na primeira chamada de função, onde o valor máximo de duas variáveis do tipo `int` está sendo solicitado, a função `max( int, int )` é chamado. No entanto, na segunda chamada de função, os argumentos são do tipo `double`, portanto a função `max( double, double )` é chamado.  
  
## Consulte também  
 [Sobrecarga \(C\+\+\)](../misc/overloading-cpp.md)