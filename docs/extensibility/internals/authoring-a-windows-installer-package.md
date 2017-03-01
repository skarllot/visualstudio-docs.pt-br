---
title: "Criação de um pacote do Windows Installer | Documentos do Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- .msi files, VSPackages
- msi files, VSPackages
ms.assetid: 0ce7c21d-0d3f-47fe-a0bb-eed506e32609
caps.latest.revision: 20
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
ms.openlocfilehash: 814dd1633d7cc8a7f76327b4d57e972d4fcd44d1
ms.lasthandoff: 02/22/2017

---
# <a name="authoring-a-windows-installer-package"></a>Criação de um pacote do Windows Installer
Unidades de dados de modelo do Windows Installer. Em vez de escrever um script de procedimento para copiar arquivos e gravar as entradas do registro, por exemplo, você cria linhas e colunas nas tabelas de banco de dados que contêm dados de arquivos e do registro.  
  
## <a name="database-entries"></a>Entradas de banco de dados  
 Para instalar um VSPackage, um pacote do Windows Installer deve conter entradas de banco de dados para executar as seguintes tarefas:  
  
-   Pesquise o sistema para localizar as versões do [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] o VSPackage suporta (usando tabelas do Windows Installer que incluem AppSearch, CompLocator, RegLocator, DrLocator e assinatura).  
  
-   Cancelar a instalação se nenhuma versão com suporte do [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] está instalado ou se outro requisito de sistema do VSPackage não for atendido (usando a tabela de LaunchCondition).  
  
-   Instale o VSPackage e arquivos dependentes (usando o diretório, componente e tabelas de arquivos).  
  
-   Adicione informações apropriadas para o VSPackage no registro (usando a tabela de registro).  
  
-   Integrar o VSPackage no [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] chamando **devenv.exe /setup** (usando a tabela CustomAction).  
  
 Para obter mais informações, consulte [do Windows Installer](http://msdn.microsoft.com/library/cc185688\(VS.85\).aspx).  
  
## <a name="setup-tools"></a>Ferramentas de instalação  
 Uma variedade de ferramentas de instalação de terceiros fornecem um ambiente de desenvolvimento de pacotes do Windows Installer. Duas ferramentas gratuitas são os seguintes:  
  
-   InstallShield Limited Edition  
  
     Você pode obter uma versão limitada do InstallShield por meio do Visual Studio **novo projeto** caixa de diálogo. Expanda **Other Project Types** e, em seguida, selecione **Setup and Deployment**. Selecione o modelo do InstallShield.  
  
-   Conjunto de Ferramentas XML do Windows Installer  
  
     O conjunto de ferramentas cria pacotes do Windows Installer XML dos arquivos de origem. O conjunto de ferramentas é um projeto de código-fonte aberto da Microsoft. Você pode baixar o código-fonte e os executáveis de [http://sourceforge.net/projects/wix](http://sourceforge.net/projects/wix).  
  
 Para os produtos comerciais que se integra [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] usando o [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)], consulte [http://visualstudiogallery.com](http://visualstudiogallery.com/).  
  
## <a name="see-also"></a>Consulte também  
 [Instalando os VSPackages com o Windows Installer](../../extensibility/internals/installing-vspackages-with-windows-installer.md)
