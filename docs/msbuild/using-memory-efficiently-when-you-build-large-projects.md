---
title: "Usando mem&#243;ria com efici&#234;ncia ao compilar projetos grandes | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "cache (MSBuild)"
  - "uso da memória (MSBuild)"
  - "msbuild, uso eficiente da memória compilando árvores grandes"
ms.assetid: 853a21ed-69f7-4817-af00-57f73e2c74b5
caps.latest.revision: 11
caps.handback.revision: 11
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Usando mem&#243;ria com efici&#234;ncia ao compilar projetos grandes
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Projetos grandes costumam contenham vários subprojetos e outras dependências e eles podem consumir muita memória do sistema em tempo de compilação.  Quando a memória disponível no sistema é reduzida, também pode diminuir o desempenho do sistema.  Versões mais antigas do [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] projetos permanecem na memória ou na versão 3.5, os projetos foram removidos, mas ele mantido resultados de compilação em um cache para recuperação posterior.  
  
 Versão 4.0 manipula o gerenciamento de memória automaticamente, salvando projetos de ter que usar propriedades, como `UnloadProjectsOnCompletion` e `UseResultsCache`.  
  
## Consulte também  
 [Criando vários projetos paralelamente](../msbuild/building-multiple-projects-in-parallel-with-msbuild.md)