---
title: "Erro/aviso do processador de licen&#231;as: &lt;reason&gt; | Microsoft Docs"
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
  - "vs.tasklisterror.licx_generator_task"
ms.assetid: 85750198-7bd3-4936-b1eb-954dcc3ff573
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Erro/aviso do processador de licen&#231;as: &lt;reason&gt;
Um erro ou mensagem de aviso será exibida se uma ferramenta retorna um erro ou um aviso ao processar um arquivo. licx.  Como parte do processo de compilação, o sistema de projeto transforma o arquivo licenses. licx \(se presente\) em um arquivo binário compreendido pelo [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] Gerenciador de licenças.  Essa transformação é feita usando ferramentas no processo.  
  
 Causa mais provável do erro ou aviso é um arquivo. licx inválido.  Um arquivo. licx pode se tornar corrompido se o arquivo tiver sido editado fora do [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ou no [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] usando um editor de texto.  
  
 Esses arquivos normalmente são gerenciados pelo Windows Forms e Web Designers de formulários.  
  
### Para corrigir este erro  
  
1.  Corrigi o formato de arquivo. licx.  
  
     Um erro significa que o arquivo binário não foi gerado e o processo de compilação falhará.  Os avisos são apenas para fins informativos.  
  
## Consulte também  
 [Tipos de arquivo e extensões de arquivo em Visual Basic e C\# Visual](http://msdn.microsoft.com/pt-br/f793852c-da06-4d52-a826-65f635844772)