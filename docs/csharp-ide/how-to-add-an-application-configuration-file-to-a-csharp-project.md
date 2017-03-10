---
title: "How to: Add an Application Configuration File to a C# Project | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "app.config files, adding to C# projects"
ms.assetid: 9caf6bb0-c2fc-4ab6-ba69-bed3b880fbf8
caps.latest.revision: 20
caps.handback.revision: 20
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# How to: Add an Application Configuration File to a C# Project
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Adicionando um arquivo de configuração do aplicativo \(arquivo app.config\) em um projeto C\#, você pode personalizar como o common language runtime continua e carregar arquivos de assembly.  Para obter mais informações sobre arquivos de configuração do aplicativo, consulte [Como o tempo de execução localiza assemblies](../Topic/How%20the%20Runtime%20Locates%20Assemblies.md).  
  
> [!NOTE]
>  A Windows Store não oferece suporte a <xref:System.Configuration>.  Como resultado, aplicativos de armazenamento não contêm um modelo app.config.  
  
 Quando você compila seu projeto, o ambiente de desenvolvimento automaticamente copia o arquivo app.config, altere o nome do arquivo de impressão para coincidir com o executável, e então move a cópia no diretório bin.  
  
### Para adicionar um arquivo de configuração do aplicativo ao seu projeto C\#  
  
1.  Na barra de menus, escolha **Projeto**, **Adicionar novo item**.  
  
     A caixa de diálogo **Adicionar Novo Item** aparece.  
  
2.  Expanda **Instalado**, expanda **Itens do Visual C\#**, e então escolha o modelo de **Arquivo de Configuração do Aplicativo** .  
  
3.  Na caixa de texto **Nome** , digite um nome, e clique no botão de **Adicionar** .  
  
     Um arquivo chamado app.config é adicionado ao seu projeto.  
  
## Consulte também  
 [Gerenciando configurações de aplicativo \(.NET\)](../ide/managing-application-settings-dotnet.md)   
 [Esquema de arquivos de configuração](../Topic/Configuration%20File%20Schema%20for%20the%20.NET%20Framework.md)   
 [Configurando aplicativos](../Topic/Configuring%20Apps%20by%20using%20Configuration%20Files.md)   
 [How to: Configure an App to Target a .NET Framework Version](http://msdn.microsoft.com/pt-br/5247b307-89ca-417b-8dd0-e8f9bd2f4717)   
 [Usando o ambiente de desenvolvimento do Visual Studio c\#](../csharp-ide/using-the-visual-studio-development-environment-for-csharp.md)