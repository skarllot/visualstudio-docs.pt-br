---
title: "Erro MSB3161 (MSBuild) | Microsoft Docs"
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
  - "MSBuild.GenerateBootstrapper.CircularDependency"
helpviewer_keywords: 
  - "MSB3161"
ms.assetid: 2871d071-7c3a-4103-8b14-6ee56564a7f7
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Erro MSB3161 (MSBuild)
**MSB3161: Foi detectada uma dependência circular entre os seguintes pacotes compilados: '\< pacote \>'**  
  
 Esse aviso é gerado quando há uma dependência circular no gráfico de dependências do pacote de bootstrapper \(por exemplo: A→B→C→A\). Nesses casos o bootstrapper não pode determinar qual pacote de instalação pela primeira vez.  
  
### Para corrigir este erro  
  
-   Remova a dependência circular, alterando as dependências descritas nos arquivos de pacote de bootstrapper ou por não instalar um dos pacotes interdependentes.  
  
## Consulte também  
 [Referência de esquema de produto e pacote](../deployment/product-and-package-schema-reference.md)   
 [Elemento \<PackageFiles\>](../deployment/packagefiles-element-bootstrapper.md)