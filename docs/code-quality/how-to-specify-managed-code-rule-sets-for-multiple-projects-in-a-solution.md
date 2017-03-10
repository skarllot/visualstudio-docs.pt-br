---
title: "Como especificar conjuntos de regras de c&#243;digo gerenciado para v&#225;rios projetos em uma solu&#231;&#227;o | Microsoft Docs"
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
  - "vs.codeanalysis.propertypages.solution"
ms.assetid: 92dc3250-a010-4396-b515-f03a0b30cd2a
caps.latest.revision: 12
caps.handback.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Como especificar conjuntos de regras de c&#243;digo gerenciado para v&#225;rios projetos em uma solu&#231;&#227;o
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Por padrão, todos os projetos de uma solução gerenciados são atribuídos ao mínimo do Microsoft recomendaram *o conjunto de regras*de análise de código de regras.  Você pode modificar os conjuntos da regra que são atribuídos aos projetos de uma solução na caixa de diálogo propriedades da solução.  
  
> [!NOTE]
>  Por padrão, a análise de código de projeto não é executada como uma etapa de compilação.  Para habilitar a análise de código como uma etapa de construção, consulte [Como configurar a análise de código para um projeto de código gerenciado](../code-quality/how-to-configure-code-analysis-for-a-managed-code-project.md).  
  
### Para especificar uma regra definida para vários projetos em uma solução de código gerenciado  
  
1.  Em [!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)].  [!INCLUDE[vsUltLong](../code-quality/includes/vsultlong_md.md)], ou [!INCLUDE[vsPro](../code-quality/includes/vspro_md.md)] e abra a solução.  
  
2.  No menu de **Analisar** , clique **Configurar Análise de Código para Solução**.  
  
3.  Se necessário, expanda **Propriedades Comuns**, e clique em **Configurações da Análise de Código**.  
  
4.  Você pode especificar uma regra definida para um ou mais projetos.  
  
    -   Para especificar uma regra definida para um projeto individual, clique no nome do projeto.  
  
    -   Para especificar uma regra definida para vários projetos, mantenha a tecla CTRL pressionada e clique nos nomes do projeto.  
  
    -   Para especificar todos os projetos na solução, mantenha a tecla SHIFT pressionada e clique em no projeto listar.  
  
5.  Clique no campo de **Conjunto de Regras** de um projeto e clique no nome da regra definida que deseja aplicar.