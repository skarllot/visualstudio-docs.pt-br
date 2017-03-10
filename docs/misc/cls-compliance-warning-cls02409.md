---
title: "CLS02409 de aviso de conformidade CLS | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CLS02409"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CLS02409"
ms.assetid: 71d566ce-59c2-4d3d-97ff-72f4e9bd21ee
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "douge"
---
# CLS02409 de aviso de conformidade CLS
Os métodos que implementam os métodos getter e setter de uma propriedade devem ser marcados como SpecialName nos metadados  
  
 Os métodos que implementam os métodos getter e setter de uma propriedade não foram marcados com **como specialname** nos metadados.  
  
 Para mais informações sobre conformidade verificação CLS, consulte [Assemblies compatíveis com CLS](http://msdn.microsoft.com/pt-br/3320b57e-ea55-4697-a17d-f509a36a3c93).  
  
 A seguinte declaração de função \(usando a linguagem do assembly MSIL\) mostra o que poderia causar CLS02409:  
  
```  
.method public instance int32 get_MyProperty() cil managed  
```  
  
 Adicionando a **como specialname** palavra\-chave, você pode resolver este aviso:  
  
```  
.method public specialname instance int32 get_MyProperty() cil managed  
```