---
title: "Ocultar propriedades que t&#234;m propriedades filho | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Propriedades [Visual Studio SDK], ocultando"
  - "Janela de propriedades, ocultando as propriedades que têm propriedades filho"
ms.assetid: 6003607e-fc19-4bf9-a299-9f6adf8e92eb
caps.latest.revision: 13
caps.handback.revision: 13
manager: "douge"
---
# Ocultar propriedades que t&#234;m propriedades filho
Você gostaria de ocultar propriedades que possuem propriedades filho:  
  
-   Se você tiver projetos aninhados, onde o projeto pai controla alguns aspectos do projeto filho programaticamente.  
  
-   Se você usa um controle com um designer especializado e você não deseja dar aos desenvolvedores acesso total a todas as propriedades do controle.  
  
-   Se você tiver a propriedade do escopo de um objeto e para limitar a exibição de propriedades.  
  
### Para ocultar as propriedades que possuem propriedades filho  
  
1.  Set the `pfDisplay` parameter in <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.DisplayChildProperties%2A> to `FALSE`.  
  
2.  Set the `pfHide` parameter in <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.HideProperty%2A> to `TRUE`.  
  
## Consulte também  
 [Grade de exibição de propriedades](../extensibility/internals/properties-display-grid.md)