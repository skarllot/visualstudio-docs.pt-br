---
title: "Como: for&#231;ar um VSPackage carga | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "VSPackages, force carregamento"
  - "VSPackages, carregando"
ms.assetid: 05f4dc3f-3c9a-45ea-96da-986553b5c5f2
caps.latest.revision: 20
caps.handback.revision: 20
manager: "douge"
---
# Como: for&#231;ar um VSPackage carga
Os VSPackages normalmente são carregados somente quando sua funcionalidade que o acompanha é necessária para concluir um processo.  Em algumas circunstâncias, no entanto, um VSPackage pode ter que forçar o VSPackage outro a ser carregado.  Por exemplo, um leve VSPackage pode carregar VSPackage maior em um contexto de programação que não está disponível como um CMDUIContext.  
  
 Você pode usar o <xref:Microsoft.VisualStudio.Shell.Interop.IVsShell.LoadPackage%2A> método para forçar um VSPackage para carregar.  
  
### Para forçar um VSPackage para carregar  
  
-   Inserir este código para o <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> método do VSPackage que força o outro VSPackage carregar:  
  
     [!code-cs[ForceVSPackageLoad#01](../misc/codesnippet/CSharp/how-to-force-a-vspackage-to-load_1.cs)]  
  
     Quando o VSPackage é inicializado, ele forçará `PackageToBeLoaded` para carregar.  
  
## Programação robusta  
 Carregamento de força não deve ser usado para comunicação VSPackage.  Use [Usando e fornecer serviços](../extensibility/using-and-providing-services.md) em vez disso.  
  
## Consulte também  
 [Gerenciando os VSPackages](../extensibility/managing-vspackages.md)   
 [VSPackages](../extensibility/internals/vspackages.md)