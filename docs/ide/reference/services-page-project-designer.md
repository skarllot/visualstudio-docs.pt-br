---
title: "Página Serviços, Designer de Projeto | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vb.ProjectPropertiesServices
helpviewer_keywords:
- Services page in Project Designer
- Project Designer, Services page
ms.assetid: 6dd9e0fa-acba-4d7d-b081-705b0fc86ff5
caps.latest.revision: 26
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Human Translation
ms.sourcegitcommit: 3d32d11a430227800cb3ed53831a9565eb6adeb3
ms.openlocfilehash: 35ef3c227b1a5f8af2fd3daa3cb00b51b69f5beb
ms.contentlocale: pt-br
ms.lasthandoff: 05/30/2017

---
# <a name="services-page-project-designer"></a>Página Serviços, Designer de Projeto
Os serviços de aplicativo cliente fornecem acesso simplificado ao logon, às funções e aos serviços de perfil do [!INCLUDE[ajax_current_short](../../ide/reference/includes/ajax_current_short_md.md)] por meio dos aplicativos Windows Forms e WPF (Windows Presentation Foundation). Você pode usar a página **Serviços** do **Designer de Projeto** para habilitar e configurar serviços de aplicativo cliente para seu projeto.  
  
 Com os serviços de aplicativo cliente, você pode usar um servidor centralizado para autenticar usuários, determinar a função ou as funções atribuídas a cada usuário e armazenar configurações de aplicativo por usuário que você pode compartilhar pela rede. Para obter mais informações, consulte [Serviços de aplicativo cliente](/dotnet/framework/common-client-technologies/client-application-services).  
  
 Para acessar a página **Serviços**, selecione um nó do projeto no **Gerenciador de Soluções** e, em seguida, clique em **Propriedades** no menu **Projeto**. Quando o **Designer de Projeto** for exibido, clique na guia **Serviços**.  
  
> [!NOTE]
>  Os serviços do aplicativo cliente exigem a versão completa do .NET Framework e não há suporte para o .NET Framework Client Profile. Se a caixa de seleção **Habilitar serviços do aplicativo cliente** estiver desabilitada, verifique se a **Estrutura de destino** está definida como .NET Framework 3.5 ou posterior. Para exibir a configuração da **Estrutura de destino** em C#, abra o Designer de Projeto e clique na página **Aplicativo**. Para exibir a configuração **Estrutura de destino** no Visual Basic, abra o Designer de Projeto, clique na página **Compilar** e, em seguida, clique em **Opções Avançadas de Compilação**.  
  
## <a name="task-list"></a>Lista de Tarefas  
 [Como configurar serviços de aplicativo cliente](/dotnet/framework/common-client-technologies/how-to-configure-client-application-services)  
  
## <a name="uielement-list"></a>Lista UIElement  
 **Configuração**  
 Esse controle não é editável nesta página. Para obter uma descrição desse controle, consulte [Página de compilação, Designer de Projeto (Visual Basic)](../../ide/reference/compile-page-project-designer-visual-basic.md) ou [Página de Build, Designer de Projeto (C#)](../../ide/reference/build-page-project-designer-csharp.md).  
  
 **Plataforma**  
 Esse controle não é editável nesta página. Para obter uma descrição desse controle, consulte [Página de compilação, Designer de Projeto (Visual Basic)](../../ide/reference/compile-page-project-designer-visual-basic.md) ou [Página de Build, Designer de Projeto (C#)](../../ide/reference/build-page-project-designer-csharp.md).  
  
 **Habilitar serviços do aplicativo cliente**  
 Selecione para habilitar serviços do aplicativo cliente. Você deve especificar locais de serviço na página **Serviços** para usar serviços de aplicativo cliente.  
  
 **Usar a autenticação do Windows**  
 Indica que o provedor de autenticação usará a autenticação baseada em Windows, ou seja, a identidade fornecida pelo sistema operacional Windows.  
  
 **Usar autenticação de Formulários**  
 Indica que o provedor de autenticação usará a autenticação de formulários. Isso significa que seu aplicativo deve fornecer uma interface do usuário para logon. Para obter mais informações, consulte [Como implementar o logon do usuário com os serviços de aplicativo cliente](/dotnet/framework/common-client-technologies/how-to-implement-user-login-with-client-application-services).  
  
 **Local do serviço de autenticação**  
 Utilizado somente com autenticação de formulários. Especifica o local do serviço de autenticação.  
  
 **Opcional: provedor de credenciais**  
 Utilizado somente com autenticação de formulários. Indica a implementação <xref:System.Web.ClientServices.Providers.IClientFormsAuthenticationCredentialsProvider> que o serviço de autenticação usará para exibir uma caixa de diálogo de logon quando o aplicativo chamar o método `static`<xref:System.Web.Security.Membership.ValidateUser%2A?displayProperty=fullName> e passar cadeias de caracteres vazias ou `null` para os parâmetros. Se deixar essa caixa em branco, você deverá passar um nome de usuário válido e uma senha para o método <xref:System.Web.Security.Membership.ValidateUser%2A?displayProperty=fullName>. Você deve especificar o provedor de credenciais como um nome de tipo qualificado pelo assembly. Para obter mais informações, consulte <xref:System.Type.AssemblyQualifiedName%2A?displayProperty=fullName> e [Assembly Names](/dotnet/framework/app-domains/assembly-names) (Nomes de assembly). Em sua forma mais simples, um nome de tipo qualificado pelo assembly é semelhante ao exemplo a seguir: `MyNamespace.MyLoginClass, MyAssembly`  
  
 **Local do serviço de funções**  
 Especifica o local do serviço de funções.  
  
 **Local do serviço de configurações da Web**  
 Especifica o local do serviço de perfil (configurações da Web).  
  
 **Avançado**  
 Abre [Configurações Avançadas para a Caixa de Diálogo Serviços](../../ide/reference/advanced-settings-for-services-dialog-box.md), que você pode usar para substituir o comportamento padrão. Por exemplo, você pode usar essa caixa de diálogo para especificar um banco de dados para armazenamento offline, em vez de usar o sistema de arquivos local. Para obter mais informações, consulte [Configurações Avançadas para a Caixa de Diálogo Serviços](../../ide/reference/advanced-settings-for-services-dialog-box.md).  
  
## <a name="see-also"></a>Consulte também  
 [Serviços de aplicativo cliente](/dotnet/framework/common-client-technologies/client-application-services)   
 [Configurações Avançadas para a Caixa de Diálogo Serviços](../../ide/reference/advanced-settings-for-services-dialog-box.md)   
 [Como configurar serviços de aplicativo cliente](/dotnet/framework/common-client-technologies/how-to-configure-client-application-services)   
 [Página de Compilação, Designer de Projeto (Visual Basic)](../../ide/reference/compile-page-project-designer-visual-basic.md)   
 [Página de Build, Designer de Projeto (C#)](../../ide/reference/build-page-project-designer-csharp.md)   

