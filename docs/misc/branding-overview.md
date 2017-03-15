---
title: "Vis&#227;o geral da identidade Visual | Microsoft Docs"
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
  - "Caixa de diálogo sobre"
  - "VSPackages, telas de abertura"
  - "VSPackages, identidade Visual"
ms.assetid: a47b3645-574c-41c7-8a97-d071cd6b1e82
caps.latest.revision: 11
caps.handback.revision: 11
manager: "douge"
---
# Vis&#227;o geral da identidade Visual
Para mostrar informações sobre o produto na tela de abertura ou  **Ajuda sobre** caixa de diálogo, o VSPackage deverá destes:  
  
-   Fornece informações detalhadas do produto na chave do registro InstalledProducts.  
  
     \- ou \-  
  
-   Implemente <xref:Microsoft.VisualStudio.Shell.Interop.IVsInstalledProduct>.  
  
 A estrutura de pacote gerenciado \(MPF\) fornece a <xref:Microsoft.VisualStudio.Shell.InstalledProductRegistrationAttribute> atributo para controlar o registro na chave do registro InstalledProducts.  Para obter mais informações, consulte [Como: definir a marca um VSPackage \(c\# e Visual Basic\)](../misc/how-to-brand-a-vspackage-csharp-and-visual-basic.md).  
  
 A biblioteca de Visual Studio fornece a `IVsInstalledProductImpl` a classe de modelo para criar uma implementação de <xref:Microsoft.VisualStudio.Shell.Interop.IVsInstalledProduct>.  Para obter mais informações, consulte [Como: definir a marca um VSPackage \(C\+\+\)](../misc/how-to-brand-a-vspackage-cpp.md).  
  
 Implementação de <xref:Microsoft.VisualStudio.Shell.Interop.IVsInstalledProduct> explicitamente é mais poderoso do que usando o atributo ou modelo.  
  
-   Você pode especificar um ícone de tela de splash que difere do  **Ajuda sobre** ícone.  
  
-   Você pode especificar um nome de produto da tela de splash que difere do  **Ajuda sobre** nome do produto.  
  
    > [!IMPORTANT]
    >  Se você usar <xref:Microsoft.VisualStudio.Shell.InstalledProductRegistrationAttribute> e também implementar <xref:Microsoft.VisualStudio.Shell.Interop.IVsInstalledProduct>, a interface tem precedência.  
  
    > [!NOTE]
    >  O mesmo recurso de ícone é usado para a tela de abertura e o  **Ajuda sobre** caixa de diálogo.  O recurso de ícone VSPackage deve incluir uma imagem de 16 × 16 para a tela de abertura e uma imagem de 32 × 32 para o  **Ajuda sobre** caixa de diálogo.  Se você fornecer o tamanho de apenas uma imagem, ela será redimensionada conforme necessário, mas os resultados visuais serão subótimos.  
  
 Para obter uma lista de tarefas relacionadas, consulte [VSPackages](../extensibility/internals/vspackages.md).  
  
## Consulte também  
 [VSPackages](../extensibility/internals/vspackages.md)   
 [Visão geral de biblioteca do Visual Studio](../misc/visual-studio-library-overview.md)