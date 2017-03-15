---
title: "Erro MSB3146 (MSBuild) | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "MSBuild.GenerateBootstrapper.MissingDependency"
helpviewer_keywords: 
  - "MSB3146"
ms.assetid: 717fd649-3024-427d-a068-cff8034ffc0a
caps.latest.revision: 5
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Erro MSB3146 (MSBuild)
**MSB3146: Item '\< pacote \>' é exigido pelo '\< pacote \>', mas não foi incluído.**  
  
 Esse erro ocorre quando um pacote de bootstrapper depende de outro, mas você optou por instalar somente o pacote dependente. Por exemplo, o pacote que b depende de um pacote, mas somente B está instalado.  
  
### Para corrigir este erro  
  
-   Inclua o pacote obrigatório.