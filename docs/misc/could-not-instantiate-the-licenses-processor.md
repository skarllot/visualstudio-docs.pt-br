---
title: "N&#227;o foi poss&#237;vel instanciar o processador de licen&#231;as | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.tasklisterror.no_licx_generator"
ms.assetid: 9e95d590-f41f-4cfa-bc73-fadeacfdb879
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# N&#227;o foi poss&#237;vel instanciar o processador de licen&#231;as
A ferramenta usada para transformar arquivos. licx em recursos binários não pôde ser instanciada.  
  
 Como parte da compilação, o sistema do projeto transformará um arquivo de texto. licx em um recurso binário que fornece suporte para licenciamento do controle .NET. Em seguida, o recurso binário será inserido na saída do projeto.  
  
 O processo de compilação falhará se esse erro ocorrer.  
  
 O arquivo. licx é gerado automaticamente ou atualizado pelo Designer de formulários do Windows sempre que um controle licenciado é adicionado ao formulário. Há um arquivo. licx por projeto. ele é sempre na pasta raiz e é sempre denominado licenses.  
  
 **Para corrigir este erro**  
  
-   Reinstale [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
## Consulte também  
 [How to: License Components and Controls](../Topic/How%20to:%20License%20Components%20and%20Controls.md)