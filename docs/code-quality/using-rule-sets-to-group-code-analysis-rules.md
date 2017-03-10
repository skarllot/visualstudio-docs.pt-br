---
title: "Usando conjuntos de regras para agrupar regras de an&#225;lise de c&#243;digo | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.codeanalysis.rulesets.learnmore"
helpviewer_keywords: 
  - "análise de código, conjuntos de regras"
ms.assetid: ed0f3a2a-1516-42e2-92de-b8986dc75d42
caps.latest.revision: 36
caps.handback.revision: 36
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Usando conjuntos de regras para agrupar regras de an&#225;lise de c&#243;digo
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Quando você configura a análise de código em [!INCLUDE[vsUltLong](../code-quality/includes/vsultlong_md.md)], em [!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)], ou em [!INCLUDE[vsPro](../code-quality/includes/vspro_md.md)], você pode escolher de uma lista*de conjuntos de regra*interno do Microsoft.  Um conjunto de regras é um agrupamento lógico das regras de análise de código que identificam problemas de destino e condições específicas.  Por exemplo, você pode aplicar uma regra definida que é criado ao código de auditoria para as APIs publicamente disponíveis, ou pode aplicar uma regra definida que inclua apenas as regras recomendadas mínimo.  Você também pode aplicar uma regra definida que inclui todas as regras.  
  
 Você pode personalizar uma regra definida adicionando ou excluindo regras, ou alterando regras para serem exibidas na janela de **Lista de Erros** como avisos ou erros.  Os conjuntos personalizadas da regra pode atender a uma necessidade para o ambiente de desenvolvimento específico.  Quando você personaliza um conjunto de regras, a página de definição de regra fornece ferramentas de pesquisa e de filtragem para ajudá\-lo no processo.  
  
## Tarefas comuns  
  
|Tarefa|Conteúdo relacionado|  
|------------|--------------------------|  
|Uso de**Obter a prática para trabalhar:** as ferramentas de análise de código especificar uma regra personalizada definida para localizar e corrigir problemas em um aplicativo. NET Framework simples.|-   [Instruções passo a passo: configurando e usando um conjunto de regras personalizado](../code-quality/walkthrough-configuring-and-using-a-custom-rule-set.md)|  
|**Configurar a análise de código para um projeto:** Escolher uma regra existente definida para um projeto, um site, ou uma solução.|-   [Como configurar a análise de código para um projeto de código gerenciado](../code-quality/how-to-configure-code-analysis-for-a-managed-code-project.md)<br />-   [Usando conjuntos de regras para especificar as regras do C\+\+ para execução](../code-quality/using-rule-sets-to-specify-the-cpp-rules-to-run.md)<br />-   [Como configurar a análise de código para um aplicativo Web do ASP.NET](../code-quality/how-to-configure-code-analysis-for-an-aspnet-web-application.md)<br />-   [Como especificar conjuntos de regras para vários projetos em uma solução](../code-quality/how-to-specify-managed-code-rule-sets-for-multiple-projects-in-a-solution.md)|  
|**Personalizar uma regra definida:** Especificar regras a serem aplicadas ao seu projeto.|-   [Criando conjuntos de regras personalizados](../code-quality/creating-custom-code-analysis-rule-sets.md)|  
|A exibição de**Entenda os conjuntos de regra interna:** as regras de análise de código que compõem a regra define interno.|-   [Referência do conjunto de regras da análise de código](../code-quality/code-analysis-rule-set-reference.md)|  
|as políticas de check\-in de**Integrar a análise de código com Team Foundation Server:**[!INCLUDE[esprtfs](../code-quality/includes/esprtfs_md.md)] habilitam a equipe de desenvolvimento para garantir que todos os registros de código atendam a um conjunto comum de padrões de análise de código.|-   [Como sincronizar conjuntos de regras do projeto de código com política de check\-in do projeto da equipe](../code-quality/how-to-synchronize-code-project-rule-sets-with-team-project-check-in-policy.md)|