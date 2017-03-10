---
title: "The property &lt;property name&gt; cannot be deleted | Microsoft Docs"
ms.custom: ""
ms.date: "09/21/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 55873f74-7834-4ec1-8815-eeeb65618d87
caps.latest.revision: 2
caps.handback.revision: 2
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# The property &lt;property name&gt; cannot be deleted
A propriedade \< property name \> não pode ser excluída porque ele está definido como a propriedade de discriminador para herança entre \< nome da classe \> e \< nome da classe \>  
  
 A propriedade selecionada é definida como **Propriedade Discriminatória** para herança entre as classes mencionadas na mensagem de erro.  Propriedades não podem ser excluídas estão participando na configuração de herança entre classes de dados.  
  
 Definir **Propriedade Discriminatória** a uma propriedade de classe diferente de dados para permitir a exclusão com êxito da propriedade desejada.  
  
### Para corrigir este erro  
  
1.  Em object relational Designer de Objetos, selecione a linha de herança que conecta as classes de dados mencionadas na mensagem de erro.  
  
2.  Defina a propriedade de **Discriminador** a uma propriedade diferente.  
  
3.  Tente excluir novamente a propriedade.  
  
## Consulte também  
 [Como: configurar a herança usando Object Relational Designer](../data-tools/how-to-configure-inheritance-by-using-the-o-r-designer.md)   
 [Herança de classe de dados \(Object Relational Designer\)](../data-tools/data-class-inheritance-o-r-designer.md)   
 [Walkthrough: Creating LINQ to SQL Classes by Using Single\-Table Inheritance \(O\/R Designer\)](../data-tools/walkthrough-creating-linq-to-sql-classes-by-using-single-table-inheritance-o-r-designer.md)