---
title: "Como definir propriedades de an&#225;lise de c&#243;digo para projetos do C/C++ | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.codeanalysis.propertypages.native"
  - "VC.Project.VCCLCompilerTool.EnablePrefast"
  - "VC.Project.VCFxCopTool.EnablePREfast"
  - "VC.Project.VCFxCopTool.IgnoreGeneratedCode"
helpviewer_keywords: 
  - "propriedades de análise de código C/C++"
  - "propriedades de análise de código"
  - "propriedades, Análise de Código C/C++"
  - "propriedades, Análise de Código"
ms.assetid: 7af52097-6d44-4785-9b9f-43b7a7d447d7
caps.latest.revision: 17
caps.handback.revision: 17
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Como definir propriedades de an&#225;lise de c&#243;digo para projetos do C/C++
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Você pode configurar regras que a ferramenta análise de código analisar o código em cada configuração do seu projeto.  Além disso, você pode análise de código direto suprimir avisos de código que foi gerado e adicionado ao seu projeto por uma ferramenta de terceiros.  
  
## Página de propriedades de análise de código  
 A página de propriedades de **Análise de Código** contém todos os parâmetros de configuração do código do projeto.  Para abrir a página de propriedades do código do projeto em **Gerenciador de Soluções**, clique com o botão direito do mouse no projeto e clique em **Propriedades**.  Em seguida, expanda **Propriedades de Configuração** e selecione a guia de **Análise de Código** .  
  
## Configuração e plataforma do projeto  
 A lista de **Configuração** e a lista de **Plataforma** permitem aplicar configurações diferentes de análise de código a combinações diferentes de configuração e da plataforma do projeto.  Por exemplo, você pode análise de código direto aplicar um conjunto de regras ao projeto para construções de depuração e um conjunto diferente para construções de versão.  
  
## Habilitando a análise de código  
 Você pode decidir se deseja habilitar a análise de código para seu projeto selecionando **Habilitar a análise de código para C\/C\+\+ na construção**.  Em combinação com a lista de **Configuração** , você poderá, por exemplo, decidir desabilitar a análise de código para construções de depuração e habilite\-o para construções de versão.  
  
 Se o projeto contém o código gerenciado, você pode decidir se deseja habilitar ou desabilitar a análise de código **Habilitar Análise de Código na Compilação**selecionando.  
  
 A análise de código é criada para ajudá\-lo a melhorar a qualidade de seu código e a evitar armadilhas comuns.  Consequentemente, considere cuidadosamente se desabilitar a análise de código.  Geralmente é melhor desabilitar os conjuntos de regra ou as regras individuais que você não deseja aplicado ao seu projeto.  
  
## Código gerado  
 Os desenvolvedores ferramentas do usam frequentemente para ajudar a desenvolver aplicativos rapidamente.  Essas ferramentas podem gerar o código que é adicionado ao projeto.  Você pode querer ver as violações da regra que afeta a análise de descoberta no código gerado.  No entanto, talvez você não queira fazer se você não quiser manter o código.  
  
 A caixa de seleção de **Suprimir resultados do código gerado** na página de propriedades de **Geral** permite que você selecione para ver os avisos de análise de código de código gerenciado que é gerado por uma ferramenta de terceiros.  
  
## Conjuntos de regras  
 Se o projeto contém o código gerenciado, você pode selecionar as regras a serem aplicadas em uma análise de código selecionando uma regra definida na lista de **Executar este conjunto de regras** .  
  
## Consulte também  
 [Analisando a qualidade do código gerenciado](../code-quality/analyzing-managed-code-quality-by-using-code-analysis.md)   
 [Análise de código para avisos do C\/C\+\+](../code-quality/code-analysis-for-c-cpp-warnings.md)