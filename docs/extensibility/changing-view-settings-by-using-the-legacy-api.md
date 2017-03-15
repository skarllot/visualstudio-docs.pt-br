---
title: "Alterando as configurações de exibição usando a API herdada | Documentos do Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - changing view settings
ms.assetid: 12c9b300-0894-4124-96a1-764326176d77
caps.latest.revision: 18
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
ms.openlocfilehash: 7e2d2d9c44e325068ca80bd367d5a76ad473723b
ms.lasthandoff: 02/22/2017

---
# <a name="changing-view-settings-by-using-the-legacy-api"></a>Alterando as configurações de exibição usando a API herdada
As configurações para os principais recursos do editor, como quebra automática de linha, margem de seleção e espaço virtual, podem ser alteradas pelo usuário por meio do **opções** caixa de diálogo. No entanto, também é possível alterar essas configurações por meio de programação.  
  
## <a name="changing-settings-by-using-the-legacy-api"></a>Alterando as configurações usando a API herdada  
 O <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyCategoryContainer>interface expõe um conjunto de propriedades do editor de texto.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyCategoryContainer> A exibição de texto contém uma categoria de propriedades (GUID_EditPropCategory_View_MasterSettings) que representa o grupo de configurações alteradas por meio de programação para a exibição de texto. Depois de exibir configurações foram alteradas dessa maneira, eles não podem ser alterados a **opções** caixa de diálogo até que sejam redefinidos.  
  
 A seguir está o processo típico para alterar as configurações de exibição para uma instância do editor principal.  
  
1.  Chamar `QueryInterface` sobre o (<xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView>) para o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyCategoryContainer>interface.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyCategoryContainer> </xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView>  
  
2.  Chamar o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyCategoryContainer.GetPropertyCategory%2A>método, especificando um valor de GUID_EditPropCategory_View_MasterSettings para o `rguidCategory` parâmetro.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyCategoryContainer.GetPropertyCategory%2A>  
  
     Isso retorna um ponteiro para o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyCategoryContainer>interface, que contém o conjunto de propriedades forçados para a exibição.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyCategoryContainer> Todas as configurações neste grupo são forçadas permanentemente. Se uma configuração não estiver nesse grupo, ele seguirá as opções especificadas no **opções** caixa de diálogo ou os comandos do usuário.  
  
3.  Chamar o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyContainer.SetProperty%2A>método, especificando o valor de configurações apropriadas no `idprop` parâmetro.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyContainer.SetProperty%2A>  
  
     Por exemplo, para forçar a quebra automática de linha, chamar <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyContainer.SetProperty%2A>e especifique um valor de VSEDITPROPID_ViewLangOpt_WordWrap, `vt` para o `idprop` parâmetro.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyContainer.SetProperty%2A> Nessa chamada, `vt` é uma VARIANTE do tipo VT_BOOL e `vt.boolVal` é VARIANT_TRUE.  
  
## <a name="resetting-changed-view-settings"></a>Redefinindo as configurações de exibição alterada  
 Para redefinir qualquer exibição alterada configuração para uma instância do editor de núcleo, chamar o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyContainer.RemoveProperty%2A>método e especifique o valor de configuração apropriada no `idprop` parâmetro.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyContainer.RemoveProperty%2A>  
  
 Por exemplo, para permitir quebra flutue livremente, você deve removê-lo da categoria de propriedade chamando <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyContainer.RemoveProperty%2A>e especificando um valor de VSEDITPROPID_ViewLangOpt_WordWrap para o `idprop` parâmetro.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyContainer.RemoveProperty%2A>  
  
 Para remover configurações alteradas todos editor principal de uma só vez, especifique um valor de VSEDITPROPID_ViewComposite_AllCodeWindowDefaults, vt para o `idprop` parâmetro. Nessa chamada, vt é uma VARIANTE do tipo VT_BOOL e vt.boolVal é VARIANT_TRUE.  
  
## <a name="see-also"></a>Consulte também  
 [Dentro do Editor de núcleo](../extensibility/inside-the-core-editor.md)   
 [Acessando theText exibição usando a API herdada](../extensibility/accessing-thetext-view-by-using-the-legacy-api.md)   
 [Caixa de diálogo Opções](../ide/reference/options-dialog-box-visual-studio.md)
