---
title: "XSLT Default Templates | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 773dd34e-67d3-4997-8df9-b71e7f880d88
caps.latest.revision: 2
caps.handback.revision: 2
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# XSLT Default Templates
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Um modelo padrão será usado durante XSLT que processa quando não há nenhuma regra explícita modelo correspondente da folha de estilos.  O modelo padrão, também conhecido como regra de modelo interno, é definido na seção 5,8 de recomendação W3C XSLT 1,0.  O modelo padrão permite que o processador XSLT processe um nó, mesmo que não haja nenhuma regra explícita de modelo que corresponde a ele.  Entretanto, porque a regra de modelo interno não é explicitamente definida na folha de estilos, isso pode levar a resultados inesperados ou confundindo de transformação XSLT.  
  
 O depurador XSLT agora exibe o código de modelos de opção XSLT.  Quando você percorre uma transformação XSLT, se um modelo padrão é usado, o depurador exibe o modelo padrão em uma janela.  Isso permite que você percorrer o código de modelo padrão e os pontos de interrupção em suas declarações.  
  
## Consulte também  
 [Debugging XSLT](../xml-tools/debugging-xslt.md)