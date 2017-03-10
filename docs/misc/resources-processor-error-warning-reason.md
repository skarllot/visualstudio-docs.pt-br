---
title: "Erro/aviso do processador de recursos: &lt;reason&gt; | Microsoft Docs"
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
  - "vs.tasklisterror.resx_generator_task"
ms.assetid: eb9a1bd0-7e63-4a2b-ad37-54f6e67d9b5a
caps.latest.revision: 7
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Erro/aviso do processador de recursos: &lt;reason&gt;
Um erro ou mensagem de aviso será exibida se uma ferramenta retorna um erro ou um aviso ao processar um arquivo. resx.  Como parte do processo de compilação, o sistema de projeto transforma cada arquivo. resx em um arquivo binário compreendido pelo [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] Gerenciador de recursos.  Essa transformação é feita usando ferramentas no processo.  
  
 Causa mais provável do erro ou aviso é um arquivo. resx inválida.  Um arquivo. resx pode se tornar corrompido se o arquivo tiver sido editado fora de Visual Studio ou Visual Studio usando um editor de texto.  
  
 Esses arquivos normalmente são gerenciados pelo Windows Forms e Web Designers de formulários.  
  
### Para corrigir este erro  
  
1.  Corrigi o formato de arquivo. resx.  
  
     Um erro significa que o arquivo binário não foi gerado e o processo de compilação falhará.  Os avisos são apenas para fins informativos.  
  
## Consulte também  
 [Resources in .Resx File Format](http://msdn.microsoft.com/pt-br/0c476133-87e4-47e8-b0ef-4b88f4ef3dc5)