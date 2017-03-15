---
title: "Usando o servi&#231;o de gradiente em uma janela de ferramenta | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "explicações passo a passo, os serviços"
  - "janelas de ferramentas, o serviço de gradiente"
  - "serviço de gradiente, instruções passo a passo"
  - "consumindo serviços"
ms.assetid: 67590982-6e1f-4e4b-be18-7d1b294cabff
caps.latest.revision: 44
caps.handback.revision: 44
manager: "douge"
---
# Usando o servi&#231;o de gradiente em uma janela de ferramenta
Porque [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] janelas de ferramentas são construídas com Windows Presentation Foundation \(WPF\), não é necessário que chamar o serviço de gradiente no código.  Em vez disso, o designer que representa a superfície de janela de ferramentas , selecione o  `StackPanel` elemento e em seguida, no  **Propriedades** janela, modificar o  **plano de fundo**depropriedade para definir o gradiente.    Para mais informações, consulte [Definindo cores, gradientes e opacidade](../misc/setting-colors-gradients-and-opacity.md).  
  
## Consulte também  
 [NOT IN BUILD: Tool Window Walkthroughs](http://msdn.microsoft.com/pt-br/ecffc579-0e96-48ad-90f3-01a3d80f3ce5)   
 [Estendendo janelas de ferramenta](../misc/extending-tool-windows.md)   
 [Definindo cores, gradientes e opacidade](../misc/setting-colors-gradients-and-opacity.md)