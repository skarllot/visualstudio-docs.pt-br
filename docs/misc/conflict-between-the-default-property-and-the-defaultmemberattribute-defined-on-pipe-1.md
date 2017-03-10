---
title: "Conflito entre a propriedade padr&#227;o e &#39;DefaultMemberAttribute&#39; definido em &#39;| 1&#39; | Microsoft Docs"
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
  - "vbc32304"
  - "bc32304"
helpviewer_keywords: 
  - "BC32304"
ms.assetid: 42803d13-ff1d-40ed-a4a8-269e2fb4aa01
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Conflito entre a propriedade padr&#227;o e &#39;DefaultMemberAttribute&#39; definido em &#39;| 1&#39;
Uma classe, estrutura ou interface declara uma propriedade padrão com o [Padrão](/dotnet/visual-basic/language-reference/modifiers/default) palavra\-chave, mas também se aplica a <xref:System.Reflection.DefaultMemberAttribute> para designar um membro diferente como o membro padrão.  
  
 Um tipo pode ter no máximo um membro padrão. Quando você declara uma propriedade padrão, Visual Basic aplica automaticamente a <xref:System.Reflection.DefaultMemberAttribute> para a classe, estrutura ou interface designando essa propriedade.  
  
 **ID do erro:** BC32304  
  
### Para corrigir este erro  
  
1.  Decida qual membro deve ser o membro padrão de classe, estrutura ou interface.  
  
2.  Remova a declaração conflitante \(tanto o `Default` palavra\-chave ou o <xref:System.Reflection.DefaultMemberAttribute>\).  
  
## Consulte também  
 <xref:System.Reflection.DefaultMemberAttribute>   
 [Padrão](/dotnet/visual-basic/language-reference/modifiers/default)   
 [NÃO está em compilação: Propriedades do padrão](http://msdn.microsoft.com/pt-br/a70f2a27-8176-4858-935e-f25afdd43ab5)   
 [Como declarar e chamar uma propriedade padrão no Visual Basic](../Topic/How%20to:%20Declare%20and%20Call%20a%20Default%20Property%20in%20Visual%20Basic.md)