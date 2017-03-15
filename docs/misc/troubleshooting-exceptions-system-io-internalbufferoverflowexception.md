---
title: "Exce&#231;&#245;es de solu&#231;&#227;o de problemas: System.IO.InternalBufferOverflowException | Microsoft Docs"
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
  - "Classe InternalBufferOverflowException"
ms.assetid: 1f58ca15-c4e4-4af9-9a3d-42d2cf919cbe
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Exce&#231;&#245;es de solu&#231;&#227;o de problemas: System.IO.InternalBufferOverflowException
Um <xref:System.IO.InternalBufferOverflowException> exceção é lançada quando o buffer interno estoura.  
  
## Dicas associadas  
 **Ao usar FileSystemWatcher, filtre notificações de alteração indesejadas.**  
 Um Inspetor de sistema de arquivos, quando você for notificado de alterações de arquivo, o sistema armazena essas alterações em um buffer que o componente cria e passa para as interfaces de programação de aplicativo \(APIs\). Se houver muitas alterações em um curto período de tempo, o buffer pode estourar, resultando em um <xref:System.IO.InternalBufferOverflowException> exceção, que perde todas as alterações. Para evitar que o buffer estoure, use o <xref:System.IO.FileSystemWatcher.NotifyFilter%2A> e <xref:System.IO.FileSystemWatcher.IncludeSubdirectories%2A> notificações de alteração de propriedades para filtrar indesejados. Para obter mais informações, consulte <xref:System.IO.FileSystemWatcher>.  
  
## Comentários  
 Você também pode aumentar o tamanho do buffer interno através do <xref:System.IO.FileSystemWatcher.InternalBufferSize%2A> propriedade. No entanto, aumentar o tamanho do buffer afetará o desempenho é melhor manter o buffer o menor possível.  
  
## Consulte também  
 <xref:System.IO.InternalBufferOverflowException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)