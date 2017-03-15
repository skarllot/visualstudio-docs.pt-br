---
title: "Como: criar uma associa&#231;&#227;o (rela&#231;&#227;o) entre classes LINQ to SQL (Object Relational Designer) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 56133e65-81f3-44c3-bc28-ffdd0671a0d2
caps.latest.revision: 3
caps.handback.revision: 3
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Como: criar uma associa&#231;&#227;o (rela&#231;&#227;o) entre classes LINQ to SQL (Object Relational Designer)
Associações entre classes de entidade em [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] são análogas às relações entre tabelas em um banco de dados. Você pode criar associações entre classes de entidade usando o **Editor de associação** caixa de diálogo.  
  
 Você deve selecionar uma classe pai e filho, quando você usa o **Editor de associação** caixa de diálogo para criar uma associação. A classe pai é a classe de entidade que contém a chave primária; a classe filho é a classe de entidade que contém a chave estrangeira. Por exemplo, se a classes de entidade criadas que mapeiam para as tabelas Northwind Customers e Orders, a classe Customer seria a classe pai e a classe Order seria a classe filho.  
  
> [!NOTE]
>  Quando você arrasta tabelas de **Server Explorer**\/**Database Explorer** até o [!INCLUDE[vs_ordesigner_long](../data-tools/includes/vs_ordesigner_long_md.md)] \([!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]\), associações são criadas automaticamente com base nas relações de chave estrangeira existentes no banco de dados.  
  
 Depois de criar uma associação, quando você seleciona a associação em Object Relational Designer, há algumas propriedades configuráveis do **propriedades** janela. \(A associação é a linha entre as classes relacionadas.\) A tabela a seguir fornece descrições das propriedades de uma associação.  
  
|Propriedade|Descrição|  
|-----------------|---------------|  
|**Cardinalidade**|Controla se a associação um\-para\-muitos ou um para um.|  
|**Propriedade filho**|Especifica se deve criar uma propriedade no pai que é uma coleção ou referência para os registros filho no lado de chave estrangeira da associação. Por exemplo, na associação entre Customer e Order, se o **propriedade filho** é definido como **True**, uma propriedade chamada Orders é criada na classe pai.|  
|**Propriedade pai**|A propriedade na classe filho que referencia a classe pai associada. Por exemplo, a associação entre Customer e Order, uma propriedade chamada Customer que referencia o cliente associado para um pedido é criada na classe Order.|  
|**Propriedades participantes**|Exibe as propriedades de associação e fornece um **reticências** botão \(...\) que reabre o **Editor de associação** caixa de diálogo.|  
|**Exclusivo**|Especifica se as colunas de destino estrangeiras têm uma restrição de exclusividade.|  
  
### Para criar uma associação entre classes de entidade  
  
1.  A classe de entidade que representa a classe pai na associação de atalho, aponte para **Add**, e, em seguida, clique em **associação**.  
  
2.  Verifique a correta **classe pai** selecionado no **Editor de associação** caixa de diálogo.  
  
3.  Selecione o **classe filha** na caixa de combinação.  
  
4.  Selecione o **Propriedades de associação** que relacionam as classes. Normalmente, isso mapeia para a relação de chave estrangeira definida no banco de dados. Por exemplo, na associação Customers e Orders, o **Propriedades de associação** são a CustomerID para cada classe.  
  
5.  Clique em **OK** para criar a associação.  
  
## Consulte também  
 [LINQ to SQL Tools no Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
 [Walkthrough: Creating LINQ to SQL Classes \(O\/R Designer\)](../Topic/Walkthrough:%20Creating%20LINQ%20to%20SQL%20Classes%20\(O-R%20Designer\).md)   
 [LINQ to SQL](../Topic/LINQ%20to%20SQL.md)   
 [DataContext Methods \(O\/R Designer\)](../data-tools/datacontext-methods-o-r-designer.md)   
 [How to: Represent Primary Keys](../Topic/How%20to:%20Represent%20Primary%20Keys.md)