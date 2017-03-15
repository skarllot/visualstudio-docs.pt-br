---
title: "O arquivo pai, &#39;file1&#39;, para o arquivo &#39;file2&#39; n&#227;o foi encontrado no arquivo do projeto. | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.tasklisterror.projfile_missing_dependency"
ms.assetid: 1902c0b5-d09d-49b9-8f71-e325f7b9cfd7
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# O arquivo pai, &#39;file1&#39;, para o arquivo &#39;file2&#39; n&#227;o foi encontrado no arquivo do projeto.
O sistema do projeto não pode localizar um nó correspondente a um arquivo.  
  
 Arquivos dependentes são mantidos no arquivo de projeto, adicionando um `DependentUpon` de atributo para o `<File>` nó. Por exemplo:  
  
```  
<File  
    RelPath = "Form1.resx"  
    SubType = "Code"  
    BuildAction = "EmbeddedResource"  
    DependentUpon="Form1.vb"  
/>  
```  
  
 Isso tornará Form1 aparecer abaixo Form1. vb na hierarquia do projeto.  
  
 Esse erro provavelmente é causado editando manualmente o arquivo de projeto.  
  
### Para corrigir este erro  
  
-   Editar e atualizar o arquivo de projeto.  
  
     Os arquivos afetados serão adicionados ao projeto, no entanto, a dependência não será preservada.  
  
## Consulte também  
 [NIB: Propriedades de projeto \(Visual Studio\)](http://msdn.microsoft.com/pt-br/eb4c97ed-f667-4850-98d0-6e2a4d21bbca)