---
title: "Escolha o diretório de instalação para um VSPackage | Documentos do Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- VSPackages, installation directory
ms.assetid: 01fbbb5b-f747-446c-afe0-2a081626a945
caps.latest.revision: 17
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
ms.openlocfilehash: 677cb507474bf00050289cff185454578c0fcfdb
ms.lasthandoff: 02/22/2017

---
# <a name="choosing-the-installation-directory-for-a-vspackage"></a>Escolha o diretório de instalação para um VSPackage
Um VSPackage e seus arquivos de suporte devem estar no sistema de arquivos do usuário. O local depende se o VSPackage é gerenciado ou não, o esquema de versão lado a lado e a opção de usuário.  
  
## <a name="unmanaged-vspackages"></a>VSPackages não gerenciados  
 Um VSPackage não gerenciado é um servidor COM que pode ser instalado em qualquer local. Suas informações de registro deve reflete com precisão o seu local. Sua interface de usuário (UI) de instalador deve fornecer um local padrão como uma subpasta da propriedade ProgramFilesFolder Windows Installer. Por exemplo:  
  
 [ProgramFilesFolder] MyCompany\MyVSPackageProduct\V1.0\  
  
 O usuário deve ser permitido para alterar o diretório padrão para acomodar os usuários que mantêm uma partição de inicialização pequeno e preferir instalar aplicativos e ferramentas em outro volume.  
  
 Se o esquema de lado a lado usa um VSPackage com controle de versão, você pode usar subdiretórios para armazenar versões diferentes. Por exemplo:  
  
 [ProgramFilesFolder] MyCompany\MyVSPackageProduct\V1.0\2002\  
  
 [ProgramFilesFolder] MyCompany\MyVSPackageProduct\V1.0\2003\  
  
 [ProgramFilesFolder] MyCompany\MyVSPackageProduct\V1.0\2005\  
  
## <a name="managed-vspackages"></a>VSPackages gerenciados  
 VSPackages gerenciados também podem ser instalados em qualquer local. No entanto, você deve considerar sempre instalá-los para o cache de assembly global (GAC) para reduzir os tempos de carregamento de assembly. Como sempre, VSPackages gerenciados são assemblies de nomes fortes, instalá-los no GAC significa que a verificação de assinatura de nome forte leva apenas no momento da instalação. Assemblies com nomes fortes instalados em outro lugar no sistema de arquivos devem ter suas assinaturas verificadas sempre que eles são carregados. Quando você instala os VSPackages gerenciados no GAC, use a ferramenta de regpkg **/assembly** switch para gravar entradas apontando para o nome forte do assembly.  
  
 Se você instalar VSPackages gerenciados em um local diferente no GAC, seguir o conselho anterior fornecido para VSPackages não gerenciados para a escolha de hierarquias de diretório. Use a ferramenta de regpkg **/codebase** switch para gravar entradas apontando para o caminho do assembly VSPackage.  
  
 Para obter mais informações, consulte [Registrando e Cancelando o registro VSPackages](../../extensibility/registering-and-unregistering-vspackages.md).  
  
## <a name="satellite-dlls"></a>DLLs satélite  
 Por convenção, VSPackage DLLs satélite — que contêm recursos para uma localidade específica — estão localizados em subpastas da pasta de VSPackage. Os subdiretórios correspondem aos valores de ID (LCID) de localidade.  
  
 [Gerenciando os VSPackages](../../extensibility/managing-vspackages.md) indica que as entradas do registro controlam onde [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] realmente procura um VSPackage satélite DLL. No entanto, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] tenta carregar uma DLL satélite em um subdiretório nomeado para um valor LCID, na seguinte ordem:  
  
1.  LCID (VS LCID por exemplo \1033 para inglês) padrão  
  
2.  LCID padrão com a subidioma padrão.  
  
3.  LCID padrão do sistema.  
  
4.  Padrão do sistema LCID com subidioma do padrão.  
  
5.  DOS EUA Inglês (. \1033 ou. \0x409).  
  
 Se sua DLL VSPackage inclui recursos e os pontos de entrada de registro SatelliteDll\DllName, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] tenta carregá-los na ordem acima.  
  
## <a name="see-also"></a>Consulte também  
 [Escolhendo entre os VSPackages compartilhados e controle de versão](../../extensibility/choosing-between-shared-and-versioned-vspackages.md)   
 [Gerenciando os VSPackages](../../extensibility/managing-vspackages.md)   
 [Registro do pacote gerenciado](http://msdn.microsoft.com/en-us/f69e0ea3-6a92-4639-8ca9-4c9c210e58a1)
