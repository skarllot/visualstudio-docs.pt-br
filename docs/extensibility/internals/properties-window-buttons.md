---
title: "Botões da janela de propriedades | Documentos do Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Properties window, buttons
ms.assetid: bdd2e3a7-ae6e-4e88-be1a-e0e3b7ddbbcc
caps.latest.revision: 14
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
ms.openlocfilehash: 18cee1d193514693e1a70b3e525af11d133f05aa
ms.lasthandoff: 02/22/2017

---
# <a name="properties-window-buttons"></a>Botões da janela de propriedades
Dependendo da linguagem de desenvolvimento e o tipo de produto, determinados botões são exibidos por padrão na barra de ferramentas para a **propriedades** janela. Em todos os casos, o **categorizado**, **Alphabetized**, **propriedades**, e **páginas de propriedade** botões são exibidos. No Visual c# e Visual Basic, o **eventos** botão também é exibido. Em determinados projetos Visual C++, o **VC + + mensagens** e **VC substituições** botões são exibidos. Botões adicionais podem ser exibidas para outros tipos de projeto. Para obter mais informações sobre botões de **propriedades** janela, consulte [janela propriedades](../../ide/reference/properties-window.md).  
  
## <a name="implementation-of-properties-window-buttons"></a>Implementação de botões da janela de propriedades  
 Quando você clica o **categorizado** botão, o Visual Studio chama o <xref:Microsoft.VisualStudio.Shell.Interop.ICategorizeProperties>interface no objeto que tem o foco para classificar suas propriedades por categoria.</xref:Microsoft.VisualStudio.Shell.Interop.ICategorizeProperties> <xref:Microsoft.VisualStudio.Shell.Interop.ICategorizeProperties>é implementado no `IDispatch` objeto que é apresentado para o **propriedades** janela.</xref:Microsoft.VisualStudio.Shell.Interop.ICategorizeProperties>  
  
 Há 11 categorias de propriedade predefinidos, que possuem valores negativos. Você pode definir categorias personalizadas, mas é recomendável que você atribua-os valores positivos para diferenciá-los a categorias predefinidas.  
  
 O <xref:Microsoft.VisualStudio.Shell.Interop.ICategorizeProperties.MapPropertyToCategory%2A>método retorna o valor de categoria de propriedade apropriada para a propriedade especificada.</xref:Microsoft.VisualStudio.Shell.Interop.ICategorizeProperties.MapPropertyToCategory%2A> O <xref:Microsoft.VisualStudio.Shell.Interop.ICategorizeProperties.GetCategoryName%2A>método retorna uma cadeia de caracteres que contém o nome da categoria.</xref:Microsoft.VisualStudio.Shell.Interop.ICategorizeProperties.GetCategoryName%2A> Você só precisa fornecer suporte para valores de categoria personalizada porque o Visual Studio sabe os valores de categoria de propriedade padrão.  
  
 Quando você clica o **Alphabetized** botão, as propriedades são exibidas em ordem alfabética por nome. Os nomes são recuperados pelo `IDispatch` acordo com um algoritmo de classificação localizado.  
  
 Quando o **propriedades** janela está aberta, o **propriedades** botão automaticamente é mostrado como selecionado. Em outras partes do ambiente, o mesmo botão é exibido e você poderá clicar nele para mostrar o **propriedades** janela.  
  
 O **páginas de propriedade** botão não estará disponível se `ISpecifyPropertyPages` não está implementado para o objeto selecionado. Páginas de propriedades exibe as propriedades dependentes de configuração que são normalmente associadas com soluções e projetos, mas eles podem também ser associadas a itens de projeto (por exemplo, no Visual C++).  
  
> [!NOTE]
>  Não é possível adicionar botões de barra de ferramentas para a **propriedades** janela usando código não gerenciado. Para adicionar um botão da barra de ferramentas, você deve criar um objeto gerenciado que deriva de <xref:System.Windows.Forms.Design.PropertyTab>.</xref:System.Windows.Forms.Design.PropertyTab>  
  
## <a name="see-also"></a>Consulte também  
 [Estendendo propriedades](../../extensibility/internals/extending-properties.md)
