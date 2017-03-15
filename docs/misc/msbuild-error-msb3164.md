---
title: "Erro MSB3164 (MSBuild) | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "MSBuild.GenerateBootstrapper.PackageHomeSiteMissing"
helpviewer_keywords: 
  - "MSB3164"
ms.assetid: 5a1e31fc-0322-4d4e-8c26-013b1efb82c9
caps.latest.revision: 5
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Erro MSB3164 (MSBuild)
**MSB3164: Nenhum atributo 'HomeSite' foi fornecido para '\< pacote \>', para que o pacote será publicado no mesmo local que o bootstrapper.**  
  
 Esse aviso é gerado quando o usuário deseja usar HomeSite, mas as informações HomeSite apropriada para o pacote especificado não estão disponível.  
  
### Para corrigir este erro  
  
-   Atualize os arquivos de manifesto para incluir informações HomeSite.  
  
-   Como alternativa, não use HomeSite.  
  
## Consulte também  
 [Elemento \<PackageFiles\>](../deployment/packagefiles-element-bootstrapper.md)