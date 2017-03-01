---
title: Especificando o local do arquivo de VSPackage ao Shell do VS | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- managed VSPackages, file location
- VSPackages, managed package file location
ms.assetid: beb8607a-4183-4ed2-9ac8-7527f11513b1
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
ms.openlocfilehash: 5155b9e277f071b522887236ab7399654f578a17
ms.lasthandoff: 02/22/2017

---
# <a name="specifying-vspackage-file-location-to-the-vs-shell"></a>Especificando o local do arquivo de VSPackage ao Shell do VS
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]deve ser capaz de localizar o assembly DLL para carregar o VSPackage. Você pode localizá-lo de várias maneiras, conforme descrito na tabela a seguir.  
  
|Método|Descrição|  
|------------|-----------------|  
|Use a chave de registro de base de código.|A chave de base de código pode ser usada para direcionar o [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] para carregar o assembly de VSPackage qualquer caminho de arquivo totalmente qualificado. O valor da chave deve ser o caminho para a DLL. Essa é a melhor maneira de ter [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] carregar seu assembly de pacote. Essa técnica é às vezes conhecida como a "técnica de diretório de instalação de base de código/privada". Durante o registro o valor da Base de código é passado para as classes de atributo do registro por meio de uma instância das <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute.RegistrationContext>tipo.</xref:Microsoft.VisualStudio.Shell.RegistrationAttribute.RegistrationContext>|  
|Coloque a DLL para o **PrivateAssemblies** directory.|Coloque o assembly no **PrivateAssemblies** subdiretório o [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] directory. Assemblies localizados na **PrivateAssemblies** são detectadas automaticamente, mas não são visíveis no **adicionar referências** caixa de diálogo. A diferença entre **PrivateAssemblies** e **PublicAssemblies** é que os assemblies em **PublicAssemblies** são enumerados no **adicionar referências** caixa de diálogo. Se você optou por não usar a técnica de "CodeBase/privada installation directory", você deve instalar para o **PrivateAssemblies** directory.|  
|Use um assembly de nome forte e a chave de registro de Assembly.|A chave do Assembly pode ser usada para direcionar explicitamente [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] para carregar um forte denominado assembly VSPackage. O valor da chave deve ser o nome forte do assembly.|  
|Coloque a DLL para o **PublicAssemblies** directory.|Por fim, o assembly também pode ser colocado no **PublicAssemblies** subdiretório. Assemblies localizados na **PublicAssemblies** são detectados automaticamente e também aparecerão no **adicionar referências** da caixa de diálogo [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].<br /><br /> Assemblies de VSPackage só devem ser colocados no **PublicAssemblies** diretório se eles contêm gerenciado componentes que devem ser reutilizado por outros desenvolvedores de VSPackage. A maioria dos assemblies não atende a esse critério.|  
  
> [!NOTE]
>  Use assemblies de nome forte, assinados para todos os assemblies dependentes. Esses assemblies também devem ser instalados em seu próprio diretório ou cache de assembly global (GAC). Isso protege contra conflitos com assemblies que têm o mesmo nome de arquivo de base, conhecido como associação de nome fraco.
