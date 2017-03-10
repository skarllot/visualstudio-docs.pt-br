---
title: "Exce&#231;&#245;es de solu&#231;&#227;o de problemas: System.IO.IOException | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Classe IOException"
ms.assetid: 87812daa-0784-43dc-b3dc-6652a960c362
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Exce&#231;&#245;es de solu&#231;&#227;o de problemas: System.IO.IOException
A <xref:System.IO.IOException> é lançada quando ocorre um erro de e\/s, como falha para ler ou gravar em um arquivo.  
  
## Dicas associadas  
 **Verifique se o arquivo e diretório existe.**  
 Verifique se que o diretório que você está tentando ler \/ gravar existe. Verifique se o arquivo que você está tentando ler existe.  
  
### Comentários  
 <xref:System.IO.IOException> é a classe base para exceções geradas ao acessar informações usando fluxos, arquivos e diretórios.  
  
 Biblioteca de classes Base inclui os seguintes tipos, cada um deles é uma classe derivada de <xref:System.IO.IOException>:  
  
-   <xref:System.IO.DirectoryNotFoundException>  
  
-   <xref:System.IO.EndOfStreamException>  
  
-   <xref:System.IO.FileNotFoundException>  
  
-   <xref:System.IO.FileLoadException>  
  
-   <xref:System.IO.PathTooLongException>  
  
## Consulte também  
 <xref:System.IO.IOException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)   
 [NOTINBUILD como: criar aplicativos do Console CLR](http://msdn.microsoft.com/pt-br/b8af4197-e65f-4b17-b18e-b9e92965d026)