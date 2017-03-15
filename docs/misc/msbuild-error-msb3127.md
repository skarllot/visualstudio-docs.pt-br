---
title: "Erro MSB3127 (MSBuild) | Microsoft Docs"
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
  - "GenerateManifest.FileAssociationDefaultIconNotInstalled"
helpviewer_keywords: 
  - "MSB3127"
ms.assetid: 161eea9a-332f-463e-a49e-d4030e937d52
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Erro MSB3127 (MSBuild)
**Msb3127 \(\): O ícone padrão \< iconname \> não pôde ser encontrado nas referências de arquivo atual ou não faz parte do grupo de download necessário. O nome do arquivo de ícone padrão diferencia maiúsculas de minúsculas, portanto, o nome do arquivo referenciado no manifesto do aplicativo deve corresponder exatamente o nome de arquivo do ícone.**  
  
 Quando você publica um aplicativo que está configurado para usar associações de arquivo, o ícone padrão que é referenciado no manifesto deve estar localizado nas referências de arquivo atual ou deve ser parte do grupo de download necessário. O ícone padrão é o ícone que aparece para os arquivos que possuem a associação de arquivo configurado \(a extensão de nome de arquivo configurado\).  
  
### Para corrigir este erro  
  
-   Adicione o arquivo de ícone para o projeto atual e inclua\-o no grupo de download necessário. Para obter mais informações, consulte [Como especificar os arquivos a serem publicados pelo ClickOnce](../Topic/How%20to:%20Specify%20Which%20Files%20Are%20Published%20by%20ClickOnce.md).  
  
## Consulte também  
 [Página de Publicação, Designer de Projeto](../ide/reference/publish-page-project-designer.md)