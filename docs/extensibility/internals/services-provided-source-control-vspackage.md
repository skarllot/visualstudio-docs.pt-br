---
title: "Serviços fornecidos (VSPackage de controle de origem) | Documentos do Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- services, source control packages
- source control packages, services
ms.assetid: 9db07d70-87d2-4401-bc88-e3a49d81e9a2
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
ms.openlocfilehash: 4af96f17a7a3e1e0d3a9447015d1e37ee695e56e
ms.lasthandoff: 02/22/2017

---
# <a name="services-provided-source-control-vspackage"></a>Serviços fornecidos (VSPackage de controle de origem)
Os serviços são o mecanismo primário por meio do qual funcionalidade é compartilhada entre os VSPackages e entre o ambiente de desenvolvimento integrado (IDE) do Visual Studio e sua VSPackages instalado. Para obter uma descrição detalhada dos serviços e sua importância no IDE do Visual Studio, consulte[usando e fornecer serviços](../../extensibility/using-and-providing-services.md).  
  
## <a name="the-source-control-service"></a>O serviço de controle de origem  
 O Visual Studio fornece duas camadas de serviços, serviços de nível de IDE e serviços de nível de pacote. O Visual Studio IDE nativamente fornece serviços de nível de IDE. O pacote de controle de origem consome alguns desses serviços. O pacote de controle de origem como um VSPackage compartilha sua funcionalidade de controle do código-fonte, fornecendo um serviço de controle de origem particular de seu próprio. O pacote de controle de origem encapsula o conjunto de interfaces relacionada ao controle de origem implementada na forma de um contrato que pode ser usado pelo Visual Studio IDE.  
  
## <a name="see-also"></a>Consulte também  
 [Elementos de design](../../extensibility/internals/source-control-vspackage-design-elements.md)
