---
title: "Caixa de di&#225;logo N&#227;o &#233; Poss&#237;vel Alterar Valor | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.variables.failededit"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "Caixa de diálogo Não É Possível Alterar Valor"
  - "variáveis [depurador], edição"
ms.assetid: 19e930c2-5fbf-4c83-aae8-a1dc3f8fcae8
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Caixa de di&#225;logo N&#227;o &#233; Poss&#237;vel Alterar Valor
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

## Erro  
 `The value of this variable cannot be changed`  &#124; `The name` *name* `does not exist in the current context` &#124; *various other messages*  
  
 Essa caixa de mensagem aparece quando você tenta alterar o conteúdo de uma variável para um valor inválido em uma janela do depurador \(janelas Autos, Inspeção ou Locais\) ou na caixa de diálogo QuickWatch.  Por exemplo, se você tentar definir o valor de uma variável de inteiro como uma cadeia de caracteres, essa caixa de mensagem é exibida.  
  
## Solução  
 Certifique\-se que o valor inserido na janela do depurador ou na caixa de diálogo QuickWatch representa um valor válido para a variável que você está tentando definir.  
  
## Consulte também  
 [Expressões no depurador](../debugger/expressions-in-the-debugger.md)