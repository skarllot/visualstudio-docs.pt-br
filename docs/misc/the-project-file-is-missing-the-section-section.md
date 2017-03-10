---
title: "O arquivo de projeto n&#227;o possui a se&#231;&#227;o &#39;se&#231;&#227;o&#39;. | Microsoft Docs"
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
  - "vs.tasklisterror.projfile_sectionerr"
ms.assetid: 516ab410-1b73-4539-9654-6323af6135b2
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# O arquivo de projeto n&#227;o possui a se&#231;&#227;o &#39;se&#231;&#227;o&#39;.
O arquivo. vbproj ou. csproj está corrompido. Uma das seções a seguir está ausente:  
  
-   Build  
  
-   Arquivos  
  
-   VisualStudio  
  
-   Visual Basic ou CSHARP  
  
 Se a seção VisualStudio, Visual Basic ou CSHARP estiver ausente, o projeto não será carregado. Se a seção de compilação ou arquivos estiver ausente, o arquivo de projeto será carregado da seguinte maneira:  
  
-   Se a compilação estiver ausente, todas as configurações de compilação e informações de configuração serão perdidas.  
  
-   Se os arquivos estão faltando, o projeto não terá nenhum arquivo nele.  
  
 **Para corrigir este erro**  
  
-   Recrie seu projeto.  
  
## Consulte também  
 [Arquivos de projeto](/visual-cpp/ide/project-files)   
 [NIB: Propriedades de projeto \(Visual Studio\)](http://msdn.microsoft.com/pt-br/eb4c97ed-f667-4850-98d0-6e2a4d21bbca)