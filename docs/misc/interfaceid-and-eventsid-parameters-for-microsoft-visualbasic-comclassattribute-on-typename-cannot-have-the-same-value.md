---
title: "Par&#226;metros &#39;InterfaceId&#39; e &#39;EventsId&#39; para &#39;Microsoft.VisualBasic.ComClassAttribute&#39; em &#39;&lt; typename &gt;&#39; n&#227;o podem ter o mesmo valor | Microsoft Docs"
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
  - "bc32507"
  - "vbc32507"
helpviewer_keywords: 
  - "BC32507"
ms.assetid: 762e2990-e578-492d-b8ee-11658b6069fc
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Par&#226;metros &#39;InterfaceId&#39; e &#39;EventsId&#39; para &#39;Microsoft.VisualBasic.ComClassAttribute&#39; em &#39;&lt; typename &gt;&#39; n&#227;o podem ter o mesmo valor
Um `COMClassAttribute` Bloco de atributo especifica o mesmo identificador globalmente exclusivo \(GUID\) para a interface quanto ao evento de criação. Se estes identificadores são ambos fornecidos, eles devem ser diferentes. Eles também precisam ser diferentes do identificador de classe.  
  
 Um GUID consiste de 16 bytes, dos quais os oito primeiros são numéricos e os oito últimos são binários. Ele é gerado por utilitários Microsoft como uuidgen.exe e garantido como sendo exclusivo.  
  
 **ID do erro:** BC32507  
  
### Para corrigir este erro  
  
1.  Determina os GUIDs corretos necessários para identificar o evento de criação e a interface para o objeto COM.  
  
2.  Certifique\-se de que as cadeias de caracteres GUID apresentadas para o `COMClassAttribute` Bloco de atributo são copiados corretamente.  
  
## Consulte também  
 [NÃO está em compilação: Atributos usados no Visual Basic](http://msdn.microsoft.com/pt-br/22231318-8a40-49af-9245-e0aab723563b)   
 [NÃO está em compilação: Aplicação de atributos](http://msdn.microsoft.com/pt-br/2b1703ed-4437-49b3-bc0b-568094324f47)   
 [Classe ComClassAttribute](http://msdn.microsoft.com/pt-br/5c2f0835-9210-47dc-bc59-5c1769953574)