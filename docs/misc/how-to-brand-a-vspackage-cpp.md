---
title: "Como: definir a marca um VSPackage (C++) | Microsoft Docs"
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
  - "Caixa de diálogo sobre"
  - "VSPackages, telas de abertura"
  - "VSPackages, identidade Visual"
ms.assetid: a1b9213f-8702-4716-8623-cd3705d531fa
caps.latest.revision: 10
caps.handback.revision: 10
manager: "douge"
---
# Como: definir a marca um VSPackage (C++)
Apareça na  **Ajuda sobre** caixa de diálogo e a tela de abertura, VSPackages deve implementar a <xref:Microsoft.VisualStudio.Shell.Interop.IVsInstalledProduct> interface.  Isso fornece as seguintes informações para [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]:  
  
-   Nome  
  
-   ID, como o número de série ou de versão  
  
-   Informações  
  
-   Ícone de logotipo  
  
 O `IVsInstalledProductImpl` classe usa parâmetros de modelo para essas informações.  Cada parâmetro do modelo é uma identificação.  As três primeiras são identificações dos recursos de seqüência de caracteres e a quarta é a identificação do recurso de um ícone.  
  
## Exemplo  
 A seguinte declaração de classe para a classe VSPackage provém do [Exemplos VSSDK](../misc/vssdk-samples.md).  
  
```  
class ATL_NO_VTABLE BasicPackage :   
  ...  
  public IVsInstalledProductImpl<  
    IDS_BASICPACKAGE_PRODUCT_NAME,  
    IDS_BASICPACKAGE_PRODUCT_IDENTIFIER,   
    IDS_BASICPACKAGE_PRODUCT_DETAILS,   
    IDI_BASICPACKAGE_LOGO>  
```  
  
 Para testar sua VSPackage, consulte [Como: testar a Ajuda sobre e telas de abertura](../misc/how-to-test-the-help-about-and-splash-screens.md).  
  
## Consulte também  
 [Marca de VSPackage](/visual-cpp/misc/vspackage-branding)