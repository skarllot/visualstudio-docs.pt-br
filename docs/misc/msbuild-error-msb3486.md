---
title: "Erro MSB3486 (MSBuild) | Microsoft Docs"
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
  - "MSBuild.SignFile.CertificateError"
helpviewer_keywords: 
  - "MSB3486"
ms.assetid: 75d03d8e-3a28-4010-b602-61fe037dec74
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Erro MSB3486 (MSBuild)
**MSB3486: Não é possível obter o certificado de armazenamento '\< armazenamento de certificado \>'.**  
  
 O `ResolveKeySource` tarefa MSBuild gera este erro quando o certificado que corresponda a impressão digital do arquivo. pfx de seu projeto não for encontrado no repositório de certificados pessoal.  
  
### Para corrigir este erro  
  
-   Certifique\-se de que a impressão digital do arquivo. pfx de seu projeto é a mesma do certificado no repositório de certificados pessoal.  
  
## Consulte também  
 [Elemento \<PackageFiles\>](../deployment/packagefiles-element-bootstrapper.md)