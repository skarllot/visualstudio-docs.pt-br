---
title: "Erro MSB3148 (MSBuild) | Microsoft Docs"
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
  - "MSBuild.GenerateBootstrapper.NoOutputPath"
helpviewer_keywords: 
  - "MSB3148"
ms.assetid: 389b335f-5760-4dcc-9146-c52d6d7ac81f
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Erro MSB3148 (MSBuild)
**MSB3148: Nenhum caminho de saída especificado nas configurações de compilação.**  
  
 Esse erro ocorre quando um caminho de saída nulo ou inválido é especificado; Por exemplo, se `OutputPath=""` no arquivo de projeto. O valor padrão para o caminho de saída é `CurrentDirectory`.  
  
### Para corrigir este erro  
  
-   Certifique\-se de que `OutputPath` não está em branco ou que não está incluído no arquivo de projeto.  
  
## Consulte também  
 [Referência de esquema de produto e pacote](../deployment/product-and-package-schema-reference.md)