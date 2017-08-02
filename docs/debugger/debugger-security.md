---
title: "Seguran&#231;a do depurador | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "depuração [Visual Studio], segurança"
  - "depurador, segurança"
  - "segurança [Visual Studio], práticas recomendadas de depuração"
ms.assetid: d4fc3c43-e844-419c-8dbb-551cc2a9b09e
caps.latest.revision: 16
caps.handback.revision: 16
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Seguran&#231;a do depurador
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

A capacidade de depurar outro processo oferece poderes extremamente grandes que você não teria, especialmente quando estiver depurando remotamente. Um depurador mal\-intencionado pode impor danos extensivos no computador que está sendo depurado.  
  
 No entanto, muitos desenvolvedores não percebem que a ameaça de segurança também pode fluir na direção oposta. É possível que código mal\-intencionado no processo a ser depurado possa comprometer a segurança da máquina depuração: há um número de vulnerabilidades de segurança que devem ser protegidas.  
  
## Práticas recomendadas de segurança  
 Há uma relação de confiança implícita entre o código que você está depurando e o depurador. Se você estiver disposto a depurar algo, você também deve estar disposto a executá\-lo. O resultado final é que você deve ser capaz de confiar que você está depurando. Se você não puder confiar, então você não deve depurar ou depurá\-lo de uma máquina que você possam ser comprometidos e em um ambiente isolado.  
  
 Para reduzir a superfície de ataque potencial, a depuração deve ser desabilitada em computadores de produção. Pelo mesmo motivo, depuração nunca deve ser habilitada indefinidamente.  
  
### Segurança de depuração gerenciada  
 Aqui estão algumas recomendações gerais que se aplicam a toda depuração gerenciada.  
  
-   Tenha cuidado ao anexar ao processo de um usuário não confiável: quando você fizer isso, você assume que ele é confiável. Quando você tentar anexar a processo de um usuário não confiável, uma confirmação da caixa de diálogo de aviso de segurança será exibida perguntando se você deseja anexar ao processo. "Usuários confiáveis" incluem você, e um conjunto de usuários padrão normalmente definidos em computadores que tenham o .NET Framework instalado, como **aspnet**, **localsystem**, **networkservice**, e **localservice**. Para obter mais informações, consulte [Aviso de segurança: anexar a um processo de propriedade de um usuário não confiável pode ser perigoso. Caso as informações a seguir pareçam suspeitas ou você não tenha certeza, não anexe a esse processo](../debugger/security-warning-attaching-to-a-process-owned-by-an-untrusted-user-can-be-dangerous-if-the-following-information-looks-suspicious-or-you-are-unsure-do-not-attach-to-this-process.md).  
  
-   Tenha cuidado ao fazer o download de um projeto de fora da Internet e carregá\-la em [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Isso é muito arriscado para fazer mesmo sem depuração. Quando você fizer isso, você está assumindo que o projeto e o código que ele contém são confiáveis.  
  
 Para obter mais informações, consulte [Depurando código gerenciado](../debugger/debugging-managed-code.md).  
  
### Segurança de depuração remota  
 Depuração local é geralmente mais segura do que a depuração remota. Depuração remota aumenta a área de superfície total que pode ser analisada.  
  
 O Visual Studio Monitor de depuração remota \(msvsmon.exe\) é usado na depuração remota, e há várias recomendações de segurança para configurá\-lo. A melhor maneira de configurar o modo de autenticação é a autenticação do Windows, como o modo de autenticação não é inseguro.  
  
 ![Diálogo de erro](~/debugger/media/dbg_err_remotepermissionschanged.png "DBG\_ERR\_RemotePermissionsChanged")  
  
 Ao usar o modo de autenticação do Windows, esteja ciente que conceder uma permissão de usuário não confiável para se conectar a msvsmon é perigoso, pois o usuário recebe todas as permissões no computador...  
  
 Não depure um processo desconhecido em um computador remoto: há explorações potenciais que podem afetar o computador executando o depurador, ou que pode comprometer msvsmon.exe, o Visual Studio Monitor de depuração remota. Se for absolutamente necessário depurar um processo desconhecido, tente depurá\-lo localmente e usar um firewall para manter quaisquer ameaças em potencial localizadas.  
  
 Para obter mais informações, consulte [Depuração remota](../debugger/remote-debugging.md).  
  
### Segurança de depuração de serviços da Web  
 É mais seguro depurar localmente, mas como você provavelmente não tem [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] instalado no servidor web, a depuração local pode não ser prático. Em geral, depuração de serviços da Web é feita remotamente, exceto durante o desenvolvimento, portanto as recomendações de segurança de depuração remota também se aplicam a depuração de serviços Web. Aqui estão algumas práticas recomendadas adicionais. Para obter mais informações, consulte [Debugging XML Web Services](http://msdn.microsoft.com/pt-br/c900b137-9fbd-4f59-91b5-9c2c6ce06f00).  
  
-   Não habilite a depuração em um servidor Web que tenha sido comprometido.  
  
-   Verifique se que você sabe que o servidor Web é seguro antes de depurá\-lo. Se você não tiver certeza é seguro, não faça a depuração.  
  
-   Tome cuidado principalmente se você estiver depurando um serviço Web que é exposto na Internet.  
  
### Componentes externos  
 Lembre\-se o status de confiança de componentes externos que seu programa interage, especialmente se você não escreveu o código. Também estar ciente dos componentes que [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ou pode usar o depurador.  
  
### Símbolos e código\-fonte  
 Dois [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ferramentas que demandam preocupações com segurança são os seguintes:  
  
-   Servidor de origem, que lhe fornece versões de código\-fonte de um repositório de código fonte. Ele é útil quando você não tem a versão atual do código\-fonte do programa.[Aviso de segurança: o depurador deve executar o comando não confiável](../debugger/security-warning-debugger-must-execute-untrusted-command.md).  
  
-   Servidor de símbolo, que é usado para fornecer os símbolos necessários para depurar uma falha durante uma chamada do sistema.  
  
 Consulte [Especificar arquivos de símbolo \(.pdb\) e de origem](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).  
  
## Consulte também  
 [Configurações de depuração e preparação](../debugger/debugger-settings-and-preparation.md)   
 [Noções básicas do depurador](../debugger/debugger-basics.md)   
 [Aviso de segurança: anexar a um processo de propriedade de um usuário não confiável pode ser perigoso. Caso as informações a seguir pareçam suspeitas ou você não tenha certeza, não anexe a esse processo](../debugger/security-warning-attaching-to-a-process-owned-by-an-untrusted-user-can-be-dangerous-if-the-following-information-looks-suspicious-or-you-are-unsure-do-not-attach-to-this-process.md)   
 [Aviso de segurança: o depurador deve executar o comando não confiável](../debugger/security-warning-debugger-must-execute-untrusted-command.md)