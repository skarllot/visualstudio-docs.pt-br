---
title: "CLS02809 de aviso de conformidade CLS | Microsoft Docs"
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
  - "CLS02809"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CLS02809"
ms.assetid: a6e7b8e5-1587-437e-9d07-8a32fc5c4842
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "douge"
---
# CLS02809 de aviso de conformidade CLS
Propriedades deverão seguir um padrão de nomenclatura específico  
  
 Propriedades deverão seguir um padrão de nomenclatura específico; o nome de funções do acessador de propriedade será o mesmo que o nome da propriedade, precedido por **get \_** ou **set \_**.  
  
 O **como specialname** atributo deverá ser ignorado em comparações de nome apropriadas e respeitar as regras do identificador.  
  
 Para mais informações sobre conformidade verificação CLS, consulte [Assemblies compatíveis com CLS](http://msdn.microsoft.com/pt-br/3320b57e-ea55-4697-a17d-f509a36a3c93).  
  
 A seguinte declaração de função \(usando a linguagem do assembly MSIL\) mostra o que poderia causar CLS02809:  
  
```  
.method public specialname instance void set_MyPropertya(int32 __unnamed000) cil managed { } // end of method One::set_MyProperty .method public specialname instance int32 get_MyPropertya() cil managed { } // end of method One::get_MyProperty .property instance int32 MyProperty() { .get instance int32 One::get_MyPropertya() .set instance void One::set_MyPropertya(int32) } // end of property One::MyProperty  
```  
  
 Observe que os nomes dos métodos de acessador diferem do nome da propriedade.  Assegurando que todos os nomes de propriedade sigam o padrão de nomenclatura, você pode resolver CLS02809.