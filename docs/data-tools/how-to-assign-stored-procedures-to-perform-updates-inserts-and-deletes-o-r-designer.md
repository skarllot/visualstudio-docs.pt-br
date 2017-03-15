---
title: "Como: atribuir procedimentos armazenados para executar atualiza&#231;&#245;es, inser&#231;&#245;es e exclus&#245;es (Object Relational Designer) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e88224ab-ff61-4a3a-b6b8-6f3694546cac
caps.latest.revision: 2
caps.handback.revision: 2
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Como: atribuir procedimentos armazenados para executar atualiza&#231;&#245;es, inser&#231;&#245;es e exclus&#245;es (Object Relational Designer)
Os procedimentos armazenados podem ser adicionados ao Designer Relacional de Objetos e executados como métodos típicos do <xref:System.Data.Linq.DataContext>.  Eles também podem ser usados para substituir o comportamento padrão em tempo de execução do [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] que executa inserções, atualizações e exclusões quando alterações são salvas de classes de entidade para um banco de dados \(por exemplo, ao chamar o método <xref:System.Data.Linq.DataContext.SubmitChanges%2A>\).  
  
> [!NOTE]
>  Se seu procedimento armazenado retornar valores que precisem ser reenviados ao cliente \(por exemplo, valores calculados no procedimento armazenado\), crie parâmetros de saída em seus procedimentos armazenados.  Se você não pode usar parâmetros de saída, escreva uma implementação de método parcial em vez de depender das substituições geradas pelo Designer Relacional de Objetos.  Os membros mapeados para os valores gerados por banco de dados precisam ser definidos para valores apropriados após a conclusão com êxito de operações INSERT ou UPDATE.  Para obter mais informações, consulte [Responsibilities of the Developer In Overriding Default Behavior](../Topic/Responsibilities%20of%20the%20Developer%20In%20Overriding%20Default%20Behavior.md).  
  
> [!NOTE]
>  O [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] manipula automaticamente os valores gerados por banco de dados para colunas de identidade \(incremento automático\), rowguidcol \(GUID gerado por banco de dados\) e carimbo de data\/hora.  Os valores gerados pelo banco de dados em outros tipos de coluna resultarão inesperadamente em um valor nulo.  Para retornar os valores gerados por banco de dados, defina manualmente <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A> como `true` e <xref:System.Data.Linq.Mapping.ColumnAttribute.AutoSync%2A> como um dos seguintes: <xref:System.Data.Linq.Mapping.AutoSync>, <xref:System.Data.Linq.Mapping.AutoSync> ou <xref:System.Data.Linq.Mapping.AutoSync>.  
  
## Configurando o comportamento de atualização de uma classe de entidade  
 Por padrão, a lógica para atualizar um banco de dados \(inserções, atualizações e exclusões\), com alterações que foram feitas nos dados em classes de entidade [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)], é fornecida em tempo de execução pelo [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)].  O tempo de execução cria comandos padrão Insert, Update e Delete que se baseiam no esquema da tabela \(as informações de coluna e chave primária\).  Quando o comportamento padrão não é desejado, você pode configurar o comportamento de atualização atribuindo procedimentos armazenados específicos para executar as inserções, atualizações e exclusões necessárias para manipular os dados na sua tabela. Você também pode fazer isso quando o comportamento padrão não é gerado, por exemplo, quando as classes de entidade são mapeadas para exibições.  Finalmente, você pode substituir o comportamento de atualização padrão quando o banco de dados exige o acesso à tabela através de procedimentos armazenados.  
  
 [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
#### Para atribuir procedimentos armazenados para substituir o comportamento padrão de uma classe de entidade  
  
1.  Abra o arquivo **LINQ to SQL** no designer.  \(Clique duas vezes no arquivo .dbml no **Gerenciador de Soluções**.\)  
  
2.  Em **Gerenciador de Servidores**\/**Gerenciador de Banco de Dados**, expanda **Procedimentos Armazenados** e localize os procedimentos armazenados a serem usados com os comandos Insert, Update e\/ou Delete da classe de entidade.  
  
3.  Arraste o procedimento armazenado para o Designer Relacional de Objetos.  
  
     O procedimento armazenado é adicionado ao painel de métodos como um método <xref:System.Data.Linq.DataContext>.  Para obter mais informações, consulte [DataContext Methods \(O\/R Designer\)](../data-tools/datacontext-methods-o-r-designer.md).  
  
4.  Selecione a classe de entidade para a qual você deseja usar o procedimento armazenado para executar atualizações.  
  
5.  Na janela **Propriedades**, selecione o comando a ser substituído \(**Insert**, **Update** ou **Delete**\).  
  
6.  Clique nas reticências \(...\) ao lado das palavras **Usar tempo de execução** para abrir a caixa de diálogo **Configurar Comportamento**.  
  
7.  Selecione **Personalizar**.  
  
8.  Selecione o procedimento armazenado desejado na lista **Personalizar**.  
  
9. Inspecione a lista de **Argumentos de Método** e de **Propriedades de Classe** para verificar se **Argumentos de Método** é mapeado para **Propriedades de Classe** apropriado.  Mapeie os argumentos de método originais \(original \_*ArgumentName*\) para as propriedades originais \(*PropertyName* \(Original\)\) para os comandos Update e Delete.  
  
    > [!NOTE]
    >  Por padrão, os argumentos do método são mapeados para as propriedades de classe quando os nomes coincidem.  Se os nomes de propriedade forem modificados, não haverá mais correspondência entre a tabela e a classe de entidade. Talvez seja necessário selecionar a propriedade de classe equivalente para mapeamento se o designer não puder determinar o mapeamento correto.  
  
10. Clique em **OK** ou em **Aplicar**.  
  
    > [!NOTE]
    >  Você pode continuar a configurar o comportamento para cada combinação de classe\/comportamento quando você clica em **Aplicar** depois de cada alteração.  Se você alterar a classe ou o comportamento antes de clicar em **Aplicar**, uma caixa de diálogo de aviso com uma oportunidade de aplicar as alterações será exibida.  
  
     Para voltar a usar a lógica padrão em tempo de execução para atualizações, clique nas reticências ao lado do comando Insert, Update ou Delete, na janela **Propriedades**, e selecione **Usar tempo de execução** na caixa de diálogo **Configurar Comportamento**.  
  
## Consulte também  
 [LINQ to SQL Tools no Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
 [DataContext Methods \(O\/R Designer\)](../data-tools/datacontext-methods-o-r-designer.md)   
 [Walkthrough: Creating LINQ to SQL Classes \(O\/R Designer\)](../Topic/Walkthrough:%20Creating%20LINQ%20to%20SQL%20Classes%20\(O-R%20Designer\).md)   
 [Instruções passo a passo: criando procedimentos armazenados atualizados para a tabela Clientes do Northwind](../data-tools/walkthrough-creating-update-stored-procedures-for-the-northwind-customers-table.md)   
 [LINQ to SQL](../Topic/LINQ%20to%20SQL.md)   
 [Insert, Update, and Delete Operations](../Topic/Insert,%20Update,%20and%20Delete%20Operations.md)