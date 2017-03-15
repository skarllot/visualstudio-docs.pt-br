---
title: "Matrizes do tipo &#39;System. Void&#39; n&#227;o s&#227;o permitidas nesta express&#227;o | Microsoft Docs"
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
  - "vbc31428"
  - "bc31428"
helpviewer_keywords: 
  - "BC31428"
ms.assetid: 21d77b56-585f-4107-b7ec-21933ba58017
caps.latest.revision: 5
caps.handback.revision: 5
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Matrizes do tipo &#39;System. Void&#39; n&#227;o s&#227;o permitidas nesta express&#227;o
Uma expressão em uma instrução de atribuição ou uma declaração especifica uma matriz do tipo <xref:System.Void>.  
  
 O <xref:System.Void> estrutura é um tipo especializado usado internamente pelo .NET Framework e particularmente por Visual c\# e Visual C\+\+. Representa um tipo de valor de retorno para um método que não retorna um valor. Visual Basic usa uma `Sub` procedimento quando um valor não é retornado e um `Function` procedimento quando um valor é retornado.  
  
 Matrizes do tipo <xref:System.Void> não são significativas e não são permitidas em qualquer contexto.  
  
 **ID do erro:** BC31428  
  
### Para corrigir este erro  
  
1.  Remova os parênteses que designa uma matriz.  
  
2.  A menos que você tenha um motivo específico para comparar um tipo de tempo de execução para <xref:System.Void>, remova as referências a ele mesmo.  
  
## Consulte também  
 <xref:System.Void>