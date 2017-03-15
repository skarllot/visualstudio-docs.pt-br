---
title: Campos da janela de propriedades e Interfaces | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Properties window, fields and interfaces
ms.assetid: 0328f0e5-2380-4a7a-a872-b547cb775050
caps.latest.revision: 12
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
ms.openlocfilehash: 75056862b91c8bc2afd652485e6611922f2daefe
ms.lasthandoff: 02/22/2017

---
# <a name="properties-window-fields-and-interfaces"></a>Interfaces e os campos da janela de propriedades
O modelo de seleção determinar quais informações são exibidas no **propriedades** janela baseia-se na janela que tem o foco no IDE. Cada janela e objeto dentro da janela selecionada, podem ter seu objeto de contexto de seleção enviado para o contexto de seleção global. O ambiente atualiza o contexto da seleção global com valores de um quadro de janela quando essa janela tem o foco. Quando o foco muda, aumenta também o contexto da seleção.  
  
## <a name="tracking-selection-in-the-ide"></a>Seleção de controle no IDE  
 O quadro de janela ou site, o IDE, de propriedade tem um serviço chamado <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection>.</xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection> As etapas a seguir mostram como uma alteração em uma seleção, causada por usuário, alterar o foco para outra janela aberta ou selecionando um item de projeto diferente em **Solution Explorer**, é implementado para alterar o conteúdo exibido no **propriedades** janela.  
  
1.  O objeto criado pelo VSPackage é colocado na janela selecionada chama <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider.QueryService%2A>ter <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection>invocar <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection>.</xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection> </xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection> </xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider.QueryService%2A>  
  
2.  O contêiner de seleção, fornecido pela janela selecionada, cria seu próprio <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>objeto.</xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> Quando a seleção é alterada, o VSPackage chama <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection.OnSelectChange%2A>para notificar todos os ouvintes no ambiente, incluindo o **propriedades** janela, da alteração.</xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection.OnSelectChange%2A> Ele também fornece acesso a informações de hierarquia e item relacionados à nova seleção.  
  
3.  Chamando <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection.OnSelectChange%2A>e passando-os itens da hierarquia selecionada no `VSHPROPID_BrowseObject` parâmetro preenche o <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>objeto.</xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> </xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection.OnSelectChange%2A>  
  
4.  Um objeto derivado do [IDispatch Interface](http://msdn.microsoft.com/en-us/ebbff4bc-36b2-4861-9efa-ffa45e013eb5) é retornado para <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID>para o item solicitado e o ambiente encapsula em um <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>(consulte a etapa a seguir).</xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> </xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID> Se a chamada falhar, o ambiente torna uma segunda chamada para `IVsHierarchy::GetProperty`, passando o contêiner de seleção <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID>que fornecem o item de hierarquia ou itens.</xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID>  
  
     Seu projeto de VSPackage não cria <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>porque a janela fornecidos pelo ambiente de VSPackage que o implementa (por exemplo, **Solution Explorer**) constrói <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>em seu nome.</xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> </xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>  
  
5.  O ambiente chama os métodos do <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>para obter os objetos com base no `IDispatch` interface para preencher o **propriedades** janela.</xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>  
  
 Quando um valor na **propriedades** janela for alterada, os VSPackages implementar `IVsTrackSelectionEx::OnElementValueChangeEx` e `IVsTrackSelectionEx::OnSelectionChangeEx` para relatar a alteração para o valor do elemento. Em seguida, invoca o ambiente <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell>ou <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer>para manter as informações exibidas no **propriedades** janela de sincronizados com os valores de propriedade.</xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer> </xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> Para obter mais informações, consulte [atualizar valores de propriedade na janela propriedades](../../misc/updating-property-values-in-the-properties-window.md).  
  
 Além de selecionar um outro item de projeto no **Solution Explorer** para exibir as propriedades relacionadas a esse item, você também pode escolher um objeto diferente de dentro de uma janela de formulário ou documento usando a lista suspensa disponível no **propriedades** janela. Para obter mais informações, consulte [lista de objetos de janela de propriedades](../../extensibility/internals/properties-window-object-list.md).  
  
 Você pode alterar o modo de exibição de informações de **propriedades** grade da janela de alfabética para categórica, e, se estiver disponível, você também pode abrir uma página de propriedades para um objeto selecionado clicando nos botões adequado no **propriedades** janela. Para obter mais informações, consulte [botões de janela de propriedades](../../extensibility/internals/properties-window-buttons.md) e [páginas de propriedade](../../extensibility/internals/property-pages.md).  
  
 Por fim, a parte inferior da **propriedades** janela também contém uma descrição do campo selecionado no **propriedades** grade da janela. Para obter mais informações, consulte [obter descrições dos campos na janela de propriedades](../../misc/getting-field-descriptions-from-the-properties-window.md).  
  
## <a name="see-also"></a>Consulte também  
 [Estendendo propriedades](../../extensibility/internals/extending-properties.md)
