---
title: "Exce&#231;&#245;es de solu&#231;&#227;o de problemas: Microsoft.VisualBasic.FileIO.TextFieldParser.MalformedLineException | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
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
  - "Exceção Microsoft.VisualStudio.Tools.Applications.Runtime.ControlNotFoundException"
ms.assetid: d780b8cc-c3f1-45ed-8f8e-3f8728a4b770
caps.latest.revision: 14
caps.handback.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Exce&#231;&#245;es de solu&#231;&#227;o de problemas: Microsoft.VisualBasic.FileIO.TextFieldParser.MalformedLineException
Um <xref:Microsoft.VisualBasic.FileIO.MalformedLineException> exceção é lançada quando um <xref:Microsoft.VisualBasic.FileIO.TextFieldParser> não é possível analisar uma linha usando o formato especificado.  
  
 O `Error Line` propriedade do objeto de exceção contém o texto da linha que causou o erro.  
  
## Dicas associadas  
 **Verifique se que os parâmetros TextFieldType e delimitadores sejam definidos corretamente**  
 O `TextFieldType` \(delimitado ou de largura fixa\) deve corresponder ao formato do arquivo. Se o `TextFieldType` é `FixedWidth`, verifique se o `FieldWidths` propriedade foi definida corretamente. Se o `TextFieldType` é `Delimited`, verifique se o `Delimiters` propriedade foi definida corretamente.  
  
## Consulte também  
 <xref:Microsoft.VisualBasic.FileIO.MalformedLineException>   
 [Analisando arquivos de texto com o objeto TextFieldParser](/dotnet/visual-basic/developing-apps/programming/drives-directories-files/parsing-text-files-with-the-textfieldparser-object)   
 [Como ler a partir de arquivos de texto separados por vírgulas](../Topic/How%20to:%20Read%20From%20Comma-Delimited%20Text%20Files%20in%20Visual%20Basic.md)   
 [Como ler a partir de arquivos de texto de largura fixa](../Topic/How%20to:%20Read%20From%20Fixed-width%20Text%20Files%20in%20Visual%20Basic.md)