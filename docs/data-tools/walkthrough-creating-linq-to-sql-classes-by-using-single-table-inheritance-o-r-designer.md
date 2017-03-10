---
title: "Walkthrough: Creating LINQ to SQL Classes by Using Single-Table Inheritance (O/R Designer) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 63bc6328-e0df-4655-9ce3-5ff74dbf69a4
caps.latest.revision: 4
caps.handback.revision: 4
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Walkthrough: Creating LINQ to SQL Classes by Using Single-Table Inheritance (O/R Designer)
O [LINQ to SQL Tools no Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md) oferece suporte a herança de tabela única como geralmente é implementado em sistemas relacionais. Este passo a passo expande as etapas genéricas fornecidas a [Como: configurar a herança usando Object Relational Designer](../data-tools/how-to-configure-inheritance-by-using-the-o-r-designer.md) tópico e fornece alguns dados reais para demonstrar o uso de herança na [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)].  
  
 Durante essa explicação passo a passo, você executará as seguintes tarefas:  
  
-   Criar uma tabela de banco de dados e adicionar dados a ele.  
  
-   Crie um aplicativo Windows Forms.  
  
-   Adicione um [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] arquivo a um projeto.  
  
-   Crie novas classes de entidade.  
  
-   Configure classes de entidade para usar a herança.  
  
-   Consulte a classe herdada.  
  
-   Exiba os dados em um Windows Form.  
  
## Criar uma tabela para herdar de  
 Para ver como funciona a herança, criar uma pequena tabela Person, usá\-lo como uma classe base e, em seguida, crie um objeto Employee que herda dela.  
  
#### Para criar uma tabela base para demonstrar a herança  
  
1.  Em **Server Explorer**\/**Database Explorer**, com o botão direito do **tabelas** nó e clique em **Adicionar nova tabela**.  
  
    > [!NOTE]
    >  Você pode usar o banco de dados Northwind ou qualquer outro banco de dados que você pode adicionar uma tabela.  
  
2.  No Designer de tabela, adicione as seguintes colunas na tabela:  
  
    |Nome da coluna|Tipo de dados|Permitir nulos|  
    |--------------------|-------------------|--------------------|  
    |**ID**|**int**|**False**|  
    |**Tipo**|**int**|**True**|  
    |**FirstName**|**nvarchar \(200\)**|**False**|  
    |**Sobrenome**|**nvarchar \(200\)**|**False**|  
    |**Gerenciador de**|**int**|**True**|  
  
3.  Defina a coluna ID como a chave primária.  
  
4.  Salve a tabela e nomeie\-o **pessoa**.  
  
## Adicionar dados à tabela  
 Para que você possa verificar que a herança está configurada corretamente, a tabela precisa de alguns dados para cada classe na herança de tabela única.  
  
#### Para adicionar dados à tabela  
  
1.  Abra a tabela no modo de exibição de dados. \(Com o botão direito do **pessoa** na tabela **Server Explorer**\/**Database Explorer** e clique em **Mostrar dados da tabela**.\)  
  
2.  Copie os seguintes dados na tabela. \(Você pode copiá\-lo e colá\-lo na tabela selecionando a linha inteira no painel de resultados.\)  
  
    ||||||  
    |-|-|-|-|-|  
    |**ID**|**Tipo**|**FirstName**|**Sobrenome**|**Gerenciador de**|  
    |**1**|**1**|**Anne**|**Wallace**|**NULL**|  
    |**2**|**1**|**Carlos**|**Grilo**|**NULL**|  
    |**3**|**1**|**Yael**|**Peled**|**NULL**|  
    |**4**|**2**|**Gatis**|**Ozolins**|**1**|  
    |**5**|**2**|**Andreas**|**Farinha**|**1**|  
    |**6**|**2**|**Tiffany**|**Phuvasate**|**1**|  
    |**7**|**2**|**Alexey**|**Orekhov**|**2**|  
    |**8**|**2**|**Michał**|**Poliszkiewicz**|**2**|  
    |**9**|**2**|**Parte fina**|**Yee**|**2**|  
    |**10**|**2**|**Fabricio**|**Noriega**|**3**|  
    |**11**|**2**|**Mariana**|**Martin**|**3**|  
    |**12**|**2**|**Ken**|**Kwok**|**3**|  
  
## Criar um novo projeto  
 Agora que você criou a tabela, crie um novo projeto para demonstrar a configuração de herança.  
  
#### Para criar o novo aplicativo do Windows  
  
1.  Do **arquivo** menu, crie um novo projeto.  
  
2.  Nomeie o projeto **InheritanceWalkthrough**.  
  
    > [!NOTE]
    >  O [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] tem suporte em projetos Visual Basic e c\#. Crie o novo projeto em uma dessas linguagens.  
  
3.  Clique o **Windows Forms Application** modelo e clique **OK**. Para obter mais informações, consulte [Aplicativos cliente](../Topic/Developing%20Client%20Applications%20with%20the%20.NET%20Framework.md).  
  
4.  O projeto InheritanceWalkthrough é criado e adicionado ao **Solution Explorer**.  
  
## Adicionar um LINQ to SQL Classes de arquivo para o projeto  
  
#### Para adicionar um LINQ to SQL arquivo ao projeto  
  
1.  Sobre o **projeto** menu, clique em **Add New Item**.  
  
2.  Clique o **Classes LINQ to SQL** modelo e clique **Add**.  
  
     O arquivo. dbml é adicionado ao projeto e o [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] é aberto.  
  
## Criar a herança usando Object Relational Designer  
 Configurar a herança arrastando um **herança** de objeto o **Toolbox** na superfície de design.  
  
#### Para criar a herança  
  
1.  Em **Server Explorer**\/**Database Explorer**, navegue até o **pessoa** tabela que você criou anteriormente.  
  
2.  Arraste o **pessoa** tabela para o [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] superfície de design.  
  
3.  Arraste uma segunda **pessoa** tabela para o [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] e altere seu nome para **funcionário**.  
  
4.  Excluir o **Manager** propriedade a partir de **pessoa** objeto.  
  
5.  Excluir o **tipo**, **ID**, **FirstName**, e **LastName** propriedades a partir de **funcionário** objeto. \(Em outras palavras, exclua todas as propriedades, exceto **Manager**.\)  
  
6.  Do **Object Relational Designer** guia do **Toolbox**, criar um **herança** entre o **pessoa** e **funcionário** objetos. Para fazer isso, clique o **herança** item o **Toolbox** e solte o botão do mouse. Em seguida, clique o **funcionário** objeto e, em seguida, o **pessoa** objeto o [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]. A seta na linha de herança irá apontar para o **pessoa** objeto.  
  
7.  Clique o **herança** linha na superfície de design.  
  
8.  Definir o **propriedade discriminatória** propriedade **tipo**.  
  
9. Definir o **valor Discriminatório da classe derivada** propriedade **2**.  
  
10. Definir o **valor Discriminatório da classe Base** propriedade **1**.  
  
11. Definir a **padrão de herança** propriedade **pessoa**.  
  
12. Compile o projeto.  
  
## A classe herdada da consulta e exibir os dados no formulário  
 Agora você irá adicionar algum código ao formulário que consulta uma classe específica no modelo de objeto.  
  
#### Para criar uma consulta LINQ e exibir os resultados no formulário  
  
1.  Arraste um **ListBox** para Form1.  
  
2.  Clique duas vezes no formulário para criar um `Form1_Load` manipulador de eventos.  
  
3.  Adicione o seguinte código para o `Form1_Load` manipulador de eventos:  
  
    ```vb#  
    Dim dc As New DataClasses1DataContext  
    Dim results = From emp In dc.Persons _  
        Where TypeOf emp Is Employee _  
        Select emp  
  
    For Each Emp As Employee In results  
        ListBox1.Items.Add(Emp.LastName)  
    Next  
    ```  
  
    ```c#  
    NorthwindDataContext dc = new DataClasses1DataContext();  
    var results = from emp in dc.Persons  
                  where emp is Employee  
                  select emp;  
  
    foreach(Employee Emp in results)  
    {  
        listBox1.Items.Add(Emp.LastName)  
    }  
    ```  
  
## Testar o aplicativo  
 Execute o aplicativo e verificar se os registros exibidos na caixa de listagem são todos os funcionários \(registros que têm um valor de 2 na coluna tipo\).  
  
#### Para testar o aplicativo  
  
1.  Pressione F5.  
  
2.  Verifique se apenas os registros que têm um valor de 2 na coluna tipo são exibidos.  
  
3.  Feche o formulário. \(No **Depurar** menu, clique em **parar depuração**.\)  
  
## Consulte também  
 [LINQ to SQL Tools no Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
 [How to: Add LINQ to SQL Classes to a Project \(O\/R Designer\)](../Topic/How%20to:%20Add%20LINQ%20to%20SQL%20Classes%20to%20a%20Project%20\(O-R%20Designer\).md)   
 [Walkthrough: Creating LINQ to SQL Classes \(O\/R Designer\)](../Topic/Walkthrough:%20Creating%20LINQ%20to%20SQL%20Classes%20\(O-R%20Designer\).md)   
 [Como: atribuir procedimentos armazenados para executar atualizações, inserções e exclusões \(Object Relational Designer\)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md)   
 [LINQ to SQL](../Topic/LINQ%20to%20SQL.md)   
 [How to: Generate the Object Model in Visual Basic or C\#](../Topic/How%20to:%20Generate%20the%20Object%20Model%20in%20Visual%20Basic%20or%20C%23.md)