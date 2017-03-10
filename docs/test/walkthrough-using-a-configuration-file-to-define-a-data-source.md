---
title: "Instru&#231;&#245;es passo a passo: usando um arquivo de configura&#231;&#227;o para definir uma fonte de dados | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "arquivos de configuração [Visual Studio ALM], definindo fontes de dados"
  - "fontes de dados, definindo com arquivos de configuração"
  - "testes de unidade, passo a passo"
ms.assetid: 95fa5214-b12e-4e1f-84e5-cc4c2d86b0d7
caps.latest.revision: 32
caps.handback.revision: 32
ms.author: "mlearned"
manager: "douge"
---
# Instru&#231;&#245;es passo a passo: usando um arquivo de configura&#231;&#227;o para definir uma fonte de dados
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Este passo a passo ilustra como usar uma fonte de dados definida em um arquivo App. config para teste de unidade.  Você aprenderá a criar um arquivo App. config que define uma fonte de dados que pode ser usada pela <xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataSourceAttribute> classe.  Tarefas apresentadas neste passo a passo incluem o seguinte:  
  
-   Criando um arquivo App. config.  
  
-   Definindo uma seção de configuração personalizada.  
  
-   Definindo cadeias de conexão.  
  
-   Definindo as fontes de dados.  
  
-   Acessando os dados de fontes usando o <xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataSourceAttribute> classe.  
  
## Pré-requisitos  
 Para concluir esta explicação passo a passo, será necessário:  
  
-   O Visual Studio Enterprise  
  
-   Microsoft Access ou no Microsoft Excel para fornecer dados para pelo menos um dos métodos de teste.  
  
-   Uma solução do Visual Studio que contém um projeto de teste.  
  
## Crie o arquivo App. config  
  
#### Para adicionar um arquivo App. config no projeto  
  
1.  Se seu projeto de teste já possui um arquivo App. config, vá para [definir uma seção de configuração personalizada](#DefineCustomConfigurationSection).  
  
2.  Com o botão direito no seu projeto de teste de **Solution Explorer**, aponte para **Add**, e, em seguida, clique em **Novo Item**.  
  
     O **Add New Item** janela é aberta.  
  
3.  Selecione o **arquivo de configuração do aplicativo** modelo e clique em **Add**.  
  
##  <a name="DefineCustomConfigurationSection"></a> Definir uma seção de configuração personalizada  
 Examine o arquivo App. config.  Ele contém pelo menos a declaração XML e um elemento raiz.  
  
#### Para adicionar a seção de configuração personalizada para o arquivo App. config  
  
1.  O elemento raiz do App. config deve ser o `configuration` elemento.  Criar um `configSections` elemento dentro do `configuration` elemento.  O `configSections` deve ser o primeiro elemento no arquivo App. config.  
  
2.  Dentro do `configSections` elemento, criar uma `section` elemento.  
  
3.  No `section` elemento, adicione um atributo chamado `name` e atribua a ela um valor igual `microsoft.visualstudio.testtools`.  Adicione outro atributo chamado `type` e atribua a ela um valor igual `Microsoft.VisualStudio.TestTools.UnitTesting.TestConfigurationSection, Microsoft.VisualStudio.QualityTools.UnitTestFramework, Version=8.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a`  
  
 O `section` elemento deve ser semelhante a este:  
  
```  
<section name="microsoft.visualstudio.testtools" type="Microsoft.VisualStudio.TestTools.UnitTesting.TestConfigurationSection, Microsoft.VisualStudio.QualityTools.UnitTestFramework, Version=8.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a"/>  
```  
  
> [!NOTE]
>  O nome do assembly deve corresponder a compilação do Microsoft Visual Studio .NET Framework que você está usando.  Defina a versão para 9.0.0.0 se você estiver usando o Visual Studio .NET Framework 3.5.  Se você estiver usando o Visual Studio .NET Framework 2.0, defina a versão para 8.0.0.0.  
  
## Definir as cadeias de conexão  
 As cadeias de conexão definem informações específicas de provedor para acessar fontes de dados.  Cadeias de conexão definidas em arquivos de configuração fornecem informações sobre o provedor de dados reutilizáveis através de um aplicativo.  Nesta seção, você criará duas cadeias de caracteres de conexão que serão usadas por fontes de dados que são definidos na seção de configuração personalizado.  
  
#### Para definir as cadeias de conexão  
  
1.  Após o `configSections` elemento, criar uma `connectionStrings` elemento.  
  
2.  Dentro do `connectionStrings` elemento, criar dois `add` elementos.  
  
3.  Na primeira `add` elemento, crie os seguintes atributos e valores para uma conexão com um banco de dados do Microsoft Access:  
  
|Atributo|Valores|  
|--------------|-------------|  
|`name`|`"MyJetConn"`|  
|`connectionString`|`"Provider=Microsoft.Jet.OLEDB.4.0; Data Source=C:\testdatasource.accdb; Persist Security Info=False;"`|  
|`providerName`|`"System.Data.OleDb"`|  
  
 No segundo `add` elemento, crie os seguintes atributos e valores para uma conexão com uma planilha do Microsoft Excel:  
  
|||  
|-|-|  
|`name`|`"MyExcelConn"`|  
|`connectionString`|`"Dsn=Excel Files;dbq=data.xlsx;defaultdir=.; driverid=790;maxbuffersize=2048;pagetimeout=5"`|  
|`providerName`|`"System.Data.Odbc"`|  
  
 O `connectionStrings` elemento deve ser semelhante a este:  
  
```  
<connectionStrings>  
    <add name="MyJetConn" connectionString="Provider=Microsoft.Jet.OLEDB.4.0; Data Source=C:\testdatasource.accdb; Persist Security Info=False;" providerName="System.Data.OleDb" />  
    <add name="MyExcelConn" connectionString="Dsn=Excel Files;dbq=data.xlsx;defaultdir=.; driverid=790;maxbuffersize=2048;pagetimeout=5" providerName="System.Data.Odbc" />  
</connectionStrings>  
```  
  
## Definir fontes de dados  
 A seção de fontes de dados contém quatro atributos que são usados pelo mecanismo de teste para recuperar dados de uma fonte de dados.  
  
-   `name` Define a identidade usada pelo <xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataSourceAttribute> para especificar qual fonte de dados usar.  
  
-   `connectionString` identifica a seqüência de conexão criada na seção anterior Defina seqüências de conexão.  
  
-   `dataTableName` Define a tabela ou planilha que contém os dados a serem usados no teste.  
  
-   `dataAccessMethod` Define a técnica para acessar valores de dados na fonte de dados.  
  
 Nesta seção, você irá definir duas fontes de dados para usar em um teste de unidade.  
  
#### Para definir fontes de dados  
  
1.  Após o `connectionStrings` elemento, criar uma `microsoft.visualstudio.testtools` elemento.  Esta seção foi criada na seção defina uma seção de configuração personalizada.  
  
2.  Dentro do `microsoft.visualstudio.testtools` elemento, criar uma `dataSources` elemento.  
  
3.  Dentro do `dataSources` elemento, criar dois `add` elementos.  
  
4.  Na primeira `add` elemento, crie os seguintes atributos e valores para uma fonte de dados do Microsoft Access:  
  
|Atributo|Valores|  
|--------------|-------------|  
|`name`|`"MyJetDataSource"`|  
|`connectionString`|`"MyJetConn"`|  
|`dataTableName`|`"MyDataTable"`|  
|`dataAccessMethod`|`"Sequential"`|  
  
 No segundo `add` elemento, crie os seguintes atributos e valores de uma fonte de dados do Microsoft Excel:  
  
|||  
|-|-|  
|`Name`|`"MyExcelDataSource"`|  
|`connectionString`|`"MyExcelConn"`|  
|`dataTableName`|`"Sheet1$"`|  
|`dataAccessMethod`|`"Sequential"`|  
  
 O `microsoft.visualstudio.testtools` elemento deve ser semelhante a este:  
  
```  
<microsoft.visualstudio.testtools>  
    <dataSources>  
        <add name="MyJetDataSource" connectionString="MyJetConn" dataTableName="MyDataTable" dataAccessMethod="Sequential"/>  
        <add name="MyExcelDataSource" connectionString="MyExcelConn" dataTableName="Sheet1$" dataAccessMethod="Sequential"/>  
    </dataSources>  
</microsoft.visualstudio.testtools>  
```  
  
 O arquivo App. config final deve parecer semelhante a este:  
  
```  
<?xml version="1.0" encoding="utf-8" ?>  
<configuration>  
    <configSections>  
        <section name="microsoft.visualstudio.testtools" type="Microsoft.VisualStudio.TestTools.UnitTesting.TestConfigurationSection, Microsoft.VisualStudio.QualityTools.UnitTestFramework, Version=8.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a"/>   
    </configSections>  
    <connectionStrings>  
        <add name="MyJetConn" connectionString="Provider=Microsoft.Jet.OLEDB.4.0; Data Source=C:\testdatasource.accdb; Persist Security Info=False;" providerName="System.Data.OleDb" />  
        <add name="MyExcelConn" connectionString="Dsn=Excel Files;dbq=data.xlsx;defaultdir=.; driverid=790;maxbuffersize=2048;pagetimeout=5" providerName="System.Data.Odbc" />  
    </connectionStrings>  
    <microsoft.visualstudio.testtools>  
        <dataSources>  
            <add name="MyJetDataSource" connectionString="MyJetConn" dataTableName="MyDataTable" dataAccessMethod="Sequential"/>  
            <add name="MyExcelDataSource" connectionString="MyExcelConn" dataTableName="Sheet1$" dataAccessMethod="Sequential"/>  
        </dataSources>  
    </microsoft.visualstudio.testtools>  
</configuration>  
```  
  
## Criar um teste de unidade usando fontes de dados definidas no App. config  
 Agora que um arquivo App. config foi definido, você criará um teste de unidade que usa dados localizados em fontes de dados que são definidas no arquivo App. config.  Nesta seção, você irá:  
  
-   Crie fontes de dados encontradas no arquivo App. config.  
  
-   Use as fontes de dados em dois métodos de teste que comparam os valores em cada fonte de dados.  
  
#### Para criar uma fonte de dados do Microsoft Access  
  
1.  Criar um banco de dados do Microsoft Access chamado `testdatasource.accdb`.  
  
2.  Criar uma tabela e denomine\- `MyDataTable` em `testdatasource.accdb`.  
  
3.  Crie dois campos no `MyDataTable` chamado `Arg1` e `Arg2` usando o `Number` tipo de dados.  
  
4.  Adicione cinco entidades para `MyDataTable` com os seguintes valores para `Arg1` e `Arg2`, respectivamente: \(10,50\), \(3,2\), \(6,0\), \(0,8\) e \(12312,1000\).  
  
5.  Salve e feche o banco de dados.  
  
6.  Altere a cadeia de conexão para apontar para o local do banco de dados.  Altere o valor de `Data Source` para refletir o local do banco de dados.  
  
#### Para criar uma fonte de dados do Microsoft Excel  
  
1.  Crie uma planilha do Microsoft Excel chamada `data.xlsx`.  
  
2.  Criar uma planilha chamada `Sheet1` se ele ainda não existir no `data.xlsx`.  
  
3.  Crie dois cabeçalhos de coluna e os `Val1` e `Val2` em `Sheet1`.  
  
4.  Adicione cinco entidades para `Sheet1` com os seguintes valores para `Val1` e `Val2`, respectivamente: \(1,1\), \(2,2\), \(3,3\), \(4,4\) e \(5,0\).  
  
5.  Salve e feche a planilha.  
  
6.  Altere a cadeia de conexão para apontar para o local da planilha.  Altere o valor de `dbq` para refletir o local da planilha.  
  
#### Para criar um teste de unidade usando as fontes de dados do App. config  
  
1.  Adicione um teste de unidade ao projeto de teste.  
  
     Para obter mais informações, consulte [Creating and Running Unit Tests for Existing Code](http://msdn.microsoft.com/pt-br/e8370b93-085b-41c9-8dec-655bd886f173).  
  
2.  Substitua o conteúdo gerado automaticamente do teste de unidade com o seguinte código:  
  
    ```  
    using System;  
    using Microsoft.VisualStudio.TestTools.UnitTesting;  
  
    namespace TestProject1  
    {  
         [TestClass]  
        public class UnitTest1  
        {  
            private TestContext context;  
  
            public TestContext TestContext  
            {  
                get { return context; }  
                set { context = value; }  
            }  
  
            [TestMethod()]  
            [DeploymentItem("MyTestProject\\testdatasource.accdb")]  
            [DataSource("MyJetDataSource")]  
            public void MyTestMethod()  
            {  
                int a = Int32.Parse(context.DataRow["Arg1"].ToString());  
                int b = Int32.Parse(context.DataRow["Arg2"].ToString());  
                Assert.AreNotEqual(a, b, "A value was equal.");  
            }  
  
            [TestMethod()]  
            [DeploymentItem("MyTestProject\\data.xlsx")]  
            [DataSource("MyExcelDataSource")]  
            public void MyTestMethod2()  
            {  
                Assert.AreEqual(context.DataRow["Val1"], context.DataRow["Val2"]);  
            }  
        }  
    }  
    ```  
  
3.  Examine os atributos de fonte de dados.  Observe os nomes de configuração do arquivo App. config.  
  
4.  Compile sua solução e execute testes MyTestMethod e MyTestMethod2.  
  
> [!IMPORTANT]
>  Implante itens como fontes de dados para que fiquem acessíveis para o teste no diretório de implantação.  
  
## Consulte também  
 [Teste de unidade de código](../test/unit-test-your-code.md)   
 [Creating and Running Unit Tests for Existing Code](http://msdn.microsoft.com/pt-br/e8370b93-085b-41c9-8dec-655bd886f173)   
 [Testando o aplicativo](/devops-test-docs/test/test-apps-early-and-often)   
 [Como criar um teste de unidade orientado a dados](../test/how-to-create-a-data-driven-unit-test.md)