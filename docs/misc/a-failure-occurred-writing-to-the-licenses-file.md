---
title: "Ocorreu um erro ao gravar o arquivo de licen&#231;as | Microsoft Docs"
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
  - "vs.tasklisterror.fail_writing_licenses_file"
ms.assetid: 7ea1e2ac-fc94-4d53-8ce9-2ae31bcba85d
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Ocorreu um erro ao gravar o arquivo de licen&#231;as
Não foi possível gravar o arquivo transformado pelo sistema do projeto. Como parte da preparação de licenças, o sistema do projeto transformará arquivos do texto. licx em arquivos de licenças binário que sejam entendidos pelo [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] o licenciamento do sistema.  
  
 Possíveis razões para esse erro não incluem nenhum espaço em disco disponível no dispositivo ou exceder o limite de MAX\_PATH para nomes de arquivo.  
  
 **Para corrigir este erro**  
  
-   Mover o projeto para uma pasta diferente com um nome de caminho absoluto curto ou Encurte o nome do arquivo de saída.  
  
     O processo de compilação falhará se esse erro ocorrer.  
  
## Consulte também  
 [How to: License Components and Controls](../Topic/How%20to:%20License%20Components%20and%20Controls.md)