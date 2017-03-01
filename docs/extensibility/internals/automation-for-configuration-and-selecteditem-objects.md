---
title: "Automação de configuração e objetos SelectedItem | Documentos do Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- automation [Visual Studio SDK], SelectedItem object
- automation [Visual Studio SDK], builds
ms.assetid: 120377f1-51aa-4445-b2f7-06ab7fc2b47f
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
ms.openlocfilehash: 52ca58a6e85b20ab3bf8741eeaf4cc8c07baec71
ms.lasthandoff: 02/22/2017

---
# <a name="automation-for-configuration-and-selecteditem-objects"></a>Automação de configuração e objetos SelectedItem
Você pode automatizar a compilação e os processos do item selecionado no [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
## <a name="automation-for-builds"></a>Automação de compilações  
 Compilação ou a configuração tem um modelo de automação que é fornecido quando você implementar <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider>.</xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider> Para obter mais informações, consulte [Noções básicas sobre configurações de compilação](../../ide/understanding-build-configurations.md).  
  
 Se você criar um VSPackage e controlar as opções de configuração, você deve usar o modelo de automação.  
  
## <a name="automation-for-selecteditem"></a>Automação de SelectedItem  
 Você não precisa fornecer uma implementação para o `SelectedItem` porque o Visual Studio contém uma implementação padrão. No entanto, você pode implementar o `SelectedItem` se você preferir do objeto. Você deve implementar um objeto que contém o `SelectedItem` de interface e retornar uma resposta a uma chamada para o <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A>método com VSITEMID definida como <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID>.</xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID> </xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A>  
  
## <a name="see-also"></a>Consulte também  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A></xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A>   
 [Contribuir com o modelo de automação](../../extensibility/internals/contributing-to-the-automation-model.md)   
 [Noções sobre configurações de build](../../ide/understanding-build-configurations.md)
