---
title: "O projeto &#39;&lt; projectname1 &gt;&#39; faz uma refer&#234;ncia indireta ao projeto &#39;&lt; projectname2 &gt;&#39;, que cont&#233;m &#39;&lt; typename &gt;&#39; | Microsoft Docs"
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
  - "vbc31532"
  - "bc31532"
helpviewer_keywords: 
  - "BC31532"
ms.assetid: 9ef6574e-b049-4a2e-9b12-fea2dfe06cd1
caps.latest.revision: 6
caps.handback.revision: 6
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# O projeto &#39;&lt; projectname1 &gt;&#39; faz uma refer&#234;ncia indireta ao projeto &#39;&lt; projectname2 &gt;&#39;, que cont&#233;m &#39;&lt; typename &gt;&#39;
O projeto '\< projectname1 \>' faz uma referência indireta ao projeto '\< projectname2 \>', que contém '\< typename \>'. Adicione uma referência de projeto para '\< projectname2 \>' ao seu projeto.  
  
 Código no seu projeto acessa um tipo definido em outro projeto, mas seu projeto não tem uma referência direta ao projeto de definição.  
  
 O tipo pode ser uma classe, estrutura, interface, módulo ou enumeração.  
  
 O projeto que define o tipo citado produz um assembly que contém o tipo. Se seu projeto não referencia diretamente o projeto de definição, o compilador não pode garantir que o assembly que contém o tipo está na solução e disponível para acesso.  
  
 **ID do erro:** BC31532  
  
### Para corrigir este erro  
  
-   Determine qual projeto define o tipo citado e adicione uma referência a ele.  
  
## Consulte também  
 [NIB: Referenciando Namespaces e componentes](http://msdn.microsoft.com/pt-br/568fa759-796b-44cd-bf5e-1cf8de6e38fd)   
 [Gerenciando referências em um projeto](../ide/managing-references-in-a-project.md)   
 [PONTA: Referências](http://msdn.microsoft.com/pt-br/910912ce-0dc9-4569-9274-32c44a20cb2c)   
 [PONTA como: Adicionar ou remover referências usando a caixa de diálogo Adicionar referência](http://msdn.microsoft.com/pt-br/3bd75d61-f00c-47c0-86a2-dd1f20e231c9)