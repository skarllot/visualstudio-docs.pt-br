---
title: "Criando e usando pol&#237;ticas de check-in de an&#225;lise do c&#243;digo | Microsoft Docs"
ms.custom: ""
ms.date: "12/12/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "análise de código, políticas de check-in"
ms.assetid: 3fa5a849-e05f-4e31-8ba3-b014c889d94d
caps.latest.revision: 39
caps.handback.revision: 39
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Criando e usando pol&#237;ticas de check-in de an&#225;lise do c&#243;digo
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Quando você usa Controle de versão do Team Foundation \(TFVC\), você pode criar uma política de check\-in de análise de código para o.NET Framework e projetos nativos de código \(C\/C\+\+\) em um projeto de equipe.  Você pode usar a política de check\-in de análise de código para controlar e melhorar a qualidade de código que é verificado na base de código.  
  
 A política é aprovada quando a compilação local é atualizada e a análise do código é executada nos arquivos de origem mais recentes.  Pelo menos, as regras de análise de código que são ativadas no projeto de código devem conter as mesmas regras que aquelas que são definidas na política de check\-in do projeto de equipe.  As regras que foram especificadas como erros nas Configurações de Projeto de Equipe também devem ser especificadas como erros no projeto de código  
  
> [!IMPORTANT]
>  As políticas de check\-in de análise de código não podem ser aplicadas a projetos de site.  Elas podem ser aplicadas a projetos de aplicativos Web.  
  
 Você cria políticas de check\-in de análise de código usando Configurações de Projeto de Equipe do [!INCLUDE[esprscc](../code-quality/includes/esprscc_md.md)].  As políticas de check\-in são especificadas e impostas para um projeto de equipe, mas as execuções de análise de código são configuradas e executadas para projetos individuais de código em computadores de desenvolvimento locais.  Esta seção descreve como especificar políticas de check\-in de análise de código para um projeto de equipe e como implementar políticas de análise de código personalizado para código gerenciado.  
  
## Nesta seção  
 [Como criar ou atualizar políticas de check\-in de análise do código padrão](../Topic/How%20to:%20Create%20or%20Update%20Standard%20Code%20Analysis%20Check-in%20Policies.md)  
 Explica as etapas usadas para definir e modificar uma política de análise código para um projeto de equipe.  
  
 [Implementando políticas de check\-in personalizadas para código gerenciado](../code-quality/implementing-custom-code-analysis-check-in-policies-for-managed-code.md)  
 Explica as etapas usadas para criar uma regra personalizada definida para a política de check\-in de um projeto de equipe, e para sincronizar os projetos de código da equipe com a política de check\-in.  
  
 [Compatibilidade da versão para políticas de check\-in de análise do código](../code-quality/version-compatibility-for-code-analysis-check-in-policies.md)  
 Explica os problemas de compatibilidade de check\-in de análise de código entre versões do [!INCLUDE[vstsLong](../code-quality/includes/vstslong_md.md)].  
  
 [Como personalizar o dicionário de análise do código](../Topic/How%20to:%20Customize%20the%20Code%20Analysis%20Dictionary.md)  
 Explica como adicionar palavras e tokens ao dicionário referenciado em regras de nomenclatura de análise de código.  
  
## Seções relacionadas  
 [Set and Enforce Quality Gates](../Topic/Set%20and%20Enforce%20Quality%20Gates.md)  
  
 [Melhorando a qualidade do código com políticas de check\-in do projeto da equipe](../code-quality/enhancing-code-quality-with-team-project-check-in-policies.md)