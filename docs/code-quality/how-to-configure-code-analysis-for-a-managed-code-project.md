---
title: "Como configurar a an&#225;lise de c&#243;digo para um projeto de c&#243;digo gerenciado | Microsoft Docs"
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
  - "vs.codeanalysis.propertypages.csvb"
helpviewer_keywords: 
  - "análise de código, selecionando os conjuntos de regras"
  - "conjuntos de regras de análise de código"
ms.assetid: 618f6ff3-db0e-46cb-b08d-dfa35e62c9e7
caps.latest.revision: 33
caps.handback.revision: 33
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Como configurar a an&#225;lise de c&#243;digo para um projeto de c&#243;digo gerenciado
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Em [!INCLUDE[vsUltLong](../code-quality/includes/vsultlong_md.md)], [!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)] e [!INCLUDE[vsPro](../code-quality/includes/vspro_md.md)], você pode escolher de uma lista  *de conjuntos da regra*de análise de código para aplicar a um projeto de código gerenciado.  O conjunto de regras padrão são as regras recomendadas mínimo da Microsoft.  Você pode aplicar outra regra definida em um projeto ou a todos os projetos em uma solução.  
  
> [!NOTE]
>  Para obter informações sobre como configurar uma regra definida para aplicativos Web ASP.NET, consulte [Como configurar a análise de código para um aplicativo Web do ASP.NET](../code-quality/how-to-configure-code-analysis-for-an-aspnet-web-application.md).  
  
### Para configurar uma regra definida para o .NET Framework projeto  
  
1.  Em **Gerenciador de Soluções**, clique no projeto.  
  
2.  No menu de **Analisar** , clique **Configurar a análise de código para** *ProjectName*.  
  
3.  Em listas de **Configuração** e de **Plataforma** , clique na configuração de criação e direcionar a plataforma.  
  
4.  Para executar a análise de código cada vez que o projeto é compilado com a configuração selecionada, marque a caixa de seleção de **Habilitar a análise de código na construção \(define a constante de CODE\_ANALYSIS\)** .  Você também pode executar a análise de código manualmente abrindo o menu de **Analisar** e clicando em **Executar análise de código sobre** *ProjectName*.  
  
5.  Por padrão, a análise de código não relata avisos de código gerado automaticamente por ferramentas externas.  Para exibir avisos de código gerado, desmarque a caixa de seleção de **Suprimir resultados do código gerado** .  
  
    > [!NOTE]
    >  Essa opção não suprime erros e avisos de análise de código de código gerado quando os erros e avisos aparecem em formulários e modelos.  Você pode exibir e manter o código\-fonte de um formulário ou um modelo.  
  
6.  Na lista de **Executar este conjunto de regras** , siga um destes procedimentos:  
  
    -   Clique na regra definida que você deseja usar.  
  
    -   Clique **\<Procurar…\>** para especificar uma regra personalizada existente definida que não está na lista.  
  
    -   Define um conjunto de regra personalizada.  
  
         Para obter mais informações, consulte [Criando conjuntos de regras personalizados](../code-quality/creating-custom-code-analysis-rule-sets.md).  
  
## Consulte também  
 [Instruções passo a passo: configurando e usando um conjunto de regras personalizado](../code-quality/walkthrough-configuring-and-using-a-custom-rule-set.md)