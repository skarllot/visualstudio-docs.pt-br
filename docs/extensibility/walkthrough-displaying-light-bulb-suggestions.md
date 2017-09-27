---
title: "Passo a passo: Exibindo sugestões de lâmpada | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 99e5566d-450e-4660-9bca-454e1c056a02
caps.latest.revision: 16
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
ms.openlocfilehash: 1096b04fee06415e65a93b0ecd8a6257de64edfc
ms.contentlocale: pt-br
ms.lasthandoff: 09/26/2017

---
# <a name="walkthrough-displaying-light-bulb-suggestions"></a>Passo a passo: Exibindo sugestões de lâmpada
Lâmpadas são ícones usados no editor do Visual Studio que se expanda para exibir um conjunto de ações, por exemplo correções para problemas identificados pelo analisadores de código internos ou código de refatoração.  
  
 Nos editores de Visual c# e Visual Basic, você também pode usar a plataforma de compilador .NET ("Roslyn") para gravar e empacotar seus próprios analisadores de código com ações que exibem lâmpadas automaticamente. Para obter mais informações, consulte:  
  
-   [Como Gravar um c# diagnóstico e correção de código](https://github.com/dotnet/roslyn/wiki/How-To-Write-a-C%23-Analyzer-and-Code-Fix)  
  
-   [Como Gravar um diagnóstico do Visual Basic e correção de código](https://github.com/dotnet/roslyn/wiki/How-To-Write-a-Visual-Basic-Analyzer-and-Code-Fix)  
  
 Outras linguagens, como C++ também fornecem lâmpadas para algumas ações rápidas, como uma sugestão para criar uma implementação de stub dessa função.  
  
 Uma lâmpada é semelhante ao seguinte. Em um projeto do Visual Basic ou Visual c#, um rabisco vermelho é exibido em um nome de variável quando ele é inválido. Quando você passa o mouse sobre o identificador inválido, uma lâmpada é exibida próximo ao cursor.  
  
 ![lâmpada](../extensibility/media/lightbulb.png "LightBulb")  
  
 Se você clicar na seta para baixo por lâmpada, é exibido um conjunto de ações sugeridas, junto com uma visualização da ação selecionada. Nesse caso, ele mostra as alterações que serão feitas no seu código se você executar a ação.  
  
 ![visualização de lâmpada](../extensibility/media/lightbulbpreview.png "LightBulbPreview")  
  
 Você pode usar lâmpadas para fornecer suas próprias ações sugeridas. Por exemplo, você pode fornecer ações para mover a abertura de chaves para uma nova linha ou movê-los para o fim da linha anterior. A instrução a seguir mostra como criar uma lâmpada que aparece na palavra atual e tem duas ações sugeridas: **converter para letras maiusculas** e **converter em letras minúsculas**.  
  
## <a name="prerequisites"></a>Pré-requisitos  
 A partir do Visual Studio 2015, você não instalar o SDK do Visual Studio no Centro de download. Ele está incluído como um recurso opcional na instalação do Visual Studio. Você também pode instalar o SDK do VS posteriormente. Para obter mais informações, consulte [instalar o SDK do Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-managed-extensibility-framework-mef-project"></a>Criando um projeto do Managed Extensibility Framework (MEF)  
  
1.  Crie um projeto c# VSIX. (No **novo projeto** caixa de diálogo, selecione **Visual C# / extensibilidade**, em seguida, **projeto VSIX**.) Nome da solução `LightBulbTest`.  
  
2.  Adicionar uma **Editor classificador** modelo de item ao projeto. Para obter mais informações, consulte [criando uma extensão com um modelo de Item Editor](../extensibility/creating-an-extension-with-an-editor-item-template.md).  
  
3.  Exclua os arquivos de classe existente.  
  
4.  Adicione a seguinte referência ao projeto e defina **Copy Local** para `False`:  
  
     Microsoft.VisualStudio.Language.Intellisense  
  
5.  Adicione um novo arquivo de classe e denomine- **LightBulbTest**.  
  
6.  Adicione o seguinte usando instruções:  
  
    ```csharp  
    using System;  
    using System.Linq;  
    using System.Collections.Generic;  
    using System.Threading.Tasks;  
    using Microsoft.VisualStudio.Language.Intellisense;  
    using Microsoft.VisualStudio.Text;  
    using Microsoft.VisualStudio.Text.Editor;  
    using Microsoft.VisualStudio.Text.Operations;  
    using Microsoft.VisualStudio.Utilities;  
    using System.ComponentModel.Composition;  
    using System.Threading;  
  
    ```  
  
## <a name="implementing-the-light-bulb-source-provider"></a>Implementando o provedor de origem de lâmpada  
  
1.  No arquivo de classe LightBulbTest.cs, exclua a classe LightBulbTest. Adicione uma classe denominada **TestSuggestedActionsSourceProvider** que implementa <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSourceProvider>. Exportá-lo com um nome de **ações sugeridas do teste** e um <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> de "texto".  
  
    ```csharp  
    [Export(typeof(ISuggestedActionsSourceProvider))]  
    [Name("Test Suggested Actions")]  
    [ContentType("text")]  
    internal class TestSuggestedActionsSourceProvider : ISuggestedActionsSourceProvider  
    ```  
  
2.  Dentro da classe do provedor de origem, importar o <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService> e adicioná-lo como uma propriedade.  
  
    ```csharp  
    [Import(typeof(ITextStructureNavigatorSelectorService))]  
    internal ITextStructureNavigatorSelectorService NavigatorService { get; set; }  
    ```  
  
3.  Implementar o <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSourceProvider.CreateSuggestedActionsSource%2A> método para retornar um <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource> objeto. Vamos discutir o código-fonte na próxima seção.  
  
    ```csharp  
    public ISuggestedActionsSource CreateSuggestedActionsSource(ITextView textView, ITextBuffer textBuffer)  
    {  
        if (textBuffer == null && textView == null)  
        {  
            return null;  
        }  
        return new TestSuggestedActionsSource(this, textView, textBuffer);  
    }  
    ```  
  
## <a name="implementing-the-isuggestedactionsource"></a>Implementando o ISuggestedActionSource  
 A origem da ação sugerida é responsável por coletar o conjunto de ações sugeridas e adicioná-los no contexto à direita. Nesse caso, o contexto é a palavra atual e as ações sugeridas são **UpperCaseSuggestedAction** e **LowerCaseSuggestedAction**, que discutiremos na seção a seguir.  
  
1.  Adicionar uma classe **TestSuggestedActionsSource** que implementa <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource>.  
  
    ```csharp  
    internal class TestSuggestedActionsSource : ISuggestedActionsSource  
    ```  
  
2.  Adicione campos particulares de somente leitura para o provedor de origem da ação sugerida, o buffer de texto e a exibição de texto.  
  
    ```csharp  
    private readonly TestSuggestedActionsSourceProvider m_factory;  
    private readonly ITextBuffer m_textBuffer;  
    private readonly ITextView m_textView;  
    ```  
  
3.  Adicione um construtor que define os campos particulares.  
  
    ```csharp  
    public TestSuggestedActionsSource(TestSuggestedActionsSourceProvider testSuggestedActionsSourceProvider, ITextView textView, ITextBuffer textBuffer)  
    {  
        m_factory = testSuggestedActionsSourceProvider;  
        m_textBuffer = textBuffer;  
        m_textView = textView;  
    }  
    ```  
  
4.  Adicione um método privado que retorna a palavra que está sob o cursor. O método a seguir examina o local atual do cursor e solicita que o navegador de estrutura de texto para a extensão do word. Se o cursor estiver em uma palavra, o <xref:Microsoft.VisualStudio.Text.Operations.TextExtent> é retornado no parâmetro out; caso contrário o `out` parâmetro é `null` e o método retornará `false`.  
  
    ```csharp  
    private bool TryGetWordUnderCaret(out TextExtent wordExtent)  
    {  
        ITextCaret caret = m_textView.Caret;  
        SnapshotPoint point;  
  
        if (caret.Position.BufferPosition > 0)  
        {  
            point = caret.Position.BufferPosition - 1;  
        }  
        else  
        {  
            wordExtent = default(TextExtent);  
            return false;  
        }  
  
        ITextStructureNavigator navigator = m_factory.NavigatorService.GetTextStructureNavigator(m_textBuffer);  
  
        wordExtent = navigator.GetExtentOfWord(point);  
        return true;  
    }  
    ```  
  
5.  Implementar o método de <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource.HasSuggestedActionsAsync%2A> . O editor chama esse método para descobrir se deseja exibir lâmpada. Essa chamada é feita com muita frequência, por exemplo, sempre que o cursor se move de uma linha para outro, ou quando o mouse passa sobre um rabisco do erro. É assíncrona para permitir que outras operações de interface do usuário executar enquanto esse método está funcionando. Na maioria dos casos que esse método precisa executar alguma análise e a análise da linha atual, portanto o processamento pode demorar algum tempo.  
  
     Em nossa implementação ele obtém de maneira assíncrona o <xref:Microsoft.VisualStudio.Text.Operations.TextExtent> e determina se a extensão é importante, por exemplo, se ele tem um texto que não seja espaço em branco.  
  
    ```csharp  
    public Task<bool> HasSuggestedActionsAsync(ISuggestedActionCategorySet requestedActionCategories, SnapshotSpan range, CancellationToken cancellationToken)  
    {  
        return Task.Factory.StartNew(() =>  
        {  
            TextExtent extent;  
            if (TryGetWordUnderCaret(out extent))  
            {  
                // don't display the action if the extent has whitespace  
                return extent.IsSignificant;  
              }  
            return false;  
        });  
    }  
    ```  
  
6.  Implementar o <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource.GetSuggestedActions%2A> método, que retorna uma matriz de <xref:Microsoft.VisualStudio.Language.Intellisense.SuggestedActionSet> objetos que contêm diferentes <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedAction> objetos. Esse método é chamado quando a lâmpada é expandida.  
  
    > [!WARNING]
    >  Assegure-se de que as implementações de `HasSuggestedActionsAsync()` e `GetSuggestedActions()` são consistente; é, se `HasSuggestedActionsAsync()` retorna `true`, em seguida, `GetSuggestedActions()` devem ter algumas ações para exibir. Em muitos casos `HasSuggestedActionsAsync()` é chamado antes `GetSuggestedActions()`, mas isso não é sempre o caso. Por exemplo, se o usuário invoca as ações de lâmpada pressionando (CTRL +.) somente `GetSuggestedActions()` é chamado.  
  
    ```csharp  
    public IEnumerable<SuggestedActionSet> GetSuggestedActions(ISuggestedActionCategorySet requestedActionCategories, SnapshotSpan range, CancellationToken cancellationToken)  
    {  
        TextExtent extent;  
        if (TryGetWordUnderCaret(out extent) && extent.IsSignificant)  
        {  
            ITrackingSpan trackingSpan = range.Snapshot.CreateTrackingSpan(extent.Span, SpanTrackingMode.EdgeInclusive);  
            var upperAction = new UpperCaseSuggestedAction(trackingSpan);  
            var lowerAction = new LowerCaseSuggestedAction(trackingSpan);  
            return new SuggestedActionSet[] { new SuggestedActionSet(new ISuggestedAction[] { upperAction, lowerAction }) };  
        }  
        return Enumerable.Empty<SuggestedActionSet>();  
    }   
    ```  
  
7.  Definir um `SuggestedActionsChanged` eventos.  
  
    ```csharp  
    public event EventHandler<EventArgs> SuggestedActionsChanged;  
    ```  
  
8.  Para concluir a implementação, adicione as implementações para o `Dispose()` e `TryGetTelemetryId()` métodos. Não queremos fazer telemetria, portanto, basta retornar false e o GUID do conjunto para vazio.  
  
    ```csharp  
    public void Dispose()  
    {  
    }  
  
    public bool TryGetTelemetryId(out Guid telemetryId)  
    {  
        // This is a sample provider and doesn't participate in LightBulb telemetry  
        telemetryId = Guid.Empty;  
        return false;  
    }  
    ```  
  
## <a name="implementing-light-bulb-actions"></a>Implementação de ações de lâmpada  
  
1.  No projeto, adicione uma referência a Microsoft.VisualStudio.Imaging.Interop.14.0.DesignTime.dll e defina **Copy Local** para `False`.  
  
2.  Crie duas classes, a primeira chamada `UpperCaseSuggestedAction` e a segunda chamada `LowerCaseSuggestedAction`. Ambas as classes implementam <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedAction>.  
  
    ```csharp  
    internal class UpperCaseSuggestedAction : ISuggestedAction   
    internal class LowerCaseSuggestedAction : ISuggestedAction  
    ```  
  
     Ambas as classes são semelhantes, exceto que um chama <xref:System.String.ToUpper%2A> e as outras chamadas <xref:System.String.ToLower%2A>. As etapas a seguir abrangem somente a classe de ação de letras maiusculas, mas você deve implementar ambas as classes. Use as etapas para implementar a ação de letras maiusculas como um padrão para implementar a ação em minúsculas.  
  
3.  Adicione o seguinte usando instruções para essas classes:  
  
    ```csharp  
    using Microsoft.VisualStudio.Imaging.Interop;  
    using System.Windows;  
    using System.Windows.Controls;  
    using System.Windows.Documents;  
    using System.Windows.Media;  
  
    ```  
  
4.  Declare um conjunto de campos particulares.  
  
    ```csharp  
    private ITrackingSpan m_span;  
    private string m_upper;  
    private string m_display;  
    private ITextSnapshot m_snapshot;  
    ```  
  
5.  Adicione um construtor que define os campos.  
  
    ```csharp  
    public UpperCaseSuggestedAction(ITrackingSpan span)  
    {  
        m_span = span;  
        m_snapshot = span.TextBuffer.CurrentSnapshot;  
        m_upper = span.GetText(m_snapshot).ToUpper();  
        m_display = string.Format("Convert '{0}' to upper case", span.GetText(m_snapshot));  
    }  
    ```  
  
6.  Implementar o <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedAction.GetPreviewAsync%2A> método assim que ele exibe a visualização de ação.  
  
    ```csharp  
    public Task<object> GetPreviewAsync(CancellationToken cancellationToken)  
    {  
        var textBlock = new TextBlock();  
        textBlock.Padding = new Thickness(5);  
        textBlock.Inlines.Add(new Run() { Text = m_upper });  
        return Task.FromResult<object>(textBlock);  
    }  
    ```  
  
7.  Implementar o <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedAction.GetActionSetsAsync%2A> método para que retorne um vazio <xref:Microsoft.VisualStudio.Language.Intellisense.SuggestedActionSet> enumeração.  
  
    ```csharp  
    public Task<IEnumerable<SuggestedActionSet>> GetActionSetsAsync(CancellationToken cancellationToken)  
    {  
        return Task.FromResult<IEnumerable<SuggestedActionSet>>(null);  
    }  
    ```  
  
8.  Implemente as propriedades da seguinte maneira.  
  
    ```csharp  
    public bool HasActionSets  
    {  
        get { return false; }  
    }  
    public string DisplayText  
    {  
        get { return m_display; }  
    }  
    public ImageMoniker IconMoniker  
    {  
       get { return default(ImageMoniker); }  
    }  
    public string IconAutomationText  
    {  
        get  
        {  
            return null;  
        }  
    }  
    public string InputGestureText  
    {  
        get  
        {  
            return null;  
        }  
    }  
    public bool HasPreview  
    {  
        get { return true; }  
    }  
    ```  
  
9. Implementar o <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedAction.Invoke%2A> método substituindo o texto no trecho com o seu equivalente em letras maiusculas.  
  
    ```csharp  
    public void Invoke(CancellationToken cancellationToken)  
    {  
        m_span.TextBuffer.Replace(m_span.GetSpan(m_snapshot), m_upper);  
    }  
    ```  
  
    > [!WARNING]
    >  A ação de lâmpada **Invoke** método não é esperado para mostrar a interface do usuário.  Se a ação Exibir nova interface do usuário (por exemplo, um diálogo preview ou seleção), não exibir a interface do usuário diretamente de dentro do **Invoke** método mas em vez disso, agendar para exibir a interface do usuário depois de retornar de **Invoke**.  
  
10. Para concluir a implementação, adicione o `Dispose()` e `TryGetTelemetryId()` métodos.  
  
    ```csharp  
    public void Dispose()  
    {  
    }  
  
    public bool TryGetTelemetryId(out Guid telemetryId)  
    {  
        // This is a sample action and doesn't participate in LightBulb telemetry  
        telemetryId = Guid.Empty;  
        return false;  
    }  
    ```  
  
11. Não se esqueça de fazer o mesmo `LowerCaseSuggestedAction` alterar o texto de exibição para "Converter '{0}' para letras minúsculas" e a chamada <xref:System.String.ToUpper%2A> para <xref:System.String.ToLower%2A>.  
  
## <a name="building-and-testing-the-code"></a>Compilar e testar o código  
 Para testar esse código, compile a solução LightBulbTest e executá-lo na instância Experimental.  
  
1.  Compile a solução.  
  
2.  Quando você executa este projeto no depurador, uma segunda instância do Visual Studio é instanciada.  
  
3.  Crie um arquivo de texto e digite algum texto. Você deve ver uma lâmpada à esquerda do texto.  
  
     ![teste de lâmpada](../extensibility/media/testlightbulb.png "TestLIghtBulb")  
  
4.  Aponte a lâmpada. Você verá uma seta para baixo.  
  
5.  Quando você clica na lâmpada, duas ações sugeridas devem ser exibidas, juntamente com a visualização da ação selecionada.  
  
     ![teste de lâmpada expandida](../extensibility/media/testlightbulbexpanded.gif "TestLIghtBulbExpanded")  
  
6.  Se você clicar na primeira ação, todo o texto da palavra atual deve ser convertido em maiusculas. Se você clicar na segunda ação, todo o texto deve ser convertido em letras minúsculas.  
  
