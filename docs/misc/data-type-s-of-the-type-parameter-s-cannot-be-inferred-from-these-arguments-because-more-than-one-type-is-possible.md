---
title: "Tipos de dados dos par&#226;metros de tipo n&#227;o podem ser inferidos esses argumentos porque h&#225; mais de um tipo poss&#237;vel | Microsoft Docs"
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
  - "vbc36653"
  - "bc36653"
  - "vbc36650"
  - "bc36650"
helpviewer_keywords: 
  - "BC36650"
  - "BC36653"
ms.assetid: 79287e1f-7070-4a71-96d2-aee0a0c9d8bd
caps.latest.revision: 6
caps.handback.revision: 6
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Tipos de dados dos par&#226;metros de tipo n&#227;o podem ser inferidos esses argumentos porque h&#225; mais de um tipo poss&#237;vel
Tipos de dados dos parâmetros de tipo não podem ser inferidos a partir destes argumentos porque há mais de um tipo possível. Especificar os dados de tipos explicitamente podem corrigir esse erro.  
  
 Esse erro ocorre quando ocorre falha na resolução de sobrecarga. Ele ocorre como uma mensagem subordinada que indica por que um candidato sobrecarga específica foi eliminado. O erro explica que, se a inferência de tipos é aplicada para determinar o tipo de dados dos parâmetros de tipo do procedimento chamado genérico, o compilador encontrar mais de um tipo de dados para pelo menos um deles.  
  
> [!NOTE]
>  Quando especificar argumentos não é uma opção \(por exemplo, para operadores de consulta em expressões de consulta\), a mensagem de erro aparece sem a segunda frase.  
  
 Para obter mais informações e exemplos, consulte [Tipos de dados dos parâmetros de tipo no método '\< methodname \>' não podem ser inferidos esses argumentos porque há mais de um tipo possível](../Topic/Data%20type\(s\)%20of%20the%20type%20parameter\(s\)%20in%20method%20'%3Cmethodname%3E'%20cannot%20be%20inferred%20from%20these%20arguments%20because%20more%20than%20one%20type%20is%20possible.md).  
  
 **ID do erro:** BC36653 e BC36650  
  
## Consulte também  
 [Procedimentos genéricos no Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-procedures)   
 [Resolução de sobrecarga](/dotnet/visual-basic/programming-guide/language-features/procedures/overload-resolution)