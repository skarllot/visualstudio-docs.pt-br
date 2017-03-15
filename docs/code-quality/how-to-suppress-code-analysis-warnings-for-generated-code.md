---
title: "Como suprimir avisos de an&#225;lise do c&#243;digo para c&#243;digo gerenciado | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 3a96434e-d419-43a7-81ba-95cccac835b8
caps.latest.revision: 5
caps.handback.revision: 5
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Como suprimir avisos de an&#225;lise do c&#243;digo para c&#243;digo gerenciado
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Os compiladores de código gerenciado gerenciem que frequência o código que é adicionado a um projeto facilitar o desenvolvimento rápido de código.  Além disso, os desenvolvedores ferramentas de terceiros de uso com frequência para ajudar a desenvolver aplicativos rapidamente.  Essas ferramentas também gerenciam o código que é adicionado ao projeto.  
  
 Você pode querer ver as violações da regra que afeta a análise de descoberta no código gerado.  No entanto, talvez você não queira fazer se você não pode exibir e manter o código que contém a violação.  
  
 A caixa de seleção de **Suprimir resultados do código gerado** na página de propriedades do código de um projeto permite que você selecione para ver os avisos de análise de código de código gerado por uma ferramenta de terceiros.  
  
> [!NOTE]
>  Essa opção não suprime erros e avisos de análise de código de código gerado quando os erros e avisos aparecem em formulários e modelos.  Você pode exibir e manter o código\-fonte de um formulário ou um modelo.  
  
### Para suprimir avisos para o código gerado em um projeto  
  
1.  Clique com o botão direito do mouse no projeto do no Solution Explorer, e clique em **Propriedades**.  
  
2.  Clique **Análise de Código**.  
  
3.  Marque a caixa de seleção de **Suprimir resultados do código gerado** .