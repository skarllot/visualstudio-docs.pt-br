---
title: "Erro: o &#39;arquivo&#39; de depend&#234;ncia no projeto &#39;projeto&#39; n&#227;o pode ser copiada para o diret&#243;rio de execu&#231;&#227;o porque ela entraria em conflito com o &#39;arquivo&#39; de depend&#234;ncia. | Microsoft Docs"
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
  - "vs.tasklisterror.copy_version_conflict"
ms.assetid: cd7de1eb-7d58-4e2c-9811-a7201f7817be
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Erro: o &#39;arquivo&#39; de depend&#234;ncia no projeto &#39;projeto&#39; n&#227;o pode ser copiada para o diret&#243;rio de execu&#231;&#227;o porque ela entraria em conflito com o &#39;arquivo&#39; de depend&#234;ncia.
Há um conflito entre referências; mais de uma dependência distinta com o mesmo nome de arquivo que está sendo copiado para o diretório bin para a execução do aplicativo. O diretório de execução não pode resolver o conflito porque nenhuma das dependências são referências principais.  
  
 Esse erro fará com que a compilação falhar.  
  
 Clicar duas vezes neste item de lista de tarefas, você serão levado para o nó de referências do projeto no qual o conflito está ocorrendo.  
  
 **Para corrigir este erro**  
  
-   Verifique um dos assemblies de referência a uma conexão direta de seu projeto. Uma possível desvantagem dessa abordagem é que o assembly que você escolher não é garantido para trabalhar com conjuntos que requerem alguma outra versão do assembly referenciado.  
  
     \- ou \-  
  
-   Certifique\-se de que ambas as cópias do assembly são fortes e no cache de assembly global. Isso elimina a necessidade de copiar os assemblies no diretório bin.  
  
## Consulte também  
 [Gerenciando referências em um projeto](../ide/managing-references-in-a-project.md)   
 [Cache de assemblies global](../Topic/Global%20Assembly%20Cache.md)   
 [Assemblies de nomes fortes](../Topic/Strong-Named%20Assemblies.md)   
 [Controle de versão de assemblies](../Topic/Assembly%20Versioning.md)   
 [Como criar e remover dependências de projeto](../Topic/How%20to:%20Create%20and%20Remove%20Project%20Dependencies.md)