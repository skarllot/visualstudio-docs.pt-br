---
title: "Conceitos básicos de integração de controle de origem | Documentos do Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Source Control Integration, essentials
- Source Control Integration,overview
- essentials, Source Control Integration
ms.assetid: 442057cb-fd54-4283-96f8-2f6dc8bf2de7
caps.latest.revision: 9
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
ms.openlocfilehash: 7f23fee0acd6dfe6bf53fa5d0c2ff6b87ee55bd2
ms.lasthandoff: 02/22/2017

---
# <a name="source-control-integration-essentials"></a>Conceitos básicos de integração de controle de origem
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]oferece suporte a dois tipos de integração de controle do código-fonte: um plug-in de controle de origem que fornece a funcionalidade básica e é criada usando a API de plug-in de controle de origem (anteriormente conhecido como API MSSCCI) e uma solução de integração de controle de origem baseado em VSPackage que fornece a funcionalidade mais robusta.  
  
## <a name="source-control-plug-in"></a>Plug-in de Controle do Código-fonte  
 Um plug-in de controle de origem é gravada como uma DLL que implementa a API de plug-in de controle de origem. Funcionalidade de integração do controle de registro e código-fonte é fornecida por meio da API. Essa abordagem é mais fácil de implementar do que um controle da fonte VSPackage e usa o [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] interface de usuário (UI) para a maioria das operações de controle de origem.  
  
 Para implementar um plug-in usando a API de plug-in de controle de origem de controle de origem, siga estas etapas:  
  
1.  Criar uma DLL que implementa as funções especificadas na [Plug-ins de controle de origem](../../extensibility/source-control-plug-ins.md).  
  
2.  Registrar a DLL, tornando as entradas de registro apropriadas, conforme descrito em [como: instalar um plug-in de controle de origem](../../extensibility/internals/how-to-install-a-source-control-plug-in.md).  
  
3.  Criar um interface do usuário do auxiliar e exibi-la quando solicitado pelo pacote de adaptador de controle de origem (o [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] componente que manipula a funcionalidade de controle do código-fonte por meio de plug-ins de controle de origem).  
  
 Para obter mais informações, consulte [criar um plug-in de controle de origem](../../extensibility/internals/creating-a-source-control-plug-in.md).  
  
## <a name="source-control-vspackage"></a>VSPackage de controle de origem  
 Um controle de origem VSPackage implementação permite que você desenvolva uma substituição personalizada para o [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] da interface do usuário do controle de origem. Essa abordagem fornece controle total sobre a integração de controle do código-fonte, mas exige que você forneça os elementos de interface do usuário e implementar as interfaces de controle de origem que outra forma seriam fornecidas sob a abordagem de plug-in.  
  
 Para implementar um controle de origem VSPackage, faça o seguinte:  
  
1.  Criar e registrar o seu próprio controle de origem VSPackage, conforme descrito em [registro e seleção](../../extensibility/internals/registration-and-selection-source-control-vspackage.md).  
  
2.  Substitua o controle da fonte padrão da interface do usuário com a interface do usuário personalizada. Consulte [Interface de usuário personalizada](../../extensibility/internals/custom-user-interface-source-control-vspackage.md).  
  
3.  Especificar glifos para ser usado e manipular **Solution Explorer** eventos de glifo. Consulte [controle de glifo](../../extensibility/internals/glyph-control-source-control-vspackage.md).  
  
4.  Tratar eventos de consulta editar e salvar consulta, conforme mostrado na [consulta Editar consulta salvar](../../extensibility/internals/query-edit-query-save-source-control-vspackage.md).  
  
 Para obter mais informações, consulte [criando um VSPackage de controle do código-fonte](../../extensibility/internals/creating-a-source-control-vspackage.md).  
  
## <a name="see-also"></a>Consulte também  
 [Visão geral](../../extensibility/internals/source-control-integration-overview.md)   
 [Criando um controle da fonte de plug-in](../../extensibility/internals/creating-a-source-control-plug-in.md)   
 [Criando um VSPackage de controle de origem](../../extensibility/internals/creating-a-source-control-vspackage.md)
