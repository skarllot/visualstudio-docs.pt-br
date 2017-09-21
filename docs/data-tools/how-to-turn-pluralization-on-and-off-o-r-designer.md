---
title: "Como: ative em pluralization e off (Object Relational Designer) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 9b693bc3-303a-40a9-97ee-9cef5ca3ae81
caps.latest.revision: 2
caps.handback.revision: 2
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Como: ative em pluralization e off (Object Relational Designer)
Por padrão, quando você arrasta os objetos de base de dados que têm nomes que terminam em s ou em ies de **Gerenciador de Servidores**\/**Gerenciador de Banco de Dados** em [LINQ to SQL Tools no Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md), os nomes das classes de entidade gerados são alterados de plural a única.  Isso é feito a representa mais precisamente o fato que a classe instanciado de entidade mapeia para um único registro de dados.  Por exemplo, adicione uma tabela de clientes para os resultados de [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] em uma classe de entidade chamada Cliente porque a classe conterá dados para apenas um único cliente.  
  
> [!NOTE]
>  Pluralization está ativada por padrão somente na versão de língua inglesa do Visual Studio.  
  
 [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
### Para desativar o pluralization e sobre  
  
1.  No menu **Ferramentas**, clique em **Opções**.  
  
2.  Na caixa de diálogo **Opções** , expanda **Ferramentas de Banco de Dados**.  
  
> [!NOTE]
>  Selecione **Mostrar todas as configurações** se o nó de **Ferramentas de Banco de Dados** não estiver visível.  
  
1.  Clique **Object relational Designer de Objetos**.  
  
2.  Definir **Pluralização de nomes** a **Habilitado** \= a **False** para definir [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] de modo que não modifique nomes de classe.  
  
3.  Definir **Pluralização de nomes** a **Habilitado** \= a **Verdadeiro** para aplicar regras de pluralization os nomes de classe de objetos adicionados a [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)].  
  
## Consulte também  
 [LINQ to SQL Tools no Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
 [LINQ to SQL](../Topic/LINQ%20to%20SQL.md)   
 [Acessando dados no Visual Studio](../data-tools/accessing-data-in-visual-studio.md)