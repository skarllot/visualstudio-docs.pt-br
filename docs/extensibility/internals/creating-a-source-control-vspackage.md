---
title: "Criando um VSPackage de controle do código-fonte | Documentos do Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- source control [Visual Studio SDK], creating source control packages
- source control packages
ms.assetid: cca0a9ed-48ff-409f-8036-ed8db0f7533e
caps.latest.revision: 23
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
ms.openlocfilehash: f58ce1fb01db2f466bba91151aaab6f694635e55
ms.lasthandoff: 02/22/2017

---
# <a name="creating-a-source-control-vspackage"></a>Criando um VSPackage de controle de origem
Esta documentação inclui links para a visão geral da arquitetura de um pacote de controle de origem integrado com [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], a API que é definida por interfaces a serem implementadas e os serviços a serem consumidos e um exemplo que ilustra uma implementação de pacote de controle de origem simples.  
  
 Com um controle de fonte VSPackage, você pode criar um caminho profunda integração de controle de origem para integrar [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Ele permite que o pacote ignorar o controle da fonte padrão da interface do usuário hospedada por [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], responder a solicitações de controle de origem do sistema de projeto e interagir com [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] componentes como **Solution Explorer**. O [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] capacita [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] parceiros com um mecanismo para criar um VSPackage que pode se integrar com [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] usando um modelo de serviço.  
  
## <a name="in-this-section"></a>Nesta seção  
 [Introdução](../../extensibility/internals/getting-started-with-source-control-vspackages.md)  
 Descreve o pacote de controle de origem, que é uma alternativa mais avançada para o plug-in para implementar recursos de controle do código-fonte no controle da fonte [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
 [Arquitetura](../../extensibility/internals/source-control-vspackage-architecture.md)  
 Apresenta um diagrama e explica os componentes de um pacote de controle de origem.  
  
 [Recursos](../../extensibility/internals/source-control-vspackage-features.md)  
 Descreve os vários recursos de um pacote de controle de origem.  
  
 [Elementos de design](../../extensibility/internals/source-control-vspackage-design-elements.md)  
 Descreve a estrutura do VSPackage que um pacote de controle de origem deve implementar para integração profunda.  
  
## <a name="related-sections"></a>Seções relacionadas  
 [Criando um controle da fonte de plug-in](../../extensibility/internals/creating-a-source-control-plug-in.md)  
 Discute como criar um plug-in de controle de origem que fornece funcionalidade de controle do código-fonte no [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] interface de usuário de controle de origem (UI).  
  
 [Controle de origem](../../extensibility/internals/source-control.md)  
 Discute as opções para implementar o controle de origem como um recurso integrado de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].
