---
title: "Pr&#225;ticas recomendadas do MSBuild | Microsoft Docs"
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
  - "práticas recomendadas, MSBuild"
  - "MSBuild, práticas recomendadas"
ms.assetid: 90ef8693-e921-410a-a377-fe4d13f58c48
caps.latest.revision: 5
caps.handback.revision: 5
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Pr&#225;ticas recomendadas do MSBuild
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Recomendamos as seguintes práticas recomendadas para escrever scripts MSBuild:  
  
-   Os valores de propriedade padrão são mais facilmente tratados usando o atributo `Condition` e não declarando uma propriedade cujo valor padrão pode ser substituído na linha de comando.  Por exemplo, use  
  
     `<MyProperty Condition="$(MyProperty)" == ''>`  
  
     `MyDefaultValue`  
  
     `</MyProperty>`  
  
-   Evite curingas ao selecionar itens.  Em vez disso, especifique os arquivos explicitamente.  Isso torna mais fácil controlar os erros que podem ocorrer quando você adiciona ou exclui arquivos.  
  
## Consulte também  
 [Conceitos avançados](../msbuild/msbuild-advanced-concepts.md)