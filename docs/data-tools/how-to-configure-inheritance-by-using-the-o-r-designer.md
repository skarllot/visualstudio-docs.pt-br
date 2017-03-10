---
title: "Como: configurar a heran&#231;a usando Object Relational Designer | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e594af12-e777-434a-bc08-7dd2dac84cdc
caps.latest.revision: 4
caps.handback.revision: 4
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Como: configurar a heran&#231;a usando Object Relational Designer
O [!INCLUDE[vs_ordesigner_long](../data-tools/includes/vs_ordesigner_long_md.md)] \([!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]\) suporta o conceito de herança de tabela única como geralmente é implementado em sistemas relacionais. Herança de tabela única, há uma tabela de banco de dados único que contém campos para informações pai e informações de filho. Com dados relacionais, uma coluna de discriminador contém o valor que determina qual classe qualquer registro pertence.  
  
 Por exemplo, considere uma tabela de pessoas que contém todos empregado por uma empresa. Algumas pessoas são funcionários e algumas pessoas são gerentes. A tabela de pessoas contém uma coluna denominada `EmployeeType` que tem um valor de 1 para gerentes e um valor de 2 para funcionários; esta é a coluna de discriminador. Nesse cenário, você pode criar uma subclasse de funcionários e preencher a classe com apenas os registros que têm um `EmployeeType` valor 2. Você também pode remover colunas que não se aplicam de cada uma das classes.  
  
 Criar um modelo de objeto que usa herança \(e corresponde a dados relacionais\) pode ser um pouco confuso. O procedimento a seguir descreve as etapas necessárias para configurar a herança com Object Relational Designer. Após as etapas genéricos sem se referir a uma tabela existente e colunas podem ser difícil, portanto um passo a passo que usa dados foi fornecida. Para instruções passo a passo detalhadas para configurar a herança usando o [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)], consulte [Walkthrough: Creating LINQ to SQL Classes by Using Single\-Table Inheritance \(O\/R Designer\)](../data-tools/walkthrough-creating-linq-to-sql-classes-by-using-single-table-inheritance-o-r-designer.md).  
  
### Para criar classes de dados herdado  
  
1.  Abra o [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] Adicionando um **Classes LINQ to SQL** item a um projeto existente do Visual Basic ou c\#.  
  
2.  Arraste a tabela que você deseja usar como a classe base para o [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)].  
  
3.  Arraste uma segunda cópia da tabela para o [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] e renomeá\-lo. Essa é a classe derivada, ou subclasse.  
  
4.  Clique em **herança** no **Object Relational Designer** guia o **ferramentas**, e clique na subclasse \(a tabela que você renomeou\) e conectar\-se a classe base.  
  
    > [!NOTE]
    >  Clique o **herança** item o **Toolbox** e solte o botão do mouse, clique na segunda cópia da classe que você criou na etapa 3 e, em seguida, clique na primeira classe que você criou na etapa 2. A seta na linha de herança irá apontar para a primeira classe.  
  
5.  Em cada classe, exclua quaisquer propriedades de objeto que você não deseja exibir e que não são usadas para associações. Você receberá um erro se você tentar excluir propriedades de objeto usadas para associações: [The property \<property name\> cannot be deleted because it is participating in the association \<association name\>](../data-tools/the-property-property-name-cannot-be-deleted-because-it-is-participating-in-the-association-association-name.md).  
  
    > [!NOTE]
    >  Como uma classe derivada herda as propriedades definidas na sua classe base, as mesmas colunas não podem ser definidas em cada classe. \(As colunas são implementadas como propriedades.\) Você pode habilitar a criação de colunas na classe derivada, definindo o modificador de herança na propriedade na classe base. Para obter mais informações, consulte [não está em compilação: substituindo propriedades e métodos](http://msdn.microsoft.com/pt-br/2167e8f5-1225-4b13-9ebd-02591ba90213).  
  
6.  Selecione a linha de herança na [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)].  
  
7.  No **propriedades** janela, defina o **propriedade discriminatória** para o nome da coluna que é usado para distinguir os registros em suas classes.  
  
8.  Definir o **valor Discriminatório da classe derivada** propriedade para o valor no banco de dados que designa o registro como o tipo herdado. \(Esse é o valor que é armazenado na coluna de discriminador e que é usado para designar a classe herdada.\)  
  
9. Definir o **valor Discriminatório da classe Base** propriedade para o valor que designa o registro como um tipo base. \(Esse é o valor que é armazenado na coluna de discriminador e que é usado para designar a classe base.\)  
  
10. Opcionalmente, você também pode definir a **padrão de herança** propriedade para designar um tipo em uma hierarquia de herança usado ao carregar linhas que não correspondem a nenhum código de herança definido. Em outras palavras, se um registro tem um valor na coluna de discriminador que não corresponde ao valor no **valor Discriminatório da classe derivada** ou **valor Discriminatório da classe Base** propriedades, o registro será carregado no tipo designado como o **padrão de herança**.  
  
## Consulte também  
 [LINQ to SQL Tools no Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
 [Walkthrough: Creating LINQ to SQL Classes \(O\/R Designer\)](../Topic/Walkthrough:%20Creating%20LINQ%20to%20SQL%20Classes%20\(O-R%20Designer\).md)   
 [PREPARAR o que há de novo para o desenvolvimento de aplicativos de dados no Visual Studio 2012](http://msdn.microsoft.com/pt-br/3d50d68f-5f44-4915-842f-6d42fce793f1)   
 [Acessando dados no Visual Studio](../data-tools/accessing-data-in-visual-studio.md)   
 [LINQ to SQL](../Topic/LINQ%20to%20SQL.md)   
 [Walkthrough: Creating LINQ to SQL Classes by Using Single\-Table Inheritance \(O\/R Designer\)](../data-tools/walkthrough-creating-linq-to-sql-classes-by-using-single-table-inheritance-o-r-designer.md)   
 [NÃO está em compilação: Herança no Visual Basic](http://msdn.microsoft.com/pt-br/e5e6e240-ed31-4657-820c-079b7c79313c)   
 [Herança](/dotnet/csharp/programming-guide/classes-and-structs/inheritance)