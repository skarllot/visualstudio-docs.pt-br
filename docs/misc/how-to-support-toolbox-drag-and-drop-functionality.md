---
title: "Como: oferecer suporte &#224; funcionalidade de arrastar e soltar da caixa de ferramentas | Microsoft Docs"
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
  - "arrastar e soltar, na caixa de ferramentas de suporte"
  - "Cliente do [Visual Studio SDK], caixa de ferramentas"
  - "Caixa de ferramentas [Visual Studio SDK], arrastar e soltar"
ms.assetid: 2f73a03c-1eb1-4b88-9c1b-d63ba0e2ac90
caps.latest.revision: 18
caps.handback.revision: 18
manager: "douge"
---
# Como: oferecer suporte &#224; funcionalidade de arrastar e soltar da caixa de ferramentas
> [!NOTE]
>  A maneira recomendada para adicionar controles personalizados à caixa de ferramentas é usar o controle de caixa de ferramentas, modelos que acompanham o Visual Studio 10 SDK, que incluem arrastar e soltar de suporte. Este tópico é mantido somente para compatibilidade com versões anteriores e para trabalhar com os controles existentes.  
>   
>  Para obter mais informações sobre como criar controles de caixa de ferramentas, usando os modelos, consulte [Como: criar um controle de caixa de ferramentas que usa o Windows Forms](../misc/how-to-create-a-toolbox-control-that-uses-windows-forms.md) e [Criando um controle de caixa de ferramentas do WPF](../extensibility/creating-a-wpf-toolbox-control.md).  
  
 Os VSPackages deve implementar o suporte a arrastar e soltar se eles usarem **Toolbox** controles em modos de exibição de documento, como designers ou editores.  
  
 Por padrão, todos os [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] objetos derivados de <xref:System.Windows.Forms.Control?displayProperty=fullName> automática e transparente fornecem suporte para o consumo **Toolbox** controles e os procedimentos descritos abaixo são desnecessários. A funcionalidade básica pode ser estendida com a criação de um designer.  
  
 Para obter mais informações, consulte [Visão geral dos Windows Forms](../Topic/Windows%20Forms%20Overview.md) e [Extending Design\-Time Support](../Topic/Extending%20Design-Time%20Support.md).  
  
### Para implementar a funcionalidade de arrastar e soltar  
  
1.  Oferecem suporte a arrastar e soltar implementando <xref:Microsoft.VisualStudio.OLE.Interop.IDropTarget> em um objeto de exibição. Isso fornece a exibição com a funcionalidade de arrastar e soltar OLE e serialização do controle.  
  
     Para obter mais informações sobre como implementar a funcionalidade de arrastar e soltar, consulte [Arrastar e soltar \(OLE\)](/visual-cpp/mfc/drag-and-drop-ole).  
  
     Quedas podem ser itens da área de transferência ou controles que está sendo descartados em um designer. Para obter informações sobre formatos de área de transferência padrão com suporte a [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] **Toolbox**, consulte [Estendendo a caixa de ferramentas](../misc/extending-the-toolbox.md).  
  
2.  Fornecer uma implementação básica do <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolboxUser> interface em uma exibição de documento.  
  
     Quando um usuário tenta arrastar um controle de caixa de ferramentas para um modo de exibição, o [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] shell consultas VSPackage do modo de exibição para ver se ele implementa o <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolboxUser> interface.  
  
    1.  Implementar <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolboxUser.IsSupported%2A> para retornar <xref:Microsoft.VisualStudio.VSConstants.S_OK> para aqueles **Toolbox** formata o destino de soltar oferece suporte. O exemplo a seguir verifica se o objeto de dados está no formato de área de transferência personalizado \(`CF_CUSTOM_FORMAT`\) e se o objeto é um controle ActiveX.  
  
        ```cpp#  
        STDMETHODIMP CustTbxUser::IsSupported(IDataObject* pDO) { HRESULT hr; STGMEDIUM stm; if (!pDO) return E_POINTER; // Determine if the data object is in the Custom clip board format // fetc is the dialog editor toolbox item template. FORMATETC fetc = { m_CF_CUSTOM_FORMAT, //Value set with RegisterClipboardFormat NULL, DVASPECT_CONTENT, // DVASCPECT_ICON might be better -1, TYMED_HGLOBAL }; if (FAILED(hr = pDO->GetData(&fetc, &stm))) { // Determine if the object is in the class-id clipboard format ... this // would be the case if the control is an activeX toolbox item. FORMATETC xfetc = { m_CF_CLSID, NULL, DVASPECT_CONTENT, // DVASCPECT_ICON might be better -1, TYMED_HGLOBAL }; if (SUCCEEDED(hr = pDO->GetData(&xfetc,&stm))) { USES_CONVERSION; GUID guid; LPSTR pData = (LPSTR)GlobalLock(stm.hGlobal); if (pData) { // Convert from the string format to a binary GUID. if (CLSIDFromString(A2W(pData), &guid) != S_OK) return E_FAIL; // HTML data objects could have CLSID format ... so any data object could // be returned as a NULL guid ... fail on null guid, obviously they are // not active X controls. if (guid == GUID_NULL) return E_FAIL; } } } return hr; }  
        ```  
  
         Para essas informações quando a janela do modo de exibição é carregado pela primeira vez e para cada ativação da janela do modo de exibição após uma redefinição do que o IDE verifica o **Toolbox** por um usuário por meio do IDE **Personalizar Toolbox** caixa de diálogo.  Normalmente, o **Toolbox** faz a exibição não sem suporte **Toolbox** itens.  
  
         Os usuários podem definir uma opção para exibir todas as páginas da caixa de ferramentas em todos os momentos. Nesse caso, o ambiente não consulta o editor para <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolboxUser.IsSupported%2A>.  
  
    2.  Após um <xref:Microsoft.VisualStudio.OLE.Interop.IDropTarget> implementação \(como o descrito acima\) manipula com êxito um componente solto, o objeto de exibição deve notificar o [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ambiente isso chamando <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox2.DataUsed%2A>  
  
     Se desejar, um VSPackage pode estender o suporte de arrastar e soltar, estendendo seu <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolboxUser> implementação.  
  
3.  Um <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolboxUser> oferece suporte a arrastar **Toolbox** itens para uma janela pela ação de seleção em vez de mouse. Ou seja, arrastando um item quando um usuário clica duas vezes ou em um **Toolbox** item ou cliques únicos em e, em seguida, pressionar ENTER. Para fazer isso:  
  
    1.  Implementar o <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolboxUser.ItemPicked%2A> método.  
  
         Esse método, chamado pelo IDE é selecionado por meio de um clique ou pressionando ENTER.  
  
         O método deve inserir o **Toolbox** item na janela de destino.  
  
    2.  Se você não deseja dar suporte à implementação pela seleção, o método deve retornar <xref:Microsoft.VisualStudio.VSConstants.S_FALSE>.  
  
         No exemplo abaixo, a implementação de <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolboxUser.ItemPicked%2A> método verifica se o objeto selecionado é suportado e nesse caso o desserializa o código:  
  
        ```cpp#  
        STDMETHODIMP CustTbxUser::ItemPicked(IDataObject* pDataObject) { if (!pDataObject) return E_POINTER; UINT nIDTool; if (IsSupported(pDataObject) == S_OK) { SetToolCursor(); m_pDataObject = pDataObject; nIDTool = DeserializeObject(); // Get the focus back m_pResObject->m_spWndFrame->Show(); return S_OK; } }  
        ```  
  
4.  Execute as etapas a seguir para assegurar que o foco adequado é mantido para seu aplicativo:  
  
    1.  Se a janela do editor implementa dois painéis diferentes, não dois diferentes modos de exibição, em seguida, chame o <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox2.UpdateToolboxUI%2A> quando você alterna as ativações do painel na janela editor de método. Somente você saberá quando alterações de ativação ocorrem dentro de sua janela.  
  
    2.  Para ativar corretamente a janela e certifique\-se de que o roteamento de comando é atualizado corretamente, você deve chamar o <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.Show%2A> método no componente. Essa ação deve ser tomada quando você está definindo o foco para uma janela de componente, como um editor, criado ou modificado por uma operação de arrastar e soltar que envolvem a caixa de ferramentas.  
  
 Talvez seja necessário intervir em uma operação de arrastar e modificar o item descartado por meio de um VSPackage o <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolboxActiveUserHook> interface.  
  
 Por exemplo, em vez de adicionar um novo **Toolbox** controlar explicitamente como a **Toolbox**, um VSPackage pode interceptar um padrão **Toolbox** como ele é descartado e substituí\-la por uma implementação personalizada.  
  
### Para modificar dinamicamente os controles de caixa de ferramentas  
  
1.  Implementar o <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolboxActiveUserHook> método.  
  
     Sempre que um **ferramentas** item está selecionado ou descartado, o **ferramentas** consultará o local de destino para ver se ele oferece suporte a <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolboxActiveUserHook> interface, e se ele faz chamadas a <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolboxActiveUserHook.InterceptDataObject%2A> método.  
  
2.  O <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolboxActiveUserHook.InterceptDataObject%2A> método deve retornar um novo <xref:Microsoft.VisualStudio.OLE.Interop.IDataObject> objeto a ser usado em vez do original <xref:Microsoft.VisualStudio.OLE.Interop.IDataObject>.  
  
     Se o local de destino não precisa substituir o objeto de dados, ele deverá retornar sua entrada.  
  
 Um VSPackage pode permitir aos usuários percorrer o conteúdo da área de transferência pressionando CTRL \+ SHIFT \+ V.  
  
### Para oferecer suporte a uma área de transferência  
  
1.  Implemente um manipulador para o `CMDIDPasteNextTBXCBItem` comando usando:  
  
    -   <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> para VSPackages baseadas em assembly de interoperabilidade.  
  
    -   <xref:Microsoft.VisualStudio.Shell.OleMenuCommandService> para VSPackages baseados na estrutura de pacote gerenciado.<xref:Microsoft.VisualStudio.Shell.Interop.IVsToolboxClipboardCycler> interface.  
  
2.  No manipulador de comando, implemente o <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolboxClipboardCycler.AreDataObjectsAvailable%2A> método para determinar se há quaisquer objetos da área de transferência para percorrer.  
  
    1.  Se não houver nenhum item na área de transferência de caixa de ferramentas, o ambiente verifica o sistema para ver se há quaisquer itens da área de transferência.  
  
    2.  Se houver itens na área de transferência da sistema, mas não na área de transferência de caixa de ferramentas, a área de transferência é preenchida com itens do sistema.  
  
    3.  Para selecionar o próximo item na lista, a implementação chama o <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolboxClipboardCycler.GetAndSelectNextDataObject%2A> método.  
  
    4.  Para retornar ao início do ciclo de área de transferência, chame o <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolboxClipboardCycler.BeginCycle%2A> método.  
  
## Consulte também  
 [Estendendo a caixa de ferramentas](../misc/extending-the-toolbox.md)   
 [Como: fornecer itens de caixa de ferramentas personalizado usando Assemblies de interoperabilidade](../Topic/How%20to:%20Provide%20Custom%20Toolbox%20Items%20By%20Using%20Interop%20Assemblies.md)   
 [Desenvolvimento de controle de caixa de ferramentas avançadas](/visual-cpp/misc/advanced-toolbox-control-development)   
 [Registrar os recursos de suporte da caixa de ferramentas](../misc/registering-toolbox-support-features.md)   
 [Gerenciando a caixa de ferramentas](/visual-cpp/misc/managing-the-toolbox)