---
title: "Ativa&#231;&#227;o in-loco | Microsoft Docs"
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
  - "editores [Visual Studio SDK], personalizado - ativação do modo de exibição no local"
ms.assetid: 7d316945-06e0-4d8e-ba3a-0ef96fc75399
caps.latest.revision: 26
caps.handback.revision: 26
manager: "douge"
---
# Ativa&#231;&#227;o in-loco
Se o modo de exibição do editor hospeda ActiveX ou outros controles ativos, você deve implementar o modo de exibição do editor como um controle ActiveX ou um objeto de dados de documento ativo usando o modelo de ativação no local.  
  
## Suporte de Menus, barras de ferramentas e comandos  
 O Visual Studio permite a exibição do editor para usar os menus e barras de ferramentas do IDE. Essas extensões são conhecidas como *componentes no local de OLE*. Para obter mais informações, consulte o <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponent> e <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponentUIManager>.  
  
 Se você implementar um controle ActiveX, você pode hospedar outros objetos incorporados. Se você implementar um objeto de dados de documento, o quadro de janela restringe a capacidade de usar os controles ActiveX.  
  
> [!NOTE]
>  O <xref:Microsoft.VisualStudio.OLE.Interop.IOleDocument> e <xref:Microsoft.VisualStudio.OLE.Interop.IOleDocumentView> interfaces permitem uma separação de dados e exibir. No entanto, o Visual Studio não oferece suporte a essa funcionalidade, e essas interfaces são usadas apenas para representar o objeto de exibição de documento.  
  
 Editores que usam o <xref:Microsoft.VisualStudio.Shell.Interop.SOleComponentUIManager> service pode fornecer o menu, a barra de ferramentas e a integração de comando chamando os métodos do <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponentUIManager> interface implementada pelo <xref:Microsoft.VisualStudio.Shell.Interop.SOleComponentUIManager> service. Editores podem também oferecem outras funcionalidades do Visual Studio, como seleção de controle e desfazer o gerenciamento. Para obter mais informações, consulte [Criar Designers e editores personalizados](../extensibility/creating-custom-editors-and-designers.md).  
  
## Objetos e Interfaces usadas  
 Os objetos que são usados para criar a ativação no local são mostrados na ilustração a seguir.  
  
 ![Editor de ativação in&#45;loco](../misc/media/vsinplaceactivationeditor.png "vsInPlaceActivationEditor")  
Editor de ativação no local  
  
> [!NOTE]
>  Os objetos neste desenho, apenas o `CYourEditorFactory` objeto é necessária para criar um editor padrão. Se você estiver criando um editor personalizado, você não precisa implementar <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2> porque seu editor provavelmente terá seu próprio mecanismo de persistência particular. Para obter mais informações, consulte [Criar Designers e editores personalizados](../extensibility/creating-custom-editors-and-designers.md).  
  
 Todas as interfaces que são implementadas para criar uma ativação in\-loco editor são mostradas no único `CYourEditorDocument` objeto, mas essa configuração só oferece suporte a uma única exibição de dados de documentos. Para obter mais informações sobre o suporte a vários modos de exibição de seus dados de documentos, consulte [Suporte a vários modos de exibição de documento](../extensibility/supporting-multiple-document-views.md).  
  
|Interface|Tipo de objeto|Use|  
|---------------|--------------------|---------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponent>|Modo de Exibição|Permite que objetos de VSPackage in\-loco operar como componentes totalmente integradas do IDE usando o <xref:Microsoft.VisualStudio.Shell.Interop.SOleComponentUIManager> service. Esse serviço integra os menus, barras de ferramentas e comandos do objeto ao IDE e emite notificações de alterações de estado.|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleObject>|Modo de Exibição|Principais meios pelos quais um objeto incorporado fornece a funcionalidade básica para seu contêiner e se comunica com ele.|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleInPlaceActiveObject>|Modo de Exibição|Gerencia a ativação e desativação de objetos no local e determina o quanto do objeto local deve estar visível.|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleInPlaceObject>|Modo de Exibição|Fornece um canal de comunicação entre um objeto no local, janela de quadro mais externo do aplicativo associado e a janela de documento no aplicativo que contém o objeto incorporado direto.|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleDocument>|Modo de Exibição|Implementa um objeto ActiveX. Observe que os métodos de <xref:Microsoft.VisualStudio.OLE.Interop.IOleDocument> e `T:Microsoft.VisualStudio.OLE.Interop.IOleDocumentView` dados de documentos separada e exibição não são usados no IDE.|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>|Exibir\/dados|Permite que o objeto de dados de documento, o objeto de exibição do documento ou ambos para participar de manipulação de comandos.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser>|Modo de Exibição|Permite atualizações da barra de status.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsToolboxUser>|Modo de Exibição|Permite adicionar itens à caixa de ferramentas.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsFileChangeEvents>|Dados|Envia notificação de alterações para o arquivo editado. \(Essa interface é opcional.\)|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat>|Dados|Usada para habilitar o recurso Salvar como para um tipo de arquivo.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData>|Dados|Permite a persistência para o documento. Para arquivos somente leitura, chame <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.SetDocDataReadOnly%2A> para fornecer o ícone de "bloqueio" que indica os arquivos somente leitura.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsDocDataFileChangeControl>|Dados|Determina se as alterações de dados de documentos devem ser ignoradas.|