---
title: "The connection string contains credentials with a clear text password and is not using integrated security | Microsoft Docs"
ms.custom: ""
ms.date: "11/23/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 501d85af-92e0-4471-b280-8a59c0688575
caps.latest.revision: 3
caps.handback.revision: 3
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# The connection string contains credentials with a clear text password and is not using integrated security
Você deseja salvar a cadeia de conexão para o arquivo DBML atual e os arquivos de configuração do aplicativo com essas informações confidenciais?  Clique em não para salvar a cadeia de conexão sem as informações confidenciais.  
  
 Ao trabalhar com conexões de dados que contêm informações confidenciais \(senhas que são incluídos na cadeia de conexão\), você terá a opção de salvar a cadeia de conexão no arquivo DBML de um projeto e o arquivo de configuração do aplicativo com ou sem as informações confidenciais.  
  
> [!WARNING]
>  Definir explicitamente o **conexão** propriedades **configurações do aplicativo** propriedade **False** adicionará a senha para o arquivo DBML.  
  
### Para salvar a cadeia de conexão com informações sigilosas nas configurações do aplicativo do projeto  
  
-   Clique em **Sim**.  
  
     A cadeia de conexão é armazenada como uma configuração de aplicativo. A cadeia de conexão inclui as informações confidenciais em texto sem formatação. O arquivo DBML não contém as informações confidenciais.  
  
### Para salvar a cadeia de conexão sem informações sigilosas nas configurações do aplicativo do projeto  
  
-   Clique em **não**.  
  
     A cadeia de conexão é armazenada como uma configuração de aplicativo, mas a senha não está incluída.  
  
## Consulte também  
 [LINQ to SQL Tools no Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)