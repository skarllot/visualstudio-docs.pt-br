---
title: "Erro MSB3143 (MSBuild) | Microsoft Docs"
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
  - "MSBuild.GenerateBootstrapper.CopyPackageError"
helpviewer_keywords: 
  - "MSB3143"
ms.assetid: b4278c8c-31df-4b4f-9ef9-7b9327e8ee77
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Erro MSB3143 (MSBuild)
**Msb3143 \(\): Erro ao tentar copiar '\< arquivo \>' item '\< pacote \>': '\< erro \>'**  
  
 Esse erro ocorre quando os pacotes de bootstrapper forem copiados para o diretório de saída de compilação. Possíveis causas para esse erro pode ser:  
  
-   Você não tem permissão para copiar para diretório de saída de compilação.  
  
-   O disco está cheio.  
  
 Esses são os mesmos motivos possíveis que file.copy ou directory.createdirectory falhar.  
  
## Consulte também  
 [Referência de esquema de produto e pacote](../deployment/product-and-package-schema-reference.md)   
 [Elemento \<PackageFiles\>](../deployment/packagefiles-element-bootstrapper.md)