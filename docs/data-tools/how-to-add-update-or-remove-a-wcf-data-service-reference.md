---
title: "How to: Add, Update, or Remove a WCF Data Service Reference | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "service references [Visual Studio]"
  - "WCF Data Service reference"
  - "WCF data service references"
  - "ADO.NET service references"
  - "ADO.NET Data Service reference"
ms.assetid: 892ebf37-3af4-472e-8744-92837677d611
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# How to: Add, Update, or Remove a WCF Data Service Reference
Um *referência de serviço* permite que um projeto para acessar um ou mais [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)]. Use o **Add Service Reference** caixa de diálogo para procurar [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)] na solução atual, localmente, em uma rede local ou na Internet.  
  
 [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
## Adicionando uma referência de serviço  
  
#### Para adicionar uma referência para um serviço externo  
  
1.  Em **Solution Explorer**, clique no nome do projeto que você deseja adicionar o serviço e, em seguida, clique em **Add Service Reference**.  
  
     O **Add Service Reference** caixa de diálogo é exibida.  
  
2.  No **endereço** caixa, digite a URL para o serviço e, em seguida, clique em **vá** para procurar o serviço. Se o serviço implementar segurança de nome e senha de usuário, você receberá um nome de usuário e senha.  
  
    > [!NOTE]
    >  Você deve referenciar apenas serviços de uma fonte confiável. Adicionando referências de uma fonte não confiável pode comprometer a segurança.  
  
     Você também pode selecionar a URL do **endereço** lista, que armazena as URLs de 15 anteriores na qual os metadados de serviço válida foi encontrado.  
  
     Uma barra de progresso é exibida quando a pesquisa está sendo executada. Você pode parar a pesquisa a qualquer momento clicando em **Parar**.  
  
3.  No **serviços** lista, expanda o nó para o serviço que você deseja usar e selecione um conjunto de entidades.  
  
4.  No **Namespace** digite o namespace que você deseja usar para a referência.  
  
5.  Clique em **OK** para adicionar a referência ao projeto.  
  
     Um cliente de serviço \(proxy\) é gerado e metadados que descrevem o serviço é adicionado ao arquivo App. config.  
  
#### Para adicionar uma referência a um serviço na solução atual  
  
1.  Em **Solution Explorer**, clique no nome do projeto que você deseja adicionar o serviço e, em seguida, clique em **Add Service Reference**.  
  
     O **Add Service Reference** caixa de diálogo é exibida.  
  
2.  Clique em **descobrir**.  
  
     Todos os serviços \(ambos [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)] e serviços WCF\) na solução atual são adicionadas a **serviços** lista.  
  
3.  No **serviços** lista, expanda o nó para o serviço que você deseja usar e selecione um conjunto de entidades.  
  
4.  No **Namespace** digite o namespace que você deseja usar para a referência.  
  
5.  Clique em **OK** para adicionar a referência ao projeto.  
  
     Um cliente de serviço \(proxy\) é gerado e metadados que descrevem o serviço é adicionado ao arquivo App. config.  
  
## Atualizando uma referência de serviço  
 O modelo de dados de entidade para uma [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)] às vezes será alterado. Quando isso acontece, a referência de serviço deve ser atualizada.  
  
#### Para atualizar uma referência de serviço  
  
-   Em **Solution Explorer**, clique com botão direito a referência de serviço e, em seguida, clique em **Update Service Reference**.  
  
     Uma caixa de diálogo de progresso é exibida enquanto a referência é atualizada de seu local original e o cliente do serviço será gerada novamente para refletir quaisquer alterações nos metadados.  
  
## Removendo uma referência de serviço  
 Se uma referência de serviço não estiver sendo usada, você poderá ser removido de sua solução.  
  
#### Para remover uma referência de serviço  
  
-   Em **Solution Explorer**, clique com botão direito a referência de serviço e, em seguida, clique em **Excluir**.  
  
     O cliente do serviço será removido da solução, e os metadados que descrevem o serviço serão removido do arquivo App. config.  
  
    > [!NOTE]
    >  Qualquer código que faz referência a referência de serviço precisará ser removido manualmente.  
  
## Consulte também  
 [Serviços do Windows Communication Foundation e WCF Data Services no Visual Studio](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md)