---
title: "Erro MSB3156 (MSBuild) | Microsoft Docs"
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
  - "MSBuild.GenerateBootstrapper.ProductValidation"
helpviewer_keywords: 
  - "MSB3156"
ms.assetid: 98b1bd42-9efe-44a2-8a43-476edc03590d
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Erro MSB3156 (MSBuild)
**MSB3156: A validação de Xml não foi passada ao item '\< pacote \>' localizado em '\< pasta \>'.**  
  
 Esse aviso é gerado quando o manifesto \(especificamente Product\) não passa na validação de XML. Os problemas específicos são listados em uma mensagem de erro subsequente \([Erro MSB3159 \(MSBuild\)](/visual-cpp/misc/msbuild-error-msb3159) ou [Erro MSB3160 \(MSBuild\)](../misc/msbuild-error-msb3160.md)\).  
  
### Para corrigir este erro  
  
-   Resolva os problemas de validação manifesto listados nas mensagens de erro subsequentes.  
  
## Consulte também  
 [Referência de esquema de produto e pacote](../deployment/product-and-package-schema-reference.md)   
 [Elemento \<PackageFiles\>](../deployment/packagefiles-element-bootstrapper.md)