---
title: 'Passo a passo: Adicionando recursos a um Editor personalizado | Documentos do Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], custom - add features
ms.assetid: bfe083b6-3e35-4b9c-ad4f-b30b9ff412a5
caps.latest.revision: 38
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
ms.openlocfilehash: f3706a260f75e81bc5bd229d73bd6f8b90ed0134
ms.lasthandoff: 02/22/2017

---
# <a name="walkthrough-adding-features-to-a-custom-editor"></a>Passo a passo: Adicionando recursos a um Editor personalizado
Depois de criar um editor personalizado, você pode adicionar mais recursos a ele.  
  
### <a name="to-create-an-editor-for-a-vspackage"></a>Criar um editor para um VSPackage  
  
1.  Crie um editor personalizado, usando o modelo de projeto do Visual Studio Package.  
  
     Para obter mais informações, consulte [passo a passo: Criando um Editor personalizado](../extensibility/walkthrough-creating-a-custom-editor.md).  
  
2.  Decida se deseja que o seu editor para dar suporte a um modo de exibição único ou vários modos de exibição.  
  
     Um editor que ofereça suporte a **nova janela** comando, ou tem o modo de exibição de formulário e de código, requer que objetos de dados de documentos separada e objetos de exibição de documento. Em um editor que oferece suporte a apenas uma única exibição, o objeto de dados de documento e o objeto de exibição de documento podem ser implementados no mesmo objeto.  
  
     Para obter um exemplo de vários modos de exibição, consulte [suporte a várias exibições de documento](../extensibility/supporting-multiple-document-views.md).  
  
3.  Implementar uma fábrica de editor Implementando o <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory>interface.</xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory>  
  
     Para obter mais informações, consulte [fábricas](../extensibility/editor-factories.md).  
  
4.  Decida se deseja que o editor para usar a ativação no local ou simplificado de incorporação para gerenciar a janela de objeto de exibição de documento.  
  
     Uma janela do editor de inserção simplificada hospeda uma visualização de documento padrão, enquanto uma janela do editor de ativação no local hospeda um controle ActiveX ou outro objeto ativo como seu modo de exibição de documento. Para obter mais informações, consulte [simplificado inserindo](../extensibility/simplified-embedding.md) e [da ativação In loco](../misc/in-place-activation.md).  
  
5.  Implementar o <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>interface para lidar com comandos.</xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>  
  
6.  Fornecem persistência de documento e resposta a alterações de arquivo externo, fazendo o seguinte:  
  
    1.  Para manter o arquivo, implementar <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2>e <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat>no objeto de dados de documento do editor.</xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat> </xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2>  
  
    2.  Para responder a alterações de arquivo externo, implementar <xref:Microsoft.VisualStudio.Shell.Interop.IVsFileChangeEx>e <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocDataFileChangeControl>no objeto de dados de documento do editor.</xref:Microsoft.VisualStudio.Shell.Interop.IVsDocDataFileChangeControl> </xref:Microsoft.VisualStudio.Shell.Interop.IVsFileChangeEx>  
  
        > [!NOTE]
        >  Chamar `QueryService` em <xref:Microsoft.VisualStudio.Shell.Interop.SVsFileChangeEx>para obter um ponteiro para `IVsFileChangeEx`.</xref:Microsoft.VisualStudio.Shell.Interop.SVsFileChangeEx>  
  
7.  Coordene eventos de edição de documentos com controle do código fonte. Para fazer isso:  
  
    1.  Obter um ponteiro para `IVsQueryEditQuerySave2` chamando `QueryService` em <xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave>.</xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave>  
  
    2.  Quando ocorre o primeiro evento de edição, chamar o <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A>método.</xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A>  
  
         Isso solicita que o usuário fazer check-out do arquivo se ele já não fez isso. Certifique-se de lidar com uma condição de "arquivo não check-out" avert erros  
  
    3.  Da mesma forma, antes de salvar o arquivo, chamar o <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFile%2A>método.</xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFile%2A>  
  
         Este método solicita ao usuário para salvar o arquivo se ele não tiver sido salvo, ou se ele tiver sido alterado desde a última gravação.  
  
8.  Habilitar o **propriedades** janela para exibir as propriedades do texto selecionado no editor. Para fazer isso:  
  
    1.  Chamar <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection.OnSelectChange%2A>cada seleção de texto de tempo for alterado, passando na sua implementação de <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>.</xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> </xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection.OnSelectChange%2A>  
  
    2.  Chamar `QueryService` no <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection>serviço para obter um ponteiro para <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection>.</xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection> </xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection>  
  
9. Permitir que os usuários arrastar e soltar itens entre o editor e o **Toolbox**, ou entre editores externos (como o Microsoft Word) e o **ferramentas**. Para fazer isso:  
  
    1.  Implementar `IDropTarget` em seu editor para alertar o IDE seu editor é um destino de soltar.  
  
    2.  Implementar o <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolboxUser>interface no modo de exibição para o editor pode habilitar e desabilitar itens do **ferramentas**.</xref:Microsoft.VisualStudio.Shell.Interop.IVsToolboxUser>  
  
    3.  Implemente <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.ResetDefaults%2A>e chamar `QueryService` na <xref:Microsoft.VisualStudio.Shell.Interop.SVsToolbox>service para obter um ponteiro para o <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox2>e <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox3>interfaces.</xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox3> </xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox2> </xref:Microsoft.VisualStudio.Shell.Interop.SVsToolbox> </xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.ResetDefaults%2A>  
  
         Isso permite que o VSPackage adicionar novos itens para o **ferramentas**.  
  
10. Decida se deseja que os outros recursos opcionais para o editor.  
  
    -   Se você quiser que o editor para dar suporte a localizar e substituir comandos, implementar <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget>.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget>  
  
    -   Se você quiser usar uma janela de ferramentas da estrutura de tópicos de documento em seu editor, implementar `IVsDocOutlineProvider`.  
  
    -   Se você quiser usar uma barra de status em seu editor, implementar <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser>e chamar `QueryService` para <xref:Microsoft.VisualStudio.Shell.Interop.SVsStatusbar>para obter um ponteiro para `IVsStatusBar`.</xref:Microsoft.VisualStudio.Shell.Interop.SVsStatusbar> </xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser>  
  
         Por exemplo, um editor pode exibir linha / informações de coluna, o modo de seleção (transmitir / caixa) e o modo de inserção (Inserir / /overstrike).  
  
    -   Se você quiser que o editor para oferecer suporte a `Undo` de comando, o método recomendado é usar o modelo do Gerenciador de desfazer OLE. Como alternativa, você pode ter o identificador do editor de `Undo` comando diretamente.  
  
11. Crie registro de informações, incluindo os GUIDs para o VSPackage, menus, o editor e outros recursos.  
  
     Este é um exemplo de código que você deve colocar o script do arquivo. rgs para demonstrar como registrar corretamente um editor genérico.  
  
    ```  
    NoRemove Editors  
    {  
          ForceRemove {...guidEditor...} = s 'RTF Editor'  
          {  
             val Package = s '{...guidVsPackage...}'  
             ForceRemove Extensions  
             {  
                val rtf = d 50  
             }  
          }  
    }  
    NoRemove Menus  
    {  
          val {...guidVsPackage...} = s ',203,11'  
    }  
    ```  
  
12. Implemente o suporte a Ajuda contextual.  
  
     Isso permite que você forneça suportam a Ajuda F1 e a janela Ajuda dinâmica para itens em seu editor. Para obter mais informações sobre isso, consulte [como: fornecer contexto para os editores](../extensibility/how-to-provide-context-for-editors.md).  
  
13. Expor um modelo de objeto de automação do seu editor Implementando o `IDispatch` interface.  
  
     Para obter mais informações, consulte [contribuem para o modelo de automação](../extensibility/internals/contributing-to-the-automation-model.md).  
  
## <a name="robust-programming"></a>Programação robusta  
  
-   A instância do editor é criada quando o IDE chama o <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A>método.</xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> Se o editor dá suporte a vários modos de exibição `CreateEditorInstance` cria dados de documento e os objetos de exibição do documento. Se o objeto de dados de documento já está aberto, não null `punkDocDataExisting` valor é passado para `IVsEditorFactory::CreateEditorInstance`. A implementação de fábrica de editor deve determinar se um objeto de dados de documento existente é compatível, consultando as interfaces apropriadas nele. Para obter mais informações, consulte [suporte a várias exibições de documento](../extensibility/supporting-multiple-document-views.md).  
  
-   Se você usar a abordagem de incorporação simplificada, implementar o <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane>interface.</xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane>  
  
-   Se você decidir usar a ativação no local, implemente as seguintes interfaces:  
  
     <xref:Microsoft.VisualStudio.OLE.Interop.IOleObject></xref:Microsoft.VisualStudio.OLE.Interop.IOleObject>  
  
     <xref:Microsoft.VisualStudio.OLE.Interop.IOleInPlaceActiveObject></xref:Microsoft.VisualStudio.OLE.Interop.IOleInPlaceActiveObject>  
  
     <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponent></xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponent>  
  
    > [!NOTE]
    >  O `IOleInPlaceComponent` interface é usada para evitar a mesclagem de menus OLE 2.  
  
     O `IOleCommandTarget` implementação trata comandos como **Recortar**, **cópia**, e **colar**. Ao implementar `IOleCommandTarget`, decidir se seu editor requer seu próprio arquivo. VSCT para definir sua própria estrutura do menu de comando ou se ele pode implementar comandos padrão definidos pela [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Normalmente, editores de usarem e estendem os menus do IDE e definem suas próprias barras de ferramentas. No entanto, geralmente é necessário para um editor definir seus próprios comandos específicos, além de usar o conjunto de comandos padrão do IDE. Para fazer isso, seu editor deve declarar os comandos padrão, ele usa e, em seguida, defina quaisquer novos comandos menus de contexto, menus de nível superior e barras de ferramentas em um arquivo. VSCT. Se você criar uma ativação in-loco no editor, implementar <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponent>e defina os menus e barras de ferramentas para o editor de um arquivo. VSCT em vez de usar a mesclagem de menus OLE 2.</xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponent>  
  
-   Para evitar que o comando de menu lotado na interface do usuário, você deve usar os comandos existentes no IDE antes de inventar novos comandos. Comandos compartilhados são definidos em SharedCmdDef.vsct e ShellCmdDef.vsct. Esses arquivos são instalados por padrão no subdiretório VisualStudioIntegration\Common\Inc do seu [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] instalação.  
  
-   `ISelectionContainer`pode expressar únicas e várias seleções. Cada objeto selecionado é implementado como um `IDispatch` objeto.  
  
-   O IDE implementa `IOleUndoManager` como um serviço acessível de um <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2.CreateInstance%2A>ou um objeto que pode ser criado por meio de <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2.CreateInstance%2A>.</xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2.CreateInstance%2A> </xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2.CreateInstance%2A> Implementa o editor de `IOleUndoUnit` interface para cada `Undo` ação.  
  
-   Há dois locais um editor personalizado pode expor objetos de automação:  
  
    -   `Document.Object`  
  
    -   `Window.Object`  
  
## <a name="see-also"></a>Consulte também  
 [Contribuir com o modelo de automação](../extensibility/internals/contributing-to-the-automation-model.md)   
 [Como: fornecer contexto para editores](../extensibility/how-to-provide-context-for-editors.md)
