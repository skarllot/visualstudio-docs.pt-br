---
title: Adicionar pesquisa uma janela de ferramentas | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- tool windows, adding search
ms.assetid: f78c4892-8060-49c4-8ecd-4360f1b4d133
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
ms.sourcegitcommit: bca8c87d4f7d89d491fab13e1a511febce81d3d8
ms.openlocfilehash: 845bbc5c34280f7ceafcaa3d763065f6d73388fe
ms.lasthandoff: 02/22/2017

---
# <a name="adding-search-to-a-tool-window"></a>Adicionando pesquisa a uma janela de ferramentas
Quando você cria ou atualiza uma janela de ferramenta na sua extensão, você pode adicionar a mesma funcionalidade de pesquisa que aparece em outro lugar no Visual Studio. Essa funcionalidade inclui os seguintes recursos:  
  
-   Uma caixa de pesquisa está sempre localizada em uma área personalizada da barra de ferramentas.  
  
-   Um indicador de progresso sobreposto a própria caixa de pesquisa.  
  
-   A capacidade de mostrar os resultados assim que você insere cada caractere (pesquisa instantânea) ou somente depois que você escolhe a tecla Enter (pesquisa sob demanda).  
  
-   Uma lista que mostra os termos para os quais você pesquisou mais recentemente.  
  
-   A capacidade de filtrar pesquisas por campos específicos ou aspectos dos destinos de pesquisa.  
  
 Seguindo este passo a passo, você aprenderá como realizar as seguintes tarefas:  
  
1.  Crie um projeto de VSPackage.  
  
2.  Crie uma janela de ferramenta que contém um UserControl com uma caixa de texto somente leitura.  
  
3.  Adicione uma caixa de pesquisa para a janela da ferramenta.  
  
4.  Adicione a implementação de pesquisa.  
  
5.  Habilite a pesquisa instantânea e a exibição de uma barra de progresso.  
  
6.  Adicionar uma **diferenciar maiusculas de minúsculas** opção.  
  
7.  Adicionar uma **pesquisar apenas linhas pares** filtro.  
  
## <a name="to-create-a-vsix-project"></a>Para criar um projeto do VSIX  
  
1.  Crie um projeto do VSIX chamado `TestToolWindowSearch` com uma janela de ferramenta chamada **TestSearch**. Se você precisar de ajuda para fazer isso, consulte [criando uma extensão com uma janela da ferramenta](../extensibility/creating-an-extension-with-a-tool-window.md).  
  
## <a name="to-create-a-tool-window"></a>Para criar uma janela de ferramentas  
  
1.  No `TestToolWindowSearch` de projeto, abra o arquivo TestSearchControl.xaml.  
  
2.  Substituir o `<StackPanel>` bloco com o seguinte bloco, que adiciona somente leitura <xref:System.Windows.Controls.TextBox>para o <xref:System.Windows.Controls.UserControl>na janela da ferramenta.</xref:System.Windows.Controls.UserControl> </xref:System.Windows.Controls.TextBox>  
  
    ```xaml  
    <StackPanel Orientation="Vertical">  
        <TextBox Name="resultsTextBox" Height="800.0"  
            Width="800.0"  
            IsReadOnly="True">  
        </TextBox>  
    </StackPanel>  
    ```  
  
3.  No arquivo TestSearchControl.xaml.cs, adicione a seguinte instrução using:  
  
    ```c#  
    using System.Text;  
    ```  
  
4.  Remover o `button1_Click()` método.  
  
     No **TestSearchControl** , adicione o código a seguir.  
  
     Este código adiciona um público <xref:System.Windows.Controls.TextBox>propriedade chamada **SearchResultsTextBox** e uma propriedade de cadeia de caracteres pública chamada **SearchContent**.</xref:System.Windows.Controls.TextBox> No construtor, SearchResultsTextBox é definido para a caixa de texto e SearchContent é inicializada com um conjunto de cadeias de caracteres delimitada de nova linha. O conteúdo da caixa de texto também é inicializado com o conjunto de cadeias de caracteres.  
  
    ```c#  
    public partial class TestSearchControl : UserControl  
    {  
        public TextBox SearchResultsTextBox { get; set; }  
        public string SearchContent { get; set; }  
  
        public TestSearchControl()  
        {  
            InitializeComponent();  
  
            this.SearchResultsTextBox = resultsTextBox;  
            this.SearchContent = BuildContent();  
  
            this.SearchResultsTextBox.Text = this.SearchContent;  
        }  
  
        private string BuildContent()  
        {  
            StringBuilder sb = new StringBuilder();  
            sb.AppendLine("1 go");  
            sb.AppendLine("2 good");  
            sb.AppendLine("3 Go");  
            sb.AppendLine("4 Good");  
            sb.AppendLine("5 goodbye");  
            sb.AppendLine("6 Goodbye");  
  
            return sb.ToString();  
        }  
    }  
    ```  
  
     [!code-cs[&#1; ToolWindowSearch](../extensibility/codesnippet/CSharp/adding-search-to-a-tool-window_1.cs) ] 
     [!code-vb [ToolWindowSearch n º&1;](../extensibility/codesnippet/VisualBasic/adding-search-to-a-tool-window_1.vb)]  
  
5.  Compile o projeto e iniciar a depuração. A instância experimental do Visual Studio é exibida.  
  
6.  Na barra de menus, escolha **exibição**, **outras janelas**, **TestSearch**.  
  
     A janela de ferramenta é exibida, mas o controle de pesquisa ainda não aparecer.  
  
## <a name="to-add-a-search-box-to-the-tool-window"></a>Para adicionar uma caixa de pesquisa para a janela da ferramenta  
  
1.  No arquivo TestSearch.cs, adicione o seguinte código para o `TestSearch` classe. O código substitui o <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.SearchEnabled%2A>propriedade para que o acessador get retorna `true`.</xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.SearchEnabled%2A>  
  
     Para habilitar a pesquisa, você deve substituir o <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.SearchEnabled%2A>propriedade.</xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.SearchEnabled%2A> O <xref:Microsoft.VisualStudio.Shell.ToolWindowPane>classe implementa <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch>e fornece uma implementação padrão que não permite a pesquisa.</xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch> </xref:Microsoft.VisualStudio.Shell.ToolWindowPane>  
  
    ```c#  
    public override bool SearchEnabled  
    {  
        get { return true; }  
    }  
    ```  
  
2.  Compile o projeto e iniciar a depuração. A instância experimental aparece.  
  
3.  Na instância experimental do Visual Studio, abra **TestSearch**.  
  
     Na parte superior da janela de ferramenta, um controle de pesquisa é exibida com uma **pesquisa** marca d'água e um ícone de Lente de aumento. No entanto, a pesquisa não funciona ainda porque o processo de pesquisa ainda não foi implementado.  
  
## <a name="to-add-the-search-implementation"></a>Para adicionar a implementação de pesquisa  
 Quando você habilita a pesquisa em um <xref:Microsoft.VisualStudio.Shell.ToolWindowPane>, como no procedimento anterior, a janela da ferramenta cria um host de pesquisa.</xref:Microsoft.VisualStudio.Shell.ToolWindowPane> Esse host configura e gerencia os processos de pesquisa, que sempre ocorrem em um thread em segundo plano. Porque o <xref:Microsoft.VisualStudio.Shell.ToolWindowPane>classe gerencia a criação do host de pesquisa e a configuração de backup da pesquisa, você só precisa criar uma tarefa de pesquisa e fornecem o método search.</xref:Microsoft.VisualStudio.Shell.ToolWindowPane> O processo de pesquisa ocorre em um thread em segundo plano, e chamadas para o controle de janela de ferramenta ocorrerem no thread da interface do usuário. Portanto, você deve usar o <xref:Microsoft.VisualStudio.Shell.ThreadHelper.Invoke%2A>método para gerenciar todas as chamadas feitas ao lidar com o controle.</xref:Microsoft.VisualStudio.Shell.ThreadHelper.Invoke%2A>  
  
1.  No arquivo TestSearch.cs, adicione o seguinte `using` instruções:  
  
    ```c#  
    using System;  
    using System.Collections.Generic;  
    using System.Runtime.InteropServices;  
    using System.Text;  
    using System.Windows.Controls;  
    using Microsoft.Internal.VisualStudio.PlatformUI;  
    using Microsoft.VisualStudio;  
    using Microsoft.VisualStudio.PlatformUI;  
    using Microsoft.VisualStudio.Shell;  
    using Microsoft.VisualStudio.Shell.Interop;  
    ```  
  
2.  No `TestSearch` da classe, adicione o código a seguir, que executa as seguintes ações:  
  
    -   Substitui o <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.CreateSearch>método para criar uma tarefa de pesquisa.</xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.CreateSearch>  
  
    -   Substitui o <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.ClearSearch%2A>método para restaurar o estado da caixa de texto.</xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.ClearSearch%2A> Esse método é chamado quando um usuário cancelou uma tarefa de pesquisa e quando um usuário configura ou desconfigura opções ou filtros. Ambos <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.CreateSearch%2A>e <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.ClearSearch%2A>são chamados no thread da interface do usuário.</xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.ClearSearch%2A> </xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.CreateSearch%2A> Portanto, você não precisa acessar a caixa de texto por meio do <xref:Microsoft.VisualStudio.Shell.ThreadHelper.Invoke%2A>método.</xref:Microsoft.VisualStudio.Shell.ThreadHelper.Invoke%2A>  
  
    -   Cria uma classe chamada `TestSearchTask` que herda de <xref:Microsoft.VisualStudio.Shell.VsSearchTask>, que fornece uma implementação padrão de <xref:Microsoft.VisualStudio.Shell.Interop.IVsSearchTask>.</xref:Microsoft.VisualStudio.Shell.Interop.IVsSearchTask> </xref:Microsoft.VisualStudio.Shell.VsSearchTask>  
  
         Em `TestSearchTask`, o construtor define um campo privado que referencia a janela da ferramenta. Para fornecer o método de pesquisa, você deve substituir o <xref:Microsoft.VisualStudio.Shell.VsSearchTask.OnStartSearch%2A>e <xref:Microsoft.VisualStudio.Shell.VsSearchTask.OnStopSearch%2A>métodos.</xref:Microsoft.VisualStudio.Shell.VsSearchTask.OnStopSearch%2A> </xref:Microsoft.VisualStudio.Shell.VsSearchTask.OnStartSearch%2A> O <xref:Microsoft.VisualStudio.Shell.VsSearchTask.OnStartSearch%2A>método é onde você pode implementar o processo de pesquisa.</xref:Microsoft.VisualStudio.Shell.VsSearchTask.OnStartSearch%2A> Esse processo inclui realizando a pesquisa, exibindo os resultados da pesquisa na caixa de texto e chamar a implementação da classe base desse método para relatar que a pesquisa foi concluída.  
  
    ```c#  
    public override IVsSearchTask CreateSearch(uint dwCookie, IVsSearchQuery pSearchQuery, IVsSearchCallback pSearchCallback)  
    {  
        if (pSearchQuery == null || pSearchCallback == null)  
            return null;  
         return new TestSearchTask(dwCookie, pSearchQuery, pSearchCallback, this);  
    }  
  
    public override void ClearSearch()  
    {  
        TestSearchControl control = (TestSearchControl)this.Content;  
        control.SearchResultsTextBox.Text = control.SearchContent;  
    }  
  
    internal class TestSearchTask : VsSearchTask  
    {  
        private TestSearch m_toolWindow;  
  
        public TestSearchTask(uint dwCookie, IVsSearchQuery pSearchQuery, IVsSearchCallback pSearchCallback, TestSearch toolwindow)  
            : base(dwCookie, pSearchQuery, pSearchCallback)  
        {  
            m_toolWindow = toolwindow;  
        }  
  
        protected override void OnStartSearch()  
        {  
            // Use the original content of the text box as the target of the search.   
            var separator = new string[] { Environment.NewLine };  
            TestSearchControl control = (TestSearchControl)m_toolWindow.Content;  
            string[] contentArr = control.SearchContent.Split(separator, StringSplitOptions.None);  
  
            // Get the search option.   
            bool matchCase = false;  
            // matchCase = m_toolWindow.MatchCaseOption.Value;   
  
                // Set variables that are used in the finally block.  
                StringBuilder sb = new StringBuilder("");  
                uint resultCount = 0;  
                this.ErrorCode = VSConstants.S_OK;  
  
                try  
                {  
                    string searchString = this.SearchQuery.SearchString;  
  
                    // Determine the results.   
                    uint progress = 0;  
                    foreach (string line in contentArr)  
                    {  
                        if (matchCase == true)  
                        {  
                            if (line.Contains(searchString))  
                            {  
                                sb.AppendLine(line);  
                                resultCount++;  
                            }  
                        }  
                        else  
                            {  
                                if (line.ToLower().Contains(searchString.ToLower()))  
                                {  
                                    sb.AppendLine(line);  
                                    resultCount++;  
                                }  
                            }  
  
                            // SearchCallback.ReportProgress(this, progress++, (uint)contentArr.GetLength(0));   
  
                            // Uncomment the following line to demonstrate the progress bar.   
                            // System.Threading.Thread.Sleep(100);  
                        }  
                    }  
                    catch (Exception e)  
                    {  
                        this.ErrorCode = VSConstants.E_FAIL;  
                    }  
                    finally  
                    {  
                        ThreadHelper.Generic.Invoke(() =>  
                        { ((TextBox)((TestSearchControl)m_toolWindow.Content).SearchResultsTextBox).Text = sb.ToString(); });  
  
                        this.SearchResults = resultCount;  
                    }  
  
            // Call the implementation of this method in the base class.   
            // This sets the task status to complete and reports task completion.   
            base.OnStartSearch();  
        }  
  
        protected override void OnStopSearch()  
        {  
            this.SearchResults = 0;  
        }  
    }  
    ```  
  
3.  Teste a implementação de pesquisa, executando as seguintes etapas:  
  
    1.  Recompilar o projeto e iniciar a depuração.  
  
    2.  Na instância experimental do Visual Studio, abra a janela da ferramenta novamente, digite algum texto de pesquisa na janela Pesquisar e clique em ENTER.  
  
         Os resultados corretos devem aparecer.  
  
## <a name="to-customize-the-search-behavior"></a>Para personalizar o comportamento de pesquisa  
 Alterando as configurações de pesquisa, você pode fazer várias alterações na aparência do controle de pesquisa e como a pesquisa é realizada. Por exemplo, você pode alterar a marca d'água (o texto padrão que aparece na caixa de pesquisa), o mínimo e máximo largura do controle de pesquisa e se deseja mostrar uma barra de progresso. Você também pode alterar o ponto no início dos resultados da pesquisa aparecem (sob demanda ou a pesquisa instantânea) e se deseja mostrar uma lista de termos recentemente procurada. Você encontrará a lista completa das configurações de <xref:Microsoft.VisualStudio.PlatformUI.SearchSettingsDataSource>classe.</xref:Microsoft.VisualStudio.PlatformUI.SearchSettingsDataSource>  
  
1.  No arquivo TestSearch.cs, adicione o seguinte código para o `TestSearch` classe. Esse código permite que a pesquisa instantânea, em vez de pesquisa por demanda (significando que o usuário não precisa clicar em ENTER). O código substitui o `ProvideSearchSettings` método o `TestSearch` classe, que é necessário alterar as configurações padrão.  
  
    ```c#  
    public override void ProvideSearchSettings(IVsUIDataSource pSearchSettings)  
    {  
        Utilities.SetValue(pSearchSettings,   
            SearchSettingsDataSource.SearchStartTypeProperty.Name,   
            (uint)VSSEARCHSTARTTYPE.SST_INSTANT);}  
    ```  
  
2.  Testar a nova configuração recompilar a solução e reiniciando o depurador.  
  
     Resultados da pesquisa exibidos toda vez que você inserir um caractere na caixa de pesquisa.  
  
3.  No `ProvideSearchSettings` método, adicione a seguinte linha, que permite a exibição de uma barra de progresso.  
  
    ```c#  
    public override void ProvideSearchSettings(IVsUIDataSource pSearchSettings)  
    {  
        Utilities.SetValue(pSearchSettings,   
            SearchSettingsDataSource.SearchStartTypeProperty.Name,   
             (uint)VSSEARCHSTARTTYPE.SST_INSTANT);  
        Utilities.SetValue(pSearchSettings,   
            SearchSettingsDataSource.SearchProgressTypeProperty.Name,   
             (uint)VSSEARCHPROGRESSTYPE.SPT_DETERMINATE);  
    }  
    ```  
  
     Para a barra de progresso seja exibida, o andamento deve ser relatado. Para relatar o progresso, remova o seguinte código no `OnStartSearch` método o `TestSearchTask` classe:  
  
    ```c#  
    SearchCallback.ReportProgress(this, progress++, (uint)contentArr.GetLength(0));  
    ```  
  
4.  Diminuir o progresso de processamento suficiente para que a barra está visível, remova a seguinte linha a `OnStartSearch` método o `TestSearchTask` classe:  
  
    ```c#  
    System.Threading.Thread.Sleep(100);  
    ```  
  
5.  Teste as novas configurações de recompilar a solução e iniciando a debugb.  
  
     A barra de progresso é exibida na janela de pesquisa (como uma linha azul abaixo da caixa de texto de pesquisa) toda vez que você realiza uma pesquisa.  
  
## <a name="to-enable-users-to-refine-their-searches"></a>Habilitar usuários a refinar suas pesquisas  
 Você pode permitir que os usuários a refinar suas pesquisas por meio de opções como **diferenciar maiusculas de minúsculas** ou **coincidir palavra inteira**. Opções podem ser boolianos, que aparecem como caixas de seleção ou comandos, que aparecem como botões. Para este passo a passo, você criará uma opção boolean.  
  
1.  No arquivo TestSearch.cs, adicione o seguinte código para o `TestSearch` classe. O código substitui o `SearchOptionsEnum` método, que permite a implementação de pesquisa detectar se uma determinada opção está ativada ou desativada. O código na `SearchOptionsEnum` adiciona uma opção para diferenciar maiusculas de minúsculas para um <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumWindowSearchOptions>enumerador.</xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumWindowSearchOptions> A opção para diferenciar maiusculas de minúsculas também é disponibilizada como o `MatchCaseOption` propriedade.  
  
    ```c#  
    private IVsEnumWindowSearchOptions m_optionsEnum;  
    public override IVsEnumWindowSearchOptions SearchOptionsEnum  
    {  
        get  
        {  
            if (m_optionsEnum == null)  
            {  
                List<IVsWindowSearchOption> list = new List<IVsWindowSearchOption>();  
  
                list.Add(this.MatchCaseOption);  
  
                m_optionsEnum = new WindowSearchOptionEnumerator(list) as IVsEnumWindowSearchOptions;  
            }  
            return m_optionsEnum;  
        }  
    }  
  
    private WindowSearchBooleanOption m_matchCaseOption;  
    public WindowSearchBooleanOption MatchCaseOption  
    {  
        get  
        {  
            if (m_matchCaseOption == null)  
            {  
                m_matchCaseOption = new WindowSearchBooleanOption("Match case", "Match case", false);  
            }  
            return m_matchCaseOption;  
        }  
    }  
    ```  
  
2.  No `TestSearchTask` classe, remova o comentário de linha matchCase o `OnStartSearch` método:  
  
    ```c#  
    private IVsEnumWindowSearchOptions m_optionsEnum;  
    public override IVsEnumWindowSearchOptions SearchOptionsEnum  
    {  
        get  
        {  
            if (m_optionsEnum == null)  
            {  
                List<IVsWindowSearchOption> list = new List<IVsWindowSearchOption>();  
  
                list.Add(this.MatchCaseOption);  
  
                m_optionsEnum = new WindowSearchOptionEnumerator(list) as IVsEnumWindowSearchOptions;  
            }  
            return m_optionsEnum;  
        }  
    }  
  
    private WindowSearchBooleanOption m_matchCaseOption;  
    public WindowSearchBooleanOption MatchCaseOption  
    {  
        get  
         {  
            if (m_matchCaseOption == null)  
            {  
                m_matchCaseOption = new WindowSearchBooleanOption("Match case", "Match case", false);  
            }  
            return m_matchCaseOption;  
        }  
    }  
    ```  
  
3.  A opção de teste:  
  
    1.  Compile o projeto e iniciar a depuração. A instância experimental aparece.  
  
    2.  Na janela da ferramenta, escolha a seta para baixo no lado direito da caixa de texto.  
  
         O **diferenciar maiusculas de minúsculas** caixa de seleção é exibida.  
  
    3.  Selecione o **diferenciar maiusculas de minúsculas** caixa de seleção e, em seguida, executar algumas pesquisas.  
  
## <a name="to-add-a-search-filter"></a>Para adicionar um filtro de pesquisa  
 Você pode adicionar filtros de pesquisa que permitem aos usuários refinar o conjunto de destinos de pesquisa. Por exemplo, você pode filtrar arquivos no Explorador de arquivos, as datas em que foram modificados recentemente e as extensões de nome de arquivo. Este passo a passo, você adicionará um filtro para apenas linhas pares. Quando o usuário escolhe o filtro, o host de pesquisa adiciona as cadeias de caracteres que você especificar para a consulta de pesquisa. Você pode identificar essas cadeias de caracteres dentro do método de pesquisa e filtrar os destinos de pesquisa adequadamente.  
  
1.  No arquivo TestSearch.cs, adicione o seguinte código para o `TestSearch` classe. O código implementa `SearchFiltersEnum` adicionando um <xref:Microsoft.VisualStudio.PlatformUI.WindowSearchSimpleFilter>que especifica para filtrar os resultados da pesquisa para que sejam exibidos apenas linhas pares.</xref:Microsoft.VisualStudio.PlatformUI.WindowSearchSimpleFilter>  
  
    ```c#  
    public override IVsEnumWindowSearchFilters SearchFiltersEnum  
    {  
        get  
        {  
            List<IVsWindowSearchFilter> list = new List<IVsWindowSearchFilter>();  
            list.Add(new WindowSearchSimpleFilter("Search even lines only", "Search even lines only", "lines", "even"));  
            return new WindowSearchFilterEnumerator(list) as IVsEnumWindowSearchFilters;  
        }  
    }  
  
    ```  
  
     Agora o controle de pesquisa exibe o filtro de pesquisa `Search even lines only`. Quando o usuário escolhe o filtro, a cadeia de caracteres `lines:"even"` aparece na caixa de pesquisa. Outros critérios de pesquisa podem aparecer ao mesmo tempo como o filtro. Cadeias de caracteres de pesquisa podem aparecer antes do filtro, após o filtro, ou ambos.  
  
2.  No arquivo TestSearch.cs, adicione os seguintes métodos para o `TestSearchTask` classe, que é o `TestSearch` classe. Esses métodos aceitam o `OnStartSearch` método, que você modificará na próxima etapa.  
  
    ```c#  
    private string RemoveFromString(string origString, string stringToRemove)  
    {  
        int index = origString.IndexOf(stringToRemove);  
        if (index == -1)  
            return origString;  
        else   
             return (origString.Substring(0, index) + origString.Substring(index + stringToRemove.Length)).Trim();  
    }  
  
    private string[] GetEvenItems(string[] contentArr)  
    {  
        int length = contentArr.Length / 2;  
        string[] evenContentArr = new string[length];  
  
        int indexB = 0;  
        for (int index = 1; index < contentArr.Length; index += 2)  
        {  
            evenContentArr[indexB] = contentArr[index];  
            indexB++;  
        }  
  
        return evenContentArr;  
    }  
    ```  
  
3.  No `TestSearchTask` classe, atualize o `OnStartSearch` método com o código a seguir. Essa alteração atualiza o código para suportar o filtro.  
  
    ```c#  
    protected override void OnStartSearch()  
    {  
        // Use the original content of the text box as the target of the search.   
        var separator = new string[] { Environment.NewLine };  
        string[] contentArr = ((TestSearchControl)m_toolWindow.Content).SearchContent.Split(separator, StringSplitOptions.None);  
  
        // Get the search option.   
        bool matchCase = false;  
        matchCase = m_toolWindow.MatchCaseOption.Value;  
  
        // Set variables that are used in the finally block.  
        StringBuilder sb = new StringBuilder("");  
        uint resultCount = 0;  
        this.ErrorCode = VSConstants.S_OK;  
  
        try  
        {  
            string searchString = this.SearchQuery.SearchString;  
  
            // If the search string contains the filter string, filter the content array.   
            string filterString = "lines:\"even\"";  
  
            if (this.SearchQuery.SearchString.Contains(filterString))  
            {  
                // Retain only the even items in the array.  
                contentArr = GetEvenItems(contentArr);  
  
                // Remove 'lines:"even"' from the search string.  
                searchString = RemoveFromString(searchString, filterString);  
            }  
  
            // Determine the results.   
            uint progress = 0;  
            foreach (string line in contentArr)  
            {  
                if (matchCase == true)  
                {  
                    if (line.Contains(searchString))  
                    {  
                        sb.AppendLine(line);  
                        resultCount++;  
                    }  
                }  
                else  
                {  
                    if (line.ToLower().Contains(searchString.ToLower()))  
                    {  
                        sb.AppendLine(line);  
                        resultCount++;  
                    }  
                }  
  
                SearchCallback.ReportProgress(this, progress++, (uint)contentArr.GetLength(0));  
  
                // Uncomment the following line to demonstrate the progress bar.   
                // System.Threading.Thread.Sleep(100);  
            }  
        }  
        catch (Exception e)  
        {  
            this.ErrorCode = VSConstants.E_FAIL;  
        }  
        finally  
        {  
            ThreadHelper.Generic.Invoke(() =>  
            { ((TextBox)((TestSearchControl)m_toolWindow.Content).SearchResultsTextBox).Text = sb.ToString(); });  
  
            this.SearchResults = resultCount;  
        }  
  
        // Call the implementation of this method in the base class.   
        // This sets the task status to complete and reports task completion.   
        base.OnStartSearch();  
    }  
    ```  
  
4.  Teste seu código.  
  
5.  Compile o projeto e iniciar a depuração. Na instância experimental do Visual Studio, abra a janela da ferramenta e, em seguida, escolha a seta para baixo no controle de pesquisa.  
  
     O **diferenciar maiusculas de minúsculas** caixa de seleção e o **pesquisar apenas linhas pares** filtro aparecem.  
  
6.  Escolha o filtro.  
  
     A caixa de pesquisa contém **linhas: "mesmo"**, e os seguintes resultados são exibidos:  
  
     boa&2;  
  
     4 BOM  
  
     Adeus&6;  
  
7.  Excluir `lines:"even"` na caixa de pesquisa, selecione o **diferenciar maiusculas de minúsculas** caixa de seleção e, em seguida, digite `g` na caixa de pesquisa.  
  
     São exibidos os seguintes resultados:  
  
     ir de&1;  
  
     boa&2;  
  
     adeus&5;  
  
8.  Escolha o X no lado direito da caixa de pesquisa.  
  
     A pesquisa está desmarcada e o conteúdo original é exibido. No entanto, o **diferenciar maiusculas de minúsculas** caixa de seleção ainda está selecionada.
