---
title: "Passo a passo: Exibindo sugestões de lâmpada | Documentos do Microsoft"
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
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: e3838b7f9161991840bc5498f66abcfd3ce2b248
ms.lasthandoff: 02/22/2017

---
# <a name="walkthrough-displaying-light-bulb-suggestions"></a>Passo a passo: Exibindo sugestões de lâmpada
As lâmpadas são ícones usados no editor do Visual Studio que expanda para exibir um conjunto de ações, por exemplo, correções de problemas identificados pelo analisadores de código internos ou refatoração de código.  
  
 Nos editores do Visual c# e Visual Basic, você também pode usar o .NET Compiler Platform ("Roslyn") para gravar e empacotar seus próprios analisadores de código com ações que exibem as lâmpadas automaticamente. Para obter mais informações, consulte:  
  
-   [Como: Gravar um c# diagnóstico e correção de código](https://github.com/dotnet/roslyn/wiki/How-To-Write-a-C%23-Analyzer-and-Code-Fix)  
  
-   [Como: Gravar um diagnóstico do Visual Basic e correção de código](https://github.com/dotnet/roslyn/wiki/How-To-Write-a-Visual-Basic-Analyzer-and-Code-Fix)  
  
 Outras linguagens, como C++ também oferecem lâmpadas para algumas ações rápidas, como uma sugestão para criar uma implementação de stub dessa função.  
  
 Uma lâmpada é semelhante ao seguinte. Em um projeto Visual Basic ou Visual c#, um rabisco vermelho aparece em um nome de variável quando ela é inválida. Quando você passa o mouse sobre o identificador inválido, uma lâmpada é exibida próximo ao cursor.  
  
 ![lâmpada](~/extensibility/media/lightbulb.png "lâmpada")  
  
 Se você clicar na seta para baixo, a lâmpada, é exibido um conjunto de ações sugeridas, junto com uma visualização da ação selecionada. Nesse caso, ele mostra as alterações que serão feitas no seu código se você executar a ação.  
  
 ![visualização de lâmpada](~/extensibility/media/lightbulbpreview.png "LightBulbPreview")  
  
 Você pode usar as lâmpadas para fornecer suas próprias ações sugeridas. Por exemplo, você pode fornecer ações para mover as chaves para uma nova linha de abertura ou movê-los para o final da linha anterior. A instrução a seguir mostra como criar uma lâmpada aparece na palavra atual e tem duas ações sugeridas: **converter em maiusculas** e **converter em letras minúsculas**.  
  
## <a name="prerequisites"></a>Pré-requisitos  
 A partir do Visual Studio 2015, você não instale o SDK do Visual Studio no Centro de download. Ele é fornecido como um recurso opcional na instalação do Visual Studio. Você também pode instalar o SDK do VS mais tarde. Para obter mais informações, consulte [instalar o SDK do Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-managed-extensibility-framework-mef-project"></a>Criando um projeto do Managed Extensibility Framework (MEF)  
  
1.  Crie um projeto c# VSIX. (No **novo projeto** caixa de diálogo, selecione **Visual c# / extensibilidade**, em seguida, **projeto VSIX**.) Nomeie a solução `LightBulbTest`.  
  
2.  Adicionar uma **Editor classificador** modelo de item ao projeto. Para obter mais informações, consulte [criando uma extensão com um modelo de Item Editor](../extensibility/creating-an-extension-with-an-editor-item-template.md).  
  
3.  Exclua os arquivos de classe existentes.  
  
4.  Adicione a seguinte referência ao projeto e defina **Copy Local** para `False`:  
  
     Microsoft.VisualStudio.Language.Intellisense  
  
5.  Adicione um novo arquivo de classe e denomine- **LightBulbTest**.  
  
6.  Adicione as seguintes instruções using:  
  
    ```c#  
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
  
1.  No arquivo de classe LightBulbTest.cs, exclua a classe LightBulbTest. Adicione uma classe chamada **TestSuggestedActionsSourceProvider** que implementa <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSourceProvider>.</xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSourceProvider> Exportá-lo com um nome de **ações sugeridas do teste** e um <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>de "text".</xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>  
  
    ```c#  
    [Export(typeof(ISuggestedActionsSourceProvider))]  
    [Name("Test Suggested Actions")]  
    [ContentType("text")]  
    internal class TestSuggestedActionsSourceProvider : ISuggestedActionsSourceProvider  
    ```  
  
2.  Dentro da classe do provedor de origem, importe o <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService>e adicioná-la como uma propriedade.</xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService>  
  
    ```c#  
    [Import(typeof(ITextStructureNavigatorSelectorService))]  
    internal ITextStructureNavigatorSelectorService NavigatorService { get; set; }  
    ```  
  
3.  Implementar o <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSourceProvider.CreateSuggestedActionsSource%2A>método retorne um <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource>objeto.</xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource> </xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSourceProvider.CreateSuggestedActionsSource%2A> Discutiremos a fonte na próxima seção.  
  
    ```c#  
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
 A origem da ação sugerida é responsável por coletar o conjunto de ações sugeridas e adicioná-los no contexto certo. Nesse caso, o contexto é a palavra atual e as ações sugeridas são **UpperCaseSuggestedAction** e **LowerCaseSuggestedAction**, que discutiremos na seção a seguir.  
  
1.  Adicione uma classe **TestSuggestedActionsSource** que implementa <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource>.</xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource>  
  
    ```c#  
    internal class TestSuggestedActionsSource : ISuggestedActionsSource  
    ```  
  
2.  Adicione campos privados de somente leitura para o provedor de origem de ação sugerida, o buffer de texto e a exibição de texto.  
  
    ```c#  
    private readonly TestSuggestedActionsSourceProvider m_factory;  
    private readonly ITextBuffer m_textBuffer;  
    private readonly ITextView m_textView;  
    ```  
  
3.  Adicione um construtor que define os campos particulares.  
  
    ```c#  
    public TestSuggestedActionsSource(TestSuggestedActionsSourceProvider testSuggestedActionsSourceProvider, ITextView textView, ITextBuffer textBuffer)  
    {  
        m_factory = testSuggestedActionsSourceProvider;  
        m_textBuffer = textBuffer;  
        m_textView = textView;  
    }  
    ```  
  
4.  Adicione um método particular que retorna a palavra que está sob o cursor. O método a seguir examina o local atual do cursor e solicita que o navegador de estrutura de texto para a extensão da palavra. Se o cursor estiver em uma palavra, o <xref:Microsoft.VisualStudio.Text.Operations.TextExtent>é retornado no parâmetro de saída; caso contrário, o `out` parâmetro é `null` e o método retornará `false`.</xref:Microsoft.VisualStudio.Text.Operations.TextExtent>  
  
    ```c#  
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
  
5.  Implementar o <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource.HasSuggestedActionsAsync%2A>método.</xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource.HasSuggestedActionsAsync%2A> O editor chama esse método para descobrir se exibir a lâmpada. Essa chamada é feita com muita frequência, por exemplo, sempre que o cursor se move de uma linha para outra, ou quando o mouse passa sobre um rabisco de erro. É assíncrona para permitir que outras operações de interface do usuário executar enquanto esse método está funcionando. Na maioria dos casos que esse método precisa executar alguma análise e análise da linha atual, então o processamento pode levar algum tempo.  
  
     Em nossa implementação assíncrona obtém o <xref:Microsoft.VisualStudio.Text.Operations.TextExtent>e determina se a extensão é significativa, ou seja, se ele tem algum texto que não seja espaço em branco.</xref:Microsoft.VisualStudio.Text.Operations.TextExtent>  
  
    ```c#  
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
  
6.  Implementar o <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource.GetSuggestedActions%2A>método, que retorna uma matriz de <xref:Microsoft.VisualStudio.Language.Intellisense.SuggestedActionSet>objetos que contêm diferentes <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedAction>objetos.</xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedAction> </xref:Microsoft.VisualStudio.Language.Intellisense.SuggestedActionSet> </xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource.GetSuggestedActions%2A> Esse método é chamado quando a lâmpada é expandida.  
  
    > [!WARNING]
    >  Assegure-se de que as implementações de `HasSuggestedActionsAsync()` e `GetSuggestedActions()` são consistente; é, se `HasSuggestedActionsAsync()` retorna `true`, em seguida, `GetSuggestedActions()` deve ter algumas ações a serem exibidas. Em muitos casos `HasSuggestedActionsAsync()` é chamado pouco antes `GetSuggestedActions()`, mas isso não é sempre o caso. Por exemplo, se o usuário invoca as ações de lâmpada pressionando (CTRL +.) só `GetSuggestedActions()` é chamado.  
  
    ```c#  
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
  
    ```c#  
    public event EventHandler<EventArgs> SuggestedActionsChanged;  
    ```  
  
8.  Para concluir a implementação, adicionar implementações para o `Dispose()` e `TryGetTelemetryId()` métodos. Não queremos fazer telemetria, portanto, basta retornar false e o GUID do conjunto de vazio.  
  
    ```c#  
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
  
## <a name="implementing-light-bulb-actions"></a>Implementando a lâmpada ações  
  
1.  No projeto, adicione uma referência ao Microsoft.VisualStudio.Imaging.Interop.14.0.DesignTime.dll e defina **Copy Local** para `False`.  
  
2.  Crie duas classes, a primeira chamada `UpperCaseSuggestedAction` e a segunda chamada `LowerCaseSuggestedAction`. Ambas as classes implementam <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedAction>.</xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedAction>  
  
    ```c#  
    internal class UpperCaseSuggestedAction : ISuggestedAction   
    internal class LowerCaseSuggestedAction : ISuggestedAction  
    ```  
  
     Ambas as classes são semelhantes, exceto que um chama <xref:System.String.ToUpper%2A>e as outras chamadas <xref:System.String.ToLower%2A>.</xref:System.String.ToLower%2A> </xref:System.String.ToUpper%2A> As etapas a seguir abrangem apenas a classe de ação em maiusculas, mas você deve implementar ambas as classes. Use as etapas para implementar a ação maiusculas como um padrão para implementar a ação em minúsculas.  
  
3.  Adicione as seguintes instruções using para essas classes:  
  
    ```c#  
    using Microsoft.VisualStudio.Imaging.Interop;  
    using System.Windows;  
    using System.Windows.Controls;  
    using System.Windows.Documents;  
    using System.Windows.Media;  
  
    ```  
  
4.  Declare um conjunto de campos particulares.  
  
    ```c#  
    private ITrackingSpan m_span;  
    private string m_upper;  
    private string m_display;  
    private ITextSnapshot m_snapshot;  
    ```  
  
5.  Adicione um construtor que define os campos.  
  
    ```c#  
    public UpperCaseSuggestedAction(ITrackingSpan span)  
    {  
        m_span = span;  
        m_snapshot = span.TextBuffer.CurrentSnapshot;  
        m_upper = span.GetText(m_snapshot).ToUpper();  
        m_display = string.Format("Convert '{0}' to upper case", span.GetText(m_snapshot));  
    }  
    ```  
  
6.  Implementar o <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedAction.GetPreviewAsync%2A>método para que ele exiba a visualização de ação.</xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedAction.GetPreviewAsync%2A>  
  
    ```c#  
    public Task<object> GetPreviewAsync(CancellationToken cancellationToken)  
    {  
        var textBlock = new TextBlock();  
        textBlock.Padding = new Thickness(5);  
        textBlock.Inlines.Add(new Run() { Text = m_upper });  
        return Task.FromResult<object>(textBlock);  
    }  
    ```  
  
7.  Implementar o <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedAction.GetActionSetsAsync%2A>método para que retorne um vazio <xref:Microsoft.VisualStudio.Language.Intellisense.SuggestedActionSet>enumeração.</xref:Microsoft.VisualStudio.Language.Intellisense.SuggestedActionSet> </xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedAction.GetActionSetsAsync%2A>  
  
    ```c#  
    public Task<IEnumerable<SuggestedActionSet>> GetActionSetsAsync(CancellationToken cancellationToken)  
    {  
        return Task.FromResult<IEnumerable<SuggestedActionSet>>(null);  
    }  
    ```  
  
8.  Implemente as propriedades da seguinte maneira.  
  
    ```c#  
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
  
9. Implementar o <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedAction.Invoke%2A>método substituindo o texto na extensão com seu equivalente maiusculo.</xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedAction.Invoke%2A>  
  
    ```c#  
    public void Invoke(CancellationToken cancellationToken)  
    {  
        m_span.TextBuffer.Replace(m_span.GetSpan(m_snapshot), m_upper);  
    }  
    ```  
  
    > [!WARNING]
    >  A ação de lâmpada **Invoke** método não deve mostrar interface do usuário.  Se a ação exibir a nova interface do usuário (por exemplo, um diálogo Visualização ou seleção), não exibir a interface do usuário diretamente de dentro do **Invoke** método, mas em vez disso, agendar para exibir a interface do usuário depois de retornar do **Invoke**.  
  
10. Para concluir a implementação, adicione a `Dispose()` e `TryGetTelemetryId()` métodos.  
  
    ```c#  
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
  
11. Não se esqueça de fazer a mesma coisa para `LowerCaseSuggestedAction` alterando o texto de exibição "Converter '{0}' em letras minúsculas" e a chamada <xref:System.String.ToUpper%2A>para <xref:System.String.ToLower%2A>.</xref:System.String.ToLower%2A> </xref:System.String.ToUpper%2A>  
  
## <a name="building-and-testing-the-code"></a>Compilar e testar o código  
 Para testar esse código, crie a solução LightBulbTest e executá-lo na instância Experimental.  
  
1.  Compile a solução.  
  
2.  Quando você executa este projeto no depurador, uma segunda instância do Visual Studio é instanciada.  
  
3.  Crie um arquivo de texto e digite algum texto. Você deve ver uma lâmpada à esquerda do texto.  
  
     ![testar a lâmpada](~/extensibility/media/testlightbulb.png "TestLIghtBulb")  
  
4.  Aponte para a lâmpada. Você deve ver uma seta para baixo.  
  
5.  Quando você clica na lâmpada, duas ações sugeridas devem ser exibidas, juntamente com a visualização da ação selecionada.  
  
     ![testar a lâmpada, expandida](~/extensibility/media/testlightbulbexpanded.gif "TestLIghtBulbExpanded")  
  
6.  Se você clicar na primeira ação, todo o texto na palavra atual deve ser convertido em letras maiusculas. Se você clicar na segunda ação, todo o texto deve ser convertido em letras minúsculas.
