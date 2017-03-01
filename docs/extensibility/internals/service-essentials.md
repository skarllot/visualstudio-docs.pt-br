---
title: "Conceitos básicos do serviço | Documentos do Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- services, essentials
ms.assetid: fbe84ad9-efe1-48b1-aba3-b50b90424d47
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
ms.openlocfilehash: 579d36d63d39c7cb6b7a476e8f5f0ed78788e8d5
ms.lasthandoff: 02/22/2017

---
# <a name="service-essentials"></a>Conceitos básicos do serviço
Um serviço é um contrato entre os dois VSPackages. Um VSPackage fornece um conjunto específico de interfaces para outro VSPackage consumir. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]em si é uma coleção de VSPackages que fornece serviços a outros VSPackages.  
  
 Por exemplo, você pode usar o serviço SVsActivityLog para obter uma interface IVsActivityLog, que você pode usar para gravar no log de atividade. Para obter mais informações, consulte [como: usar o Log de atividade](../../extensibility/how-to-use-the-activity-log.md).  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]também fornece alguns serviços internos que não estão registrados. Os VSPackages pode substituir internos ou outros serviços, fornecendo uma substituição de serviço. É permitida somente um serviço de substituição para qualquer serviço.  
  
 Os serviços não têm nenhuma descoberta. Portanto, você deve saber o identificador de serviço (SID) de um serviço que você deseja consumir e você deve saber quais interfaces que ele fornece. A documentação de referência para o serviço fornece essas informações.  
  
-   Os VSPackages que fornecem serviços são chamados de provedores de serviços.  
  
-   Serviços que são fornecidos para outros VSPackages são chamados de serviços globais.  
  
-   Serviços que estão disponíveis somente para o VSPackage que implementá-las, ou para qualquer objeto que cria, são chamados de serviços locais.  
  
-   Serviços que substituam serviços internos ou serviços fornecidos por outros pacotes, são chamados de substituições de serviço.  
  
-   Serviços ou substituições de serviço, são carregadas sob demanda, ou seja, o provedor de serviços é carregado quando o serviço que fornece é solicitado por outro VSPackage.  
  
-   Para oferecer suporte a carregamento sob demanda, um provedor de serviço registra seus serviços globais com [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Para obter mais informações, consulte [Registrando serviços](../../misc/registering-services.md).  
  
-   Depois de obter um serviço, use [QueryInterface](/visual-cpp/atl/queryinterface) (código não gerenciado) ou projeção (código gerenciado) para obter a interface desejada, por exemplo:  
  
    ```vb#  
    TryCast(GetService(GetType(SVsActivityLog)), IVsActivityLog)  
    ```  
  
    ```c#  
    GetService(typeof(SVsActivityLog)) as IVsActivityLog;  
  
    ```  
  
-   Código gerenciado se refere a um serviço por seu tipo e código não gerenciado se refere a um serviço por seu GUID.  
  
-   Quando [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] carrega um VSPackage, ele passa um provedor de serviços para o VSPackage para conceder o acesso de VSPackage a serviços globais. Isso é referido como "localização" VSPackage.  
  
-   Os VSPackages pode ser provedores de serviço para os objetos que serão criados. Por exemplo, um formulário pode enviar uma solicitação para um serviço de cor ao seu quadro, o que pode passar a solicitação [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
-   Objetos gerenciados que estão profundamente aninhados ou não colocado no local, poderão chamar <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A>acesso direto a serviços globais.</xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> Para obter mais informações, consulte [como: Use GetGlobalService](../../misc/how-to-use-getglobalservice.md).  
  
## <a name="see-also"></a>Consulte também  
 [Lista de serviços disponíveis](../../extensibility/internals/list-of-available-services.md)   
 [Usando e fornecer serviços](../../extensibility/using-and-providing-services.md)   
 [Cast e conversões de tipo](/dotnet/csharp/programming-guide/types/casting-and-type-conversions)   
 [Conversão](/visual-cpp/cpp/casting)
