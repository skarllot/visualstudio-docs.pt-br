---
title: "Propriedades de exibição de grade | Documentos do Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- properties [Visual Studio SDK], grid
ms.assetid: 318e41b0-acf5-4842-b85e-421c9d5927c5
caps.latest.revision: 10
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
ms.openlocfilehash: 111f8ddefbeb55962479969e3217a4124cc023e1
ms.lasthandoff: 02/22/2017

---
# <a name="properties-display-grid"></a>Grade de exibição de propriedades
O **propriedades** janela exibe campos em uma grade. A coluna esquerda contém os nomes de propriedade; a coluna à direita contém os valores de propriedade.  
  
## <a name="working-with-the-grid"></a>Trabalhar com a grade  
 A lista de duas colunas mostra as propriedades de configuração independente que podem ser alteradas em tempo de design e suas configurações atuais. Observe que todas as propriedades não podem ser exibidas. Uma propriedade pode ser definida como oculto, por exemplo, Implementando o <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.HideProperty%2A>método.</xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.HideProperty%2A> Especificamente, para ocultar propriedades que têm propriedades filho consulte, [ocultar propriedades que têm propriedades filho](../../misc/hiding-properties-that-have-child-properties.md).  
  
 Informações de envio para o **propriedades** janela, usa o IDE <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>.</xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>é chamado pelo VSPackages para cada janela que contém objetos selecionáveis com propriedades relacionadas a serem exibidos no **propriedades** janela.</xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> **Gerenciador de soluções**da implementação de <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>chamadas `GetProperty` usando <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID>na sua hierarquia de projeto para adquirir os objetos navegáveis na hierarquia.</xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID> </xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>  
  
 Se o VSPackage não oferece suporte a <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID>, o IDE tenta usar <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A>usando os valores de <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID>que fornecem o item de hierarquia ou itens.</xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID> </xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> </xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID>  
  
 Seu projeto de VSPackage não precisa criar <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>porque o pacote de janela fornecida pelo IDE que o implementa (por exemplo, **Solution Explorer**) constrói <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>em seu nome.</xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> </xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>consiste em três métodos são chamados pelo IDE:</xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.CountObjects%2A>contém o número de objetos selecionados para serem exibidos no **propriedades** janela.</xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.CountObjects%2A>  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.GetObjects%2A>Retorna o `IDispatch` objetos selecionados a serem exibidos no **propriedades** janela.</xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.GetObjects%2A>  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.SelectObjects%2A>permite que qualquer um dos objetos retornados por <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.GetObjects%2A>para ser selecionado pelo usuário.</xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.GetObjects%2A></xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.SelectObjects%2A> Isso permite que o VSPackage visualmente Atualizar seleção exibida para o usuário na interface do usuário.  
  
 O **propriedades** janela extrai informações da `IDispatch` objetos para recuperar as propriedades que está sendo pesquisadas. O navegador de propriedades usa `IDispatch` perguntar quais propriedades de objeto, ele oferece suporte ao consultar `ITypeInfo`, que é obtido `IDispatch::GetTypeInfo`. O navegador usa esses valores para preencher o **propriedades** janela e alterar os valores de propriedades individuais são exibidos na grade. As informações de propriedades são mantidas dentro do próprio objeto.  
  
 Porque os objetos retornados suportam `IDispatch`, o chamador pode obter informações como o nome do objeto chamando `IDispatch::Invoke` ou `ITypeInfo::Invoke` com um identificador de expedição predefinidos (DISPID) que representa as informações desejadas. DISPIDs declarados são negativos para garantir que eles não entrem em conflito com identificadores definidos pelo usuário.  
  
 O **propriedades** janela exibe os diferentes tipos de campos de acordo com os atributos de propriedades específicas de um objeto selecionado. Esses campos incluem caixas de edição, listas suspensas e links para caixas de diálogo do editor personalizado.  
  
-   Os valores contidos em uma lista enumerada são recuperados por um <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.GetObjects%2A>de consulta para `IDispatch`.</xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.GetObjects%2A> Valores obtidos de uma lista enumerada podem ser alterados na grade de propriedades clicando duas vezes no nome do campo, ou clicando no valor e selecionando o novo valor da lista suspensa. Para propriedades que têm configurações de enumerado listas predefinidas, duas vezes no nome da propriedade na lista de propriedades percorre as opções disponíveis. Para propriedades predefinidas com apenas duas opções, como verdadeiro/falso, duas vezes no nome de propriedade para alternar entre as opções.  
  
-   Se <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.HasDefaultValue%2A>for `false`, indicando que o valor foi alterado, o valor é exibido em negrito.</xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.HasDefaultValue%2A> <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.CanResetPropertyValue%2A>é usado para determinar se o valor pode ser redefinido para o valor original.</xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.CanResetPropertyValue%2A> Se assim, você pode alterar para o padrão clicando duas vezes o valor e escolhendo **redefinir** no menu exibido. Caso contrário, você precisa alterar o valor para o padrão manualmente. <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing>também permite que você localize e ocultar os nomes das propriedades exibidas durante o tempo de design, mas não afeta os nomes das propriedades exibidos durante o tempo de execução.</xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing>  
  
-   Clique no botão de reticências (...) exibe uma lista de valores de propriedade na qual o usuário pode selecionar (como um seletor de cores ou a lista de fontes). <xref:Microsoft.VisualStudio.Shell.Interop.IProvidePropertyBuilder>fornece esses valores.</xref:Microsoft.VisualStudio.Shell.Interop.IProvidePropertyBuilder>  
  
## <a name="see-also"></a>Consulte também  
 [Estendendo propriedades](../../extensibility/internals/extending-properties.md)
