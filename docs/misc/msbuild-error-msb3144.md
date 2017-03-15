---
title: "Erro MSB3144 (MSBuild) | Microsoft Docs"
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
  - "MSBuild.GenerateBootstrapper.InvalidInput"
helpviewer_keywords: 
  - "MSB3144"
ms.assetid: 955e0db3-afe2-4c03-8e95-3419878374df
caps.latest.revision: 5
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Erro MSB3144 (MSBuild)
**MSB3144 \(\): Não há dados fornecidos para gerar um bootstrapper. Forneça um valor para pelo menos um dos parâmetros: 'ApplicationFile' ou 'BootstrapperItems'. "**  
  
 Esse erro ocorre quando não que há dados suficientes para gerar um bootstrapper foi fornecidos. O processo de compilação cria um bootstrapper vazio com nenhum instalador do aplicativo e não há pacotes.  
  
### Para corrigir este erro  
  
-   Forneça um valor para pelo menos um dos parâmetros `ApplicationFile` ou `BootstrapperItems`.  
  
## Consulte também  
 [Referência de esquema de produto e pacote](../deployment/product-and-package-schema-reference.md)