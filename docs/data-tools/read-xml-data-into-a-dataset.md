---
title: "Ler dados XML em um dataset | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
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
  - "lendo XML"
  - "acesso a dados [Visual Studio], dados XML"
  - "leitura de arquivos, XML"
  - "dados [Visual Studio], lendo de arquivos XML"
  - "leitura de dados, arquivos XML"
  - "Leitura de texto para XML [Visual Studio]"
  - "Documentos XML, ler"
  - "conjuntos de dados [Visual Basic], lendo dados XML"
ms.assetid: fae72958-0893-47d6-b3dd-9d42418418e4
caps.latest.revision: 18
caps.handback.revision: 16
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Ler dados XML em um dataset
O ADO.NET fornece métodos simples para trabalhar com dados XML. Este passo a passo, você criará um aplicativo do Windows que irá carregar dados XML em um conjunto de dados. O conjunto de dados será exibido em um <xref:System.Windows.Forms.DataGridView>. Finalmente, um esquema XML com base no conteúdo do arquivo XML será exibido na caixa de texto.  
  
 Este passo a passo consiste em cinco etapas principais:  
  
1.  Criar um novo projeto.  
  
2.  Criando um arquivo XML a ser lido para o dataset.  
  
3.  Criando a interface do usuário.  
  
4.  Criando o dataset, leia o arquivo XML e exibi\-lo em um <xref:System.Windows.Forms.DataGridView> controle.  
  
5.  Adicionando código para exibir o esquema XML com base no arquivo XML em um <xref:System.Windows.Forms.TextBox> controle.  
  
> [!NOTE]
>  Caixas de diálogo e comandos de menu que você vê podem diferir daqueles descritos na Ajuda, dependendo de suas configurações ativas ou edição. Para alterar suas configurações, escolha **Import and Export Settings** sobre o **ferramentas** menu. Para obter mais informações, consulte [Personalizando configurações de desenvolvimento no Visual Studio](http://msdn.microsoft.com/pt-br/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## Criar um novo projeto  
 Nesta etapa, você criará um projeto Visual Basic ou Visual c\# que conterá este passo a passo.  
  
#### Para criar o novo projeto do Windows  
  
1.  Do **arquivo** menu, crie um novo projeto.  
  
2.  Nomeie o projeto `ReadingXML`.  
  
3.  Selecione **Windows Application** e clique em **OK**. Para obter mais informações, consulte [Aplicativos cliente](../Topic/Developing%20Client%20Applications%20with%20the%20.NET%20Framework.md).  
  
     O **ReadingXML** projeto é criado e adicionado ao Solution Explorer.  
  
## Gerar o arquivo XML a ser lido para o Dataset  
 Porque essa explicação passo a passo se concentra na leitura de dados XML em um dataset, o conteúdo de um arquivo XML é fornecido.  
  
#### Para criar o arquivo XML que será lido para o conjunto de dados  
  
1.  Do **projeto** menu, escolha **Add New Item**.  
  
2.  Selecione **arquivo XML**, nomeie o arquivo `authors.xml`, e clique em **Add**.  
  
     O arquivo XML carrega no designer e está pronto para edição.  
  
3.  Cole o seguinte código no editor abaixo da declaração XML:  
  
    ```xml  
    <Authors_Table>  
      <authors>  
        <au_id>172-32-1176</au_id>  
        <au_lname>White</au_lname>  
        <au_fname>Johnson</au_fname>  
        <phone>408 496-7223</phone>  
        <address>10932 Bigge Rd.</address>  
        <city>Menlo Park</city>  
        <state>CA</state>  
        <zip>94025</zip>  
        <contract>true</contract>  
      </authors>  
      <authors>  
        <au_id>213-46-8915</au_id>  
        <au_lname>Green</au_lname>  
        <au_fname>Margie</au_fname>  
        <phone>415 986-7020</phone>  
        <address>309 63rd St. #411</address>  
        <city>Oakland</city>  
        <state>CA</state>  
        <zip>94618</zip>  
        <contract>true</contract>  
      </authors>  
      <authors>  
        <au_id>238-95-7766</au_id>  
        <au_lname>Carson</au_lname>  
        <au_fname>Cheryl</au_fname>  
        <phone>415 548-7723</phone>  
        <address>589 Darwin Ln.</address>  
        <city>Berkeley</city>  
        <state>CA</state>  
        <zip>94705</zip>  
        <contract>true</contract>  
      </authors>  
      <authors>  
        <au_id>267-41-2394</au_id>  
        <au_lname>Hunter</au_lname>  
        <au_fname>Anne</au_fname>  
        <phone>408 286-2428</phone>  
        <address>22 Cleveland Av. #14</address>  
        <city>San Jose</city>  
        <state>CA</state>  
        <zip>95128</zip>  
        <contract>true</contract>  
      </authors>  
      <authors>  
        <au_id>274-80-9391</au_id>  
        <au_lname>Straight</au_lname>  
        <au_fname>Dean</au_fname>  
        <phone>415 834-2919</phone>  
        <address>5420 College Av.</address>  
        <city>Oakland</city>  
        <state>CA</state>  
        <zip>94609</zip>  
        <contract>true</contract>  
      </authors>  
    </Authors_Table>  
    ```  
  
4.  Do **arquivo** aponte para **Salvar Authors**.  
  
## Criar a Interface do usuário  
 A interface do usuário para esse aplicativo consistirá o seguinte:  
  
-   Um <xref:System.Windows.Forms.DataGridView> controle que exibirá o conteúdo do arquivo XML como dados.  
  
-   Um <xref:System.Windows.Forms.TextBox> controle que exibirá o esquema XML para o arquivo XML.  
  
-   Dois <xref:System.Windows.Forms.Button> controles.  
  
    -   Um botão lê o arquivo XML para o dataset e exibe\-o no <xref:System.Windows.Forms.DataGridView> controle.  
  
    -   Um segundo botão extrai o esquema do dataset e por um <xref:System.IO.StringWriter> exibe no <xref:System.Windows.Forms.TextBox> controle.  
  
#### Para adicionar controles ao formulário  
  
1.  Abra `Form1` no modo de design.  
  
2.  Do **Toolbox**, arraste os seguintes controles ao formulário:  
  
    -   Um <xref:System.Windows.Forms.DataGridView> controle  
  
    -   Um <xref:System.Windows.Forms.TextBox> controle  
  
    -   Dois <xref:System.Windows.Forms.Button> controles  
  
3.  Defina as seguintes propriedades:  
  
    |Controle|Propriedade|Configuração|  
    |--------------|-----------------|------------------|  
    |`TextBox1`|**Várias linhas**|`true`|  
    ||**Barras de rolagem**|**Vertical**|  
    |`Button1`|**Nome**|`ReadXmlButton`|  
    ||**Texto**|`Read XML`|  
    |`Button2`|**Nome**|`ShowSchemaButton`|  
    ||**Texto**|`Show Schema`|  
  
## Criar o conjunto de dados que receberá os dados XML  
 No procedimento seguinte, você cria um novo dataset chamado `authors`. Para obter mais informações sobre conjuntos de dados, consulte [Ferramentas do conjunto de dados no Visual Studio](../data-tools/dataset-tools-in-visual-studio.md).  
  
#### Para criar um novo conjunto de dados que receberá os dados XML  
  
1.  Com o arquivo de origem **Form1** selecionado no **Solution Explorer**, clique o **View Designer** no botão de **Solution Explorer** barra de ferramentas.  
  
2.  Do [Caixa de Ferramentas, Guia Dados](../ide/reference/toolbox-data-tab.md), arraste um **DataSet** para **Form1**.  
  
3.  Selecione **dataset não tipado** sobre o **Adicionar conjunto de dados** caixa de diálogo e clique **OK**.  
  
     **DataSet1** é adicionado à bandeja de componentes.  
  
4.  No **propriedades** janela, defina o **nome** e <xref:System.Data.DataSet.DataSetName%2A> propriedades `AuthorsDataSet`.  
  
## Crie o manipulador de eventos para ler o XML para o conjunto de dados  
 O **Read XML** botão lê o arquivo XML para o dataset e define propriedades sobre o <xref:System.Windows.Forms.DataGridView> controle associá\-lo ao conjunto de dados.  
  
#### Para adicionar código ao manipulador de eventos ReadXmlButton\_Click  
  
1.  Em **Solution Explorer**, selecione **Form1** e clique no **View Designer** botão o **Solution Explorer** barra de ferramentas.  
  
2.  Clique duas vezes o **Read XML** botão.  
  
     O **Editor de códigos** abre no `ReadXmlButton_Click` manipulador de eventos.  
  
3.  Digite o seguinte código para o `ReadXmlButton_Click` manipulador de eventos:  
  
     [!code-cs[VbRaddataFillingAndExecuting#2](../data-tools/codesnippet/CSharp/read-xml-data-into-a-dataset_1.cs)]
     [!code-vb[VbRaddataFillingAndExecuting#2](../data-tools/codesnippet/VisualBasic/read-xml-data-into-a-dataset_1.vb)]  
  
4.  No `ReadXMLButton_Click` código de manipulador de eventos de alteração de `filepath =` entrada para o caminho correto.  
  
## Criar o manipulador de eventos para exibir o esquema na caixa de texto  
 O **Show Schema** botão cria uma <xref:System.IO.StringWriter> objeto que é preenchido com o esquema e exibido no <xref:System.Windows.Forms.TextBox> .  
  
#### Para adicionar código ao manipulador de eventos ShowSchemaButton\_Click  
  
1.  Em **Solution Explorer**, selecione **Form1** e clique no **View Designer** botão.  
  
2.  Clique duas vezes o **Show Schema** botão.  
  
     O **Editor de códigos** abre no `ShowSchemaButton_Click` manipulador de eventos.  
  
3.  Digite o seguinte código para o `ShowSchemaButton_Click` manipulador de eventos.  
  
     [!code-cs[VbRaddataFillingAndExecuting#3](../data-tools/codesnippet/CSharp/read-xml-data-into-a-dataset_2.cs)]
     [!code-vb[VbRaddataFillingAndExecuting#3](../data-tools/codesnippet/VisualBasic/read-xml-data-into-a-dataset_2.vb)]  
  
## Teste  
 Agora você pode testar o formulário para certificar\-se de que ele se comporta conforme o esperado.  
  
#### Para testar o formulário  
  
1.  Pressione F5 para executar o aplicativo.  
  
2.  Clique o **Read XML** botão.  
  
     O DataGridView exibe o conteúdo do arquivo XML.  
  
3.  Clique o **Show Schema** botão.  
  
     A caixa de texto exibe o esquema XML para o arquivo XML.  
  
## Próximas etapas  
 Este passo a passo mostra as Noções básicas de ler um arquivo XML em um dataset, bem como criar um esquema com base no conteúdo do arquivo XML. Aqui estão algumas tarefas que podem vir a seguir:  
  
-   Edite os dados no dataset e grave\-os de volta como XML. Para obter mais informações, consulte <xref:System.Data.DataSet.WriteXml%2A>.  
  
-   Editar os dados no dataset e grave\-os em um banco de dados. Para obter mais informações, consulte [Salvando dados](../data-tools/saving-data.md).  
  
## Consulte também  
 [Instruções passo a passo de dados](../Topic/Data%20Walkthroughs.md)   
 [Acessando dados no Visual Studio](../data-tools/accessing-data-in-visual-studio.md)   
 [Preparando o aplicativo para receber dados](../Topic/Preparing%20Your%20Application%20to%20Receive%20Data.md)   
 [Ferramentas XML no \(Visual Studio\)](../xml-tools/xml-tools-in-visual-studio.md)