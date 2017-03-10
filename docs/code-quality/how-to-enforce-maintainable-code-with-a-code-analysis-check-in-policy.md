---
title: "Como impor um c&#243;digo com facilidade de manuten&#231;&#227;o com uma pol&#237;tica de check-in de an&#225;lise do c&#243;digo | Microsoft Docs"
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
  - "análise de código, diretivas de check-in"
ms.assetid: d1b3b04f-4dd9-40e6-b2d4-b414d33fb647
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Como impor um c&#243;digo com facilidade de manuten&#231;&#227;o com uma pol&#237;tica de check-in de an&#225;lise do c&#243;digo
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Os desenvolvedores podem usar a ferramenta métrica de código para medir a complexidade e a manutenibilidade de seu código, mas não podem invocar a métrica de código como parte de uma política de check\-in.  No entanto, uma equipe pode habilitar as regras de análise de código que verificam a conformidade de seu código com padrões métrica de código e impõem as regras com as políticas de check\-in.  Para obter mais informações sobre a métrica de código, consulte [Valores de métricas do código](../code-quality/code-metrics-values.md).  
  
 Os desenvolvedores podem habilitar a profundidade de regras de herança, acoplamento da classe, o índice de manutenibilidade, e a complexidade para impor o código visando com as políticas de check\-in do código.  Todos os quatro essas regras são encontradas na ordem” “manutenibilidade a categoria de política no publicador do código.  
  
 Os administradores de controle de versão de [!INCLUDE[esprfound](../code-quality/includes/esprfound_md.md)] podem adicionar as regras de manutenibilidade de análise de código os requisitos de política de check\-in.  Essas políticas de check\-in exigem desenvolvedores executar análises de código com base nessas alterações de regra antes de iniciar um check\-in.  
  
### Para abrir o editor de política do código  
  
1.  Em **Team Explorer**, clique com o botão direito do mouse no projeto de equipe, clique **Configurações de Projeto de Equipe**, e clique em **Controle do Código\-Fonte**.  
  
     A caixa de diálogo de **Controle do Código\-Fonte** é exibida.  
  
2.  Na guia de **Política de Check\-in** , e clique em **Adicionar**.  
  
     A caixa de diálogo **Adicionar Política de Check\-in** aparece.  
  
3.  Na lista de **Política de Check\-in** , marque a caixa de seleção de **Análise de Código** , e clique em **OK**.  
  
     A caixa de diálogo de **Editor de Políticas de Análise de Código** é exibida.  
  
### Para habilitar regras de manutenibilidade de análise de código  
  
1.  Na caixa de diálogo de **Editor de Políticas de Análise de Código** , em **Configurações da Regra**, expanda o nó de **Regras de Facilidade de Manutenção** .  
  
2.  Marque as caixas de seleção das seguintes regras:  
  
    -   Profundidade de herança: **CA1501 AvoidExcessiveInheritance** \- Limite: Aviso a mais de 5 níveis abaixo  
  
    -   Complexidade: **CA1502 AvoidExcessiveComplexity** \- Limite: Aviso em mais de 25  
  
    -   Índice de manutenibilidade: **CA1505 AvoidUnmaintainableCode** \- Limite: Aviso em menos de 20  
  
    -   Acoplamento da classe: **CA1506 AvoidExcessiveClassCoupling** \- Limite: Aviso em mais de 80 para uma classe e mais de 30 para um método  
  
    -   Além disso, se você quiser uma violação da regra para evitar uma construção, marque a caixa de seleção ao lado de **Aviso de serem tratados como um erro** a descrição de regra.  
  
3.  Clique em **OK**.  A nova política de check\-in agora se aplica aos registros futuros.  
  
## Consulte também  
 [Valores de métricas do código](../code-quality/code-metrics-values.md)   
 [Criando e usando políticas de check\-in de análise do código](../code-quality/creating-and-using-code-analysis-check-in-policies.md)