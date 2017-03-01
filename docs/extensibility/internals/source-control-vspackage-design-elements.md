---
title: Elementos de Design de VSPackage de controle de origem | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- source control packages, design elements
ms.assetid: edd3f2ff-ca32-4465-8ace-4330493b67bb
caps.latest.revision: 15
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
ms.openlocfilehash: a4f99a6a62e0011bdcf1e61e38a96c0418d27aed
ms.lasthandoff: 02/22/2017

---
# <a name="source-control-vspackage-design-elements"></a>Elementos de Design de VSPackage de controle de origem
Os tópicos nesta seção descrevem a estrutura de controle da fonte de VSPackage deve implementar para integração profunda. Também lista as interfaces e os serviços que a fonte de controle VSPackage podem implementar e as interfaces e os serviços de controle de origem VSPackage pode usar outros [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] componentes para oferecer suporte a sua fonte de modelo e a funcionalidade de controle.  
  
## <a name="in-this-section"></a>Nesta seção  
 [Estrutura de VSPackage](../../extensibility/internals/vspackage-structure-source-control-vspackage.md)  
 Define a estrutura de controle da fonte de VSPackage.  
  
 [Interfaces e serviços relacionados](../../extensibility/internals/related-services-and-interfaces-source-control-vspackage.md)  
 Lista de serviços e interfaces relacionadas a pacotes de controle de origem.  
  
 [Serviços fornecidos](../../extensibility/internals/services-provided-source-control-vspackage.md)  
 Descreve o serviço de controle de origem fornecido pelo controle da fonte de VSPackage.  
  
## <a name="related-sections"></a>Seções relacionadas  
 [Criando um VSPackage de controle de origem](../../extensibility/internals/creating-a-source-control-vspackage.md)  
 Discute como criar um controle de origem VSPackage que não apenas fornece a funcionalidade de controle do código-fonte, mas pode ser usado para personalizar o [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] da interface do usuário do controle de origem.
