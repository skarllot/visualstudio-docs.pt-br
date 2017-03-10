---
title: "&#39;DllImportAttribute&#39; n&#227;o pode ser aplicado a m&#233;todos de inst&#226;ncia | Microsoft Docs"
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
  - "vbc31529"
  - "bc31529"
helpviewer_keywords: 
  - "BC31529"
ms.assetid: c8bde5d7-c6bf-4d21-bb1a-e8627d65ad29
caps.latest.revision: 6
caps.handback.revision: 6
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;DllImportAttribute&#39; n&#227;o pode ser aplicado a m&#233;todos de inst&#226;ncia
Um procedimento não compartilhado é declarado com o <xref:System.Runtime.InteropServices.DllImportAttribute>.  
  
 O common language runtime \(CLR\) reconhece esse atributo e seu <xref:System.Runtime.InteropServices._Assembly.EntryPoint%2A> propriedade como designar um procedimento de substituição definido em uma biblioteca de vínculo dinâmico \(DLL\) não gerenciada fora do .NET Framework. Quando o código chama o procedimento ao qual o <xref:System.Runtime.InteropServices.DllImportAttribute> é aplicado, o common language runtime chama o procedimento não gerenciado designado em vez disso.  
  
 Porque não gerenciadas plataformas fora do .NET Framework não suportam procedimentos não compartilhados da mesma forma que o .NET Framework, você não pode interoperar com eles usando procedimentos não compartilhados.  
  
 **ID do erro:** BC31529  
  
### Para corrigir este erro  
  
-   Se o procedimento não precisa aplicar individualmente para cada instância de sua classe ou estrutura, em seguida, declare\-o como `Shared`.  
  
-   Se o procedimento não pode ser `Shared`, em seguida, remova o <xref:System.Runtime.InteropServices.DllImportAttribute> da declaração deste procedimento.  
  
## Consulte também  
 <xref:System.Runtime.InteropServices.DllImportAttribute>   
 [Compartilhado](/dotnet/visual-basic/language-reference/modifiers/shared)