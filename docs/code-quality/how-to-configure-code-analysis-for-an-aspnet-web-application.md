---
title: "Como configurar a an&#225;lise de c&#243;digo para um aplicativo Web do ASP.NET | Microsoft Docs"
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
  - "vs.codeanalysis.propertypages.asp"
ms.assetid: b3000b31-fd9d-489e-81a2-a4bee49453ba
caps.latest.revision: 13
caps.handback.revision: 13
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Como configurar a an&#225;lise de c&#243;digo para um aplicativo Web do ASP.NET
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Em [!INCLUDE[vsPreShort](../code-quality/includes/vspreshort_md.md)] e em [!INCLUDE[vsUltShort](../code-quality/includes/vsultshort_md.md)] você pode selecionar em uma lista *de conjuntos da regra* de análise de código para aplicar a [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] o aplicativo Web.  O conjunto de regras padrão são as regras recomendadas Mininimum da Microsoft.  Você pode selecionar outra regra definida para aplicar ao site.  
  
### Para configurar uma regra definida para uma estrutura de página ASP.NET projeto  
  
1.  Selecione o site em **Gerenciador de Soluções**.  
  
2.  No menu de **Analisar** , clique **Configurar Análise de Código para Site**.  
  
3.  Se você selecionou a solução e a solução tiver mais de um projeto, selecione a configuração de criação e focar o sistema operacional das listas de **Configuração** e de **Plataforma** .  
  
4.  Para cada projeto na solução, clique na coluna de **Conjunto de Regras** , e clique no nome da regra definida para executar.  
  
5.  Por padrão, a análise de código é executada em todos os projetos na solução.  Para desabilitar ou habilitar a análise de código para um projeto específico, siga estas etapas:  
  
    1.  Clique com o botão direito do mouse no nome do projeto e clique em propriedades.  
  
    2.  Marque ou desmarque a caixa de seleção de **Habilitar Análise de Código** .  Você também pode executar a análise de código **Executar Análise de Código no Site** manualmente selecionando no menu de **Analisar** .  
  
6.  Na lista suspensa de **Executar este conjunto de regras** , siga estas etapas:  
  
    -   Selecione a regra definida que você deseja usar.  
  
    -   Selecione **\<Procurar\>** para especificar uma regra personalizada existente definida que não está na lista.  
  
    -   Define um conjunto de regra personalizada.  Para obter mais informações, consulte [Criando conjuntos de regras personalizados](../code-quality/creating-custom-code-analysis-rule-sets.md).