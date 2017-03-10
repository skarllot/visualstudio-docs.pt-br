---
title: "O atributo &#39;NonSerialized&#39; n&#227;o afetar&#225; esse membro porque sua classe recipiente n&#227;o &#233; exposta como &#39;Serializable&#39; | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc30772"
  - "bc30772"
helpviewer_keywords: 
  - "BC30772"
ms.assetid: 1014e944-40c1-4078-8a38-139736ef89da
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# O atributo &#39;NonSerialized&#39; n&#227;o afetar&#225; esse membro porque sua classe recipiente n&#227;o &#233; exposta como &#39;Serializable&#39;
Por padrão, as classes e seus membros são não\-serializáveis. O <xref:System.NonSerializedAttribute> atributo só é necessário se um membro de uma classe serializável não puder ser serializado.  
  
 **ID do erro:** BC30772  
  
### Para corrigir este erro  
  
-   Adicionar o <xref:System.SerializableAttribute> à classe.  
  
     – ou –  
  
-   Remover o <xref:System.NonSerializedAttribute> atributo do membro.  
  
## Consulte também  
 <xref:System.NonSerializedAttribute>   
 <xref:System.SerializableAttribute>   
 [NÃO está em compilação: Atributos no Visual Basic](http://msdn.microsoft.com/pt-br/620bfc0e-4582-4c8b-8432-ebc5c3dccc22)