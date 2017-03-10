---
title: "Exce&#231;&#245;es de solu&#231;&#227;o de problemas: System.DuplicateWaitObjectException | Microsoft Docs"
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
  - "Classe DuplicateWaitObjectException"
ms.assetid: b9ff6932-a7cf-4a89-bd7d-e4ef1a3ff353
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Exce&#231;&#245;es de solu&#231;&#227;o de problemas: System.DuplicateWaitObjectException
Um <xref:System.DuplicateWaitObjectException> exceção será gerada se a matriz de <xref:System.Threading.WaitHandle> objetos passados para <xref:System.Threading.WaitHandle.WaitAll%2A> ou <xref:System.Threading.WaitHandle.WaitAny%2A> contém os identificadores de sistema operacional duplicados.  
  
## Dicas associadas  
 **Verifique se os objetos WaitHandle passados para WaitAll ou WaitAny são exclusivos.**  
 A <xref:System.Threading.WaitHandle> matriz não pode conter várias referências ao mesmo objeto.  
  
### Comentários  
 O Common Language Runtime \(CLR\) fornece um mecanismo de sincronização de segmentos com base em objetos de sincronização aguardando execução em uma matriz de <xref:System.Threading.WaitHandle> objetos.  
  
## Consulte também  
 <xref:System.DuplicateWaitObjectException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)