---
title: "Objeto referenciado tem um valor de &#39;Nothing&#39; | Microsoft Docs"
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
  - "bc30760"
  - "vbc30760"
helpviewer_keywords: 
  - "BC30760"
ms.assetid: 7e792fd8-2880-402b-a908-c89e5b028300
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Objeto referenciado tem um valor de &#39;Nothing&#39;
O objeto que está sendo usado tem o valor `Nothing`, mas um valor utilizável é esperado.`Nothing` é um valor que indica que um objeto não tem valor, ou porque nenhum valor foi atribuído a ele, ou ele foi atribuído o valor `Nothing`.  
  
 **ID do erro:** BC30760  
  
### Para corrigir este erro  
  
1.  Verifique o objeto para certificar\-se de que ele foi declarado no escopo do procedimento onde ocorreu o erro.  
  
2.  Verifique se o valor do objeto está sendo definido.  
  
    > [!NOTE]
    >  O valor `Nothing` não é o mesmo como zero ou uma cadeia de caracteres vazia. Você pode usar `IsNothing` para verificar se um objeto contém o valor `Nothing`.  
  
## Consulte também  
 [nada](/dotnet/visual-basic/language-reference/nothing)   
 [NÃO está em compilação: Função de IsNothing](http://msdn.microsoft.com/pt-br/5b2a4626-e6a9-49d1-b9b1-fcc6a1302319)