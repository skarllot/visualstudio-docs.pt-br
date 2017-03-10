---
title: "Operador de contexto (C++) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.operators"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "expressões [C++], o depurador nativo"
  - "avaliação"
  - "especificadores de formato, expressões"
  - "operador de contexto, em expressões"
  - "depuração [C++], expressões"
  - "avaliador de expressão nativa"
ms.assetid: 73cc9afe-f4a4-474e-bb89-5a33fb5e570c
caps.latest.revision: 23
caps.handback.revision: 23
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Operador de contexto (C++)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Você pode usar o operador de contexto em C\+\+ para qualificar um local de ponto de interrupção, nome de variável ou expressão. O operador de contexto é útil para especificar um nome de um escopo externo que está oculto por um nome local.  
  
##  <a name="BKMK_Using_context_operators_to_specify_a_symbol"></a> Sintaxe  
 Há duas maneiras de especificar o contexto:  
  
1.  {, \[*módulo*\]} *expressão*  
  
     As chaves devem conter duas vírgulas e o módulo \(executável ou DLL\) nome ou o caminho completo.  
  
     Por exemplo, para definir um ponto de interrupção no `SomeFunction` função de example. dll:  
  
    ```cpp  
    {,,EXAMPLE.dll}SomeFunction  
    ```  
  
2.  *module*\!*expressão*  
  
    ```cpp  
    EXAMPLE.dll!SomeFunction  
    ```  
  
-   *módulo* é o nome de um módulo. Você pode usar um caminho completo para resolver a ambiguidade entre módulos com o mesmo nome.  
  
     Se o *módulo* caminho inclui uma vírgula, um espaço inserido ou uma chave, você deve usar o caminho entre aspas para que o analisador de contexto possa reconhecer corretamente a cadeia de caracteres. Aspas simples são consideradas parte de um nome de arquivo do Windows, você deve usar aspas duplas. Por exemplo,  
  
    ```  
    {,"a long, long, library name.dll", } g_Var  
    ```  
  
-   *expressão* é qualquer expressão C\+\+ válida que resolve para um destino válido, como um nome de função, o nome de variável ou o endereço do ponteiro no *módulo*.  
  
 Quando o avaliador da expressão encontra um símbolo em uma expressão, ele procura o símbolo na seguinte ordem:  
  
1.  Escopo léxico para fora, começando com o bloco atual, série de instruções entre chaves e continuando para fora com o bloco delimitador. O bloco atual é o código que contém o local atual, endereço do ponteiro de instrução.  
  
2.  Escopo da função. A função atual.  
  
3.  Escopo de classe, se o local atual estiver dentro de uma função de membro C\+\+. Escopo de classe inclui todas as classes base. O avaliador de expressão usa as regras de precedência normais.  
  
4.  Símbolos globais no módulo atual.  
  
5.  Símbolos públicos no programa atual.