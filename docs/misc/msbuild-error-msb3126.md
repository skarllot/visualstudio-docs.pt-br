---
title: "Erro MSB3126 (MSBuild) | Microsoft Docs"
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
  - "GenerateManifest.FileAssociationsNotInstalled"
helpviewer_keywords: 
  - "MSB3126"
ms.assetid: 0c92cbb6-9100-4433-8113-f2f3a1432243
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Erro MSB3126 (MSBuild)
**MSB3126: O aplicativo usa associações de arquivo, mas não está marcado para instalação. Associações de arquivo não podem ser usadas para aplicativos que não estão instalados, como aplicativos hospedados em um navegador da web.**  
  
 Esse erro ocorre quando um aplicativo é configurado para usar associações de arquivo, mas o modo de instalação do aplicativo está definido como online somente. Como online somente aplicativos normalmente são executados em um navegador, associações de arquivo não estão disponíveis.  
  
### Para corrigir este erro  
  
-   Definir o **modo de instalação e configurações** para **o aplicativo está disponível também offline \(pode ser iniciado a partir do menu Iniciar\)**. Para obter mais informações, consulte [Como especificar o modo de instalação offline ou online do ClickOnce](../deployment/how-to-specify-the-clickonce-offline-or-online-install-mode.md).  
  
## Consulte também  
 [Página de Publicação, Designer de Projeto](../ide/reference/publish-page-project-designer.md)   
 [Manifesto de aplicativo ClickOnce](../deployment/clickonce-application-manifest.md)