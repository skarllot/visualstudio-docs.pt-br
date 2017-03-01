---
title: "Determinar se deve implementar um VSPackage de controle do código-fonte | Documentos do Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- source control packages, about source control packages
ms.assetid: 60b3326e-e7e2-4729-95fc-b682e7ad5c99
caps.latest.revision: 24
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
ms.openlocfilehash: 9d3e2b925f7e914af7a0a4d57d931419b7a8699f
ms.lasthandoff: 02/22/2017

---
# <a name="determining-whether-to-implement-a-source-control-vspackage"></a>Determinar se deve implementar um VSPackage de controle de origem
Esta seção aborda as opções de plug-ins de controle de origem e de controle de origem VSPackages para estender o controle da fonte de soluções e fornecerá diretrizes amplas sobre como escolher um caminho de integração adequada.  
  
## <a name="small-source-control-solution-with-limited-resources"></a>Solução de controle de fonte pequeno com recursos limitados  
 Se você tiver recursos limitados e não pode ser sobrecarregados com a sobrecarga de escrever um pacote de controle de origem, você pode criar plug-ins baseados na API de plug-in de controle de origem. Isso permite que você trabalhe lado a lado com pacotes de controle de origem, e você pode alternar entre pacotes sob demanda e plug-ins de controle de origem. Para obter mais informações, consulte [registro e seleção](../../extensibility/internals/registration-and-selection-source-control-vspackage.md).  
  
## <a name="large-source-control-solution-with-a-rich-feature-set"></a>Solução de controle de origem grande com um conjunto rico de recursos  
 Se você quiser implementar uma solução de controle de origem que fornece um modelo de controle de origem avançados adequadamente não capturada usando a API de plug-in de controle de origem, você pode considerar um pacote de controle de origem como o caminho de integração. Isso se aplica especialmente se você substituiria o pacote do adaptador de controle de origem (que se comunica com plug-ins de controle de origem e fornece um controle de origem básico da interface do usuário) em vez disso, com seus próprios para que você pode manipular os eventos de controle de origem de forma personalizada. Se você já tiver uma fonte satisfatório controle da interface do usuário e para preservar a experiência em [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], a opção de controle de origem do pacote lhe permite fazer exatamente isso. O pacote de controle de origem não é genérico e destina-se somente para uso com [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE.  
  
 Se você quiser implementar uma solução de controle de origem que fornece flexibilidade e controle avançado sobre a lógica de controle de origem e a interface do usuário, talvez você prefira a rota de integração do pacote de controle de origem. Você pode:  
  
1.  Registrar seu próprio controle de origem VSPackage (consulte [registro e seleção](../../extensibility/internals/registration-and-selection-source-control-vspackage.md)).  
  
2.  Substitua o controle da fonte padrão da interface do usuário com a interface do usuário personalizada (consulte [Interface de usuário personalizada](../../extensibility/internals/custom-user-interface-source-control-vspackage.md)).  
  
3.  Especificar glifos para ser usado e manipular eventos de glifo Solution Explorer (consulte [controle de glifo](../../extensibility/internals/glyph-control-source-control-vspackage.md)).  
  
4.  Tratar eventos de consulta editar e salvar consulta (consulte [consulta Editar consulta salvar](../../extensibility/internals/query-edit-query-save-source-control-vspackage.md)).  
  
## <a name="see-also"></a>Consulte também  
 [Criando um controle da fonte de plug-in](../../extensibility/internals/creating-a-source-control-plug-in.md)
