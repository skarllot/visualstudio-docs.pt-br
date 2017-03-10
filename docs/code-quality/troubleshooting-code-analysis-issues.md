---
title: "Solucionando problemas de an&#225;lise do c&#243;digo | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 61c7e44d-2780-4df5-9bcb-49e40c1152fc
caps.latest.revision: 5
caps.handback.revision: 5
author: "erickson-doug"
ms.author: "douge"
manager: "douge"
---
# Solucionando problemas de an&#225;lise do c&#243;digo
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Este tópico contém informações de solução de problemas para os seguintes problemas de análise de código do Visual Studio.  
  
-   [As alterações em um conjunto de regras do Visual Studio 2010 não são refletidas em versões anteriores do Visual Studio](#ChildRuleSetChangesInPreviousVersions)  
  
##  <a name="ChildRuleSetChangesInPreviousVersions"></a> As alterações em um conjunto de regras do Visual Studio 2010 não são refletidas em versões anteriores do Visual Studio  
 Quando você cria uma regra definida em [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)] que contém um conjunto filho da regra, uma alteração no conjunto filho de regra não pode ser aplicada em execuções do código em computadores que usam uma versão anterior do Visual Studio.  Para resolver esse problema, você deverá forçar uma recriação do conjunto pai da regra, que é a regra definida que contém o conjunto filho da regra.  
  
1.  Abra a regra definida em [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)]pai.  
  
2.  Faça uma alteração, como adicionar ou remover uma regra, e salve o conjunto de regras.  
  
3.  Reabra o conjunto de regras, inverta a alteração, e salve a regra definida novamente.  
  
## Consulte também  
 [Analisando a qualidade do aplicativo](../code-quality/analyzing-application-quality-by-using-code-analysis-tools.md)   
 [Analisando a qualidade do código gerenciado](../code-quality/analyzing-managed-code-quality-by-using-code-analysis.md)   
 [Usando conjuntos de regras para agrupar regras de análise de código](../code-quality/using-rule-sets-to-group-code-analysis-rules.md)