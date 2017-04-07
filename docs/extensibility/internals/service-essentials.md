---
title: "Conceitos básicos do serviço | Microsoft Docs"
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
ms.sourcegitcommit: ca7c86466fa23fb21a932f26dc24e37c71cf29b4
ms.openlocfilehash: 8ff357d7ed3542a01cf8d98e36b9d0e99a122864
ms.lasthandoff: 04/05/2017

---
# <a name="service-essentials"></a>Informações gerais de serviço
Um serviço é um contrato entre dois VSPackages. Um VSPackage fornece um conjunto específico de interfaces para outro VSPackage consumir. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]é uma coleção de VSPackages que fornece serviços a outros VSPackages.  
  
 Por exemplo, você pode usar o serviço de SVsActivityLog para obter uma interface IVsActivityLog, que você pode usar para gravar no log de atividade. Para obter mais informações, consulte [como: usar o Log de atividades](../../extensibility/how-to-use-the-activity-log.md).  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]também fornece alguns serviços internos que não estão registrados. VSPackages pode substituir internos ou outros serviços, fornecendo uma substituição de serviço. É permitida somente um serviço de substituição para qualquer serviço.  
  
 Os serviços não têm nenhuma capacidade de descoberta. Portanto, você deve saber o identificador de serviço (SID) de um serviço que você deseja consumir e você deve saber quais interfaces que ele fornece. A documentação de referência para o serviço fornece essas informações.  
  
-   VSPackages que fornecem serviços são chamados de provedores de serviços.  
  
-   Serviços que são fornecidos para outros VSPackages são chamados de serviços globais.  
  
-   Serviços que estão disponíveis somente para o VSPackage que implementá-las, ou para qualquer objeto que cria, são chamados de serviços locais.  
  
-   Serviços que substituam serviços internos ou serviços fornecidos por outros pacotes, são chamados de substituições de serviço.  
  
-   Serviços ou substituições de serviço, são carregadas sob demanda, ou seja, o provedor de serviços é carregado quando o serviço fornece é solicitado por outro VSPackage.  
  
-   Para dar suporte a carregamento sob demanda, um provedor de serviços registra seus serviços globais com [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Para obter mais informações, consulte [Registrando serviços](../../misc/registering-services.md).  
  
-   Depois de obter um serviço, use [QueryInterface](/cpp/atl/queryinterface) (código não gerenciado) ou projeção (código gerenciado) para obter a interface desejada, por exemplo:  
  
    ```vb#  
    TryCast(GetService(GetType(SVsActivityLog)), IVsActivityLog)  
    ```  
  
    ```c#  
    GetService(typeof(SVsActivityLog)) as IVsActivityLog;  
  
    ```  
  
-   Código gerenciado se refere a um serviço por seu tipo, enquanto o código não gerenciado se refere a um serviço pelo seu GUID.  
  
-   Quando [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] carrega um VSPackage, ele passa um provedor de serviços para o VSPackage para conceder o acesso de VSPackage a serviços globais. Isso é referido como "localização" o VSPackage.  
  
-   VSPackages pode ser provedores de serviços para os objetos que eles criam. Por exemplo, um formulário pode enviar uma solicitação para um serviço de cor para o período, o que pode passar a solicitação [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
-   Objetos gerenciados que estão profundamente aninhados ou não foi localizados, poderão chamar <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A>para acesso direto aos serviços globais.</xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> Para obter mais informações, consulte [como: Use GetGlobalService](../../misc/how-to-use-getglobalservice.md).  
  
## <a name="see-also"></a>Consulte também  
 [Lista de serviços disponíveis](../../extensibility/internals/list-of-available-services.md)   
 [Usando e fornecer serviços](../../extensibility/using-and-providing-services.md)   
 [Conversões cast e conversões de tipo](/dotnet/csharp/programming-guide/types/casting-and-type-conversions)   
 [Conversão](/cpp/cpp/casting)
