---
title: "Como usar a fun&#231;&#227;o ReadFile do Windows (Guia de Programa&#231;&#227;o em C#) | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "função ReadFile [C#]"
ms.assetid: 46bb53e0-a658-48c9-ae36-6720da7781c1
caps.latest.revision: 18
caps.handback.revision: 18
ms.author: "billchi"
manager: "douge"
---
# Como usar a fun&#231;&#227;o ReadFile do Windows (Guia de Programa&#231;&#227;o em C#)
Este exemplo demonstra o Windows `ReadFile` função lendo e exibindo um arquivo de texto.  O `ReadFile` função requer o uso de `unsafe` código porque ele requer um ponteiro como um parâmetro.  
  
 A matriz de bytes transmitidos para o `Read` função é um tipo gerenciado.  Isso significa que o coletor de lixo do common language runtime \(CLR\) pode realocar a memória usada no array, será.  Para evitar isso,  [fixa](/dotnet/csharp/language-reference/keywords/fixed-statement) é usado para obter um apontador para a memória e marcá\-la para que o coletor de lixo não o moverá.  No final do `fixed` bloco, a memória retorna automaticamente para ficar sujeito a movimentação por meio da coleta de lixo.  
  
 Esse recurso é conhecido como  *a fixação declarativa*.  Com a fixação, há muito pouca sobrecarga, a menos que uma coleta de lixo ocorre na `fixed` block, que é pouco provável.  No entanto, a fixação pode levar a alguns efeitos colaterais indesejáveis durante a coleta de lixo global será executada.  A capacidade do coletor de lixo para compactar memória bastante é limitada por buffers fixados.  Portanto, a fixação deve ser evitada se possível.  
  
## Exemplo  
 [!code-cs[csProgGuidePointers#2](../misc/codesnippet/CSharp/how-to-use-the-windows-readfile-function-csharp-programming-guide_1.cs)]  
  
## Consulte também  
 [Guia de Programação em C\#](/dotnet/csharp/programming-guide/index)   
 [Referência de C\#](/dotnet/csharp/language-reference/index)   
 [Código não seguro e ponteiros](/dotnet/csharp/programming-guide/unsafe-code-pointers/index)   
 [Tipos de ponteiro](/dotnet/csharp/programming-guide/unsafe-code-pointers/pointer-types)   
 [Garbage Collection](../Topic/Garbage%20Collection.md)