---
title: "Escolhendo entre os VSPackages compartilhados e controle de versão | Documentos do Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SxS
- side-by-side installation
- installation [Visual Studio SDK], side-by-side
ms.assetid: e3128ac3-2e92-48e9-87ab-3b6c9d80e8c9
caps.latest.revision: 22
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
ms.openlocfilehash: e9bce2cbcd5f43b2a45c440e23f3be55ba2d00c2
ms.lasthandoff: 02/22/2017

---
# <a name="choosing-between-shared-and-versioned-vspackages"></a>Escolhendo entre os VSPackages compartilhados e controle de versão
Versões diferentes do Visual Studio podem coexistir no mesmo computador. Os VSPackages pode dar suporte a qualquer combinação de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] versões.  
  
 Você pode habilitar instalações lado a lado de VSPackages por meio de qualquer uma das duas estratégias, a estratégia compartilhada ou a estratégia de controle de versão. Ambos acomodar a presença de várias versões do [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] e associadas a versões do [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)].  
  
 A estratégia compartilhado, um VSPackage é registrado para uso em várias versões do [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. A estratégia de controle de versão, várias DLLs de VSPackage são instalados, uma para cada versão do [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] que você dá suporte.  
  
## <a name="shared-vspackages"></a>VSPackages compartilhados  
 Usar um VSPackage compartilhado é apropriado quando você usa o mesmo VSPackage em várias versões do [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Para implementar um VSPackage compartilhado, você deve executar as seguintes etapas:  
  
-   Tornar o VSPackage compatível com várias versões do [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Duas maneiras de fazer, portanto, estão disponíveis:  
  
    -   Limitar o VSPackage usando apenas os recursos da versão mais antiga do [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] que você dá suporte.  
  
    -   Programar o VSPackage para adaptar-se à versão do [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] no qual ele está sendo executado. Em seguida, se as consultas para serviços mais recentes falhar, o VSPackage pode oferecer outros serviços que têm suporte em versões mais antigas do [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
-   Registre o VSPackage adequadamente. Para obter mais informações, consulte [registro VSPackage](../extensibility/internals/vspackage-registration.md) e [gerenciado VSPackage registro](http://msdn.microsoft.com/en-us/f69e0ea3-6a92-4639-8ca9-4c9c210e58a1).  
  
-   Registre extensões de arquivo adequadamente. Para obter mais informações, consulte [registrar extensões de nome de arquivo para implantações lado a lado](../extensibility/registering-file-name-extensions-for-side-by-side-deployments.md).  
  
-   Criar um instalador que implanta o VSPackage para as versões apropriadas dos [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Para obter mais informações, consulte [instalando os VSPackages com o Windows Installer](../extensibility/internals/installing-vspackages-with-windows-installer.md) e [gerenciamento de componente](../extensibility/internals/component-management.md).  
  
-   Resolva o problema de colisões de registro. Para obter mais informações, consulte [registro VSPackage](../extensibility/internals/vspackage-registration.md).  
  
-   Certifique-se de que arquivos com controle de versão e compartilhados respeitarem permitir a instalação de segurança e remoção de várias versões de contagem de referência. Para obter mais informações, consulte [gerenciamento de componente](../extensibility/internals/component-management.md).  
  
## <a name="versioned-vspackages"></a>VSPackages com controle de versão  
 Sob a estratégia de VSPackage com controle de versão, você cria um VSPackage para cada versão do [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] que você dá suporte. Isso é apropriado quando você pretende aproveitar os serviços fornecidos por versões mais recentes do [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], porque cada VSPackage pode evoluir sem afetar as outras. No entanto, a estratégia de controle de versão de vários binários, a criação de uma base de código único ou de várias bases de código independente, pode envolver mais desenvolvimento inicial que a estratégia compartilhado. Além disso, o trabalho de configuração adicional pode ser necessário porque você deve criar um uma instalação separada para cada versão ou uma única instalação detecta as versões do [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] que estão instaladas e que suporta o VSPackage.  
  
## <a name="binary-compatibility"></a>Compatibilidade binária  
 Em geral, a compatibilidade binária permite que código nativo VSPackages desenvolvidos com versões anteriores do Visual Studio para executar em versões posteriores do Visual Studio. No entanto, há três exceções importantes:  
  
-   Se o VSPackage depende de uma versão específica do common language runtime, ele deve determinar qual versão do [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] está em execução.  
  
-   Um VSPackage pode ter uma dependência em um recurso específico do VSPackage outro ou outro produto. Consequentemente, o VSPackage pode executar apenas onde a dependência seja satisfeita.  
  
-   Um VSPackage pode ser afetado por uma correção de segurança em uma [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] service pack ou uma versão posterior do [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Nesses casos, um VSPackage desenvolvidos com uma versão anterior do [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] não pode ser executado em versões do [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] após a correção de segurança foi aplicada. No entanto, você pode recompilar o pacote com a versão mais recente e executá-lo também em versões anteriores.  
  
 Os VSPackages gerenciados deve ser criados usando uma versão do [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] e [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] que corresponde à versão de destino do [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
 Além de planejamento para a compatibilidade binária para seus binários de VSPackage, você também deve considerar a solução e formatos de arquivo de projeto. Se o VSPackage cria um novo tipo de projeto, você deve decidir se ele pode ser executado em apenas uma versão ou em várias versões do [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Para obter mais informações, consulte [atualização personalizada projetos](../misc/upgrading-custom-projects.md).  
  
## <a name="see-also"></a>Consulte também  
 [Instalando os VSPackages com o Windows Installer](../extensibility/internals/installing-vspackages-with-windows-installer.md)   
 [Gerenciamento de componente](../extensibility/internals/component-management.md)
