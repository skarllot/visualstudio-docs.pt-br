---
title: "Configure Service Reference Dialog Box | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "msvse_wcf.dlg.ConfigureServiceReference"
helpviewer_keywords: 
  - "WCF services, Configure Service Reference dialog box"
  - "service references [Visual Studio], configuring behavior"
  - "Configure Service Reference dialog box"
ms.assetid: 25e4c36b-2db6-4e71-9010-b7068255d09d
caps.latest.revision: 16
caps.handback.revision: 16
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Configure Service Reference Dialog Box
O **Configure Service Reference** caixa de diálogo permite que você configure o comportamento de [!INCLUDE[vsindigo](../data-tools/includes/vsindigo_md.md)] services.  
  
> [!NOTE]
>  Caixas de diálogo e comandos de menu que você vê podem diferir daqueles descritos na Ajuda, dependendo de suas configurações ativas ou edição. Para alterar as configurações, escolha Import and Export Settings no menu Ferramentas. Para obter mais informações, consulte [Personalizando configurações de desenvolvimento no Visual Studio](http://msdn.microsoft.com/pt-br/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
 Para acessar o **Configure Service Reference** caixa de diálogo com o botão direito, um serviço de referência em **Solution Explorer** e escolha **Configure Service Reference**. Você também pode acessar a caixa de diálogo clicando o **Avançado** no botão de **Add Service Reference Dialog Box**.  
  
## Lista de Tarefas  
  
-   Para alterar o endereço em que um serviço WCF está hospedado, digite o novo endereço na **endereço** campo.  
  
-   Para alterar o nível de acesso para classes em um cliente WCF, selecione uma palavra\-chave de nível de acesso no **nível para as classes geradas de acesso** lista.  
  
-   Para chamar os métodos de um serviço WCF de forma assíncrona, selecione o **Gerar operações assíncronas** caixa de seleção.  
  
-   Para gerar os tipos de contrato de mensagem em um cliente WCF, selecione o **sempre gerar contratos de mensagem** caixa de seleção.  
  
-   Para especificar os tipos de coleção de lista ou de dicionário para um cliente WCF, selecione os tipos a partir de **tipo de coleção** e **tipo de coleção de dicionário** lista.  
  
-   Para desabilitar o compartilhamento de tipo, desmarque o **usar novamente os tipos em assemblies referenciados** caixa de seleção. Para habilitar o compartilhamento de um subconjunto dos assemblies referenciados de tipo, selecione o **usar novamente os tipos em assemblies referenciados** caixas de seleção **usar novamente os tipos em assemblies referenciados especificados**, e selecione as referências desejadas no **lista de assemblies referenciada**.  
  
## Lista UIElement  
 **Endereço**  
 Usado para atualizar o endereço da Web onde uma referência de serviço procura por um serviço. Por exemplo, durante o desenvolvimento de serviço pode estar hospedado em um servidor de desenvolvimento e posteriormente movido para um servidor de produção, a necessidade de uma alteração de endereço.  
  
> [!NOTE]
>  O elemento de endereço não está disponível quando o **Configure Service Reference** caixa de diálogo é exibida do **Add Service Reference Dialog Box**.  
  
 **Nível de acesso para classes geradas**  
 Determina o nível de acesso de código para as classes de cliente do WCF.  
  
> [!NOTE]
>  Para projetos de site, essa opção é sempre definida como `Public` e não pode ser alterado. Para obter mais informações, consulte [Troubleshooting Service References](../data-tools/troubleshooting-service-references.md).  
  
 **Gerar operações assíncronas**  
 Determina se os métodos de serviço WCF serão chamados síncrona \(o padrão\) ou assíncrona.  
  
 **Gerar operações baseadas em tarefas**  
 Ao escrever o código assíncrono, esta opção permite que você tire proveito da tarefa paralela TPL \(biblioteca\) que foi introduzido com o .net 4. Consulte [\(TPL\) de biblioteca paralela de tarefas](http://msdn.microsoft.com/library/dd460717.aspx).  
  
 **Sempre gerar contratos de mensagem**  
 Determina se os tipos de contrato de mensagem serão gerados para um cliente WCF. Para obter mais informações sobre contratos de mensagem, consulte [Utilizando contratos de mensagem](../Topic/Using%20Message%20Contracts.md).  
  
 **Tipo de coleção**  
 Especifica o tipo de coleção da lista para um cliente WCF. O tipo padrão é <xref:System.Array>.  
  
 **Tipo de coleção de dicionário**  
 Especifica o tipo de coleção de dicionário para um cliente WCF. O tipo padrão é <xref:System.Collections.Generic.Dictionary%602>.  
  
 **Usar novamente os tipos em assemblies referenciados**  
 Determina se um cliente WCF irá tentar reutilizar que já existem em assemblies referenciados em vez de gerar novos tipos quando um serviço é adicionado ou atualizado. Por padrão, esta opção estiver marcada.  
  
 **Usar novamente os tipos em todos os assemblies referenciados**  
 Quando selecionada, todos os tipos do **lista de assemblies referenciada** será reutilizado se possível. Por padrão, essa opção é selecionada.  
  
 **Usar novamente os tipos em assemblies referenciados especificados**  
 Quando selecionada, somente os tipos selecionados no **lista de assemblies referenciada** será reutilizado.  
  
 **Lista de assemblies referenciados**  
 Contém uma lista de assemblies referenciados para o site ou projeto. Quando **usar novamente os tipos em assemblies referenciados especificados** estiver selecionada, assemblies individuais podem ser marcados ou desmarcados.  
  
 **Adicionar referência da Web**  
 Exibe o [NIB: adicionar a caixa de diálogo de referência Web](http://msdn.microsoft.com/pt-br/bdf05776-c591-40af-bfd7-e1e2aa1e87b5).  
  
> [!NOTE]
>  Essa opção deve ser usada somente para projetos que usam a versão 2.0 do [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)].  
  
> [!NOTE]
>  O **Add Web Reference** botão está disponível apenas quando o **Configure Service Reference** caixa de diálogo é exibida do **Add Service Reference Dialog Box**.  
  
## Consulte também  
 [How to: Add, Update, or Remove a Service Reference](../Topic/How%20to:%20Add,%20Update,%20or%20Remove%20a%20Service%20Reference.md)   
 [How to: Add a Reference to a Web Service](../Topic/How%20to:%20Add%20a%20Reference%20to%20a%20Web%20Service.md)   
 [Windows Communication Foundation Services and WCF Data Services](../data-tools/configure-service-reference-dialog-box.md)