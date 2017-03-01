---
title: Desinstalando um VSPackage com o Windows Installer | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- packages, uninstalling
- VSPackages, uninstalling
- uninstalling VSPackages
ms.assetid: c4575ac7-82da-4af8-a375-ea756a101fbf
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
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
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 30298e8c4f934261009659f43ce330050ecbfaab
ms.lasthandoff: 02/22/2017

---
# <a name="uninstalling-a-vspackage-with-windows-installer"></a>Desinstalando um VSPackage com o Windows Installer
Geralmente, o Windows Installer pode desinstalar o VSPackage apenas por "Desfazer" o que fez para instalar o VSPackage. As ações personalizadas são discutidas em [comandos que devem ser executados após a instalação](../../extensibility/internals/commands-that-must-be-run-after-installation.md) deve ser executado após a desinstalação também. Como as chamadas para devenv.exe ocorrerem antes da ação padrão InstallFinalize para instalação e desinstalação, as entradas de tabela CustomAction e InstallExecuteSequence atender a ambos os casos.  
  
> [!NOTE]
>  Executar `devenv /setup` depois de desinstalar um pacote MSI.  
  
 Como regra geral, se você adicionar ações personalizadas para um pacote do Windows Installer, você deve tratar essas ações durante a desinstalação e reversão. Se você adicionar ações personalizadas para registrar o VSPackage, por exemplo, você deve adicionar ações personalizadas para cancelar o registro, muito.  
  
> [!NOTE]
>  É possível que um usuário instala o VSPackage e, em seguida, desinstale as versões do [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] com o qual ele está integrado. Você pode ajudar a garantir que a desinstalação do VSPackage funciona nesse cenário, eliminando as ações personalizadas que executam código com dependências em [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
## <a name="handling-launch-conditions-at-uninstall-time"></a>Manipulação de condições de inicialização na desinstalação  
 A ação padrão LaunchConditions lê as linhas da tabela para mostrar o erro LaunchCondition mensagens se as condições não forem atendidas. Condições de inicialização geralmente são usados para garantir que os requisitos de sistema são atendidos, você geralmente pode ignorar condições de inicialização durante a desinstalação, adicionando a condição, `NOT Installed`, para a linha LaunchConditions da tabela LaunchCondition.  
  
 Uma alternativa é adicionar `OR Installed` para iniciar as condições que não são importantes durante a desinstalação. Isso garante que a condição será sempre true durante a desinstalação e, portanto, não exibirá a mensagem de erro de condição de inicialização.  
  
> [!NOTE]
>  `Installed`é a propriedade que do Windows Installer define quando ele detecta que o VSPackage já foi instalado no sistema.  
  
## <a name="see-also"></a>Consulte também  
 [O Windows Installer](http://msdn.microsoft.com/en-us/187d8965-c79d-4ecb-8689-10930fa8b3b5)   
 [Detecção de requisitos do sistema](../../extensibility/internals/detecting-system-requirements.md)
