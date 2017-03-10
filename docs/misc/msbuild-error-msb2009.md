---
title: "Erro MSB2009 (MSBuild) | Microsoft Docs"
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
  - "MSBuild.UnrecognizedAttribute"
helpviewer_keywords: 
  - "MSB2009"
ms.assetid: 34fd83b4-dead-49e5-b1ee-b23dc5a95244
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Erro MSB2009 (MSBuild)
**O atributo '\< nome do atributo \>' do elemento '\< nome do elemento \>' não é válido.**  
  
 O nome do atributo não foi digitado corretamente ou não é reconhecido pelo [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)].  
  
### Para corrigir este erro  
  
-   Verifique a ortografia do nome do atributo.  
  
-   Verifique se o arquivo de projeto foi modificado ou corrompido. Se ele foi modificado ou corrompido, abra o projeto na versão do [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] em que ela foi criada, salvá\-lo e, em seguida, tentar convertê\-lo novamente.  
  
## Consulte também  
 [Referência do esquema de arquivos de projeto](../msbuild/msbuild-project-file-schema-reference.md)