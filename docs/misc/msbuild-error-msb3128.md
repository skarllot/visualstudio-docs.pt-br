---
title: "Erro MSB3128 (MSBuild) | Microsoft Docs"
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
  - "GenerateManifest.ManifestsSignedHashExcluded"
helpviewer_keywords: 
  - "MSB3128"
ms.assetid: e8612a4b-4016-48d2-b5f0-a1091bfe8cb1
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Erro MSB3128 (MSBuild)
**MSB3128: Os manifestos do ClickOnce não podem ser assinados porque eles contêm uma ou mais referências que não são transformadas em hash.**  
  
 Quando você publica um aplicativo que tenha um manifesto assinado, todos os arquivos devem ser incluídos no hash.  
  
### Para corrigir este erro  
  
1.  Vá para o **publicar** página do **Project Designer**.  
  
2.  Clique em **arquivos de aplicativo**.  
  
3.  Definir o **Hash** valor **incluir** para todos os arquivos que devem ser publicados.  
  
## Consulte também  
 [Página de Publicação, Designer de Projeto](../ide/reference/publish-page-project-designer.md)