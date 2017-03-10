---
title: "Exce&#231;&#245;es de solu&#231;&#227;o de problemas: System.ServiceModel.Security.MessageSecurityException | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Exceção System.ServiceModel.Security.MessageSecurityException"
  - "Exceção MessageSecurityException"
ms.assetid: 61ad69a1-ac50-49de-9a7c-8454a84ec5bd
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Exce&#231;&#245;es de solu&#231;&#227;o de problemas: System.ServiceModel.Security.MessageSecurityException
Um <xref:System.ServiceModel.Security.MessageSecurityException> exceção é lançada quando [!INCLUDE[vsindigo](../data-tools/includes/vsindigo_md.md)] determina que uma mensagem não está protegida corretamente ou foi violada. O erro ocorre com mais freqüência quando as seguintes condições forem verdadeiras:  
  
-   Você pode usar uma referência de serviço WCF em uma conexão remota, como a conexão de área de trabalho remota ou serviços de Terminal para se comunicar com um serviço WCF \(. svc\) em um projeto de aplicativo Web ou site da Web.  
  
-   Você não tem permissões de administrador no site remoto.  
  
-   Solicitações para localhost no site remoto estão sendo manipuladas pelo [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] Development Server.  
  
## Dicas associadas  
 **Resolva problemas de autenticação NTLM ao usar o ASP.Net Development Server.**  
 O [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] Development Server normalmente tem segurança de desafio\/resposta do Windows NT \(NTLM\) desativada, que permite o acesso anônimo. Por padrão, quando você executa uma sessão de serviços de Terminal ou usa uma conexão remota, a segurança NTLM é habilitada. Quando a autenticação NTLM é habilitada, todas as solicitações do host local são validadas em relação às credenciais do usuário ou processo que iniciou a [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] Development Server. Isso reduz ameaças de segurança. No entanto, WCF também realiza sua própria autenticação e não permite que uma conta de não\-administrador consuma serviços WCF.  
  
 Se um usuário remoto pode executar o site usando o [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] Development Server e também trabalhar com um serviço Web ou um serviço WCF, você pode criar uma associação de serviço personalizada ou desativar a segurança NTLM.  
  
> [!IMPORTANT]
>  Desativando a segurança NTLM não é recomendado e poderia constituir uma ameaça de segurança.  
  
 Se você criar uma associação de serviço personalizado, você ainda está protegido pela autenticação NTLM.  
  
 Use as seguintes etapas para criar uma associação de serviço personalizado para o serviço WCF.  
  
#### Para criar um serviço personalizado de associação para o serviço WCF hospedado dentro do ASP.NET Development Server  
  
1.  Abra o arquivo Web. config para o serviço WCF que está gerando a exceção.  
  
2.  Insira as informações a seguir no arquivo Web. config.  
  
    ```  
    <bindings> <customBinding> <binding name="Service1Binding"> <transactionFlow /> <textMessageEncoding /> <httpTransport authenticationScheme="Ntlm" /> </binding> </customBinding> </bindings>  
    ```  
  
3.  Salve e feche o arquivo Web. config.  
  
4.  No código para o serviço Web ou WCF, altere o valor de ponto de extremidade para o seguinte:  
  
    ```  
    <endpoint address="" binding="customBinding" bindingConfiguration="Service1Binding" contract="IService1" />  
    ```  
  
     Isso garante que o serviço usa a ligação personalizada.  
  
5.  Adicione uma referência para o serviço no aplicativo da Web que acessa o serviço. \(No **Add Service Reference** caixa de diálogo caixa, adicione uma referência ao serviço, como você fez com o serviço original que estava gerando a exceção.\)  
  
 Você pode seguir estas etapas para desabilitar a segurança NTLM quando você estiver trabalhando com uma referência de serviço do WCF.  
  
> [!IMPORTANT]
>  Desativando a segurança NTLM não é recomendado e poderia constituir uma ameaça de segurança.  
  
#### Para desativar a segurança NTLM  
  
1.  Em **Solution Explorer**, clique no nome do site da Web e, em seguida, clique em **páginas de propriedade**.  
  
2.  Selecione **Opções de inicialização**, e desmarque o **autenticação NTLM** caixa de seleção.  
  
3.  Clique em **OK**.  
  
## Consulte também  
 <xref:System.ServiceModel.Security.MessageSecurityException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)