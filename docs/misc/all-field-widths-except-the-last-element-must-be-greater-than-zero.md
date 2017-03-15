---
title: "Todas as larguras de campo, exceto o &#250;ltimo elemento, devem ser maiores que zero | Microsoft Docs"
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
  - "vbrTextFieldParser_FieldWidthsMustPositive"
ms.assetid: 41d8c661-a749-4c89-be56-905c6e7c3c9d
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Todas as larguras de campo, exceto o &#250;ltimo elemento, devem ser maiores que zero
Todas as larguras de campo, exceto o último elemento, devem ser maiores que zero. Uma largura de campo que menor ou igual a zero no último elemento indica que o último campo é de comprimento variável.  
  
 A operação falhou porque uma largura de campo que não seja o último elemento está definida como zero ou menos. Uma largura de campo que menor ou igual a zero pode ser usado como o último elemento para indicar que o último campo é de comprimento variável, mas não pode ser usada como qualquer outro elemento.  
  
### Para corrigir este erro  
  
-   Defina a largura do campo para o comprimento correto.  
  
## Consulte também  
 [Método TextFieldParser.SetFieldWidths](http://msdn.microsoft.com/pt-br/958fed9f-e0f3-4fc5-83b4-386156bdf036)   
 [Propriedade TextFieldParser.FieldWidths](http://msdn.microsoft.com/pt-br/c6985360-60c6-494e-89e7-43b6b73f2597)   
 [Como ler a partir de arquivos de texto de largura fixa](../Topic/How%20to:%20Read%20From%20Fixed-width%20Text%20Files%20in%20Visual%20Basic.md)   
 [Objeto TextFieldParser](/dotnet/visual-basic/language-reference/objects/textfieldparser-object)