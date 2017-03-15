---
title: "Analisando a qualidade do c&#243;digo gerenciado usando a an&#225;lise de c&#243;digo | Microsoft Docs"
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
  - "análise de código, código gerenciado"
  - "análise do código gerenciado"
ms.assetid: 68510a55-da51-4381-81a5-0feba76b8b4f
caps.latest.revision: 24
caps.handback.revision: 24
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Analisando a qualidade do c&#243;digo gerenciado usando a an&#225;lise de c&#243;digo
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Você pode usar as ferramentas de análise de código no Visual Studio para descobrir problemas potenciais em seu código, como o acesso a dados de não seguras, as violações de uso, e os problemas de design.  Codificar trabalho de análise no.NET Framework, no modo nativo C e C\+\+ \(2.0\), e em aplicativos de base de dados.  A análise de código para o código gerenciado organiza regras *nos conjuntos da regra* que visam problemas de codificação específica.  
  
## Tarefas comuns  
  
|Tarefas comuns|Conteúdo de suporte|  
|--------------------|-------------------------|  
|**Obter a prática para trabalhar:** Souber os fundamentos da análise de código corrigir defeitos em um aplicativo. NET Framework simples.|-   [Instruções passo a passo: analisando código gerenciado em busca de defeitos de código](../code-quality/walkthrough-analyzing-managed-code-for-code-defects.md)|  
|As regras de**Configurar a análise de código para um projeto:** para o código gerenciado são organizadas em conjuntos da regra que visam áreas específicas, como segurança e design.  Você pode usar um dos conjuntos padrão da regra da Microsoft ou criar seus próprios.|-   [Visão geral da análise de código para código gerenciado](../code-quality/code-analysis-for-managed-code-overview.md)<br />-   [Usando conjuntos de regras para agrupar regras de análise de código](../code-quality/using-rule-sets-to-group-code-analysis-rules.md)<br />-   [Suprimir avisos usando o atributo SuppressMessage](../code-quality/suppress-warnings-by-using-the-suppressmessage-attribute.md)|  
|**Análise de código de execução:** Você pode especificar a análise de código a ser executado automaticamente sempre que uma configuração de projeto for criada, e você pode executar a análise de código manualmente em um projeto.|-   [Como habilitar e desabilitar análise de código automática](../Topic/How%20to:%20Enable%20and%20Disable%20Automatic%20Code%20Analysis%20for%20Managed%20Code.md)<br />-   [Como executar a análise de código manualmente](../code-quality/how-to-run-code-analysis-manually-for-managed-code.md)|  
|Avisos e erros de análise de código de**Analisar resultados da análise de código:** são listados na janela do código.  Você pode escolher um aviso ou um título de erro exibir informações adicionais sobre o aviso, e exibir e realçar a linha do código fonte que disparou a regra.  Você pode escolher a ID de aviso para exibir informações detalhadas na Biblioteca MSDN que inclui informações e exemplos de como solucionar o problema.|-   [Como exibir defeitos de código gerenciado](../code-quality/how-to-view-managed-code-defects.md)<br />-   [Avisos da análise de código para código gerenciado](../code-quality/code-analysis-for-managed-code-warnings.md)<br />-   [Avisos por CheckId](../code-quality/code-analysis-warnings-for-managed-code-by-checkid.md)<br />-   [Métodos anônimos e análise de código](../code-quality/anonymous-methods-and-code-analysis.md)|  
|As políticas de check\-in de**Integrar a análise de código com seu ciclo de vida de desenvolvimento:** em [!INCLUDE[esprscc](../code-quality/includes/esprscc_md.md)] habilitam a equipe de desenvolvimento para garantir que todos os registros de código atendam a um conjunto comum de padrões de análise de código.  Criar um item de trabalho para uma violação da regra de análise de código é o procedimento simples que você pode executar na janela da Lista de erros.|-   [Melhorando a qualidade do código com políticas de check\-in do projeto da equipe](../code-quality/enhancing-code-quality-with-team-project-check-in-policies.md)<br />-   [Como sincronizar conjuntos de regras do projeto de código com política de check\-in do projeto da equipe](../code-quality/how-to-synchronize-code-project-rule-sets-with-team-project-check-in-policy.md)<br />-   [Como criar um item de trabalho para um defeito de código gerenciado](../code-quality/how-to-create-a-work-item-for-a-managed-code-defect.md)|