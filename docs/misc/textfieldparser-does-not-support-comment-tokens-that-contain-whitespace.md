---
title: "TextFieldParser n&#227;o d&#225; suporte a tokens de coment&#225;rio que cont&#234;m espa&#231;os em branco | Microsoft Docs"
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
  - "vbrTextFieldParser_WhitespaceInToken"
ms.assetid: 55107656-270e-4bbb-841a-478904df8e07
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# TextFieldParser n&#227;o d&#225; suporte a tokens de coment&#225;rio que cont&#234;m espa&#231;os em branco
Foi fornecido um token de comentário que contém espaço em branco. O `TextFieldParser` não oferece suporte a tokens de comentário que contêm espaços em branco, a menos que o espaço em branco ocorra no início do token. Espaço em branco ocorrendo no início de um token é ignorado.  
  
### Para corrigir este erro  
  
-   Forneça um símbolo de comentário corretos.  
  
## Consulte também  
 [Propriedade CommentTokens](http://msdn.microsoft.com/pt-br/2e6b6435-4bee-4c14-a353-e8f2c82e2d61)   
 [Analisando arquivos de texto com o objeto TextFieldParser](/dotnet/visual-basic/developing-apps/programming/drives-directories-files/parsing-text-files-with-the-textfieldparser-object)   
 [Objeto TextFieldParser](/dotnet/visual-basic/language-reference/objects/textfieldparser-object)