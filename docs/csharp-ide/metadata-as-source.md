---
title: "Metadados como origem | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "comando Ir para Definição"
  - "Janela de definição, exibindo metadados como origem de código"
  - "metadados como origem [C#]"
ms.assetid: 4945a07f-b3be-4f05-a587-fc29058aa8fa
caps.latest.revision: 14
caps.handback.revision: 14
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Metadados como origem
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Metadados como fonte permitem exibir os metadados que aparecem como código\-fonte C\# em um buffer de somente leitura.  Isso permite que um modo de exibição das declarações dos tipos e membros \(sem implementações\).  É possível visualizar metadados como fonte, executando o  **Go To Definition** comando para tipos ou membros cujo código fonte não está disponível no seu projeto ou solução.  
  
> [!NOTE]
>  Ao tentar executar o  **Go To Definition** de comando para tipos ou membros que são marcados como internos, o ambiente de desenvolvimento integrado \(IDE\) não exibe seus metadados como fonte, independentemente do assembly de referência está ou não um amigo.  
  
 É possível visualizar metadados como fonte em qualquer Editor de código ou a  **Definição do código de** janela.  
  
## Visualização de metadados como fonte no Editor de código  
 Quando você executa o  **Go To Definition** comando para um item cujo código fonte não está disponível, um documento com abas que contém um modo de exibição de metadados do item, exibido como fonte, aparece no Editor de código.  O nome do tipo, seguido por  **\[de metadados\]**, aparece na guia do documento.  
  
 Por exemplo, se você executar o  **Go To Definition** comando <xref:System.Console>, metadados para <xref:System.Console> aparece no Editor de código, como C\# código\-fonte semelhante a sua declaração, mas sem uma implementação.  
  
 ![Metadados como fonte](~/csharp-ide/media/metadatasource.png "MetadataSource")  
  
## Visualização de metadados como fonte na janela de definição de código  
 Quando o  **Definição do código de** janela está ativa ou visível, o IDE executa automaticamente o  **Go To Definition** comando para itens sob o cursor no Editor de código e para itens que estão selecionados na  **Class View** ou o  **Pesquisador de objetos**.  Se o código\-fonte não está disponível para esse item, o IDE exibe os metadados do item como fonte na  **Definição do código de** janela.  
  
 Por exemplo, se você colocar o cursor dentro da palavra <xref:System.Console> no Editor de código, metadados para <xref:System.Console> aparece como a fonte na  **Definição do código de** janela.  A fonte é semelhante a <xref:System.Console> declaração, mas sem uma implementação.  
  
 Se você deseja ver a declaração de um item que aparece no  **Definição do código de** janela, clique com o botão direito no item e clique em  **Go To Definition**.