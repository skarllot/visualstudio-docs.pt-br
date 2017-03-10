---
title: "N&#227;o &#233; poss&#237;vel gravar a sa&#237;da da ferramenta personalizada &#39;ferramenta&#39; arquivo &#39;arquivo&#39;. &lt; motivo &gt; | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.tasklisterror.cannot_write_gen_output"
ms.assetid: eafcee9e-186b-4019-9042-8d8f9fc0925a
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# N&#227;o &#233; poss&#237;vel gravar a sa&#237;da da ferramenta personalizada &#39;ferramenta&#39; arquivo &#39;arquivo&#39;. &lt; motivo &gt;
O sistema do projeto não pôde gravar a saída da ferramenta personalizada para o arquivo especificado.  
  
 Desde que o nome do arquivo de entrada de uma ferramenta personalizada permanece inalterado, a saída de uma ferramenta personalizada é gravada no mesmo arquivo. Esse erro ocorre se a saída gerada é bloqueada no disco.  
  
 **Para corrigir este erro**  
  
-   Reiniciar [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] e execute novamente a ferramenta personalizada clicando duas vezes o arquivo afetado e selecionando **Executar ferramenta personalizada** no menu de atalho.  
  
     O arquivo gerado é provavelmente desatualizado, porque o sistema do projeto não pode atualizá\-lo.