---
title: "Relacionamentos em conjuntos de dados | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbData.Microsoft.VSDesigner.DataSource.DesignRelation"
  - "vbdata.Microsoft.VSDesigner.DataSource.DesignRelation"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "aspx"
helpviewer_keywords: 
  - "relações sobre relações"
  - "conjuntos de dados [Visual Basic], relações"
  - "relações, conjuntos de dados"
ms.assetid: cfe274f0-71fe-40f6-994e-7c7f6273c9ba
caps.latest.revision: 15
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Relacionamentos em conjuntos de dados
Tabelas de conjuntos de dados que contêm dados relacionados usam <xref:System.Data.DataRelation> objetos para representar uma relação pai\/filho entre as tabelas e para retornar registros relacionados uns dos outros. Adicionar tabelas relacionadas a datasets usando o **Data Source Configuration Wizard**, ou **Dataset Designer**, cria e configura o <xref:System.Data.DataRelation> objeto para você.  
  
 O <xref:System.Data.DataRelation> objeto executa duas funções:  
  
-   Ele pode tornar disponíveis os registros relacionados a um registro que você está trabalhando. Ele fornece registros filho se você estiver em um registro pai \(<xref:System.Data.DataRow.GetChildRows%2A>\) e um registro pai se você estiver trabalhando com um registro filho \(<xref:System.Data.DataRow.GetParentRow%2A> \).  
  
-   Isto pode impor restrições de integridade referencial, como excluir registros filho relacionados quando você exclui um registro pai.  
  
 É importante compreender a diferença entre uma associação verdadeira e a função de um <xref:System.Data.DataRelation> objeto. Em uma associação verdadeira, registros são tirados das tabelas pai e filho e colocados em um conjunto de registros único e simples. Quando você usa um <xref:System.Data.DataRelation> do objeto, nenhum novo conjunto de registros é criado. Em vez disso, a relação rastreia o relacionamento entre tabelas e mantém registros pai e filho em sincronia.  
  
## Objetos DataRelation e restrições  
 Um <xref:System.Data.DataRelation> objeto também é usado para criar e impor as seguintes restrições:  
  
-   Uma restrição exclusiva, que garante que uma coluna na tabela não contenha duplicatas.  
  
-   Uma restrição de chave estrangeira, que pode ser usada para manter a integridade referencial entre uma tabela pai e filho em um conjunto de dados.  
  
 Restrições que você especifica em um <xref:System.Data.DataRelation> objeto são implementadas automaticamente criando objetos apropriados ou definindo propriedades. Se você criar uma restrição de chave estrangeira usando o <xref:System.Data.DataRelation> e instâncias de objeto a <xref:System.Data.ForeignKeyConstraint> classe são adicionados ao <xref:System.Data.DataRelation>do <xref:System.Data.DataRelation.ChildKeyConstraint%2A> propriedade.  
  
 Uma restrição exclusiva é implementada simplesmente definindo a <xref:System.Data.DataColumn.Unique%2A> propriedade de uma coluna de dados para `true` ou adicionando uma instância do <xref:System.Data.UniqueConstraint> de classe para o <xref:System.Data.DataRelation> do objeto <xref:System.Data.DataRelation.ParentKeyConstraint%2A>. Para obter informações sobre suspender restrições em um conjunto de dados, consulte [Desativar restrições ao preencher um conjunto de dados](../data-tools/turn-off-constraints-while-filling-a-dataset.md).  
  
### Regras de integridade referencial  
 Como parte da restrição de chave estrangeira, você pode especificar regras de integridade referencial que são aplicadas em três pontos:  
  
-   Quando um registro pai é atualizado  
  
-   Quando um registro pai é excluído  
  
-   Quando uma alteração é aceitas ou rejeitada  
  
 As regras que você pode fazer são especificadas no <xref:System.Data.Rule> enumeração e estão listadas na tabela a seguir.  
  
|Regra de restrição de chave estrangeira|Ação|  
|---------------------------------------------|----------|  
|<xref:System.Data.Rule>|A alteração \(atualização ou exclusão\) feita para o registro pai é feita no registros relacionados na tabela filho.|  
|<xref:System.Data.Rule>|Registros filho não são excluídos, mas a chave estrangeira nos registros filho é definida como <xref:System.DBNull>. Com essa configuração, registros filho podem ser deixados como "órfãos" — ou seja, eles não têm nenhuma relação com registros pai. **Note:**  Usar esta regra pode resultar em dados inválidos na tabela filho.|  
|<xref:System.Data.Rule>|A chave estrangeira nos registros filho relacionados é definida com o valor padrão \(conforme estabelecido pela coluna de <xref:System.Data.DataColumn.DefaultValue%2A> propriedade\).|  
|<xref:System.Data.Rule>|Nenhuma alteração é feita a registros filho relacionados. Com essa configuração, registros filho podem acabar contendo referências a registros pai inválidos.|  
  
 Para obter mais informações sobre atualizações em tabelas de dataset, consulte [Salvar dados no banco de dados](../data-tools/save-data-back-to-the-database.md).  
  
### Relações de restrição  
 Ao criar um <xref:System.Data.DataRelation> do objeto, você tem a opção de especificar que a relação seja usada somente para impor restrições — isto é, ela não será usada também para acessar registros relacionados. Esta opção permite que você gere um conjunto de dados que é ligeiramente mais eficiente e que contém menos métodos que aquela com a capacidade de registros relacionados. No entanto, você não poderá acessar registros relacionados. Por exemplo, uma relação somente\-restrição impede a exclusão de um registro pai que ainda possui filhos, e você não pode acessar os registros filho através do pai.  
  
## Para criar manualmente uma relação de dados no DataSet Designer  
 Quando você cria tabelas de dados com as ferramentas de design de dados no Visual Studio, relacionamentos são criados automaticamente se as informações podem ser obtidas de fonte de dados. Se você adicionar manualmente tabelas de dados do **DataSet** guia o **ferramentas**, você terá que criar o relacionamento manualmente. Para obter informações sobre como criar <xref:System.Data.DataRelation> objetos programaticamente, consulte [Adicionando DataRelations](../Topic/Adding%20DataRelations.md).  
  
 Relacionamentos entre DataTables aparecem como linhas no **Dataset Designer** com uma chave e uma marca inteligente ilustrando o aspecto do relacionamento de um\-para\-muitos. Por padrão o nome da relação não aparecem na superfície de design.  
  
 [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
#### Para criar uma relação entre duas tabelas de dados  
  
1.  Abra o dataset no **Dataset Designer**. Para obter mais informações, consulte [Como abrir um conjunto de dados no Designer de Conjunto de Dados](../Topic/How%20to:%20Open%20a%20Dataset%20in%20the%20Dataset%20Designer.md).  
  
2.  Arraste um **relação** de objeto o **DataSet** toolbox para a tabela de dados filho na relação.  
  
     O **relação** caixa de diálogo é aberta, preenchendo o **tabela filho** caixa com a tabela que você arrastou o **relação** em.  
  
3.  Selecione a tabela pai a partir de **tabela pai** caixa. A tabela pai contém registros no lado "um" de uma relação um\-para\-muitos.  
  
4.  Verifique se a tabela filho correta é exibida no **tabela filho** caixa. A tabela filho contém registros no lado "muitos" de uma relação um\-para\-muitos.  
  
5.  Digite um nome para a relação de **nome** caixa ou deixe o nome padrão baseado nas tabelas selecionadas. Esse é o nome de real <xref:System.Data.DataRelation> objeto no código.  
  
6.  Selecione as colunas que unem as tabelas no **colunas de chave** e **colunas de chave estrangeira** lista.  
  
7.  Selecione se deseja criar uma relação, restrição ou ambos. Para obter mais informações, veja [Introdução a objetos DataRelation](../Topic/Introduction%20to%20DataRelation%20Objects.md).  
  
8.  Marque ou desmarque o **Nested Relation** caixa. Selecionar esta opção define o <xref:System.Data.DataRelation.Nested%2A> propriedade `true`, e faz com que o filho linhas da relação sejam aninhadas dentro da coluna pai quando gravadas como dados XML ou sincronizadas com um <xref:System.Xml.XmlDataDocument>. Para obter mais informações, consulte [Aninhamento DataRelations](../Topic/Nesting%20DataRelations.md).  
  
9. Defina as regras a serem aplicadas ao fazer alterações em registros nessas tabelas. Para obter mais informações, consulte <xref:System.Data.Rule>.  
  
10. Clique em **OK** para criar a relação; uma linha de relação aparece no designer entre as duas tabelas. Você pode alternar a exibição do nome da relação na superfície de design, marcando ou desmarcando **Mostrar rótulos de relações** sobre o **dados** menu.  
  
#### Para alternar a exibição dos nomes das relações no Dataset Designer  
  
1.  Abra o dataset no **Dataset Designer**. Para obter mais informações, consulte [Como abrir um conjunto de dados no Designer de Conjunto de Dados](../Topic/How%20to:%20Open%20a%20Dataset%20in%20the%20Dataset%20Designer.md).  
  
2.  Do **dados** menu, marque ou desmarque o **Mostrar rótulos de relações** comando para alternar a exibição do nome da relação ativando ou desativando.