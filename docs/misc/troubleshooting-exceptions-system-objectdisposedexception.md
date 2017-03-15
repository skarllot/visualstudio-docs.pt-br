---
title: "Exce&#231;&#245;es de solu&#231;&#227;o de problemas: System.ObjectDisposedException | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "JScript"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "Classe ObjectDisposedException, solução de problemas"
ms.assetid: 702912b6-e927-4f8e-8b7c-2e1880312b0e
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Exce&#231;&#245;es de solu&#231;&#227;o de problemas: System.ObjectDisposedException
Um <xref:System.ObjectDisposedException> exceção é lançada quando uma operação é tentada em um objeto descartado, como uma chave de registro ou de fluxo fechado.  
  
## Dicas associadas  
 **Verifique se que você não liberou um recurso antes de tentar usá\-lo.**  
 Por exemplo, se você tentar manipular um fluxo, verifique se que ele não foi fechado anteriormente.  
  
## Consulte também  
 <xref:System.ObjectDisposedException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)