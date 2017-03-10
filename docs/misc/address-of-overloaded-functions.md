---
title: "Endere&#231;o de fun&#231;&#245;es sobrecarregadas | Microsoft Docs"
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
  - "funções de endereços [C++], sobrecarregados"
  - "endereços [C++], retornando sobrecarregado"
  - "função sobrecarga, o endereço da função"
  - "esse ponteiro, funções sobrecarregadas"
ms.assetid: e7913e65-a295-445d-b2b0-1e60f8dfbc54
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Endere&#231;o de fun&#231;&#245;es sobrecarregadas
Uso de um nome de função sem argumentos retorna o endereço dessa função. Por exemplo:  
  
```  
int Func( int i, int j );  
int Func( long l );  
  
...  
  
int (*pFunc) ( int, int ) = Func;  
```  
  
 No exemplo anterior, a primeira versão do `Func` estiver selecionada, e seu endereço é copiado para `pFunc`.  
  
 O compilador determina qual versão da função será selecionada localizando uma função com uma lista de argumentos que corresponda exatamente ao destino. Os argumentos em declarações de função sobrecarregadas são comparados com um dos seguintes:  
  
-   Um objeto que está sendo inicializado \(conforme mostrado no exemplo anterior\)  
  
-   O lado esquerdo de uma instrução de atribuição  
  
-   Um argumento formal a uma função  
  
-   Um argumento formal a um operador definido pelo usuário  
  
-   Um tipo de retorno de função  
  
 Se nenhuma correspondência exata for encontrada, a expressão que usa o endereço da função é ambígua e um erro será gerado.  
  
 Observe que, embora uma função não\-membro, `Func`, foi usada no exemplo anterior, as mesmas regras são aplicadas quando usar o endereço de funções de membro sobrecarregadas.  
  
## Consulte também  
 [Sobrecarga \(C\+\+\)](../misc/overloading-cpp.md)