---
title: "Erro MSB3141 (MSBuild) | Microsoft Docs"
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
  - "MSBuild.GenerateBootstrapper.MissingVerificationInformation"
  - "vsdeploy.chm:13141"
helpviewer_keywords: 
  - "MSB3141"
ms.assetid: f32ce5fd-bb82-4a8b-aebe-61efef89cdc1
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Erro MSB3141 (MSBuild)
**MSB3141: nenhum atributo 'PublicKey' ou 'Hash' especificado para o arquivo '\< arquivo \>' no item '\< pacote \>'. "**  
  
 Esse erro ocorre quando você tenta usar HomeSite para os pacotes de bootstrapper. No entanto, o manifesto do bootstrapper não contém as informações corretas para a verificação do arquivo \(uma chave pública ou um hash\) em tempo de execução.  
  
### Para corrigir este erro  
  
-   Baixe o arquivo de pacote para o qual as informações estão ausentes e copie\-o no cache de bootstrapper.  
  
## Consulte também  
 [Elemento \<PackageFiles\>](../deployment/packagefiles-element-bootstrapper.md)