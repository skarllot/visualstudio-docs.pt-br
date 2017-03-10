---
title: "Pelo menos uma pasta est&#225; com o atributo &#39;atributo&#39; faltando | Microsoft Docs"
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
  - "vs.tasklisterror.projfile_missing_fold_attrib"
ms.assetid: 3a0498a9-df61-47d8-a228-f88f4f138df8
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Pelo menos uma pasta est&#225; com o atributo &#39;atributo&#39; faltando
Um nó de pasta que foram lidos do arquivo. vbproj ou. csproj tem determinados atributos que requer que o sistema do projeto. Atualmente o apenas esse atributo é o **RelPath** atributo, que especifica onde a pasta particular está localizada na pasta do projeto.  
  
 Esse erro provavelmente é causado editando manualmente o arquivo de projeto.  
  
 **Para corrigir este erro**  
  
-   Remova o nó da pasta afetada do arquivo de projeto. Além disso, se a pasta ainda está no disco, você pode alternar para o modo de mostrar todos os arquivos \(clicando nesse botão na barra de ferramentas do Gerenciador de soluções\), clique na pasta afetada e escolha **incluir no projeto**.  
  
     Qualquer pasta para o qual existe um atributo não será adicionada ao projeto.  
  
## Consulte também  
 [Arquivos de projeto](/visual-cpp/ide/project-files)   
 [NIB: Propriedades de projeto \(Visual Studio\)](http://msdn.microsoft.com/pt-br/eb4c97ed-f667-4850-98d0-6e2a4d21bbca)