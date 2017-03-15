---
title: "Muitos clientes de aplicativo de DLL | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbrID47"
ms.assetid: 4b87780b-67ad-4c96-9253-db954a751dad
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Muitos clientes de aplicativo de DLL
A biblioteca de vínculo dinâmico \(DLL\) para [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] possa acomodar somente acesso por um número limitado de aplicativos de host. Seu aplicativo e outros aplicativos que são [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] hosts \(alguns dos quais podem ser acessados pelo seu aplicativo\) estão tentando acessar o [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] DLL ao mesmo tempo.  
  
### Para corrigir este erro  
  
-   Reduza o número de aplicativos abertos acessando [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)].  
  
## Consulte também  
 [Tipos de erro](/dotnet/visual-basic/programming-guide/language-features/error-types)