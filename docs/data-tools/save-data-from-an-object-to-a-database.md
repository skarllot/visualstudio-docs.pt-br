---
title: "Como salvar dados de um objeto em um banco de dados | Microsoft Docs"
ms.custom: ""
ms.date: "10/06/2016"
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
  - "dados [Visual Studio], salvar"
  - "acesso a dados [Visual Studio], Objetos "
  - "salvando dados"
ms.assetid: efd6135a-40cf-4b0d-8f8b-41a5aaea7057
caps.latest.revision: 9
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Como salvar dados de um objeto em um banco de dados
Você pode salvar dados em objetos para um banco de dados, passando os valores do objeto para um dos métodos DBDirect do TableAdapter \(por exemplo, `TableAdapter.Insert`\). Para obter mais informações, consulte [Visão geral de TableAdapter](../data-tools/tableadapter-overview.md).  
  
 Para salvar dados de uma coleção de objetos, percorrer a coleção de objetos \(por exemplo, um loop for\-next\) e envie os valores para cada objeto de banco de dados usando um dos métodos DBDirect do TableAdapter.  
  
 Por padrão, os métodos DBDirect são criados em um TableAdapter que pode ser executado diretamente no banco de dados. Esses métodos podem ser chamados diretamente e não exigem <xref:System.Data.DataSet> ou <xref:System.Data.DataTable> objetos para reconciliar as alterações para enviar atualizações para um banco de dados.  
  
> [!NOTE]
>  Quando você estiver configurando um TableAdapter, a consulta principal deve fornecer informações suficientes para que os métodos DBDirect a ser criado. Por exemplo, se um TableAdapter é configurado para consultar dados de uma tabela que não tem uma coluna de chave primária definida, ele não gera métodos DBDirect.  
  
|Método TableAdapter DBDirect|Descrição|  
|----------------------------------|---------------|  
|`TableAdapter.Insert`|Adiciona novos registros em um banco de dados permitindo que você passe valores individuais de coluna como parâmetros do método.|  
|`TableAdapter.Update`|Atualizações de registros existentes em um banco de dados. O `Update` método recebe valores de coluna original e novo como parâmetros de método. Os valores originais são usados para localizar o registro original e os novos valores são usados para atualizar esse registro.<br /><br /> O `TableAdapter.Update` método também é usado para acomodar as alterações em um conjunto de dados no banco de dados fazendo uma <xref:System.Data.DataSet>, <xref:System.Data.DataTable>, <xref:System.Data.DataRow>, ou uma matriz de <xref:System.Data.DataRow>s como parâmetros do método.|  
|`TableAdapter.Delete`|Exclui registros existentes do banco de dados com base em valores da coluna original passados como parâmetros de método.|  
  
### Para salvar novos registros de um objeto em um banco de dados  
  
-   Criar os registros passando os valores para o `TableAdapter.Insert` método.  
  
     O exemplo a seguir cria um novo registro de cliente no `Customers` tabela passando os valores a `currentCustomer` do objeto para o `TableAdapter.Insert` método.  
  
     [!code-cs[VbRaddataSaving#23](../data-tools/codesnippet/CSharp/save-data-from-an-object-to-a-database_1.cs)]
     [!code-vb[VbRaddataSaving#23](../data-tools/codesnippet/VisualBasic/save-data-from-an-object-to-a-database_1.vb)]  
  
### Para atualizar registros existentes de um objeto para um banco de dados  
  
-   Modificar os registros chamando o `TableAdapter.Update` método e passar os novos valores para atualizar o registro e passar os valores originais para localizar o registro.  
  
    > [!NOTE]
    >  O objeto deve manter os valores originais para passá\-los para o `Update` método. Este exemplo usa as propriedades com um `orig` prefixo para armazenar os valores originais.  
  
     O exemplo a seguir atualiza um registro existente no `Customers` tabela passando os valores novos e originais no `Customer` do objeto para o `TableAdapter.Update` método.  
  
     [!code-cs[VbRaddataSaving#24](../data-tools/codesnippet/CSharp/save-data-from-an-object-to-a-database_2.cs)]
     [!code-vb[VbRaddataSaving#24](../data-tools/codesnippet/VisualBasic/save-data-from-an-object-to-a-database_2.vb)]  
  
### Para excluir registros existentes de um banco de dados  
  
-   Exclua os registros chamando o `TableAdapter.Delete` método e passar os valores originais para localizar o registro.  
  
    > [!NOTE]
    >  O objeto deve manter os valores originais para passá\-los para o `Delete` método. Este exemplo usa as propriedades com um `orig` prefixo para armazenar os valores originais.  
  
     O exemplo a seguir exclui um registro do `Customers` tabela passando os valores originais no `Customer` do objeto para o `TableAdapter.Delete` método.  
  
     [!code-cs[VbRaddataSaving#25](../data-tools/codesnippet/CSharp/save-data-from-an-object-to-a-database_3.cs)]
     [!code-vb[VbRaddataSaving#25](../data-tools/codesnippet/VisualBasic/save-data-from-an-object-to-a-database_3.vb)]  
  
## Segurança do .NET Framework  
 Você deve ter permissão para executar a inserção selecionada, UPDATE ou DELETE na tabela no banco de dados.  
  
## Consulte também  
 [Salvar dados no banco de dados](../data-tools/save-data-back-to-the-database.md)