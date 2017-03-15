---
title: "Membro de atributo &#39;&lt; nome do membro &gt;&#39; n&#227;o pode ser o destino de uma atribui&#231;&#227;o porque n&#227;o est&#225; declarado como &#39;Public&#39; | Microsoft Docs"
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
  - "vbc31511"
  - "bc31511"
helpviewer_keywords: 
  - "BC31511"
ms.assetid: f8c958f6-58a4-4aff-b8c3-f2e9481e8132
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Membro de atributo &#39;&lt; nome do membro &gt;&#39; n&#227;o pode ser o destino de uma atribui&#231;&#227;o porque n&#227;o est&#225; declarado como &#39;Public&#39;
Foi feita uma tentativa para atribuir um valor a um membro particular de um atributo.  
  
 **ID do erro:** BC31511  
  
### Para corrigir este erro  
  
1.  Remova a atribuição.  
  
2.  Se usando atributos personalizados que você desenvolveu, altere o modificador de acesso do membro de atributo para `Public`.  
  
## Consulte também  
 [NÃO está em compilação: Atributos no Visual Basic](http://msdn.microsoft.com/pt-br/620bfc0e-4582-4c8b-8432-ebc5c3dccc22)   
 [Público](/dotnet/visual-basic/language-reference/modifiers/public)