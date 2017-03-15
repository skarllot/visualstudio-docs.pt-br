---
title: "Erro MSB2006 (MSBuild) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "MSBuild.UnrecognizedElement"
helpviewer_keywords: 
  - "MSB2006"
ms.assetid: 89dc1b89-1621-46bc-9fe6-6d98cbcbebc8
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Erro MSB2006 (MSBuild)
**O arquivo de projeto não contém o elemento raiz \< {0} \>.**  
  
 O nome do elemento raiz não foi digitado corretamente ou não é reconhecido pelo [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)].  
  
### Para corrigir este erro  
  
-   Verifique a ortografia do nome do elemento.  
  
-   Verifique se o arquivo de projeto foi modificado ou corrompido. Se ele foi modificado ou corrompido, abra o projeto na versão do [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] em que ela foi criada, salvá\-lo e, em seguida, tentar convertê\-lo novamente.  
  
## Consulte também  
 [Referência do esquema de arquivos de projeto](../msbuild/msbuild-project-file-schema-reference.md)   
 [Recursos adicionais](../msbuild/additional-msbuild-resources.md)