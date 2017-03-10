---
title: "Projeto j&#225; tem uma refer&#234;ncia ao assembly &lt; assemblyidentity &gt; | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc32208"
  - "vbc32208"
helpviewer_keywords: 
  - "BC32208"
ms.assetid: a9f73a2c-5135-4315-bf2c-710ef216095d
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Projeto j&#225; tem uma refer&#234;ncia ao assembly &lt; assemblyidentity &gt;
Projeto já tem uma referência ao assembly \< assemblyidentity \>. Uma segunda referência a '\< filepath \>' não pode ser adicionada.  
  
 Um projeto faz mais de uma referência ao mesmo assembly.  
  
 Identidade do assembly inclui o nome do assembly, versão, chave pública, se houver e cultura.  
  
 Uma possível causa desse erro é uma referência a outra cópia do assembly por meio de um caminho de arquivo diferente da referência original.  
  
 **ID do erro:** BC32208  
  
### Para corrigir este erro  
  
-   Remova a segunda referência. Não é necessário porque se refere ao mesmo assembly.  
  
## Consulte também  
 [Gerenciando referências em um projeto](../ide/managing-references-in-a-project.md)   
 [PONTA como: Adicionar ou remover referências usando a caixa de diálogo Adicionar referência](http://msdn.microsoft.com/pt-br/3bd75d61-f00c-47c0-86a2-dd1f20e231c9)   
 [Solucionando Problemas de Referências Quebradas](../ide/troubleshooting-broken-references.md)