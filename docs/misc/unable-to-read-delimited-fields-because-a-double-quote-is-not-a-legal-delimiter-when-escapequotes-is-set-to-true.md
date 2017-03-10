---
title: "N&#227;o &#233; poss&#237;vel ler campos delimitados porque aspas duplas n&#227;o s&#227;o um delimitador v&#225;lido quando EscapeQuotes for definida como True | Microsoft Docs"
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
  - "vbrTextFieldParser_IllegalDelimiter"
ms.assetid: ab8a0c3a-b89c-4617-9e31-7e81f5dca433
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# N&#227;o &#233; poss&#237;vel ler campos delimitados porque aspas duplas n&#227;o s&#227;o um delimitador v&#225;lido quando EscapeQuotes for definida como True
O `TextFieldParser` não pode ler o arquivo porque uma aspas \("\) foi fornecida como o delimitador e `EscapeQuotes` é definido como `True`.  
  
### Para corrigir este erro  
  
-   Defina `EscapeQuotes` para `False`.  
  
## Consulte também  
 [Método TextFieldParser.SetDelimiters](http://msdn.microsoft.com/pt-br/21fa40ec-5866-4d0e-9fd9-c708a190dcc9)   
 [Propriedade Delimiters](http://msdn.microsoft.com/pt-br/4eb18f4d-3011-40a9-b668-be93eed0444f)   
 [Como ler a partir de arquivos de texto separados por vírgulas](../Topic/How%20to:%20Read%20From%20Comma-Delimited%20Text%20Files%20in%20Visual%20Basic.md)   
 [Objeto TextFieldParser](/dotnet/visual-basic/language-reference/objects/textfieldparser-object)