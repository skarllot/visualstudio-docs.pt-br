---
title: "Criar consultas TableAdapter parametrizadas | Microsoft Docs"
ms.custom: ""
ms.date: "09/21/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "aspx"
helpviewer_keywords: 
  - "dados [Visual Studio], TableAdapters"
  - "TableAdapters, consultas parametrizadas"
  - "dados [Visual Studio], pesquisando dados"
  - "consultas [Visual Studio], criando"
  - "TableAdapters, pesquisando dados"
  - "consultas [Visual Studio], TableAdapters"
ms.assetid: 104d1d19-b5a9-4071-b81e-1b3af08e9c7b
caps.latest.revision: 20
caps.handback.revision: 18
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Criar consultas TableAdapter parametrizadas
Uma consulta parametrizada retorna dados que satisfazem às condições de uma cláusula WHERE dentro da consulta. Por exemplo, você pode parametrizar uma lista de clientes para exibir apenas clientes em uma determinada cidade, adicionando `WHERE City = @City` ao final da instrução SQL que retorna uma lista de clientes.  
  
 Criar consultas TableAdapter parametrizadas no [Dataset Designer](../data-tools/creating-and-editing-typed-datasets.md), ou durante a criação de formulários de associação de dados em um aplicativo do Windows com o **parametrizar fonte de dados** comando o **dados** menu. O **parametrizar fonte de dados** comando também cria controles em seu formulário para inserir os valores de parâmetro e executar a consulta.  
  
> [!NOTE]
>  Ao construir uma consulta parametrizada, use a notação de parâmetro específica para o banco de dados que você está codificando. Por exemplo, fontes de dados Access e OleDb usam o ponto de interrogação '?' para denotar parâmetros, portanto a cláusula WHERE teria esta aparência: `WHERE City = ?`.  
  
> [!NOTE]
>  Caixas de diálogo e comandos de menu que você vê podem diferir daqueles descritos na Ajuda, dependendo de suas configurações ativas ou edição. Para alterar suas configurações, escolha **Import and Export Settings** sobre o **ferramentas** menu. Para obter mais informações, consulte [Personalizando configurações de desenvolvimento no Visual Studio](http://msdn.microsoft.com/pt-br/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## Criando uma consulta TableAdapter parametrizada  
  
#### Para criar uma consulta parametrizada no Dataset Designer  
  
-   Crie um novo TableAdapter, adicionando uma cláusula WHERE com os parâmetros desejados à instrução SQL. Para obter mais informações, consulte [Criar e configurar TableAdapters](../data-tools/create-and-configure-tableadapters.md).  
  
     \- ou \-  
  
-   Adicione uma consulta a um TableAdapter existente, adicionando uma cláusula WHERE com os parâmetros desejados à instrução SQL. Para obter mais informações, consulte [Como criar consultas TableAdapter](../data-tools/how-to-create-tableadapter-queries.md).  
  
#### Para criar uma consulta parametrizada durante a criação de um formulário de associação de dados  
  
1.  Selecione um controle no formulário que já está associado a um conjunto de dados. Para obter mais informações, consulte [Associar controles dos Windows Forms a dados no Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md).  
  
2.  Sobre o **dados** menu, clique em **Add Query**.  
  
3.  Conclua o **Pesquisar Construtor de critérios** caixa de diálogo, adicionando uma cláusula WHERE com os parâmetros desejados à instrução SQL.  
  
### Para adicionar uma consulta a um formulário de associação de dados existente  
  
1.  Abra o formulário no **Windows Forms Designer**.  
  
2.  Clique em **Add Query** sobre o **dados** menu ou **marcas inteligentes de dados**.  
  
    > [!NOTE]
    >  Se **Add Query** não está disponível na **dados** menu, selecione um controle no formulário que exibe os fonte de dados você deseja adicionar a parametrização. Por exemplo, se o formulário exibe dados em um <xref:System.Windows.Forms.DataGridView> de controle, selecione\-o. Se o formulário exibe dados em controles individuais, selecione qualquer controle ligado a dados.  
  
3.  Selecione a tabela desejada para adicionar parametrização no **tabela fonte de dados selecione** área.  
  
4.  Digite um nome no **novo nome de consulta** caixa se você estiver criando uma nova consulta.  
  
     \- ou \-  
  
     Selecione uma consulta no **nome da consulta existente** caixa.  
  
5.  Digite uma consulta que usa parâmetros no **texto da consulta** caixa.  
  
6.  Clique em **OK**.  
  
     Um controle para o parâmetro de entrada e um **carga** botão são adicionados ao formulário em um <xref:System.Windows.Forms.ToolStrip> controle.  
  
 Parâmetros TableAdapter podem ser atribuídos valores nulos quando você desejar consultar registros que não têm nenhum valor atual. Por exemplo, considere a consulta a seguir que possui um `ShippedDate` parâmetro em seu `WHERE` cláusula:  
  
 `SELECT CustomerID, OrderDate, ShippedDate`  
  
 `FROM Orders`  
  
 `WHERE (ShippedDate = @ShippedDate) OR`  
  
 `(ShippedDate IS NULL)`  
  
 Se esta fosse uma consulta em um TableAdapter, você poderia consultar todos os pedidos que não foram enviados com o seguinte código:  
  
 [!CODE [VbRaddataTableAdapters#8](../CodeSnippet/VS_Snippets_VBCSharp/VbRaddataTableAdapters#8)]  
  
#### Para ativar uma consulta aceitar valores nulos  
  
1.  No **Dataset Designer**, selecione a consulta TableAdapter que precisa aceitar valores de parâmetro nulo.  
  
2.  Selecione **parâmetros** no **propriedades** janela e clique nas reticências \(**...**\) para abrir o **Editor de coleção de parâmetros**.  
  
3.  Selecione o parâmetro que permite valores nulos e defina a **AllowDbNull** propriedade `true`.  
  
## Consulte também  
 [Preencher datasets usando TableAdapters](../data-tools/fill-datasets-by-using-tableadapters.md)