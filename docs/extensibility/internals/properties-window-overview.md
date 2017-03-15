---
title: "Visão geral da janela Propriedades | Documentos do Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Properties window
ms.assetid: 289ed4f2-02ac-4899-855e-42dfe57ee05f
caps.latest.revision: 11
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
ms.openlocfilehash: 1ec1a650c72fbd181d176aea84b228c9973ad526
ms.lasthandoff: 02/22/2017

---
# <a name="properties-window-overview"></a>Visão geral da janela Propriedades
O **propriedades** janela é usada para exibir as propriedades de objetos selecionados os dois tipos principais de disponíveis no windows o [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ambiente de desenvolvimento integrado (IDE). Esses dois tipos de janelas são:  
  
-   Janelas de ferramentas como o navegador do Gerenciador de soluções, exibição de classe e objeto  
  
-   Janelas de documento que contém esses editores e designers como o designer de formulários, o editor de XML e o editor de HTML  
  
## <a name="using-the-properties-window"></a>Usando a janela Propriedades  
 O **propriedades** janela exibe as propriedades de um ou vários itens selecionados. Se vários itens forem selecionados, a interseção de todas as propriedades para todos os objetos selecionados será exibida.  
  
 Eventos relacionados a um objeto selecionado em um editor de HTML usando metadados de COM+ ou janela de design do formulário são exibidos na **propriedades** janela. Por exemplo, você pode selecionar um botão e exibir seus eventos associados, como um `OnClick` evento, que pode ser vinculado a esse botão.  
  
 Os eventos exibidos no **propriedades** janela são usados principalmente com objetos que estão vinculados ao código. Se você estiver editando um formato de arquivo que não tem nada a ver com o código, você não pretender ter todos os eventos. Eventos são exibidos apenas no **propriedades** janela quando há uma associação entre a execução de código e certos eventos associados a objetos específicos. Um exemplo disso seria o código por trás de um objeto selecionado que é executado quando esse objeto é ativado.  
  
 A tabela a seguir lista as interfaces primárias usadas pelo **propriedades** janela.  
  
|Nome da Interface|Descrição|  
|--------------------|-----------------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.ICategorizeProperties></xref:Microsoft.VisualStudio.Shell.Interop.ICategorizeProperties>|Fornece uma lista de categorias para o **propriedades** janela e mapeia cada propriedade a uma categoria.|  
|[Interface IDispatch](http://msdn.microsoft.com/en-us/ebbff4bc-36b2-4861-9efa-ffa45e013eb5)|Expõe métodos e propriedades à programação de ferramentas e outros aplicativos que oferecem suporte a automação de um objeto.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IProvidePropertyBuilder></xref:Microsoft.VisualStudio.Shell.Interop.IProvidePropertyBuilder>|Fornece botões de reticências (...) chamados *construtores* que abrir janelas de diálogo modal implementadas pelo próprio objeto. Usado quando um valor não é facilmente digitado pelo usuário em um campo de texto. Por exemplo, ele pode ser usado para abrir um seletor de cores que determina o valor RGB para você.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer></xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>|Fornece acesso a objetos usados para atualizar as informações exibidas de **propriedades** janela. <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>é implementada por VSPackages para cada janela que contém objetos selecionáveis com propriedades relacionadas a ser exibido.</xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>|  
|<xref:Microsoft.VisualStudio.OLE.Interop.ITypeInfo></xref:Microsoft.VisualStudio.OLE.Interop.ITypeInfo>|Fornece informações sobre o tipo de um objeto, como os métodos de uma interface e campos de uma estrutura.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection></xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection>|Permite que os VSPackages para receber notificações de eventos de seleção e recuperar informações sobre a hierarquia de projeto atual, item, valor do elemento e contexto de interface de usuário do comando.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsMultiItemSelect></xref:Microsoft.VisualStudio.Shell.Interop.IVsMultiItemSelect>|Fornece o ambiente com acesso a várias seleções.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing></xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing>|Usado para fornecer nomes localizados em algumas propriedades exibidas no **propriedades** janela.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSelectionEvents></xref:Microsoft.VisualStudio.Shell.Interop.IVsSelectionEvents>|Notifica os VSPackages registrados de alterações para a seleção atual, o valor de elemento ou o contexto de interface de usuário do comando.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx></xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx>|Notifica o ambiente de uma alteração na seleção atual e fornece acesso a informações de hierarquia e o item relacionado à nova seleção.|  
  
 Para obter mais informações sobre `IDispatch`, consulte a MSDN library.  
  
## <a name="see-also"></a>Consulte também  
 [Estendendo propriedades](../../extensibility/internals/extending-properties.md)   
 [Interfaces e os campos da janela de propriedades](../../extensibility/internals/properties-window-fields-and-interfaces.md)
