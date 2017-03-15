---
title: "Como: registrar um servi&#231;o | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Serviços de registro"
ms.assetid: d086be78-ec3c-43cc-b799-5180a71e19f1
caps.latest.revision: 16
caps.handback.revision: 16
manager: "douge"
---
# Como: registrar um servi&#231;o
A estrutura de pacote gerenciado \(MPF\) fornece atributos para controlar o registro de serviços gerenciados. O utilitário RegPkg usa esses atributos para registrar o serviço com [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
## Exemplo  
 O código a seguir é de [Exemplos VSSDK](../misc/vssdk-samples.md).  
  
 [!code-vb[VSSDKRegisterService#1](../misc/codesnippet/VisualBasic/how-to-register-a-service_1.vb)]
 [!code-cs[VSSDKRegisterService#1](../misc/codesnippet/CSharp/how-to-register-a-service_1.cs)]  
  
 O <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute> registra o serviço SMyGlobalService com [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Para obter mais informações sobre <xref:Microsoft.VisualStudio.Shell.DefaultRegistryRootAttribute> e <xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute>, consulte [VSPackages registrar e cancelar o registro](../extensibility/registering-and-unregistering-vspackages.md).  
  
 Para registrar um serviço que substitui outro serviço com o mesmo nome, use o <xref:Microsoft.VisualStudio.Shell.ProvideServiceOverrideAttribute> em vez do <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute>.  
  
## Programação robusta  
 Para facilitar a recompilação de um provedor de serviços sem alterar o cliente de serviço, ou vice\-versa, você pode definir o serviço e suas interfaces em um módulo de assembly separado. O código a seguir é do arquivo IMyGlobalService.cs no exemplo Reference.Services \(c\#\).  
  
 [!code-vb[VSSDKRegisterService#2](../misc/codesnippet/VisualBasic/how-to-register-a-service_2.vb)]
 [!code-cs[VSSDKRegisterService#2](../misc/codesnippet/CSharp/how-to-register-a-service_2.cs)]  
  
 O <xref:System.Runtime.InteropServices.ComVisibleAttribute> é necessária para obter a interface de código não gerenciado.  
  
> [!NOTE]
>  Embora você possa usar o mesmo tipo ou o GUID para o serviço e a interface, é recomendável que você separe os dois como um serviço pode expor interfaces diferentes.  
  
## Consulte também  
 [Registering VSPackages](http://msdn.microsoft.com/pt-br/31e6050f-1457-4849-944a-a3c36b76f3dd)   
 [Conceitos básicos do serviço](../extensibility/internals/service-essentials.md)