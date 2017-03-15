---
title: "Estendendo o modelo de automa&#231;&#227;o | Microsoft Docs"
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
  - "modelo de objeto de automação, estendendo"
ms.assetid: f09e1365-6291-41a7-b52b-9398270d9da2
caps.latest.revision: 12
caps.handback.revision: 12
manager: "douge"
---
# Estendendo o modelo de automa&#231;&#227;o
Esta seção discute como o modelo de automação e o modelo VSPackage representam uma abordagem de dois pinos para extensibilidade do [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ambiente.  Extensibilidade é a capacidade para aperfeiçoar e estender a funcionalidade do IDE.  Automação, por um lado, refere\-se ao código criados pelo usuário e ferramentas que automatizam tarefas no ambiente existente e programaticamente unidade IDE.  VSPackages, por outro lado, permitem adicionar nova funcionalidade no ambiente.  
  
 É possível combinar os VSPackages e automação em um aplicativo de extensibilidade.  Para um exemplo, consulte [Passo a passo: Estendendo VSPackages gerenciados através da automação](../misc/walkthrough-extending-managed-vspackages-by-using-automation.md).  
  
 Para uma amostra de ponta a ponta de um sistema de projeto de linguagem que suporta o modelo de automação, consulte o [Exemplos VSSDK](../misc/vssdk-samples.md).  
  
## Nesta seção  
 [Modelo de automação](/visual-cpp/misc/automation-model)  
 Fornece uma visão geral sobre o modelo de automação e discute como o modelo de automação permite personalizar, ajustar e automatizar o ambiente.  
  
 [Contribuir com o modelo de automação](../extensibility/internals/contributing-to-the-automation-model.md)  
 Fornece uma visão mais detalhada do modelo de automação e discute as maneiras de automação para seu VSPackage.  Esta seção também fornece exemplos de código que mostram como um consumidor de automação obtém o projeto inicial objetos de automação.  
  
## Seções relacionadas  
 [SDK do Visual Studio e automação](../Topic/Visual%20Studio%20SDK%20and%20Automation.md)  
 Aborda o uso de automação, VSPackages ou uma combinação para criar [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] aplicativos de extensibilidade.