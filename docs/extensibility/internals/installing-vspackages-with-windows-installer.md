---
title: Instalando os VSPackages com o Windows Installer | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- installation [Visual Studio SDK], with Windows Installer
- VSPackages, deploying
ms.assetid: 41d2c72c-0a97-4fcd-b3aa-33a8d3aa962a
caps.latest.revision: 30
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
ms.openlocfilehash: 1e3c04dbea804d9fcd824e9c88a53991a2ef3845
ms.lasthandoff: 02/22/2017

---
# <a name="installing-vspackages-with-windows-installer"></a>Instalando os VSPackages com o Windows Installer
Integrando o VSPackage em [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] requer mais do que simplesmente copiando arquivos para o computador do usuário. Instalador do VSPackage deve instalar o VSPackage e seus arquivos dependentes e registrar e integrá-las em [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. O VSPackage pode tirar proveito dos recursos de integração, como exibir um ícone no [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] sobre caixa de diálogo e de tela de abertura.  
  
 Arquivos do Microsoft Windows Installer são a maneira recomendada para distribuir seu VSPackages. Fácil de usar o Windows Installer pacotes podem ser executados em qualquer sistema operacional do Windows com suporte pelo [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Para obter mais informações, consulte [do Windows Installer](http://msdn.microsoft.com/en-us/121be21b-b916-43e2-8f10-8b080516d2a0).  
  
## <a name="in-this-section"></a>Nesta seção  
 [Noções básicas do Windows Installer](../../extensibility/internals/windows-installer-basics.md)  
 Fornece uma visão geral do Windows Installer.  
  
 [Cenários de instalação de VSPackage](../../extensibility/internals/vspackage-setup-scenarios.md)  
 Discute diferentes maneiras que você pode oferecer suporte a instalações lado a lado do seu os VSPackages e [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
 [Criação de um pacote do Windows Installer](../../extensibility/internals/authoring-a-windows-installer-package.md)  
 Fornece uma visão geral das etapas comuns instaladores seguem para instalar corretamente e integrar os VSPackages em [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
 [Detecção de requisitos do sistema](../../extensibility/internals/detecting-system-requirements.md)  
 Descreve como detectar um instalador [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] e seus componentes e cancelar a instalação se VSPackage requisitos não forem atendidos.  
  
 [Gerenciamento de componente](../../extensibility/internals/component-management.md)  
 Descreve como desenvolver um instalador que manterá a integridade de versões anteriores do produto.  
  
 [Escolha o diretório de instalação para um VSPackage](../../extensibility/internals/choosing-the-installation-directory-for-a-vspackage.md)  
 Resume as opções para localizar os VSPackages.  
  
 [Registro de VSPackage](../../extensibility/internals/vspackage-registration.md)  
 Discute como os VSPackages são registrados no momento da instalação e por que o auto-registro é uma boa ideia.  
  
 [Tipos de projeto de implantação](../../extensibility/internals/deploying-project-types.md)  
 Discute como usar o novo agregador de tipo de projeto para tipos de projeto de código gerenciado.  
  
 [Como: gerar informações de registro para um instalador](../../extensibility/internals/how-to-generate-registry-information-for-an-installer.md)  
 Explica como usar RegPkg.exe para gerar um manifesto de registro para um VSPackage gerenciado.  
  
 [Comandos que devem ser executados após a instalação](../../extensibility/internals/commands-that-must-be-run-after-installation.md)  
 Explica como executar comandos de pós-instalação para integrar os VSPackages em [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
 [Desinstalando um VSPackage com o Windows Installer](../../extensibility/internals/uninstalling-a-vspackage-with-windows-installer.md)  
 Descreve as etapas que o instalador deve executar quando os usuários desinstalarem o VSPackage.  
  
## <a name="related-sections"></a>Seções relacionadas  
 [Instalando VSPackages](../../misc/installing-vspackages.md)  
 Discute como criar e instalar os VSPackages e como oferecer suporte a usuários que estão executando várias versões do [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ao mesmo tempo.
