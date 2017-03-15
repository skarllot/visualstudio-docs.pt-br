---
title: "Compilador CS0809 de aviso (n&#237;vel 1) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS0809"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0809"
ms.assetid: 2c2f0248-ab3a-4cdc-a1b0-2f0e05eac4c9
caps.latest.revision: 9
caps.handback.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilador CS0809 de aviso (n&#237;vel 1)
O membro obsoleto 'MembroA' substitui o membro não obsoleto 'memberB'.  
  
 Normalmente, um membro que está marcado como obsoleto não deve substituir um membro que não está marcado como obsoleto. Esse aviso é gerado no [!INCLUDE[vs_orcas_long](../debugger/includes/vs_orcas_long_md.md)] mas não no [!INCLUDE[vsprvslong](../code-quality/includes/vsprvslong_md.md)].  
  
### Para corrigir este erro  
  
1.  Remover o `Obsolete` atributo do membro de substituição, ou adicioná\-lo para o membro da classe base.  
  
## Exemplo  
  
```  
// CS0809.cs public class Base { public virtual void Test1() { } } public class C : Base { [System.Obsolete()] public override void Test1() // CS0809 { } }  
```