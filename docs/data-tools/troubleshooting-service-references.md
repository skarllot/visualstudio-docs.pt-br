---
title: "Troubleshooting Service References | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "msvse_wcf.Err.ReferenceGroup_NamespaceConflictsOther"
  - "msvse_wcf.Err.AddSvcRefDlg_NothingSelectedOnGo"
  - "msvse_wcf.Err.ErrorOnOK"
  - "msvse_wcf.cfg.ConfigurationErrorsException"
helpviewer_keywords: 
  - "service references [Visual Studio], troubleshooting"
  - "WCF services, troubleshooting"
ms.assetid: 3b531120-1325-4734-90c6-6e6113bd12ac
caps.latest.revision: 22
caps.handback.revision: 22
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Troubleshooting Service References
Este tópico lista problemas comuns que podem ocorrer quando você estiver trabalhando com [!INCLUDE[vsindigo](../data-tools/includes/vsindigo_md.md)] ou [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)] referências em [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
## Erro retornando dados de um serviço  
 Ao retornar um `DataSet` ou `DataTable` de um serviço, você receberá uma exceção "a cota de tamanho máximo para mensagens de entrada foi excedida". Por padrão, o `MaxReceivedMessageSize` para algumas associações é definida como um valor relativamente pequeno para limitar a exposição a ataques de negação de serviço. Você pode aumentar esse valor para evitar a exceção. Para obter mais informações, consulte <xref:System.ServiceModel.BasicHttpBinding.MaxReceivedMessageSize%2A>.  
  
 Para corrigir esse erro:  
  
1.  Em **Solution Explorer**, clique duas vezes no arquivo App. config para abri\-lo.  
  
2.  Localize o `MaxReceivedMessageSize` propriedade e alterá\-lo para um valor maior.  
  
## Não é possível localizar um serviço em minha solução  
 Quando você clica o **Discover** no botão de **Adicionar referências de serviço** caixa de diálogo, um ou mais projetos de biblioteca de serviços WCF na solução não aparecem na lista de serviços. Isso pode ocorrer se uma biblioteca de serviço foi adicionada à solução, mas ainda não foram compilada.  
  
 Para corrigir esse erro:  
  
-   Em **Solution Explorer**, com o botão direito no projeto da biblioteca de serviço do WCF e clique em **criar**.  
  
## Erro ao acessar um serviço em uma área de trabalho remota  
 Quando um usuário acessa um serviço WCF hospedado na Web sobre uma conexão de área de trabalho remota e o usuário não tem permissões administrativas, a autenticação NTLM será usada. Se o usuário não tem permissões administrativas, o usuário pode receber a seguinte mensagem de erro: "a solicitação HTTP é autorizada no esquema de autenticação de cliente 'Anonymous'. O cabeçalho de autenticação recebido do servidor foi 'NTLM'."  
  
 Para corrigir esse erro:  
  
1.  No projeto de site da Web, abra o **propriedades** páginas.  
  
2.  Sobre o **Opções de inicialização** guia, desmarque o **autenticação NTLM** caixa de seleção.  
  
    > [!NOTE]
    >  Você deve desativar a autenticação NTLM somente para sites que contêm exclusivamente os serviços WCF. Segurança para os serviços WCF é gerenciada por meio da configuração no arquivo Web. config. Isso torna desnecessária a autenticação NTLM.  
  
 Para obter mais informações, consulte [Exceções de solução de problemas: System.ServiceModel.Security.MessageSecurityException](../misc/troubleshooting-exceptions-system-servicemodel-security-messagesecurityexception.md).  
  
## Nível de acesso para as Classes geradas configuração não tem efeito  
 Definindo o **nível para as classes geradas de acesso** opção o **Configurar referências de serviço** caixa de diálogo **interno** ou **amigo** talvez não funcionem sempre. Embora a opção parece estar definida na caixa de diálogo, as classes de suporte resultante serão geradas com um nível de acesso de `Public`.  
  
 Isso é uma limitação conhecida de determinados tipos, como aqueles serializado usando o <xref:System.Xml.Serialization.XmlSerializer>.  
  
## Código de serviço de depuração de erro  
 Quando você entra no código para um serviço WCF no código do cliente, você pode receber um erro relacionado à ausência de símbolos. Isso pode ocorrer quando um serviço que fazia parte de sua solução foi movido ou removido da solução.  
  
 Quando você primeiro adiciona uma referência a um serviço WCF que faz parte da solução atual, uma dependência de compilação explícita é adicionada entre o projeto de serviço e o projeto de cliente de serviço. Isso garante que o cliente acessa sempre binários de serviço atualizado, que é especialmente importante para cenários como entrar no código do cliente em código de serviço de depuração.  
  
 Se o projeto de serviço é removido da solução, essa dependência de compilação explícita é invalidada. Visual Studio não pode mais garantir que o projeto de serviço reconstituído conforme necessário.  
  
 Para corrigir esse erro, você deve recriar manualmente o projeto de serviço:  
  
1.  No menu **Ferramentas**, clique em **Opções**.  
  
2.  No **opções** caixa de diálogo caixa, expanda **projetos e soluções**, e, em seguida, selecione **geral**.  
  
3.  Verifique se o **configurações de compilação Show advanced** caixa de seleção está selecionada e, em seguida, clique em **OK**.  
  
4.  Carregar o projeto de serviço do WCF. Para obter mais informações, consulte [PONTA como: criar soluções de multiprojetos](http://msdn.microsoft.com/pt-br/02ecd6dd-0114-46fe-b335-ba9c5e3020d6).  
  
5.  No **do Configuration Manager** caixa de diálogo, defina o **configuração de solução ativa** para **Depurar**. Para obter mais informações, consulte [Como criar e editar configurações de teste](../ide/how-to-create-and-edit-configurations.md).  
  
6.  Em **Solution Explorer**, selecione o projeto de serviço do WCF.  
  
7.  No **criar** menu, clique em **recriar** para recompilar o projeto de serviço do WCF.  
  
## WCF Data Services não são exibidos no navegador  
 Quando ele tenta exibir uma representação XML dos dados em um [!INCLUDE[ss_data_service](../data-tools/includes/ss_data_service_md.md)], Internet Explorer pode interpretar incorretamente os dados como um RSS feed. Você deve certificar\-se de que a opção para exibir RSS feeds está desabilitada.  
  
 Para corrigir esse erro, desabilite feeds RSS:  
  
1.  No Internet Explorer, no **ferramentas** menu, clique em **Opções da Internet**.  
  
2.  Sobre o **conteúdo** guia o **Feeds** seção, clique em **configurações**.  
  
3.  No **configurações Feed** caixa de diálogo, desmarque o **Ativar o modo de exibição de leitura de feed** caixa de seleção e, em seguida, clique em **OK**.  
  
4.  Clique em **OK** para fechar o **Opções da Internet** caixa de diálogo.  
  
## Consulte também  
 [Serviços do Windows Communication Foundation e WCF Data Services no Visual Studio](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md)