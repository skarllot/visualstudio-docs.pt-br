---
title: "Criar e gerenciar bancos de dados e aplicativos de camada de dados no Visual Studio | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "gerenciamento de alterações, bancos de dados"
  - "recursos de banco de dados do Visual Studio, gerenciamento de alterações"
  - "bancos de dados, gerenciamento de alterações"
  - "gerenciamento de alterações, servidores de banco de dados"
ms.assetid: 40b51f5a-d52c-44ac-8f84-037a0917af33
caps.latest.revision: 37
caps.handback.revision: 37
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Criar e gerenciar bancos de dados e aplicativos de camada de dados no Visual Studio
> [!IMPORTANT]
>  Os projetos de banco de dados que foram incluídos em versões anteriores do [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] agora são fornecidos em [!INCLUDE[sql_Denali_long](../data-tools/includes/sql_denali_long_md.md)] Ferramentas. Para obter mais informações, consulte [SQL Server Developer Tools](http://go.microsoft.com/fwlink/?LinkId=228126).  
  
 Você pode usar os projetos de banco de dados para criar novos bancos de dados, novos aplicativos da camada de dados \(DACs\) e atualizar bancos de dados existentes e aplicativos de camada de dados. Projetos de banco de dados e projetos de DAC permitem aplicar as técnicas de gerenciamento de projeto e controle de versão para seus esforços de desenvolvimento de banco de dados da mesma maneira que você aplica essas técnicas para código gerenciado ou nativo. Você pode ajudar sua equipe de desenvolvimento a gerenciar as alterações de bancos de dados e servidores de banco de dados, criando um *projeto DAC*, *projeto de banco de dados*, ou um *project server* e colocá\-lo sob controle de versão. Membros de sua equipe podem consultar arquivos para fazer, compilar e testar as alterações em um *ambiente de desenvolvimento isolado*, ou de área restrita, antes de compartilhá\-los com a equipe. Para ajudar a garantir a qualidade do código, sua equipe pode concluir e testar todas as alterações para uma versão específica do banco de dados em um ambiente de preparo antes de implantar as alterações na produção.  
  
 Para obter uma lista dos recursos de banco de dados que são suportados por aplicativos de camada de dados, consulte [recursos com suporte em aplicativos de camada de dados](http://go.microsoft.com/fwlink/?LinkId=164239) no site da Microsoft. Se você usar recursos que não são suportados por aplicativos de camada de dados no banco de dados, você deve usar um projeto de banco de dados para gerenciar as alterações ao banco de dados.  
  
## Tarefas comuns de alto nível  
  
|Tarefas de alto nível|Conteúdo de suporte|  
|---------------------------|-------------------------|  
|**Começar o desenvolvimento de um aplicativo da camada de dados:** um DAC é um novo conceito apresentado com [!INCLUDE[sskatmai_r2](../data-tools/includes/sskatmai_r2_md.md)] que contém a definição de um [!INCLUDE[ssNoVersion](../data-tools/includes/ssnoversion_md.md)] objetos que são usados por um cliente\-servidor ou aplicativo da camada 3 de instância de banco de dados e o suporte. Um DAC inclui objetos de banco de dados, como tabelas e modos de exibição, junto com entidades de instância, como logons. Você pode usar [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] para criar um projeto de DAC, crie um arquivo de pacote DAC e enviar esse arquivo de pacote DAC para um administrador de banco de dados para implantação em uma instância do [!INCLUDE[ssNoVersion](../data-tools/includes/ssnoversion_md.md)] mecanismo de banco de dados.|-   [Criando e gerenciando aplicativos de camada de dados](http://go.microsoft.com/fwlink/?LinkId=160741) \(Microsoft web site\)<br />-   [SQL Server Management Studio](http://go.microsoft.com/fwlink/?LinkId=227328)|  
|**Realizam o desenvolvimento de banco de dados iterativos:** se você for um desenvolvedor ou um testador, check\-out de partes do projeto e, em seguida, atualizá\-los em um ambiente de desenvolvimento isolado. Usando esse tipo de ambiente, você pode testar suas alterações sem afetar outros membros da equipe. Depois que as alterações forem concluídas, você verificar os arquivos de volta para o controle de versão, onde outros membros da equipe podem obter as alterações e compilar e implantá\-los em um servidor de teste.|-   [Consulta e editores de texto \(SQL Server Management Studio\)](http://go.microsoft.com/fwlink/?LinkId=227327) \(Microsoft web site\)<br />-   [Depurador Transact\-SQL](http://go.microsoft.com/fwlink/?LinkId=227324) \(Microsoft web site\)|  
|**Criação de protótipos, verificando resultados de teste e modificar objetos e scripts de banco de dados:** você pode usar o [!INCLUDE[tsql](../data-tools/includes/tsql_md.md)] editor para executar qualquer uma dessas tarefas comuns.|-   [Consulta e editores de texto \(SQL Server Management Studio\)](http://go.microsoft.com/fwlink/?LinkId=227327) \(Microsoft web site\)|  
  
## Consulte também  
 [Ferramentas de dados do Visual Studio para .NET](../data-tools/visual-studio-data-tools-for-dotnet.md)