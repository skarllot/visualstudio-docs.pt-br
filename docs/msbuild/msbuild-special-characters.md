---
title: "Caracteres especiais no MSBuild | Microsoft Docs"
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
  - "escape"
  - "caracteres de escape"
  - "caracteres de escape MSBuild"
ms.assetid: 545e6a59-1093-4514-935e-78679a46fb3c
caps.latest.revision: 8
caps.handback.revision: 8
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Caracteres especiais no MSBuild
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]reserva alguns caracteres para uso especial em contextos específicos.  Você só precisará tais caracteres de escape, se você quiser usá\-los literalmente no contexto em que estão reservados.  Por exemplo, um asterisco tem significado especial somente na `Include` e `Exclude` atributos de uma definição de item e em chamadas para `CreateItem`.  Se você quiser um asterisco apareça como um asterisco em um desses contextos, você deve isolá\-lo.  Em cada contexto, basta digite o asterisco onde você deseja que ele apareça.  
  
 Para um caractere de escape especial, use a sintaxe ' %*xx*, onde  *xx* representa o valor hexadecimal de ASCII do caractere.  Para obter mais informações, consulte [Como escapar caracteres especiais no MSBuild](../msbuild/how-to-escape-special-characters-in-msbuild.md).  
  
## Caracteres Especiais  
 A tabela a seguir listas [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] caracteres especiais:  
  
|**Caracterer**|**ASCII**|**Uso reservado**|  
|--------------------|---------------|-----------------------|  
|%|%25|Metadados de referência|  
|$|%24|Referência de propriedades|  
|@|%40|Listas de itens de referência|  
|'|%27|Condições e outras expressões.|  
|;|% 3B|Separador de lista|  
|?|% 3F|O caractere curinga para nomes de arquivo em `Include` e `Exclude` atributos|  
|\*|% 2A|O caractere curinga para uso em nomes de arquivo em `Include` e `Exclude` atributos|  
  
## Consulte também  
 [Conceitos avançados](../msbuild/msbuild-advanced-concepts.md)   
 [Itens](../msbuild/msbuild-items.md)