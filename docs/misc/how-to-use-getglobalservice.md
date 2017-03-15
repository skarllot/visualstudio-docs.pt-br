---
title: "Como: usar GetGlobalService | Microsoft Docs"
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
  - "serviços, GetGlobalService"
ms.assetid: 4cdf5ab5-9f09-4caf-9011-2dcb2c62f1b7
caps.latest.revision: 14
caps.handback.revision: 14
manager: "douge"
---
# Como: usar GetGlobalService
Às vezes, você talvez precise obter um serviço de uma janela de ferramenta ou controle de recipiente que não tenha sido localizado, ou então tem sido localizado com um provedor de serviços que não conhece o serviço desejado.  Por exemplo, você talvez queira gravar no log de atividade de dentro de um controle.  Para obter mais informações sobre esses e outros cenários, consulte [Como: solucionar problemas de serviços](../extensibility/how-to-troubleshoot-services.md).  
  
 Você pode obter a maioria dos [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] serviços chamando estática <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> método.  
  
 <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A>depende de um provedor de serviços em cache que é inicializado na primeira vez que qualquer VSPackage é derivada de <xref:Microsoft.VisualStudio.Shell.Package> é localizado.  Você deve garantir que essa condição for atendida, senão estar preparada para um serviço nulo.  
  
 Felizmente, <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> funciona corretamente na maioria das vezes.  
  
-   Se um VSPackage fornece um serviço conhecido apenas por outro VSPackage, o VSPackage solicitando o serviço é localizado antes do VSPackage fornecendo que o serviço for carregado.  
  
-   Se uma janela de ferramenta é criada por um VSPackage, o VSPackage é localizado antes que a janela da ferramenta é criada.  
  
-   Se um controle contêiner for hospedado por uma janela de ferramenta criada por um VSPackage, o VSPackage é localizado antes do contêiner de controle é criado.  
  
### Para obter um serviço a partir de um contêiner de controle ou janela de ferramenta  
  
-   Inserir este código na janela da ferramenta, construtor ou contêiner de controle:  
  
     [!code-vb[UseGetGlobalService#1](../misc/codesnippet/VisualBasic/how-to-use-getglobalservice_1.vb)]
     [!code-cs[UseGetGlobalService#1](../misc/codesnippet/CSharp/how-to-use-getglobalservice_1.cs)]  
  
     Esse código obtém um serviço de SVsActivityLog e projeta\-o para um <xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog> interface, que pode ser usado para gravar no log de atividade.  Para um exemplo, consulte [Como: usar o Log de atividades](../extensibility/how-to-use-the-activity-log.md).  
  
## Consulte também  
 [Como: solucionar problemas de serviços](../extensibility/how-to-troubleshoot-services.md)   
 [Usando e fornecer serviços](../extensibility/using-and-providing-services.md)   
 [Conceitos básicos do serviço](../extensibility/internals/service-essentials.md)