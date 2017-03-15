---
title: "&#39;DllImportAttribute&#39; n&#227;o pode ser aplicado a um m&#233;todo &#233; gen&#233;rico ou aninhado em um tipo gen&#233;rico | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc31526"
  - "bc31526"
helpviewer_keywords: 
  - "BC31526"
ms.assetid: 6f153808-1945-4c99-85ae-8bd3b35ee5a2
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;DllImportAttribute&#39; n&#227;o pode ser aplicado a um m&#233;todo &#233; gen&#233;rico ou aninhado em um tipo gen&#233;rico
Um procedimento é declarado com o <xref:System.Runtime.InteropServices.DllImportAttribute>, mas o procedimento é genérico ou ele está contido em uma classe genérica ou estrutura.  
  
 O common language runtime \(CLR\) reconhece esse atributo e seu <xref:System.Runtime.InteropServices._Assembly.EntryPoint%2A> propriedade como designar um procedimento de substituição definido em uma biblioteca de vínculo dinâmico \(DLL\) não gerenciada fora do .NET Framework. Quando o código chama o procedimento ao qual o <xref:System.Runtime.InteropServices.DllImportAttribute> é aplicado, o common language runtime chama o procedimento não gerenciado designado em vez disso.  
  
 Porque não gerenciadas plataformas fora do .NET Framework não reconhecem tipos genéricos, você não pode interoperar com eles usando tipos genéricos.  
  
 **ID do erro:** BC31526  
  
### Para corrigir este erro  
  
-   Se o procedimento nem seu recipiente precisa ser genéricos, remova o `Of` cláusulas para que eles não fiquem genéricos.  
  
-   Se o procedimento ou seu recipiente precisa ser genéricos, remova o <xref:System.Runtime.InteropServices.DllImportAttribute> da declaração deste procedimento.  
  
## Consulte também  
 <xref:System.Runtime.InteropServices.DllImportAttribute>   
 [Tipos genéricos no Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)