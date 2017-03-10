---
title: "N&#227;o foi poss&#237;vel criar o diret&#243;rio&#39; diret&#243;rio de sa&#237;da&#39;. &lt; motivo &gt; | Microsoft Docs"
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
  - "vs.tasklisterror.cannot_create_output_dir"
ms.assetid: b4d1d19f-f582-49d0-a9a9-d3f4ce0a447b
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# N&#227;o foi poss&#237;vel criar o diret&#243;rio&#39; diret&#243;rio de sa&#237;da&#39;. &lt; motivo &gt;
O sistema do projeto não foi possível criar o diretório do projeto.  
  
 O sistema do projeto tentará criar todos os diretórios de saída, assim como o projeto é aberto. A seguir está uma lista dos diretórios de saída criada pelo sistema do projeto:  
  
 *PastaDoProjeto*\\obj\\`configname`  
 Um diretório de saída específicos da configuração temporário.  
  
 *PastaDoProjeto*\\obj\\`configname`\\temp  
 Área de trabalho usada pelo compilador.  
  
 *PastaDoProjeto*\\obj\\`configname`\\temppe  
 Usada pelos designers em tempo de design de assemblies temporários são criados aqui.  
  
 outputdir  
 O diretório especificado pela propriedade caminho de saída. Consulte [Página de Compilação, Designer de Projeto \(C\#\)](../ide/reference/build-page-project-designer-csharp.md) para obter mais informações.  
  
 O motivo mais comum para Falha ao criar um dos diretórios na pasta obj excede o limite MAX\_PATH para nomes de diretório.  
  
 Motivos menos comuns incluem permissão negada e fora do espaço em disco.  
  
 **Para corrigir este erro**  
  
-   Se o caminho for muito longo, alterar o local do projeto ou diminua o nome da configuração de projeto.  
  
     O processo de compilação falhará se esse erro ocorrer.  
  
## Consulte também  
 [PONTA como: modificar propriedades do projeto e as definições de configuração](http://msdn.microsoft.com/pt-br/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67)