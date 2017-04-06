---
title: "Permissões do usuário e o Visual Studio | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Visual Studio, user permissions
- user permissions
- administrative privileges
- permissions
ms.assetid: 70485ed7-6342-41bf-8250-7a6826e21b98
caps.latest.revision: 14
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
translationtype: Human Translation
ms.sourcegitcommit: ca7c86466fa23fb21a932f26dc24e37c71cf29b4
ms.openlocfilehash: 0dc9fed1e5fc5a827e836310175d558b14cd41b4
ms.lasthandoff: 04/05/2017

---
# <a name="user-permissions-and-visual-studio"></a>Permissões de usuário e Visual Studio
Por motivos de segurança, você deve executar o Visual Studio como um usuário normal sempre que possível.  

> [!WARNING]
>  Você deve se certificar de não compilar, iniciar ou depurar qualquer solução do Visual Studio que não venha de uma pessoa de confiança ou de uma localidade confiável.  

 Você pode fazer quase tudo no IDE do Visual Studio como um usuário normal, mas precisa de permissões de administrador para concluir as seguintes tarefas:  

|Área|Tarefa|Para obter mais informações|  
|----------|----------|--------------------------|  
|Instalação|Instale o Visual Studio.|[Instalar o Visual Studio](../install/install-visual-studio.md)|  
||Instalar, atualizar ou remover conteúdo da Ajuda local.|[Instalar e gerenciar o conteúdo local](../ide/install-and-manage-local-content.md)|  
|Tipos de aplicativo|Desenvolver soluções do SharePoint.|[Requisitos para desenvolver soluções do SharePoint](/office-dev/office-dev/requirements-for-developing-sharepoint-solutions)|  
||Adquirir uma licença de desenvolvedor da [!INCLUDE[win8_appstore_long](../debugger/includes/win8_appstore_long_md.md)].|[Obter uma licença da desenvolvedor (Aplicativos da Windows Store)](http://go.microsoft.com/fwlink/?LinkID=241313)|  
|Caixa de Ferramentas|Adicionar controles COM clássicos à **Caixa de Ferramentas**.|[Usando a caixa de ferramentas](../ide/using-the-toolbox.md)|  
|Suplementos|Instalar e usar suplementos escritos usando COM clássico no IDE.|[Criando suplementos e assistentes](http://msdn.microsoft.com/Library/c5a47c21-6668-4de3-898d-afa969317e73)|  
|Compilação|Usar eventos pós-compilação que registram um componente.|[Noções básicas sobre etapas e eventos de build personalizados](/cpp/ide/understanding-custom-build-steps-and-build-events)|  
||Incluir uma etapa de registro ao criar projetos do C++.|[Noções básicas sobre etapas e eventos de build personalizados](/cpp/ide/understanding-custom-build-steps-and-build-events)|  
|Depuração|Depurar aplicativos que são executados com permissões elevadas.|[Preparação e configurações do depurador](../debugger/debugger-settings-and-preparation.md)|  
||Depurar aplicativos que são executados em uma conta de usuário diferente, como sites do ASP.NET.|[Depurando aplicativos ASP.NET e AJAX](../debugger/debugging-aspnet-and-ajax-applications.md)|  
||Depurar na zona de aplicativos de navegador XAML (XBAP).|[Host do WPF (PresentationHost.exe)](http://msdn.microsoft.com/Library/3215bfa1-722c-4ac8-a7c5-bdd02d30afbd)|  
||Usar o emulador para depurar projetos de serviço de nuvem do Microsoft Azure.|[Depurando um serviço de nuvem no Visual Studio](http://go.microsoft.com/fwlink/?LinkId=266725)|  
||Configurar um firewall para depuração remota.|[Depuração remota](../debugger/remote-debugging.md)|  
|Ferramentas de desempenho|Criar perfil de um aplicativo.|[Guia do iniciante à criação de perfil de desempenho](../profiling/beginners-guide-to-performance-profiling.md)|  
|Implantação|Implantar um aplicativo Web para o IIS (Serviços de Informações da Internet) em um computador local.|[Implantando um aplicativo Web ASP .NET em um provedor de hospedagem usando o Visual Studio ou o Visual Web Developer: Implantando no IIS como um ambiente de teste](http://go.microsoft.com/fwlink/?LinkId=266478)|

## <a name="running-visual-studio-as-an-administrator"></a>Executando o Visual Studio como um administrador  
 Você pode iniciar o Visual Studio com permissões administrativas toda vez que iniciar o IDE ou pode modificar o atalho do aplicativo para sempre ser executado com permissões administrativas. Para obter mais informações, consulte a Ajuda do Windows.  

#### <a name="to-run-visual-studio-with-administrative-permissions-on-includewin8debuggerincludeswin8mdmd-includewin81debuggerincludeswin81mdmd-includewinserver8debuggerincludeswinserver8mdmd-or-includewinblueserver2ideincludeswinblueserver2mdmd"></a>Para executar o Visual Studio com permissões administrativas no [!INCLUDE[win8](../debugger/includes/win8_md.md)], [!INCLUDE[win81](../debugger/includes/win81_md.md)], [!INCLUDE[winserver8](../debugger/includes/winserver8_md.md)] ou [!INCLUDE[winblue_server_2](../ide/includes/winblue_server_2_md.md)]  

1.  Na tela **Inicial**, digite **Visual Studio**. Você deve ver a versão (ou versões) do Visual Studio que está instalado.  

2.  Selecione a versão do Visual Studio que deseja iniciar e exiba o menu de atalho (ele aparece na parte inferior da tela). Escolha **Executar como administrador**.  

     Quando o Visual Studio for iniciado, **(Administrador)** será exibido após o nome do produto na barra de título.  

#### <a name="to-run-visual-studio-with-administrative-permissions-on-includewin7debuggerincludeswin7mdmd-or-includewinsvr08r2debuggerincludeswinsvr08r2mdmd"></a>Para executar o Visual Studio com permissões administrativas no [!INCLUDE[win7](../debugger/includes/win7_md.md)] ou [!INCLUDE[winsvr08_r2](../debugger/includes/winsvr08_r2_md.md)]  

1.  No menu **Iniciar**, escolha **Todos os Programas**.  

2.  Na pasta **Versão** do *Microsoft Visual Studio*, selecione **Versão** do *Visual Studio*, abra o menu de atalho e escolha **Executar como administrador**.  

     Quando o Visual Studio for iniciado, **(Administrador)** será exibido após o nome do produto na barra de título.  

## <a name="see-also"></a>Consulte também  
 [Portabilidade, migração e atualização de projetos do Visual Studio](../porting/port-migrate-and-upgrade-visual-studio-projects.md)   
 [Instalar o Visual Studio](../install/install-visual-studio.md)

