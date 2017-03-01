---
title: Arquitetura de VSPackage de controle de origem | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- source control packages, architecture
ms.assetid: 453125fc-23dc-49b1-8476-94581f05e6c7
caps.latest.revision: 25
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
ms.openlocfilehash: 05188f3f13bf97624e467a884318a805c7d5a14b
ms.lasthandoff: 02/22/2017

---
# <a name="source-control-vspackage-architecture"></a>Arquitetura de VSPackage de controle de origem
Um pacote de controle de origem é um VSPackage que usa serviços que o [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE fornece. Em troca, um pacote de controle de origem fornece sua funcionalidade como um serviço de controle de origem. Além disso, um pacote de controle de origem é uma alternativa mais versátil que o plug-in para integrar o controle de origem em um controle de fonte [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
 Um plug-in que implementa a API de plug-in de controle de origem de controle da fonte segue um contrato rígida. Por exemplo, um plug-in não pode substituir o padrão [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] interface do usuário (IU). Além disso, a API de plug-in de controle de origem não permite um plug-in implementar seu próprio modelo de controle de origem. No entanto, um pacote de controle de origem, supera essas limitações. Um pacote de controle de origem tem total controle sobre a experiência de controle de origem de um [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] usuário. Além disso, um pacote de controle de origem pode usar seu próprio modelo de controle de origem e a lógica, e pode definir todas as interfaces de usuário relacionados ao controle de origem.  
  
## <a name="source-control-package-components"></a>Componentes do pacote de controle de origem  
 Conforme mostrado no diagrama da arquitetura, um [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] componente denominado o Stub de controle de origem é um VSPackage que integra um pacote de controle de origem com [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
 Stub de controle de origem trata as seguintes tarefas.  
  
-   Fornece a interface do usuário comum que é necessário para o registro do pacote de controle de origem.  
  
-   Carrega um pacote de controle de origem.  
  
-   Define um pacote de controle de origem como ativo/inativo.  
  
 Stub de controle de origem procura o serviço ativo para o pacote de controle de origem e roteia entrada todas as chamadas de serviço do IDE para que o pacote.  
  
 O pacote de adaptador de controle de origem é um controle de fonte especial de pacote que [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] fornece. Este pacote é o componente central para oferecer suporte a controle de origem plug-ins com base na API de plug-in de controle de origem. Quando um plug-in de controle de origem é o plug-in do ativo, o Stub de controle de origem envia seus eventos para o pacote de adaptador de controle de origem. Por sua vez, o pacote de adaptador de controle de origem se comunica com o plug-in de controle de origem usando a API de plug-in de controle de origem e também fornece uma interface do usuário que é comum para controle de origem todos os plug-ins de padrão.  
  
 Quando um pacote de controle de origem é o pacote do ativo, por outro lado, o Stub de controle de origem se comunica diretamente com o pacote usando o [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] interfaces do pacote de controle de origem. O pacote de controle de origem é responsável por hospedar o seu próprio controle da fonte de interface do usuário.  
  
 ![Gráfico de arquitetura de controle do código-fonte](../../extensibility/internals/media/vsipsccarch.gif "VSIPSCCArch")  
  
 Para um pacote de controle de origem, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] fornecem código de controle de origem ou uma API de integração. Compare isso com a abordagem descrita no [criar um plug-in de controle de origem](../../extensibility/internals/creating-a-source-control-plug-in.md) onde o plug-in de controle de origem tem que implementar um conjunto rígido de funções e retornos de chamada.  
  
 Como qualquer VSPackage, um pacote de controle de origem é um objeto COM que pode ser criado usando `CoCreateInstance`. O VSPackage se torna disponível para o [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE implementando <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>.</xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage> Quando uma instância tiver sido criada, um VSPackage recebe um ponteiro de site e um <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>interface que fornece o VSPackage acessem os serviços disponíveis e interfaces no IDE.</xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>  
  
 Escrever um pacote de controle de origem com base em VSPackage requer conhecimento de programação mais avançado que escrever uma API de plug-in de controle de origem com base em plug-in.  
  
## <a name="see-also"></a>Consulte também  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage></xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>   
 [Introdução](../../extensibility/internals/getting-started-with-source-control-vspackages.md)
