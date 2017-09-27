---
title: "Criar um Editor de núcleo e registrar um tipo de arquivo do Editor | Microsoft Docs\""
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - walkthrough
ms.assetid: 24d2bffd-a35c-46db-8515-fd60b884b7fb
caps.latest.revision: 29
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
ms.translationtype: MT
ms.sourcegitcommit: 4a36302d80f4bc397128e3838c9abf858a0b5fe8
ms.openlocfilehash: dec3e53df108377dacfc53ba308029933654b789
ms.contentlocale: pt-br
ms.lasthandoff: 09/26/2017

---
# <a name="walkthrough-creating-a-core-editor-and-registering-an-editor-file-type"></a>Passo a passo: Criando um Editor de núcleo e registrando um tipo de arquivo do Editor
Este passo a passo demonstra como criar um VSPackage que inicia o [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] editor principal quando um arquivo que tem a extensão de nome de arquivo .myext é carregado.  
  
## <a name="prerequisites"></a>Pré-requisitos  
 Para acompanhar este passo a passo, você deve instalar o SDK do Visual Studio. Para obter mais informações, consulte [SDK do Visual Studio](../extensibility/visual-studio-sdk.md).  
  
## <a name="locations-for-the-visual-studio-package-project-template"></a>Locais para o modelo de projeto de pacote do Visual Studio  
 O modelo de projeto de pacote do Visual Studio pode ser encontrado em três locais diferentes no **novo projeto** caixa de diálogo:  
  
1.  Em extensibilidade do Visual Basic. O idioma padrão do projeto é Visual Basic.  
  
2.  Em c# extensibilidade. O idioma padrão do projeto é c#.  
  
3.  Em outra extensibilidade de tipos de projeto. O idioma padrão do projeto é C++.  
  
### <a name="to-create-the-vspackage"></a>Para criar o VSPackage  
  
-   Iniciar [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] e criar um [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] VSPackage denominado `MyPackage`, conforme descrito na [passo a passo: Criando um VSPackage do comando de Menu](http://msdn.microsoft.com/en-us/d699c149-5d1e-47ff-94c7-e1222af02c32).  
  
### <a name="to-add-the-editor-factory"></a>Para adicionar a fábrica do editor  
  
1.  Clique com botão direito do **MyPackage** de projeto, aponte para **adicionar** e, em seguida, clique em **classe**.  
  
2.  No **Adicionar Novo Item** caixa de diálogo caixa, verifique se o **classe** modelo é selecionado, tipo `EditorFactory.cs` para o nome e, em seguida, clique **adicionar** para adicionar a classe ao seu projeto.  
  
     O arquivo de EditorFactory.cs deve ser aberto automaticamente.  
  
3.  Referenciar os seguintes assemblies no seu código.  
  
    ```vb  
    Imports System.Runtime.InteropServices  
    Imports Microsoft.VisualStudio  
    Imports Microsoft.VisualStudio.Shell  
    Imports Microsoft.VisualStudio.Shell.Interop  
    Imports Microsoft.VisualStudio.OLE.Interop  
    Imports Microsoft.VisualStudio.TextManager.Interop  
    Imports IOleServiceProvider = Microsoft.VisualStudio.OLE.Interop.IServiceProvider  
    ```  
  
    ```csharp  
    using System.Runtime.InteropServices;  
    using Microsoft.VisualStudio;  
    using Microsoft.VisualStudio.Shell;  
    using Microsoft.VisualStudio.Shell.Interop;  
    using Microsoft.VisualStudio.OLE.Interop;  
    using Microsoft.VisualStudio.TextManager.Interop;  
    using IOleServiceProvider = Microsoft.VisualStudio.OLE.Interop.IServiceProvider;  
  
    ```  
  
4.  Adicionar um GUID para o `EditorFactory` classe adicionando o `Guid` atributo imediatamente antes da declaração de classe.  
  
     Você pode gerar um novo GUID usando o programa de guidgen.exe o [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] prompt de comando, ou clicando em **criar GUID** no **ferramentas** menu. O GUID usado aqui é apenas um exemplo. não usá-lo em seu projeto.  
  
    ```vb  
    <Guid("0eea3187-c5fa-48d4-aa72-b5eecd3b17b1")> _  
    ```  
  
    ```csharp  
    [Guid("0eea3187-c5fa-48d4-aa72-b5eecd3b17b1")]   
    ```  
  
5.  Na definição de classe, adicione duas variáveis privadas para conter o pacote pai e um provedor de serviços.  
  
    ```vb  
    Class EditorFactory  
        Private parentPackage As Package  
        Private serviceProvider As IOleServiceProvider  
    ```  
  
    ```csharp  
    class EditorFactory  
    {  
        private Package parentPackage;  
        private IOleServiceProvider serviceProvider;  
    }  
  
    ```  
  
6.  Adicione um construtor de classe pública que leva um parâmetro de tipo <xref:Microsoft.VisualStudio.Shell.Package>:  
  
    ```vb  
    Public Sub New(ByVal parentPackage As Package)  
        Me.parentPackage = parentPackage  
    End Sub  
    ```  
  
    ```csharp  
    public EditorFactory(Package parentPackage)  
    {  
        this.parentPackage = parentPackage;  
    }  
    ```  
  
7.  Modificar o `EditorFactory` declaração derivar de classe a <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory> interface.  
  
    ```vb  
    Class EditorFactory Implements IVsEditorFacto  
    ```  
  
    ```csharp  
    class EditorFactory : IVsEditorFactory  
  
    ```  
  
8.  Clique com botão direito <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory>, clique em **implementar Interface**e, em seguida, clique em **implementar Interface explicitamente**.  
  
     Isso adiciona os quatro métodos que devem ser implementados no <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory> interface.  
  
9. Substitua o conteúdo do método de `IVsEditorFactory.Close` com o código a seguir.  
  
    ```vb  
    Return VSConstants.S_OK  
    ```  
  
    ```csharp  
    return VSConstants.S_OK;  
    ```  
  
10. Substitua o conteúdo do `IVsEditorFactory.SetSite` com o código a seguir.  
  
    ```vb  
    Me.serviceProvider = psp  
    Return VSConstants.S_OK  
    ```  
  
    ```csharp  
    this.serviceProvider = psp;  
    return VSConstants.S_OK;  
    ```  
  
11. Substitua o conteúdo do método de `IVsEditorFactory.MapLogicalView` com o código a seguir.  
  
    ```vb  
    Dim retval As Integer = VSConstants.E_NOTIMPL  
    pbstrPhysicalView = Nothing ' We support only one view.  
    If rguidLogicalView.Equals(VSConstants.LOGVIEWID_Designer)OrElse _  
    rguidLogicalView.Equals(VSConstants.LOGVIEWID_Primary) Then  
        retval = VSConstants.S_OK  
    End If  
    Return retval  
    ```  
  
    ```csharp  
    int retval = VSConstants.E_NOTIMPL;  
    pbstrPhysicalView = null;   // We support only one view.  
    if (rguidLogicalView.Equals(VSConstants.LOGVIEWID_Designer) ||  
    rguidLogicalView.Equals(VSConstants.LOGVIEWID_Primary))  
    {  
        retval = VSConstants.S_OK;  
    }  
    return retval;  
    ```  
  
12. Substitua o conteúdo do método de `IVsEditorFactory.CreateEditorInstance` com o código a seguir.  
  
    ```vb  
    Dim retval As Integer = VSConstants.E_FAIL          
  
    ' Initialize these to empty to start with   
    ppunkDocView = IntPtr.Zero  
    ppunkDocData = IntPtr.Zero  
    pbstrEditorCaption = ""  
    pguidCmdUI = Guid.Empty  
    pgrfCDW = 0  
  
    If (grfCreateDoc And (VSConstants.CEF_OPENFILE Or _  
    VSConstants.CEF_SILENT)) = 0 Then  
        Throw New ArgumentException("Only Open or Silent is valid")  
    End If  
    If punkDocDataExisting <> IntPtr.Zero Then  
        Return VSConstants.VS_E_INCOMPATIBLEDOCDATA  
    End If  
  
    ' Instantiate a text buffer of type VsTextBuffer.   
    ' Note: we only need an IUnknown (object) interface for   
    ' this invocation.   
    Dim clsidTextBuffer As Guid = GetType(VsTextBufferClass).GUID  
    Dim iidTextBuffer As Guid = VSConstants.IID_IUnknown  
    Dim pTextBuffer As Object = pTextBuffer = _  
    parentPackage.CreateInstance(clsidTextBuffer, iidTextBuffer, _  
    GetType(Object))  
  
    If Not pTextBuffer Is Nothing Then  
        ' "Site" the text buffer with the service provider we were   
        ' provided.   
        Dim textBufferSite As IObjectWithSite = TryCast(pTextBuffer, _  
        IObjectWithSite)  
        If Not textBufferSite Is Nothing Then  
            textBufferSite.SetSite(Me.serviceProvider)  
        End If  
  
        ' Instantiate a code window of type IVsCodeWindow.   
        Dim clsidCodeWindow As Guid = GetType(VsCodeWindowClass).GUID  
        Dim iidCodeWindow As Guid = GetType(IVsCodeWindow).GUID  
        Dim pCodeWindow As IVsCodeWindow = _  
        CType(Me.parentPackage.CreateInstance(clsidCodeWindow, _  
        iidCodeWindow, GetType(IVsCodeWindow)), IVsCodeWindow)  
        If Not pCodeWindow Is Nothing Then  
            ' Give the text buffer to the code window.   
            ' We are giving up ownership of the text buffer!   
            pCodeWindow.SetBuffer(CType(pTextBuffer, IVsTextLines))  
  
            ' Now tell the caller about all this new stuff   
            ' that has been created.   
            ppunkDocView = Marshal.GetIUnknownForObject(pCodeWindow)  
            ppunkDocData = Marshal.GetIUnknownForObject(pTextBuffer)  
  
            ' Specify the command UI to use so keypresses are   
            ' automatically dealt with.   
            pguidCmdUI = VSConstants.GUID_TextEditorFactory  
  
            ' This caption is appended to the filename and   
            ' lets us know our invocation of the core editor   
            ' is up and running.   
            pbstrEditorCaption = " [MyPackage]"  
  
            retval = VSConstants.S_OK  
        End If  
    End If  
    Return retval  
    ```  
  
    ```csharp  
    int retval = VSConstants.E_FAIL;  
  
    // Initialize these to empty to start with  
    ppunkDocView       = IntPtr.Zero;  
    ppunkDocData       = IntPtr.Zero;  
    pbstrEditorCaption = "";  
    pguidCmdUI         = Guid.Empty;   
    pgrfCDW            = 0;  
  
    if ((grfCreateDoc & (VSConstants.CEF_OPENFILE |   
          VSConstants.CEF_SILENT)) == 0)  
    {   
        throw new ArgumentException("Only Open or Silent is valid");  
    }  
    if (punkDocDataExisting != IntPtr.Zero)  
    {  
        return VSConstants.VS_E_INCOMPATIBLEDOCDATA;  
    }  
  
    // Instantiate a text buffer of type VsTextBuffer.  
    // Note: we only need an IUnknown (object) interface for   
    // this invocation.  
    Guid clsidTextBuffer = typeof(VsTextBufferClass).GUID;  
    Guid iidTextBuffer   = VSConstants.IID_IUnknown;  
    object pTextBuffer   = pTextBuffer = parentPackage.CreateInstance(  
          ref clsidTextBuffer,  
          ref iidTextBuffer,  
          typeof(object));  
  
    if (pTextBuffer != null)  
    {  
        // "Site" the text buffer with the service provider we were  
        // provided.  
        IObjectWithSite textBufferSite = pTextBuffer as IObjectWithSite;  
        if (textBufferSite != null)  
        {  
            textBufferSite.SetSite(this.serviceProvider);  
        }  
  
        // Instantiate a code window of type IVsCodeWindow.  
        Guid clsidCodeWindow = typeof(VsCodeWindowClass).GUID;  
        Guid iidCodeWindow   = typeof(IVsCodeWindow).GUID;  
        IVsCodeWindow pCodeWindow =  
        (IVsCodeWindow)this.parentPackage.CreateInstance(   
              ref clsidCodeWindow,  
              ref iidCodeWindow,  
              typeof(IVsCodeWindow));  
        if (pCodeWindow != null)  
        {  
            // Give the text buffer to the code window.  
            // We are giving up ownership of the text buffer!  
            pCodeWindow.SetBuffer((IVsTextLines)pTextBuffer);  
  
            // Now tell the caller about all this new stuff   
            // that has been created.  
            ppunkDocView = Marshal.GetIUnknownForObject(pCodeWindow);  
            ppunkDocData = Marshal.GetIUnknownForObject(pTextBuffer);  
  
            // Specify the command UI to use so keypresses are   
            // automatically dealt with.  
            pguidCmdUI = VSConstants.GUID_TextEditorFactory;  
  
            // This caption is appended to the filename and  
            // lets us know our invocation of the core editor   
            // is up and running.  
            pbstrEditorCaption = " [MyPackage]";  
  
            retval = VSConstants.S_OK;  
        }   
    }   
    return retval;   
    ```  
  
13. Compile o projeto e verifique se que não existem erros.  
  
### <a name="to-register-the-editor-factory"></a>Para registrar a fábrica do editor  
  
1.  Em **Solution Explorer**, duas vezes no arquivo resx para abri-lo para a tabela de cadeia de caracteres, no qual a entrada **String1 é** selecionado.  
  
2.  Alterar o nome do identificador para `IDS_EDITORNAME` e o texto a ser **MyPackage Editor.** Essa cadeia de caracteres será exibido como o nome do seu editor.  
  
3.  Abra o arquivo VSPackage.resx e adicione uma nova cadeia de caracteres, defina o nome como **101** e o valor para `IDS_EDITORNAME`. Isso fornece o pacote com uma ID de recurso para acessar a cadeia de caracteres que você acabou de criar.  
  
    > [!NOTE]
    >  Se o arquivo VSPackage.resx contém outra cadeia de caracteres que o `name` atributo definido como **101**, substitua a outro valor numérico, exclusivo, aqui e nas etapas a seguir.  
  
4.  Em **Solution Explorer**, abra o arquivo MyPackagePackage.cs.  
  
     Este é o arquivo de pacote principal.  
  
5.  Adicione os seguintes atributos de usuário antes de `Guid` atributo.  
  
    ```vb  
    <ProvideEditorFactoryAttribute(GetType(EditorFactory), 101)> _  
    <ProvideEditorExtensionAttribute(GetType(EditorFactory), _  
          ".myext", 32, NameResourceID:=101 )> _  
    ```  
  
    ```csharp  
    [ProvideEditorFactory(typeof(EditorFactory), 101)]  
    [ProvideEditorExtension(typeof(EditorFactory),   
          ".myext", 32, NameResourceID = 101)]   
    ```  
  
     O <xref:Microsoft.VisualStudio.Shell.ProvideEditorExtensionAttribute> atributo associa a extensão de arquivo .myext sua fábrica de editor para que sempre que um arquivo com que a extensão foi carregada, sua fábrica de editor é invocada.  
  
6.  Adicione uma variável particular para o `MyPackage` classe antes do construtor e dê a ele o tipo `EditorFactory`.  
  
    ```vb  
    Private editorFactory As EditorFactory  
    ```  
  
    ```csharp  
    private EditorFactory editorFactory;  
    ```  
  
7.  Localizar o `Initialize` método (talvez você precise abrir o `Package Members` região oculto) e adicione o seguinte código após a chamada a `base.Initialize()`.  
  
    ```vb  
    'Create our editor factory and register it.   
    Me.editorFactory = New EditorFactory(Me)  
    MyBase.RegisterEditorFactory(Me.editorFactory)  
    ```  
  
    ```csharp  
    // Create our editor factory and register it.  
    this.editorFactory = new EditorFactory(this);  
    base.RegisterEditorFactory(this.editorFactory);  
  
    ```  
  
8.  Compile o programa e verifique se que não existem erros.  
  
     Esta etapa registra a fábrica do editor no hive do registro experimental para [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Se você for solicitado a substituir o arquivo resource.h, clique em **Okey**.  
  
9. Crie um arquivo de exemplo chamado TextFile1.myext.  
  
10. Pressione **F5** para abrir uma instância do [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
11. No [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], no **arquivo** , aponte para **abrir** e, em seguida, clique em **arquivo**.  
  
12. Localizar TextFile1.myext e, em seguida, clique em **abrir**.  
  
     O arquivo agora deve ser carregado.  
  
## <a name="robust-programming"></a>Programação robusta  
 O [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] editor núcleo lida com uma ampla variedade de tipos de arquivo de texto e trabalha em conjunto com os serviços de idioma para fornecer um conjunto avançado de recursos, como o realce de sintaxe, correspondência de chaves e listas de conclusão de palavra e conclusão de membro do IntelliSense. Se você estiver trabalhando com arquivos de texto, você pode usar o editor de núcleo junto com um serviço de idioma personalizado que oferece suporte os tipos de arquivo específico.  
  
 Um VSPackage pode invocar o [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] editor principal, fornecendo uma fábrica de editor. Esta fábrica de editor é usada sempre que um arquivo que está associado ele é carregado. Se o arquivo for parte de um projeto, o editor de núcleo é invocado automaticamente a menos que substituída por seu VSPackage. No entanto, se o arquivo for carregado fora de um projeto, em seguida, o editor de núcleo deve ser explicitamente invocado pelo seu VSPackage.  
  
 Para obter mais informações sobre o editor de núcleo, consulte [dentro do Editor de núcleo de](../extensibility/inside-the-core-editor.md).  
  
## <a name="see-also"></a>Consulte também  
 [Dentro do Editor de núcleo](../extensibility/inside-the-core-editor.md)   
 [Criando o Editor de núcleo usando a API herdado](../extensibility/instantiating-the-core-editor-by-using-the-legacy-api.md)
