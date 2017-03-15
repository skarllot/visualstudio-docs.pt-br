---
title: "Instru&#231;&#245;es passo a passo: identificando uma exce&#231;&#227;o de simultaneidade | Microsoft Docs"
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
  - "controle de simultaneidade, exceções"
  - "controle de simultaneidade, explicações passo a passo"
  - "simultaneidade de dados, explicações passo a passo"
  - "conjuntos de dados [Visual Basic], erros"
  - "tratamento de exceção, problemas de simultaneidade"
  - "atualizando conjuntos de dados, erros"
ms.assetid: 73ee9759-0a90-48a9-bf7b-9d6fc17bff93
caps.latest.revision: 23
caps.handback.revision: 20
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Instru&#231;&#245;es passo a passo: identificando uma exce&#231;&#227;o de simultaneidade
Exceções de simultaneidade \(<xref:System.Data.DBConcurrencyException>\) são geradas quando dois usuários tentam alterar os mesmos dados em um banco de dados ao mesmo tempo. Neste passo a passo, você cria um aplicativo do Windows que ilustra a captura um <xref:System.Data.DBConcurrencyException>, localizando a linha que causou o erro, e uma estratégia para você pode usar para manipulá\-lo.  
  
 Este passo a passo leva você através do seguinte processo:  
  
1.  Criar um novo **Windows Application** projeto.  
  
2.  Criar um novo conjunto de dados com base em Northwind `Customers` tabela.  
  
3.  Criar um formulário com um <xref:System.Windows.Forms.DataGridView> para exibir os dados.  
  
4.  Preencher um dataset com dados a partir de `Customers` tabela no banco de dados Northwind.  
  
5.  Após preencher o conjunto de dados, use o [Visual Database Tools](http://msdn.microsoft.com/pt-br/6b145922-2f00-47db-befc-bf351b4809a1) no Visual Studio para acessar diretamente o `Customers` tabela de dados e alterar um registro.  
  
6.  Em seguida, no formulário, altere o mesmo registro com um valor diferente, atualizar o conjunto de dados e tentar gravar as alterações no banco de dados, o que resulta em um erro de simultaneidade que está sendo gerado.  
  
7.  Capturar o erro e, em seguida, exiba as diferentes versões do registro, permitindo que o usuário determinar se deseja continuar e atualizar o banco de dados ou para cancelar a atualização.  
  
## Pré-requisitos  
 Para concluir este passo a passo, você precisa:  
  
-   Acesso ao banco de dados de exemplo Northwind com permissão para executar atualizações. Para obter mais informações, consulte [Como instalar bancos de dados de exemplo](../data-tools/how-to-install-sample-databases.md).  
  
> [!NOTE]
>  Caixas de diálogo e comandos de menu que você vê podem diferir daqueles descritos na Ajuda, dependendo de suas configurações ativas ou edição. Para alterar suas configurações, escolha **Import and Export Settings** sobre o **ferramentas** menu. Para obter mais informações, consulte [Personalizando configurações de desenvolvimento no Visual Studio](http://msdn.microsoft.com/pt-br/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## Criar um novo projeto  
 Iniciar a passo a passo, criando um novo aplicativo do Windows.  
  
#### Para criar um novo projeto de aplicativo do Windows  
  
1.  Do **arquivo** menu, crie um novo projeto.  
  
2.  Selecione uma linguagem de programação a **tipos de projeto** painel.  
  
3.  Selecione **Windows Application** no **modelos** painel.  
  
4.  Nomeie o projeto `ConcurrencyWalkthrough`, e, em seguida, clique em **OK**.  
  
     O Visual Studio adiciona o projeto **Solution Explorer** e exibe um novo formulário no designer.  
  
## Criando o Northwind Dataset  
 Nesta seção você criará um dataset chamado `NorthwindDataSet`.  
  
#### Para criar o NorthwindDataSet  
  
1.  Do **dados** menu, escolha **fonte adicionar novos dados**.  
  
     O [Assistente para Configuração da Fonte de Dados](../data-tools/media/data-source-configuration-wizard.png) é aberto.  
  
2.  Selecione **banco de dados** sobre o **Escolher um tipo de fonte de dados** página.  
  
3.  Selecione uma conexão para o banco de dados de exemplo Northwind na lista de conexões disponíveis, ou clique em **nova conexão** se a conexão não está disponível na lista de conexões.  
  
    > [!NOTE]
    >  Se você estiver se conectando a um arquivo de banco de dados local, selecione **não** quando perguntado se você deseja adicionar o arquivo ao seu projeto.  
  
4.  Clique em **próximo** sobre o **Salvar cadeia de conexão no arquivo de configuração do aplicativo** página.  
  
5.  Expanda o **tabelas** nó e selecione o `Customers` tabela. O nome padrão para o conjunto de dados deve ser `NorthwindDataSet`.  
  
6.  Clique em **Concluir** para adicionar o conjunto de dados para o projeto.  
  
## Criar um controle DataGridView de associação de dados  
 Nesta seção você criará um <xref:System.Windows.Forms.DataGridView> arrastando o **clientes** item do **fontes de dados** window para seu formulário do Windows.  
  
#### Para criar um controle DataGridView que está associado à tabela Customers  
  
1.  Do **dados** menu, escolha **Show Data Sources** para abrir o **janela fontes de dados**.  
  
2.  Do **fontes de dados** janela Expandir o **NorthwindDataSet** nó e selecione o **clientes** tabela.  
  
3.  Clique na seta para baixo no nó da tabela e selecione **DataGridView** na lista suspensa.  
  
4.  Arraste a tabela para uma área vazia do formulário.  
  
     Um <xref:System.Windows.Forms.DataGridView> controle denominado `CustomersDataGridView` e um <xref:System.Windows.Forms.BindingNavigator> chamado `CustomersBindingNavigator` são adicionados ao formulário vinculado, o <xref:System.Windows.Forms.BindingSource> que por sua vez é associado ao `Customers` na tabela a `NorthwindDataSet`.  
  
## Ponto de verificação  
 Agora você pode testar o formulário para certificar\-se de que ele funciona como esperado até este ponto.  
  
#### Para testar o formulário  
  
1.  Pressione F5 para executar o aplicativo  
  
     O formulário aparece com um <xref:System.Windows.Forms.DataGridView> controle que é preenchido com dados do `Customers` tabela.  
  
2.  Do **Depurar** menu, escolha **parar depuração**.  
  
## Tratamento de erros de simultaneidade  
 Como tratar erros depende de regras de negócio específicas que governam o aplicativo. Para este passo a passo, após uma violação de simultaneidade é gerada, a seguinte estratégia para lidar com o erro de simultaneidade será usada como uma ilustração:  
  
 O aplicativo apresentará ao usuário três versões do registro:  
  
-   O registro atual no banco de dados.  
  
-   O registro original carregado para o conjunto de dados.  
  
-   As alterações propostas no dataset.  
  
 O usuário é então capaz de substituir o banco de dados com a versão proposta ou cancelar a atualização e atualizar o dataset com os novos valores do banco de dados.  
  
#### Para habilitar o tratamento de erros de simultaneidade  
  
1.  Crie um manipulador de erro personalizado.  
  
2.  Exibir as opções para o usuário.  
  
3.  Processe a resposta do usuário.  
  
4.  Reenviar a atualização, ou redefinir os dados no conjunto de dados.  
  
### Adicionando código para tratar a exceção de simultaneidade  
 Quando você tenta executar uma atualização e uma exceção é gerada, você geralmente deseja fazer algo com as informações fornecidas pela exceção gerada.  
  
 Nesta seção você irá adicionar código que tentará atualizar o banco de dados e manipular qualquer <xref:System.Data.DBConcurrencyException> que pode ser gerada, bem como qualquer outra exceção.  
  
> [!NOTE]
>  O `CreateMessage` e `ProcessDialogResults` métodos serão adicionados posteriormente neste passo a passo.  
  
##### Para adicionar o tratamento de erro para o erro de simultaneidade  
  
1.  Adicione o seguinte código abaixo o `Form1_Load` método:  
  
     [!code-cs[VbRaddataConcurrency#1](../data-tools/codesnippet/CSharp/handle-a-concurrency-exception_1.cs)]
     [!code-vb[VbRaddataConcurrency#1](../data-tools/codesnippet/VisualBasic/handle-a-concurrency-exception_1.vb)]  
  
2.  Substitua o `CustomersBindingNavigatorSaveItem_Click` método para chamar o `UpdateDatabase` método para que se pareça com o seguinte:  
  
     [!code-cs[VbRaddataConcurrency#2](../data-tools/codesnippet/CSharp/handle-a-concurrency-exception_2.cs)]
     [!code-vb[VbRaddataConcurrency#2](../data-tools/codesnippet/VisualBasic/handle-a-concurrency-exception_2.vb)]  
  
### Exibir as opções para o usuário  
 O código que você acabou de escrever chama o `CreateMessage` procedimento para exibir informações de erro para o usuário. Para este passo a passo, você usará uma caixa de mensagem para exibir as diferentes versões do registro para o usuário e permitir que o usuário escolha se deseja substituir o registro com as alterações ou cancelar a edição. Depois que o usuário seleciona uma opção \(clicar um botão\) na caixa de mensagem, a resposta é passada para o `ProcessDialogResult` método.  
  
##### Para criar a mensagem a ser exibida para o usuário  
  
-   Crie a mensagem, adicionando o seguinte código para o **Editor de códigos**. Digite este código abaixo o `UpdateDatabase` método.  
  
     [!code-cs[VbRaddataConcurrency#4](../data-tools/codesnippet/CSharp/handle-a-concurrency-exception_3.cs)]
     [!code-vb[VbRaddataConcurrency#4](../data-tools/codesnippet/VisualBasic/handle-a-concurrency-exception_3.vb)]  
  
### Processar a resposta do usuário  
 Você também precisará código para processar a resposta do usuário à caixa de mensagem. As opções são sobrescrever o registro atual no banco de dados com a alteração proposta ou abandonar as alterações locais e atualizar a tabela de dados com o registro no momento no banco de dados. Se o usuário escolher Sim, o <xref:System.Data.DataTable.Merge%2A> método for chamado com o *preserveChanges* argumento definido como `true`. Isso fará com que a tentativa de atualização seja bem\-sucedida, pois a versão original do registro agora coincide com o registro no banco de dados.  
  
##### Para processar o usuário de entrada da caixa de mensagem  
  
-   Adicione o código a seguir abaixo do código adicionado na seção anterior.  
  
     [!code-cs[VbRaddataConcurrency#3](../data-tools/codesnippet/CSharp/handle-a-concurrency-exception_4.cs)]
     [!code-vb[VbRaddataConcurrency#3](../data-tools/codesnippet/VisualBasic/handle-a-concurrency-exception_4.vb)]  
  
## Teste  
 Agora você pode testar o formulário para certificar\-se de que ele se comporta conforme o esperado. Para simular uma violação de simultaneidade, você precisa alterar os dados no banco de dados depois de preencher o NorthwindDataSet.  
  
#### Para testar o formulário  
  
1.  Pressione F5 para executar o aplicativo.  
  
2.  Depois que o formulário for exibido, deixá\-lo funcionando e alterne para o Visual Studio IDE.  
  
3.  Do **exibição** menu, escolha **Server Explorer**.  
  
4.  Em **Server Explorer**, expanda a conexão de seu aplicativo está usando e, em seguida, expanda o **tabelas** nó.  
  
5.  Clique com botão direito do **clientes** e selecione **Mostrar dados da tabela**.  
  
6.  No primeiro registro \(`ALFKI`\) alterar o `ContactName` para `Maria Anders2`.  
  
    > [!NOTE]
    >  Navegue até uma linha diferente para confirmar a alteração.  
  
7.  Alterne para o `ConcurrencyWalkthrough`do formulário em execução.  
  
8.  No primeiro registro no formulário \(`ALFKI`\), altere o `ContactName` para `Maria Anders1`.  
  
9. Clique o **Salvar** botão.  
  
     O erro de simultaneidade é gerado e a caixa de mensagem é exibida.  
  
10. Clicar em **não** cancela a atualização e atualiza o dataset com os valores atualmente no banco de dados, enquanto clicar em **Sim** grava o valor proposto para o banco de dados.  
  
## Consulte também  
 [Salvar dados no banco de dados](../data-tools/save-data-back-to-the-database.md)