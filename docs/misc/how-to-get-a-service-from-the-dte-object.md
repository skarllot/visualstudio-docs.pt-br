---
title: "Como: obter um servi&#231;o do objeto DTE | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "serviços do objeto DTE"
ms.assetid: c26a51d4-86f0-454b-9625-5443e55eec7d
caps.latest.revision: 13
caps.handback.revision: 13
manager: "douge"
---
# Como: obter um servi&#231;o do objeto DTE
Um serviço pode ser obtido em qualquer programa que tenha acesso a [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] automação <xref:EnvDTE.DTEClass> objeto.  Por exemplo, você pode acessar o <xref:Microsoft.VisualStudio.Shell.Interop.SVsActivityLog> serviço de um assistente através do objeto DTE.  Você pode usar esse serviço para gravar no log de atividade.  Para mais informações, consulte [Como: usar o Log de atividades](../extensibility/how-to-use-the-activity-log.md).  
  
 O objeto DTE implementa <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>, que você pode usar a consulta para um serviço do código gerenciado usando <xref:Microsoft.VisualStudio.Shell.ServiceProvider.GetService%2A>.  
  
### Para obter um serviço do objeto DTE  
  
1.  O código a seguir cria um <xref:Microsoft.VisualStudio.Shell.ServiceProvider> do objeto DTE e chamadas <xref:Microsoft.VisualStudio.Shell.ServiceProvider.GetService%2A> com o tipo da <xref:Microsoft.VisualStudio.Shell.Interop.SVsActivityLog> service.  O serviço é um conversão para a interface <xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog>, que é usado para gravar uma entrada no registro de atividades.  Para obter mais abou de informações sobre como gravar no log de atividade, consulte [Como: usar o Log de atividades](../extensibility/how-to-use-the-activity-log.md).  
  
     [!code-cs[GetAServiceFromTheDTEObject#1](../misc/codesnippet/CSharp/how-to-get-a-service-from-the-dte-object_1.cs)]
     [!code-vb[GetAServiceFromTheDTEObject#1](../misc/codesnippet/VisualBasic/how-to-get-a-service-from-the-dte-object_1.vb)]  
  
## Consulte também  
 [Usando e fornecer serviços](../extensibility/using-and-providing-services.md)   
 [Conceitos básicos do serviço](../extensibility/internals/service-essentials.md)