---
title: "Codifica&#231;&#227;o n&#227;o pode ser definida como Nothing | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 59f7c731-8291-4a85-bf51-c225e48cdc84
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Codifica&#231;&#227;o n&#227;o pode ser definida como Nothing
Uma tentativa de ler ou gravar em um arquivo falhou porque o parâmetro `encoding` foi definido como `Nothing` mas requer um valor válido.  
  
 <xref:System.Text.Encoding> é usado para determinar que codificação usar ao gravar em um arquivo. O padrão é UTF\-8.  
  
### Para corrigir este erro  
  
-   Forneça um valor válido para o `encoding` parâmetro.  
  
## Consulte também  
 [Codificações de arquivo](/dotnet/visual-basic/developing-apps/programming/drives-directories-files/file-encodings)   
 [Lendo a partir de arquivos](/dotnet/visual-basic/developing-apps/programming/drives-directories-files/reading-from-files)   
 [Gravando em arquivos](/dotnet/visual-basic/developing-apps/programming/drives-directories-files/writing-to-files)   
 [Método ReadAllText](http://msdn.microsoft.com/pt-br/3a7ac8be-fb1d-4087-bc65-167d6754d57f)   
 [Método WriteAllText](http://msdn.microsoft.com/pt-br/f507460c-87d9-4504-b74f-3ff825c7d5c4)