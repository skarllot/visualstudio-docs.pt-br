---
title: "Pelo menos um arquivo est&#225; com o atributo &#39;atributo&#39; faltando | Microsoft Docs"
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
  - "vs.tasklisterror.projfile_missing_file_attrib"
ms.assetid: 2627974b-c9cd-4d85-9af4-dd3811214ea4
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Pelo menos um arquivo est&#225; com o atributo &#39;atributo&#39; faltando
Um nó de arquivo foram lidos do arquivo. vbproj ou. csproj tem determinados atributos que requer que o sistema do projeto. Atualmente o apenas esse atributo é o `RelPath` atributo, que especifica onde o arquivo está localizado na pasta do projeto.  
  
 Esse erro provavelmente é causado editando manualmente o arquivo de projeto.  
  
 **Para corrigir este erro**  
  
-   Remova o nó do arquivo afetado do arquivo de projeto. Além disso, se o arquivo ainda está no disco, você pode alternar para mostrar **Show All Files** modo \(ao clicar nesse botão na barra de ferramentas do Gerenciador de soluções\), clique no arquivo afetado e selecione **incluir no projeto**.  
  
     Qualquer arquivo para o qual o `RelPath` está faltando o atributo não será adicionado ao projeto.  
  
## Consulte também  
 [Arquivos de projeto](/visual-cpp/ide/project-files)   
 [NIB: Propriedades de projeto \(Visual Studio\)](http://msdn.microsoft.com/pt-br/eb4c97ed-f667-4850-98d0-6e2a4d21bbca)