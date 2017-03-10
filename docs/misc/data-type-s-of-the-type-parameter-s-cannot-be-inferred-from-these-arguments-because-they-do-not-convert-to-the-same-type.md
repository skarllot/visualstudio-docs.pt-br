---
title: "Tipos de dados dos par&#226;metros de tipo n&#227;o podem ser inferidos esses argumentos porque eles n&#227;o s&#227;o convertidos no mesmo tipo | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc36659"
  - "bc36659"
  - "vbc36656"
  - "bc36656"
helpviewer_keywords: 
  - "BC36659"
  - "BC36656"
ms.assetid: 0aa809da-3b44-4d78-b3c5-0a148bdf7ce8
caps.latest.revision: 6
caps.handback.revision: 6
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Tipos de dados dos par&#226;metros de tipo n&#227;o podem ser inferidos esses argumentos porque eles n&#227;o s&#227;o convertidos no mesmo tipo
Tipos de dados dos parâmetros de tipo não podem ser inferidos a partir destes argumentos porque eles não são convertidos no mesmo tipo. Especificar os dados de tipos explicitamente podem corrigir esse erro.  
  
 Esse erro ocorre quando ocorre falha na resolução de sobrecarga. Ele ocorre como uma mensagem subordinada que indica por que um candidato sobrecarga específica foi eliminado. O erro explica que o compilador não pode usar inferência de tipo para localizar os tipos de dados para os parâmetros de tipo que são compatíveis com os argumentos.  
  
> [!NOTE]
>  Quando especificar argumentos não é uma opção \(por exemplo, para operadores de consulta em expressões de consulta\), a mensagem de erro aparece sem a segunda frase.  
  
 Para obter mais informações e exemplos, consulte [Tipos de dados dos parâmetros de tipo no método '\< methodname \>' não podem ser inferidos esses argumentos porque eles não são convertidos no mesmo tipo](../Topic/Data%20type\(s\)%20of%20the%20type%20parameter\(s\)%20in%20method%20'%3Cmethodname%3E'%20cannot%20be%20inferred%20from%20these%20arguments%20because%20they%20do%20not%20convert%20to%20the%20same%20type.md).  
  
 **ID do erro:** BC36659 e BC36656  
  
## Consulte também  
 [Conversão de delegado reduzida](/dotnet/visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion)   
 [Procedimentos genéricos no Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-procedures)   
 [Resolução de sobrecarga](/dotnet/visual-basic/programming-guide/language-features/procedures/overload-resolution)