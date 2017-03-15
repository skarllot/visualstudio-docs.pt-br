---
title: "Erro MSB3142 (MSBuild) | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "MSBuild.GenerateBootstrapper.CopyError"
helpviewer_keywords: 
  - "MSB3142"
ms.assetid: acca7437-6c72-446c-a6b5-a1c051b6855f
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Erro MSB3142 (MSBuild)
**Msb3142 \(\): Erro ao tentar copiar '\< arquivo \>' para '\< pasta \>': '\< erro \>'**  
  
 Esse erro é gerado quando copiar setup.bin à compilação do diretório de saída. Possíveis causas para esse erro pode ser:  
  
-   Você não tem permissão para copiar para diretório de saída.  
  
-   O disco está cheio.  
  
 Esses são os mesmos motivos possíveis que file.copy ou directory.createdirectory falhar.  
  
## Consulte também  
 [Referência de esquema de produto e pacote](../deployment/product-and-package-schema-reference.md)