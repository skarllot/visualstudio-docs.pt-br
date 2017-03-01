---
title: "Registrando extensões de nome de arquivo para implantações lado a lado | Documentos do Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- file extensions, registering for side-by-side
ms.assetid: 9ab046a2-147d-4167-aa14-7d661b1eaaa5
caps.latest.revision: 13
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
ms.openlocfilehash: 216fb4cc449e8a67178f587b0c199864d267ccf4
ms.lasthandoff: 02/22/2017

---
# <a name="registering-file-name-extensions-for-side-by-side-deployments"></a>Registrando extensões de nome de arquivo para implantações lado a lado
Os VSPackages implantados em um ambiente lado a lado, você deve registrar as extensões de nome de arquivo para associar os arquivos com a versão correta do [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. A menos que você use uma extensão de nome de arquivo específicos da versão, o registro permite que os usuários abrir seu projeto e arquivos de item na versão apropriada do projeto [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
## <a name="in-this-section"></a>Nesta seção  
 [Sobre as extensões de nome de arquivo](../extensibility/about-file-name-extensions.md)  
 Discute como as extensões de nome de arquivo são registradas.  
  
 [Especificando identificadores de arquivo para extensões de nome de arquivo](../extensibility/specifying-file-handlers-for-file-name-extensions.md)  
 Fornece informações sobre como registrar os aplicativos que podem abrir, editar e assim por diante, uma extensão de nome de arquivo específico.  
  
 [Registrando verbos para extensões de nome de arquivo](../extensibility/registering-verbs-for-file-name-extensions.md)  
 Descreve como registrar verbos.  
  
 [Gerenciar associações de arquivo lado a lado](../extensibility/managing-side-by-side-file-associations.md)  
 Discute como lidar com instalações lado a lado em que uma versão específica do [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] deve ser chamado para abrir um arquivo.  
  
## <a name="related-sections"></a>Seções relacionadas  
 [Suporte a várias versões do Visual Studio](../extensibility/supporting-multiple-versions-of-visual-studio.md)  
 Descreve os problemas relacionados a várias versões de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] e o VSPackage durante o desenvolvimento e implantação para os usuários finais.
