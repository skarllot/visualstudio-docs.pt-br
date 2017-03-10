---
title: "CA1504: revisar nomes de campo confusos | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "ReviewMisleadingFieldNames"
  - "CA1504"
helpviewer_keywords: 
  - "CA1504"
  - "ReviewMisleadingFieldNames"
ms.assetid: 94136ff1-4aaf-4dc2-9170-48c171ab7499
caps.latest.revision: 15
caps.handback.revision: 15
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1504: revisar nomes de campo confusos
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|ReviewMisleadingFieldNames|  
|CheckId|CA1504|  
|Categoria|Microsoft.Maintainability|  
|Alteração Significativa|Sem quebra|  
  
## Causa  
 O nome de início de um campo da instância do com “s\_” ou o nome de início de um campo de `static` \(`Shared` em [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]\) com “m\_”.  
  
## Descrição da Regra  
 Os nomes de campo que começam com “s\_” são associados a dados estáticos por muitos usuários.  Da mesma forma, os nomes de campo que começam com “m\_” estão associados com os dados da instância \(membro\).  Para o código mais facilmente mantido, os nomes devem seguir as convenções usadas normalmente.  
  
## Como Corrigir Violações  
 Para corrigir uma violação desta regra, renomeie o campo usando o prefixo apropriado.  Como alternativa, faça o campo concordar com o sufixo atual adicionando ou removendo o modificador de `static` .  
  
## Quando Suprimir Alertas  
 Não elimine um alerta desta regra.