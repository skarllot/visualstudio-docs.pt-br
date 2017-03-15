---
title: "N&#227;o foi poss&#237;vel adicionar a pasta &#39;pasta&#39; ao projeto. &lt; motivo &gt; | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.tasklisterror.projfile_no_add_folder"
ms.assetid: 3f6a5aa7-17cc-4e78-93b7-96e0970e111e
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# N&#227;o foi poss&#237;vel adicionar a pasta &#39;pasta&#39; ao projeto. &lt; motivo &gt;
Uma pasta ler o. vbproj ou. csproj arquivo não pode ser adicionado ao projeto. Pelos seguintes motivos:  
  
-   Nome inválido  
  
-   Um caminho de arquivo. Por exemplo, se você tiver um caminho relativo ao projeto de Folder1\\Folder2\\Folder3, mas também há um arquivo com o caminho relativo Folder1\\Folder2.  
  
-   Item já existe. Isso ocorre quando uma pasta é listada duas vezes no arquivo de projeto.  
  
 Esse erro provavelmente é causado editando manualmente o arquivo de projeto.  
  
 **Para corrigir este erro**  
  
-   Remova o nó da pasta afetada do arquivo de projeto.  
  
     Qualquer pasta e todos os arquivos abaixo da pasta para a qual este diagnóstico é exibido não serão adicionados ao projeto.  
  
## Consulte também  
 [Arquivos de projeto](/visual-cpp/ide/project-files)   
 [NIB: Propriedades de projeto \(Visual Studio\)](http://msdn.microsoft.com/pt-br/eb4c97ed-f667-4850-98d0-6e2a4d21bbca)