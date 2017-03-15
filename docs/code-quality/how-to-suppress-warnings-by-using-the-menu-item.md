---
title: "Como suprimir avisos usando o item de menu | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "suprimir avisos"
  - "análise de código, suprimir avisos"
ms.assetid: 36bd1850-dcde-4ed0-9bc3-0b83df434362
caps.latest.revision: 24
caps.handback.revision: 24
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Como suprimir avisos usando o item de menu
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

> [!NOTE]
>  Na origem da exclusão não há suporte para projetos do site.  
  
 Você pode usar a janela de análise de código para suprimir avisos de análise de código.  Suprimir um aviso não é a mesma que a desabilitação do.  Quando você suprime um aviso, se aplica apenas a uma instância específica de violação.  Outras violações do mesmo aviso serão relatadas na janela da Lista de erros.  
  
 Depois de executar a análise de código, você poderia determinar que um ou mais avisos de análise de código que são exibidos na janela de análise de código não são aplicáveis ao aplicativo.  Por exemplo, você poderia determinar que o código está correto como é.  Ou seja, os casos que são violações de baixa prioridade e não será corrigido no ciclo de desenvolvimento atual.  Independentemente do motivo, geralmente é útil indicar que o aviso for não aplicável deixar os membros da equipe saber que o código esteve examinado e que se determinou que o aviso pode ser suprimido.  Na origem da exclusão é útil porque permite colocar uma exclusão do onde o aviso seja gerado.  
  
 Você pode escolher se a exclusão aparecerá no código\-fonte ou no arquivo global de exclusão.  Algumas exclusões devem ser colocadas no arquivo global de exclusão.  Nesse caso, a opção de **No Código\-Fonte** será desabilitada.  
  
### Para suprimir um aviso usando o item de menu  
  
1.  No menu de **Analisar** , escolha **Janelas** e escolha **Análise de Código**.  
  
2.  Na janela de **Análise de Código** , selecione o aviso suprimem.  
  
3.  Escolha ações, então, escolha **Suprimir Mensagem**e escolha **No Código\-Fonte** ou **Na exclusão Arquivo de projeto**.  
  
     O aviso específico será suprimido, e o aviso aparece na janela de análise de código com um tachado.  
  
> [!NOTE]
>  Exclusões que não têm um destino aparecer no arquivo global de exclusão.