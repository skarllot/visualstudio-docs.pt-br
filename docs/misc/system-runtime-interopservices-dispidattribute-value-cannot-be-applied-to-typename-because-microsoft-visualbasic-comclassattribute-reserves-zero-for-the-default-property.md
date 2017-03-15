---
title: "Valor de &#39;System.Runtime.InteropServices.DispIdAttribute&#39; n&#227;o pode ser aplicado a &#39;&lt; typename &gt;&#39; porque &#39;Microsoft.VisualBasic.ComClassAttribute&#39; reserva zero para a propriedade padr&#227;o | Microsoft Docs"
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
  - "vbc32505"
  - "bc32505"
helpviewer_keywords: 
  - "BC32505"
ms.assetid: a7d5b948-2d72-48b1-8baf-bfaae36b0128
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Valor de &#39;System.Runtime.InteropServices.DispIdAttribute&#39; n&#227;o pode ser aplicado a &#39;&lt; typename &gt;&#39; porque &#39;Microsoft.VisualBasic.ComClassAttribute&#39; reserva zero para a propriedade padr&#227;o
Um <xref:System.Runtime.InteropServices.DispIdAttribute> Bloco de atributo especifica um valor DISPID de 0, que é reservado por `COMClassAttribute` para representar a propriedade padrão da classe à qual ela é aplicada.  
  
 O identificador de distribuição \(DISPID\) é usado no COM como um argumento para o `IDispatch:Invoke` método para acessar as propriedades e métodos expostos por um objeto COM.  
  
 **ID do erro:** BC32505  
  
### Para corrigir este erro  
  
-   Especifique um valor DISPID maior que zero em <xref:System.Runtime.InteropServices.DispIdAttribute>.  
  
## Consulte também  
 <xref:System.Runtime.InteropServices.DispIdAttribute>   
 [NÃO está em compilação: Atributos usados no Visual Basic](http://msdn.microsoft.com/pt-br/22231318-8a40-49af-9245-e0aab723563b)   
 [NÃO está em compilação: Aplicação de atributos](http://msdn.microsoft.com/pt-br/2b1703ed-4437-49b3-bc0b-568094324f47)   
 [Classe ComClassAttribute](http://msdn.microsoft.com/pt-br/5c2f0835-9210-47dc-bc59-5c1769953574)