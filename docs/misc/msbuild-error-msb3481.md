---
title: "Erro MSB3481 (MSBuild) | Microsoft Docs"
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
  - "MSBuild.SignFile.CertNotInStore"
helpviewer_keywords: 
  - "MSB3481"
ms.assetid: 55f99775-3bd5-4e1b-b184-c6405d75e8ff
caps.latest.revision: 5
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Erro MSB3481 (MSBuild)
**MSB3481: O certificado de autenticação não pôde ser localizado. Certifique\-se de que ele está no armazenamento pessoal do usuário atual.**  
  
 Esse erro é gerado quando o certificado de autenticação não foi encontrado no repositório de certificados pessoal. Esse erro é semelhante ao [Erro MSB3486 \(MSBuild\)](../misc/msbuild-error-msb3486.md), que significa que o certificado foi encontrado, mas não corresponde.  
  
### Para corrigir este erro  
  
-   Certifique\-se de que um certificado válido que corresponde ao arquivo. pfx de seu projeto está no repositório de certificados pessoal.  
  
## Consulte também  
 [Elemento \<PackageFiles\>](../deployment/packagefiles-element-bootstrapper.md)