---
title: "Usando e fornecer serviços de | Documentos do Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- examples [Visual Studio SDK], services
- Visual Studio, services
- services
ms.assetid: c0b415ba-b825-4da0-9faf-8a60a663e302
caps.latest.revision: 41
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
ms.openlocfilehash: fb380330420d6256190ade75e0afe89f8cbda303
ms.lasthandoff: 02/22/2017

---
# <a name="using-and-providing-services"></a>Usando e fornecer serviços
Um serviço é um contrato entre os dois VSPackages. Um VSPackage oferece um conjunto específico de interfaces para outro VSPackage consumir. Por exemplo, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] oferece o <xref:Microsoft.VisualStudio.Shell.Interop.SVsActivityLog>serviço a qualquer VSPackage cargas.</xref:Microsoft.VisualStudio.Shell.Interop.SVsActivityLog> Este serviço fornece a <xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog>interface, que pode ser usado para gravar no log de atividade.</xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog> Para obter mais informações, consulte [como: usar o Log de atividade](../extensibility/how-to-use-the-activity-log.md).  
  
 Os VSPackages podem oferecer serviços de suas próprias usando a <xref:Microsoft.VisualStudio.Shell.Interop.IProfferService>interface.</xref:Microsoft.VisualStudio.Shell.Interop.IProfferService>  
  
 O Visual Studio oferece serviços importantes, como o seguinte:  
  
|Serviço IDE|Descrição|  
|-----------------|-----------------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsShell></xref:Microsoft.VisualStudio.Shell.Interop.SVsShell>|Fornece acesso ao IDE services lidar com a funcionalidade básica, VSPackages e o registro.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell></xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>|Fornece janelas básicas e funcionalidade relacionados à interface do usuário no IDE, como a capacidade de criar ferramentas e janelas de documento.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution></xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution>|Oferece funções básicas relacionadas à solução, como a capacidade de enumerar os projetos, criar novos projetos e monitorar alterações feitas no projeto.|  
  
## <a name="in-this-section"></a>Nesta seção  
 [Conceitos básicos do serviço](../extensibility/internals/service-essentials.md)  
 Apresenta os elementos importantes de um serviço do Visual Studio.  
  
 [Como: obter um serviço](../extensibility/how-to-get-a-service.md)  
 Discute como solicitar (consumir) um serviço.  
  
 [Como: fornecer um serviço](../extensibility/how-to-provide-a-service.md)  
 Descreve como fornecer um serviço.  
  
 [Como: fornecer um serviço assíncrono do Visual Studio](../extensibility/how-to-provide-an-asynchronous-visual-studio-service.md)  
 Descreve como fornecer um serviço assíncrono.  
  
 [Como: solucionar problemas de serviços](../extensibility/how-to-troubleshoot-services.md)  
 Aborda problemas comuns e apresenta soluções para eles.  
  
## <a name="related-sections"></a>Seções relacionadas  
 [SDK do Visual Studio](../extensibility/visual-studio-sdk.md)
