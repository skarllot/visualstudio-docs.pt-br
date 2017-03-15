---
title: "Solucionando problemas do IntelliSense em projetos do C++ | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
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
  - "arquivos. NCB"
  - "arquivos ncb"
  - "IntelliSense, solução de problemas em projetos do C++"
  - "solucionando problemas do IntelliSense"
  - "Solucionando problemas do Visual C++, IntelliSense"
ms.assetid: 72e4eb39-66d3-403d-8da7-00ed288a1899
caps.latest.revision: 20
caps.handback.revision: 20
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Solucionando problemas do IntelliSense em projetos do C++
O IntelliSense pode parar de funcionar em certas condições. Use as etapas a seguir para ajudar a determinar por que o IntelliSense não funciona para projetos do C\+\+.  
  
### Investigue a falha do IntelliSense em projetos do C\+\+  
  
1.  Verifique se o projeto do Visual C\+\+ não contém nenhum erro de compilação.  
  
    1.  Se o projeto é um projeto Makefile, consulte [Como habilitar o IntelliSense para projetos de makefile](../Topic/How%20to:%20Enable%20IntelliSense%20for%20Makefile%20Projects.md).  
  
2.  Certifique\-se de que Stdafx. h está no caminho de inclusão. Para obter mais informações sobre caminhos de inclusão em projetos do Visual C\+\+, consulte [Diretiva \#include](/visual-cpp/preprocessor/hash-include-directive-c-cpp) e [\/I \(diretórios de inclusão adicionais\)](/visual-cpp/build/reference/i-additional-include-directories).  
  
## Limitações do IntelliSense  
 O IntelliSense não funciona em projetos do C\+\+ nas seguintes circunstâncias:  
  
-   O cursor estiver em um comentário do código.  
  
-   Você está criando uma cadeia de caracteres literal.  
  
-   Um erro de sintaxe aparece sobre o cursor.  
  
-   A solução consiste na sintaxe do C\+\+ gerenciado ou extensões gerenciadas anteriores para obter a sintaxe do C\+\+.  
  
-   IntelliSense não tem suporte total ao fazer referência a um arquivo de cabeçalho várias vezes usando o `#include` diretiva e o significado daquele cabeçalho arquivo alterações devido a vários estados de macro que são definidos por meio de `#define` diretiva. Em outras palavras, quando você inclui um arquivo de cabeçalho várias vezes e as alterações de uso de cabeçalho em estados diferentes de macro, IntelliSense nem sempre funcionam.  
  
## Consulte também  
 [Solucionando problemas do IntelliSense](http://msdn.microsoft.com/pt-br/c1b3adb9-0d48-4770-a51e-392ed818c484)   
 [Como organizar arquivos de saída do projeto para compilações](../Topic/How%20to:%20Organize%20Project%20Output%20Files%20for%20Builds.md)