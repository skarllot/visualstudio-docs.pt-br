---
title: "O arquivo &#39;arquivo&#39; n&#227;o p&#244;de ser adicionado ao projeto. &lt; motivo &gt; | Microsoft Docs"
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
  - "vs.tasklisterror.projfile_no_add_file"
ms.assetid: 8bd70556-596a-4e24-a71c-a340604ee93d
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# O arquivo &#39;arquivo&#39; n&#227;o p&#244;de ser adicionado ao projeto. &lt; motivo &gt;
Um arquivo que foi lida do arquivo. vbproj ou. csproj não pode ser adicionado ao projeto. Pelos seguintes motivos:  
  
-   Nome de arquivo inválido.  
  
-   Um caminho de arquivo. Por exemplo, se você tiver um caminho relativo ao projeto de File1\\File2.txt, mas também há uma pasta com o caminho relativo File1\\File2.txt.  
  
-   Item já existe. Isso ocorre quando um arquivo estiver listado duas vezes no arquivo de projeto.  
  
-   Já existe um link. O [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] e [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] sistema de projeto tem uma limitação que pode haver somente um link com o mesmo nome por projeto. Por exemplo, isso significa que você não pode ter um link para o VB na pasta A e B da pasta do projeto.  
  
 Esse erro provavelmente é causado editando manualmente o arquivo de projeto.  
  
 Qualquer arquivo para o qual este diagnóstico é exibido não será adicionado ao projeto.  
  
## Consulte também  
 [Arquivos de projeto](/visual-cpp/ide/project-files)   
 [Gerenciamento de PONTA: itens em projetos](http://msdn.microsoft.com/pt-br/762e606b-7f44-4b66-97a1-e30a703654a0)