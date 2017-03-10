---
title: "Erro MSB3165 (MSBuild) | Microsoft Docs"
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
  - "vsdeploy.chm:13165"
  - "MSBuild.GenerateBootstrapper.DifferingPublicKeys"
helpviewer_keywords: 
  - "MSB3165"
ms.assetid: 2f50462e-947d-4211-b197-e58eddcfd373
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Erro MSB3165 (MSBuild)
**Msb3165 \(\): O valor do atributo '\< chave pública \>' em '\< pacote \>' não corresponde do arquivo '\< arquivo \>'.**  
  
 Este aviso ocorre quando a chave pública especificada no bootstrapper, arquivo de pacote não coincide com a assinatura do pacote redistribuível no disco ou o pacote redistribuível não está assinado. A compilação será levar o valor da chave público do que no disco se ele estiver conectado, ou o hash do pacote redistribuível no disco se ele não está assinado.  
  
## Consulte também  
 [Elemento \<PackageFiles\>](../deployment/packagefiles-element-bootstrapper.md)   
 [Referência de esquema de produto e pacote](../deployment/product-and-package-schema-reference.md)