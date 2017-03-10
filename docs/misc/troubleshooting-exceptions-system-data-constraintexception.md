---
title: "Exce&#231;&#245;es de solu&#231;&#227;o de problemas: System.Data.ConstraintException | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "JScript"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "Classe ConstraintException"
ms.assetid: 5e9ba3b8-73d5-4657-a76e-63ab6ea32cf1
caps.latest.revision: 19
caps.handback.revision: 19
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Exce&#231;&#245;es de solu&#231;&#227;o de problemas: System.Data.ConstraintException
Um <xref:System.Data.ConstraintException> exceção é lançada quando é tentada uma ação que viola uma restrição.  
  
## Dicas associadas  
 **Relax ou desative as restrições em seus conjuntos de dados**.  
 Você pode usar o <xref:System.Data.DataSet.EnforceConstraints%2A> propriedade para desativar temporariamente restrições ao preencher tabelas em um <xref:System.Data.DataSet> objeto.  
  
 **Verifique se que você não está tentando atribuir um valor a um campo de chave primária onde a chave primária já existe na tabela de dados.**  
 Se a chave primária existir, essa exceção é lançada.  
  
 **Limpar conjuntos de dados antes de carregá\-los do estado de exibição.**  
 Se houver dados no dataset quando você carregá\-lo, essa exceção pode ser lançada.  
  
## Consulte também  
 <xref:System.Data.ConstraintException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)