---
title: "Uso de memória com eficiência ao compilar projetos grandes | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- memory use (MSBuild)
- msbuild, efficient memory use building large trees
- caching (MSBuild)
ms.assetid: 853a21ed-69f7-4817-af00-57f73e2c74b5
caps.latest.revision: 11
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Human Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 2241a4d8de1ca946c5420d977510ac5bbefd75ec
ms.lasthandoff: 02/22/2017

---
# <a name="using-memory-efficiently-when-you-build-large-projects"></a>Usando memória com eficiência ao compilar projetos grandes
Projetos grandes geralmente contêm diversos subprojetos e outras dependências que podem consumir muita memória do sistema no momento da compilação. Quando a memória disponível no sistema é reduzida, o desempenho do sistema também pode diminuir. As versões mais antigas dos projetos [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] que permanecem na memória ou os projetos que foram removidos da versão 3.5, mas que ainda mantêm resultados da compilação em um cache para que possam ser recuperados posteriormente.  
  
 A versão 4.0 manipula esse gerenciamento de memória automaticamente, evitando que projetos usem propriedades como `UnloadProjectsOnCompletion` e `UseResultsCache`.  
  
## <a name="see-also"></a>Consulte também  
 [Compilando Vários Projetos Paralelamente](../msbuild/building-multiple-projects-in-parallel-with-msbuild.md)
