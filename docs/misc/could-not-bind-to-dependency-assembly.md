---
title: "N&#227;o foi poss&#237;vel associar ao &#39;assembly&#39; de depend&#234;ncia | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.tasklisterror.cantbinddependency"
ms.assetid: 0f76190d-d57e-4e0e-bec4-532aec978d08
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# N&#227;o foi poss&#237;vel associar ao &#39;assembly&#39; de depend&#234;ncia
Uma das referências do projeto contém uma referência de assembly \(dependência\) foi localizada, mas não é um assembly válido.  Este erro não impedirá que o projeto de construção.  No entanto, um erro de tempo de execução é possível.  
  
 Essa situação implica três condições a seguir forem verdadeiras:  
  
-   Há mais de um arquivo no disco com o mesmo nome.  
  
-   Um dos arquivos não é um assembly, mas o outro.  
  
-   Caminho referências primeiro procura no diretório que contém o arquivo não é um assembly.  
  
 **Para corrigir este erro**  
  
-   Modificar a ordem na qual o seu projeto procura diretórios, procurando referências.  Consulte [NIB: Reference Paths Dialog Box \(Visual Basic\)](http://msdn.microsoft.com/pt-br/8e549b39-7256-456a-8fd7-089b23facf9c) para maiores informações.  
  
## Consulte também  
 [Solucionando Problemas de Referências Quebradas](../ide/troubleshooting-broken-references.md)   
 [Como adicionar ou remover referências usando a caixa de diálogo Adicionar Referência](http://msdn.microsoft.com/pt-br/3bd75d61-f00c-47c0-86a2-dd1f20e231c9)   
 [Assemblies in the Common Language Runtime](http://msdn.microsoft.com/pt-br/33a0bc6a-6bb3-44c7-ada7-4a046e8c0945)