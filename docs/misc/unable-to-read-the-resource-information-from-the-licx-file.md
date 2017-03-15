---
title: "N&#227;o foi poss&#237;vel ler as informa&#231;&#245;es de recurso do arquivo licx | Microsoft Docs"
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
  - "vs.tasklisterror.fail_reading_licx_file"
ms.assetid: e59f0965-fa1c-4852-bd39-63430d5b7d9f
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# N&#227;o foi poss&#237;vel ler as informa&#231;&#245;es de recurso do arquivo licx
Não foi possível ler o arquivo. licx pelo sistema do projeto. Como parte da preparação de licenças, o sistema do projeto transformará arquivos do texto. licx em arquivos de recursos binários que são adequados para uso com o modelo de licenciamento COM\+.  
  
 O arquivo. licx é gerado automaticamente ou atualizado pelo Designer de formulários do Windows sempre que um controle licenciado é adicionado ao formulário. Há um arquivo. licx por projeto. ele é sempre na pasta raiz e é sempre denominado licenses.  
  
 Algumas razões para esse erro:  
  
-   Permissão negada.  
  
-   Perdeu a comunicação com o servidor Web para projetos da Web.  
  
 O processo de compilação falhará se esse erro ocorrer.  
  
## Consulte também  
 [How to: License Components and Controls](../Topic/How%20to:%20License%20Components%20and%20Controls.md)