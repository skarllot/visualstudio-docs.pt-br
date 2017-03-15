---
title: "Ferramentas de dados do Visual Studio para .NET | Microsoft Docs"
ms.custom: ""
ms.date: "11/23/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c3175080-1dfb-4ab8-a460-92dadbb844b4
caps.latest.revision: 20
caps.handback.revision: 20
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Ferramentas de dados do Visual Studio para .NET
O Visual Studio e o .NET Framework juntos fornecem API abrangentes e ferramentas de suporte para se conectar a bancos de dados, modelagem de dados na memória e exibir os dados na interface do usuário.  As classes do .NET Framework que fornecem funcionalidade de acesso a dados são conhecidas como [ADO.NET](https://msdn.microsoft.com/en-us/library/e80y5yhx\(v=vs.110\).aspx). ADO.NET, juntamente com os dados das ferramentas no Visual Studio, foi originalmente projetado principalmente para oferecer suporte a bancos de dados relacionais e XML. Atualmente, muitos fornecedores de banco de dados NoSQL, ou de terceiros, oferecem provedores ADO.NET.  
  
 Atualização 2 do Visual Studio 2015 inclui as atualizações mais recentes de [SQL Server Data Tools](https://msdn.microsoft.com/library/hh272686\(v=vs.103\).aspx), que permitem que o suporte para os recursos mais recentes no Azure [banco de dados SQL](https://azure.microsoft.com/en-us/services/sql-database/) e [SQL Server 2016](https://www.microsoft.com/en-us/server-cloud/products/sql-server-2016/).[.NET core](https://www.dotnetfoundation.org/netcore) suporta ADO.NET, exceto para conjuntos de dados e os tipos relacionados. Se você tiver como alvo o .NET Core e exige uma camada de mapeamento relacional de objeto \(ORM\), use [Entity Framework Core](https://msdn.microsoft.com/en-us/data/ef.aspx).  
  
 O diagrama a seguir mostra uma exibição simplificada da arquitetura básica:  
  
 ![ADO.NET Architecture](../data-tools/media/raddata-ado.net-architecture-diagram.png "raddata ADO.NET Architecture Diagram")  
  
 O fluxo de trabalho típico é o seguinte:  
  
1.  Instale um banco de dados de teste ou desenvolvimento em sua máquina local. Consulte [Instalar sistemas de banco de dados, ferramentas e exemplos](../data-tools/installing-database-systems-tools-and-samples.md). Se você estiver usando um serviço de dados do Azure, essa etapa não é necessária.  
  
2.  Teste a conexão com o banco de dados \(ou serviço ou arquivo local\) no Visual Studio. Consulte [Adicionar novas conexões](../data-tools/add-new-connections.md).  
  
3.  \(Opcional\) Use as ferramentas para gerar e configurar um novo modelo. Modelos com base no Entity Framework são a recomendação padrão para novos aplicativos. O modelo, qualquer um que você usa, é a fonte de dados que o aplicativo interage com. O modelo situada logicamente entre o banco de dados ou serviço e o aplicativo.  Consulte [Adicionar novas fontes de dados](../data-tools/add-new-data-sources.md).  
  
4.  Arraste a fonte de dados de **fontes de dados** janela em uma superfície de design do Windows Forms, ASP.NET ou Windows Presentation Foundation para gerar o código de associação de dados que exibirão os dados para o usuário da maneira que você especificar. Consulte [Associar controles a dados no Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md).  
  
5.  Adicione código personalizado para coisas como as regras de negócio, pesquisa e validação de dados ou para tirar proveito da funcionalidade personalizada que expõe o banco de dados subjacente.  
  
 Você pode ignorar a etapa 3 e programar um aplicativo .NET para emitir comandos diretamente para um banco de dados, em vez de usar um modelo. Nesse caso, você encontrará a documentação relevante aqui: [ADO.NET](https://msdn.microsoft.com/en-us/library/e80y5yhx\(v=vs.110\).aspx). Observe que você ainda pode usar o Assistente de configuração de fonte de dados e designers para gerar código de associação de dados ao preencher seus próprios objetos na memória e, em seguida, controles de interface do usuário de ligação de dados para esses objetos.  
  
## Nesta seção  
  
-   [Criar um aplicativo simples de dados usando o ADO.NET](../data-tools/create-a-simple-data-application-by-using-adonet.md)  
  
-   [Adicionar novas conexões](../data-tools/add-new-connections.md)  
  
-   [Adicionar novas fontes de dados](../data-tools/add-new-data-sources.md)  
  
-   [Ferramentas do modelo de dados de entidade no Visual Studio](../data-tools/entity-data-model-tools-in-visual-studio.md)  
  
-   [Ferramentas do conjunto de dados no Visual Studio](../data-tools/dataset-tools-in-visual-studio.md)  
  
-   [LINQ to SQL Tools no Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)  
  
-   [Associar controles a dados no Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)  
  
-   [Recursos adicionais para solucionar problemas de erros de acesso a dados](../data-tools/additional-resources-for-troubleshooting-data-access-errors.md)  
  
-   [Serviços do Windows Communication Foundation e WCF Data Services no Visual Studio](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md)  
  
-   [Criar e gerenciar bancos de dados e aplicativos de camada de dados no Visual Studio](../data-tools/creating-and-managing-databases-and-data-tier-applications-in-visual-studio.md)  
  
-   [Recursos adicionais para solucionar problemas de erros de acesso a dados](../data-tools/additional-resources-for-troubleshooting-data-access-errors.md)  
  
## Consulte também  
 [Acessando dados no Visual Studio](../data-tools/accessing-data-in-visual-studio.md)