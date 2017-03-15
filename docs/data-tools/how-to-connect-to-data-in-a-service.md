---
title: "Como conectar a dados em um servi&#231;o | Microsoft Docs"
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
  - "dados [Visual Studio], conectando-se a serviços Web"
  - "dados [Visual Studio], lendo de serviços Web"
  - "fontes de dados, criando de serviços Web"
  - "lendo dados, de serviços Web"
  - "Serviços Web, como fontes de dados"
  - "Serviços Web, conectando"
  - "Serviços Web, lendo dados"
ms.assetid: a6b54353-05fe-4e5c-8631-90231fc95504
caps.latest.revision: 32
caps.handback.revision: 32
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Como conectar a dados em um servi&#231;o
Você conecta seu aplicativo aos dados retornados de um serviço executando o [Assistente para Configuração da Fonte de Dados](../data-tools/media/data-source-configuration-wizard.png) e selecionando **Service** no **Escolher um tipo de fonte de dados** página.  
  
 Após a conclusão do assistente, uma referência de serviço é adicionada ao seu projeto e fica imediatamente disponível na [Janela Fontes de Dados](../Topic/Data%20Sources%20Window.md).  
  
> [!NOTE]
>  Os itens que aparecem no **fontes de dados** janela são dependentes das informações que o serviço retorna. Alguns serviços podem não fornecer informações suficientes para que o **Data Source Configuration Wizard** para criar objetos ligáveis. Por exemplo, se o serviço retorna um conjunto de dados não tipado, nenhum item aparece no **janela fontes de dados** após concluir o assistente. Isso ocorre porque datasets não tipados não fornecem esquema, então o assistente não tem informações suficientes para criar a fonte de dados.  
  
 [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
### Para conectar seu aplicativo a um serviço  
  
1.  Sobre o **dados** menu, clique em **Add New Data Source**.  
  
2.  Selecione **Service** no **Escolher um tipo de fonte de dados** página e, em seguida, clique em **próximo**.  
  
3.  Insira o endereço do serviço que você deseja usar ou clique em **Discover** para localizar serviços na solução atual e, em seguida, clique em **vá**.  
  
4.  Opcionalmente, um novo **Namespace** podem ser digitados no lugar do valor padrão.  
  
    > [!NOTE]
    >  Clique em **Avançado** para abrir o [Configure Service Reference Dialog Box](../data-tools/configure-service-reference-dialog-box.md).  
  
5.  Clique em **OK** para adicionar uma referência ao seu projeto.  
  
6.  Clique em **Concluir**.  
  
     A fonte de dados é adicionada para o **fontes de dados** janela.  
  
## Próximas etapas  
  
#### Para adicionar funcionalidade ao seu aplicativo  
  
-   Selecione um item no **fontes de dados** janela e arraste\-o para um formulário para criar controles associados. Para obter mais informações, consulte [Associar controles a dados no Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md).  
  
## Consulte também  
 [Associar controles WPF a um WCF data service](../data-tools/bind-wpf-controls-to-a-wcf-data-service.md)   
 [Serviços do Windows Communication Foundation e WCF Data Services no Visual Studio](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md)