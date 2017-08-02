---
title: Cores e estilos para o Visual Studio | Microsoft Docs
ms.custom: 
ms.date: 04/26/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0e384ea1-4d9e-4307-8884-6e183900732c
caps.latest.revision: 4
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9524ecc3cadef58821fba857de8e82e59eea9b43
ms.openlocfilehash: 93bfad7dc919364770a7d225c09db8b432cf1be0
ms.contentlocale: pt-br
ms.lasthandoff: 05/04/2017

---
# <a name="colors-and-styling-for-visual-studio"></a>Cores e estilos para o Visual Studio
## <a name="using-color-in-visual-studio"></a>Usando a cor do Visual Studio  
No Visual Studio, a cor é usada principalmente como uma ferramenta de comunicação, não apenas como decoração. Usar cor minimamente e reservá-lo para situações em que você deseja:  
  
-   Se comunicam significado ou afiliação (por exemplo, modificadores de plataforma ou idioma)  
  
-   Atrair atenção (por exemplo, indicando uma alteração de status)  
  
-   Melhorar a legibilidade e fornecer pontos de referência para a interface do usuário de navegação  
  
-   Aumentar a finalidade  
  
Existem várias opções para a atribuição de cores para elementos de interface do usuário no Visual Studio. Às vezes, pode ser difícil figura para qual opção você deverá para usar ou como usá-la corretamente. Este tópico o ajudará a:  
  
1.  Entenda os diferentes serviços e sistemas usados para definir as cores no Visual Studio.  
  
2.  Selecione a opção correta para um determinado elemento.  
  
3.  Corretamente, use a opção que você escolheu.  
  
> **Observação:** nunca codificar hex, RGB ou cores do sistema para os elementos de interface do usuário. Usar os serviços permite flexibilidade no ajuste de matiz. Além disso, sem o serviço, você não poderá se beneficiar dos recursos de troca de tema de [o serviço de VSColor](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_TheVSColorService).
  
### <a name="methods-for-assigning-color-to-visual-studio-interface-elements"></a>Métodos para atribuir cores a elementos de interface do Visual Studio  
Escolha o método mais adequado para os elementos de interface do usuário.  
  
| A interface do usuário | Método | O que são? |  
| --- | --- | --- |  
| Você ter inserido ou caixas de diálogo autônomo. | **Cores do sistema** | Nomes de sistema que permitem que o sistema operacional definir a cor e a aparência dos elementos da interface do usuário, como controles de caixa de diálogo comuns. |
| Interface do usuário personalizada que você deseja que sejam consistentes com o ambiente do VS geral e tiver elementos de interface do usuário que correspondem a categoria e o significado semântico dos tokens compartilhados. | **Cores compartilhadas comuns** | Nomes de token de cor predefinidos existentes para elementos de interface do usuário específicos |
| Você tem um recurso individual ou um grupo de recursos e não há nenhuma cor compartilhado para elementos semelhantes. | **Cores personalizadas** | Nomes de token de cores que são específicos para uma área e não se destina a ser compartilhado com outra interface de usuário |
| Você deseja permitir que o usuário final personalizar o conteúdo ou a interface do usuário (por exemplo, para editores de texto ou janelas de designer especializadas). | **Personalização do usuário final**<br /><br />**(Ferramentas de &gt; caixa de diálogo Opções)** | As configurações definidas na página "Fontes e cores" do **ferramentas &gt; opções** caixa de diálogo ou uma página especializada específica para um recurso de interface do usuário. |
| Você tem a interface do usuário que é criado no HTML. | **Daytona** | Permite que a interface do usuário criado em HTML para acessar o serviço de fonte e cor. |
  
### <a name="visual-studio-themes"></a>Temas do Visual Studio  
O Visual Studio apresenta três temas de cores diferentes: azul claro e escuro. Ela também detecta o modo de alto contraste, o que é um tema de cores de todo o sistema projetado para acessibilidade.  
  
Os usuários são solicitados a selecionar um tema durante seu primeiro uso do Visual Studio e pode alternar os temas mais tarde, acessando a **ferramentas &gt; opções &gt; ambiente &gt; geral** e escolhendo um novo tema no menu suspenso "tema de cores".  
  
Usuários também podem usar o painel de controle para alternar os sistemas inteiros em um dos vários temas de alto contraste. Se um usuário selecionar um tema de alto contraste, em seguida, o seletor de tema de cores do Visual Studio não afeta mais cores no Visual Studio, embora as alterações de tema serão salvas para quando o usuário sai do modo de alto contraste. Para obter mais informações sobre o modo de alto contraste, consulte [cores escolhendo alto contraste](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_ChoosingHighContrastColors).
  
### <a name="the-vscolor-service"></a>O serviço VSColor  
O Visual Studio fornece um serviço de cor ambiente, conhecido como o serviço de VSColor, que permite que você vincule os valores de cor de seus elementos de interface do usuário a uma entrada nomeada que contém os valores de cor para cada tema do Visual Studio. Isso garante que as cores serão alterado automaticamente para refletir o modo atual de alto contraste de sistema ou tema selecionado pelo usuário. Uso do serviço significa que a implementação de todas as alterações de tema relacionadas à cor é tratada em um único local, e se você estiver usando cores compartilhadas comuns do serviço, a interface do usuário refletem automaticamente novos temas em versões futuras do Visual Studio.  
  
### <a name="implementation"></a>Implementação  
O código de origem do Visual Studio inclui vários arquivos de definição de pacote que contêm listas de nomes de token e os valores de cor do respectivos para cada tema. O serviço de cor lê o VSColors definidas nesses arquivos de definição de pacote. Essas cores são referenciadas na marcação XAML ou em código e, em seguida, carregadas por meio de `IVsUIShell5.GetThemedColor` método ou um mapeamento DynamicResource.  
  
### <a name="system-colors"></a>Cores do sistema  
Controles comuns referenciam as cores do sistema por padrão. Se você quiser que a interface do usuário para usar cores do sistema, como quando você estiver criando uma caixa de diálogo autônomo ou inserida, você não precisa fazer nada.  
  
### <a name="common-shared-colors-in-the-vscolor-service"></a>Cores compartilhadas comuns no serviço VSColor  
Os elementos de interface devem refletir o ambiente geral do Visual Studio. Ao reutilizar as cores comuns compartilhadas que são apropriadas para o componente da interface do usuário que você está criando, você pode garantir que a interface é consistente com outras interfaces do Visual Studio, e que as cores serão atualizadas automaticamente quando os temas são adicionados ou atualizados.  
  
Antes de usar cores compartilhadas comuns, certifique-se de que você compreenda como usá-los corretamente. Uso incorreto da cores compartilhados comuns pode resultar em uma experiência inconsistente, frustrante ou confusa para seus usuários.  
  
### <a name="user-customizable-colors"></a>Cores personalizadas pelo usuário  
Consulte: [exposição de cores para os usuários finais](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_ExposingColorsForEndUsers)  
  
Às vezes, convém permitir que o usuário final personalizar a interface do usuário, como quando você estiver criando um editor de código ou a superfície de design. Componentes de interface de usuário personalizáveis são encontrados no **fontes e cores** seção o **ferramentas &gt; opções** caixa de diálogo, em que os usuários podem escolher para alterar a cor de primeiro plano, cor de plano de fundo ou ambos.  
  
![Ferramentas &gt; caixa de diálogo Opções](../../extensibility/ux-guidelines/media/0301-a_toolsoptionsdialog.png "0301-a_ToolsOptionsDialog")<br />Ferramentas &gt; caixa de diálogo Opções
  
### <a name="web-ui-colors"></a>Cores de interface do usuário da Web  
Ele está se tornando comuns para criar componentes de interface do usuário usando HTML para que eles podem ser usados no Visual Studio Online e no Visual Studio. Interface do usuário, escrito em HTML ainda deve usar o serviço VSColor quando é executado dentro do ambiente do Visual Studio. Para obter informações sobre Daytona e como usá-lo, consulte [Daytona e web da interface do usuário](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_DaytonaAndWebUI).  
  
##  <a name="BKMK_TheVSColorService"></a>O serviço VSColor  
Visual Studio fornece um serviço de cor ambiente, também chamado de VSColor ou o serviço de cor do shell. Esse serviço permite que você vincule os valores de cor de seus elementos de interface do usuário a um conjunto que contém cores para cada tema de cores de nome-valor. O serviço de VSColor deve ser usado para todos os elementos de interface do usuário, para que as cores automaticamente alterado para refletir o tema atual do usuário selecionado e para que a interface do usuário associado ao serviço de cor ambiente integra-se ao novo temas em futuras versões do Visual Studio.  
  
### <a name="how-the-service-works"></a>Como funciona o serviço  
O serviço de cor ambiente lê que vscolors definido em .pkgdef para o componente de interface do usuário. Essas VSColors são referenciados na marcação XAML ou código e são carregados por meio de `IVsUIShell5.GetThemedColor` ou um `DynamicResource` mapeamento.  
  
![Arquitetura de serviço de cor do ambiente](../../extensibility/ux-guidelines/media/0302-a_environmentcolorservicearchitecture.png "0302-a_EnvironmentColorServiceArchitecture")<br />Arquitetura de serviço de cor do ambiente
  
### <a name="accessing-the-service"></a>Acessando o serviço
Há várias maneiras diferentes para acessar o serviço VSColor, dependendo de qual tipo de cor tokens que você está usando e tipo de código que você tem.  

#### <a name="predefined-environment-colors"></a>Cores de ambiente predefinidas  
  
##### <a name="from-native-code"></a>No código nativo  
O shell fornece um serviço que fornece acesso para o `COLORREF` das cores. A interface de serviço/é:  
  
```  
IVsUIShell2::GetVSSysColorEx(VSSYSCOLOR dwSysColIndex, DWORD *pdwRGBval)  
```  
  
No arquivo VSShell80.idl, a enumeração `__VSSYSCOLOREX` tem constantes de cor do shell. Para usá-lo, passe em como o valor de índice qualquer um dos valores do `enum __VSSYSCOLOREX` documentados no MSDN ou um índice regular número que o sistema do Windows API, `GetSysColor`, aceita. Isso obtém de volta o valor RGB da cor que deve ser usado no segundo parâmetro.  
  
Se armazenar uma caneta ou um pincel com uma cor nova, você deve `AdviseBroadcastMessages` (do shell do Visual Studio) e escutar `WM_SYSCOLORCHANGE` e `WM_THEMECHANGED` mensagens.  
  
  
Para acessar o serviço de cor no código nativo, você fará uma chamada que é semelhante a esta: 

```
pUIShell2->GetVSSysColorEx(VSCOLOR_COLOR_NAME, &rgbLOCAL_COLOR);    
```  

> **Observação:** o `COLORREF` valores retornados por `GetVSSysColorEx()` contêm apenas R, G, componentes de B de uma cor de tema. Se uma entrada de tema usa transparência, o valor de canal alfa será descartado antes de retornar. Portanto, se a cor do ambiente de interesse deve ser usada em um local em que o canal de transparência é importante, você deve usar `IVsUIShell5.GetThemedColor` em vez de `IVsUIShell2::GetVSSysColorEx`, conforme descrito posteriormente neste tópico.  
  
##### <a name="from-managed-code"></a>No código gerenciado  
Acessando o serviço de VSColor código nativo é bastante simples. Se você estiver trabalhando por meio de código gerenciado, no entanto, determinar como usar o serviço pode ser complicado. Com isso em mente, aqui está um trecho de código c# demonstra esse processo:  
  
```  
private void VSColorPaint(object sender, System.Windows.Forms.PaintEventArgs e)  
{  
    //getIVSUIShell2  
    IVsUIShell2 uiShell2 = Package.GetService(typeof(SVsUIShell)) as IVsUIShell2;  
    Debug.Assert (uiShell2 != null, "failed to get IVsUIShell2");  
  
    if (uiShell2 != null)  
    {  
        //get the COLORREF structure  
        uint win32Color;  
        uiShell.GetVSSysColorEx(VSSYSCOLOREX.VSCOLOR_SMARTTAG_HOVER_FILL, out win32Color);  
  
        //translate it to a managed Color structure  
        Color myColor = ColorTranslator.FromWin32((int)win32Color);  
        //use it  
        e.Graphics.FillRectangle(new SolidBrush(myColor), 0, 0, 100, 100);  
    }  
}  
```  
  
Se você estiver trabalhando no Visual Basic, use:  
  
```  
Dim myColor As Color = ColorTranslator.FromWin32((Integer)win32Color)  
```  
  
##### <a name="from-wpf-ui"></a>Na interface do usuário do WPF  
Você pode vincular a cores do Visual Studio por meio de valores exportados para o aplicativo `ResourceDictionary`. Abaixo está um exemplo de usando os recursos de tabela de cores, bem como a associação para os dados da fonte de ambiente em XAML.  
  
```  
<Style TargetType="{x:Type Button}">  
    <Setter Property="TextBlock.FontFamily"  
            Value="{DynamicResource VsFont.EnvironmentFontFamily}" />  
    <Setter Property="TextBlock.FontSize"  
            Value="{DynamicResource VsFont.EnvironmentFontSize}" />  
    <Setter Property="Background"  
            Value="{DynamicResource VsBrush.EnvironmentBackgroundGradient}" />  
</Style>  
```  
  
#### <a name="helper-classes-and-methods-for-managed-code"></a>Classes de auxiliar e métodos para código gerenciado  
Para código gerenciado, a biblioteca de estrutura de pacote gerenciado do shell (`Microsoft.VisualStudio.Shell.12.0.dll`) contém algumas classes auxiliares que facilita o uso de cores de tema.  
  
Os métodos auxiliares no `Microsoft.VisualStudio.Shell.VsColors` classe MPF incluem `GetThemedGDIColor()` e `GetThemedWPFColor()`. Esses métodos auxiliares retornam o valor de cor de uma entrada de tema como `System.Drawing.Color` ou `System.Windows.Media.Color`, para ser usado em WinForms ou WPF UI.  
  
```  
IVsUIShell5 shell5;  
Button button = new Button();  
button.BackColor = GetThemedGDIColor(shell5, SolutionExplorerColors.SelectedItemBrushKey);  
button.ForeColor = GetThemedGDIColor(shell5, SolutionExplorerColors.SelectedItemTextBrushKey);  
  
/// <summary>  
/// Gets a System.Drawing.Color value from the current theme for the given color key.  
/// </summary>  
/// <param name="vsUIShell">The IVsUIShell5 service, used to get the color's value.</param>  
/// <param name="themeResourceKey">The key to find the color for.</param>  
/// <returns>The current theme's value of the named color.</returns>  
public static System.Drawing.Color GetThemedGDIColor(this IVsUIShell5 vsUIShell, ThemeResourceKey themeResourceKey)  
{  
   Validate.IsNotNull(vsUIShell, "vsUIShell");  
   Validate.IsNotNull(themeResourceKey, "themeResourceKey");  
  
   byte[] colorComponents = GetThemedColorRgba(vsUIShell, themeResourceKey);  
  
   // Note: The Win32 color we get back from IVsUIShell5.GetThemedColor is ABGR  
   return System.Drawing.Color.FromArgb(colorComponents[3], colorComponents[0], colorComponents[1], colorComponents[2]);  
}  
  
private static byte[] GetThemedColorRgba(IVsUIShell5 vsUIShell, ThemeResourceKey themeResourceKey)  
{  
   Guid category = themeResourceKey.Category;  
   __THEMEDCOLORTYPE colorType = __THEMEDCOLORTYPE.TCT_Foreground  
   if (themeResourceKey.KeyType == ThemeResourceKeyType.BackgroundColor || themeResourceKey.KeyType == ThemeResourceKeyType.BackgroundBrush)  
   {  
      colorType = __THEMEDCOLORTYPE.TCT_Background;  
   }  
  
   // This call will throw an exception if the color is not found  
   uint rgbaColor = vsUIShell.GetThemedColor(ref category, themeResourceKey.Name, (uint)colorType);  
   return BitConverter.GetBytes(rgbaColor);  
}  
public static System.Windows.Media.Color GetThemedWPFColor(this IVsUIShell5 vsUIShell, ThemeResourceKey themeResourceKey)  
{  
   Validate.IsNotNull(vsUIShell, "vsUIShell");  
   Validate.IsNotNull(themeResourceKey, "themeResourceKey");  
  
   byte[] colorComponents = GetThemedColorComponents(vsUIShell, themeResourceKey);  
  
    return System.Windows.Media.Color.FromArgb(colorComponents[3], colorComponents[0], colorComponents[1], colorComponents[2]);  
}    
```  
  
A classe também pode ser usada para obter os identificadores VSCOLOR para uma determinada chave de recurso de cor WPF, ou vice-versa.  
  
```  
public static string GetColorBaseKey(int vsSysColor);  
public static bool TryGetColorIDFromBaseKey(string baseKey, out int vsSysColor);  
```  
  
Os métodos de `VsColors` classe consultar o serviço de VSColor para retornar o valor de cor de cada vez que são invocados. Para obter um valor de cor como `System.Drawing.Color`, é uma alternativa com melhor desempenho em vez disso, usar os métodos do `Microsoft.VisualStudio.PlatformUI.VSThemeColor` classe, que armazena em cache os valores de cor obtidos do serviço VSColor. A classe internamente assina eventos de mensagens de difusão de shell e descartará o valor armazenado em cache quando ocorre um evento de alteração de tema. Além disso, a classe fornece um. Evento NET amigável para inscrever-se nas alterações de tema. Use o `ThemeChanged` eventos para adicionar um novo manipulador e usar o `GetThemedColor()` método obter cor valores para o `ThemeResourceKeys` de interesse. Um exemplo de código pode ter esta aparência:  
  
```  
public MyWindowPanel()  
{  
    InitializeComponent();  
  
    // Subscribe to theme changes events so we can refresh the colors  
    VSColorTheme.ThemeChanged += VSColorTheme_ThemeChanged;  
  
    RefreshColors();  
}  
  
private void VSColorTheme_ThemeChanged(ThemeChangedEventArgs e)  
{  
    RefreshColors();  
  
    // Also post a message to all the children so they can apply the current theme appropriately  
    foreach (System.Windows.Forms.Control child in this.Controls)  
    {  
        NativeMethods.SendMessage(child.Handle, e.Message, IntPtr.Zero, IntPtr.Zero);  
    }  
}  
  
private void RefreshColors()  
{  
    this.BackColor = VSColorTheme.GetThemedColor(EnvironmentColors.ToolWindowBackgroundColorKey);  
    this.ForeColor = VSColorTheme.GetThemedColor(EnvironmentColors.ToolWindowTextColorKey);  
}  
  
protected override void Dispose(bool disposing)  
{  
    if (disposing)  
    {  
        VSColorTheme.ThemeChanged -= this.VSColorTheme_ThemeChanged;  
        base.Dispose(disposing);}  
}  
```  
  
##  <a name="BKMK_ChoosingHighContrastColors"></a>Escolha de cores de alto contraste  
  
### <a name="overview"></a>Visão Geral  
O Windows usa vários temas de nível de sistema de alto contraste que aumentam o contraste de cor de texto, planos de fundo e imagens, fazendo com que elementos são mais destacadas na tela. Por motivos de acessibilidade, é importante que elementos da interface do Visual Studio respondem corretamente quando os usuários alternam a um tema de alto contraste.  
  
Apenas algumas das cores do sistema podem ser usada para temas de alto contraste. Ao escolher o sistema de nomes de cores, lembre-se as dicas a seguir:  
  
1.  **Escolha as cores do sistema que têm o mesmo significado semântico** que o elemento que são cores. Por exemplo, se você escolher uma cor de alto contraste para texto em uma janela, use WindowText e não ControlText.  
  
2.  **Escolha os pares de primeiro e segundo plano** juntas ou não ser seguro de que sua opção de cor funcionará em todos os temas de alto contraste.  
  
3.  **Determinar quais partes de sua interface do usuário são os mais importantes e certifique-se de que as áreas de conteúdo destacará.** Você perderá muitos detalhes que normalmente seriam distinguir os diferenças sutis de matiz da cor, portanto, o uso de cores de borda de alta segurança é comum para definir as áreas de conteúdo, porque não há nenhum variantes de cor para diferentes áreas de conteúdo.  
  
### <a name="system-color-set"></a>Conjunto de cores do sistema  
A tabela [Blog da equipe do WPF: referência SystemColors](http://blogs.msdn.com/b/wpf/archive/2010/11/30/systemcolors-reference.aspx) indica o conjunto completo de nomes de cores do sistema e os matizes correspondentes exibidos em cada tema.  
  
Ao aplicar este conjunto limitado de cores para a interface do usuário, *é esperado que você perderá detalhes sutis que estavam presentes nos temas "normais"*. Aqui está um exemplo da interface do usuário com cores cinzas sutis que são usados para distinguir áreas dentro de uma janela de ferramenta. Quando combinado com a mesma janela exibida no modo de alto contraste, você pode ver que todos os planos de fundo são o mesmo matiz e as bordas dessas áreas são indicadas por borda autônoma:  
  
![Exemplo de como sutis detalhes serão perdidas em alto contraste](../../extensibility/ux-guidelines/media/030303-a_propertieswindow.png "030303-a_PropertiesWindow")<br />Exemplo de como sutis detalhes serão perdidas em alto contraste
  
#### <a name="choosing-text-colors-in-an-editor"></a>Escolher as cores de texto em um editor  
Texto coloridos serão é usado em um editor ou em uma superfície de design para indicar o significado, como permitir para facilitar a identificação de grupos de itens semelhantes. Em um tema de alto contraste, no entanto, você não tem a capacidade de diferenciar entre mais de três cores de texto. WindowText, GrayText e HotTrackText são as cores somente disponíveis nas superfícies de WindowBackground. Desde que você não pode usar mais de três cores, escolha cuidadosamente as diferenças mais importantes que você deseja exibir no modo de alto contraste.  
  
Matizes para cada um dos nomes de token permitidos em uma superfície de editor, como eles aparecem em cada tema de alto contraste:  
  
![Comparação de editor alto contraste](../../extensibility/ux-guidelines/media/030303-b_hceditorcomparison.png "030303-b_HCEditorComparison")<br />Comparação de editor alto contraste
  
Exemplos da superfície de editor no tema azul:  
  
![Editor no tema azul](~/docs/extensibility/ux-guidelines/media/030303-c_editorblue.png "030303-c_EditorBlue")<br />Editor no tema azul
  
![Editor do tema de alto contraste n º 1](../../extensibility/ux-guidelines/media/030303-d_editorhc1.png "030303-d_EditorHC1")<br />Editor do tema de alto contraste n º 1
  
### <a name="usage-patterns"></a>Padrões de uso
Vários elementos de interface de usuário comuns já definidas de cores de alto contraste. Você pode consultar esses padrões de uso ao escolher seu próprio sistema de nomes de cores para que os elementos de interface do usuário são consistentes com os componentes similares.  
  
| Cor do sistema | Uso |
| --- | --- |
| Legenda ativa | -Active IDE e glifos de botão de janela rafted no hover e pressione<br />-Plano de fundo do título barra do IDE e windows rafted<br />-Plano de fundo de barra de status padrão |
| ActiveCaptionText | -Active IDE e windows rafted de primeiro plano da barra de título (texto e glifos)<br />-Em segundo plano e da borda dos botões de janela ativa no hover e pressione |
| Controle | -Caixa de combinação lista suspensa e pesquisa de padrão de controle e desabilitados em segundo plano, incluindo o botão suspenso<br />-Plano de fundo do botão encaixe destino<br />-Plano de fundo de barra de comando<br />-Plano de fundo de janela de ferramenta |
| ControlDark | -Plano de fundo IDE<br />-Separadores de barra de menu e comando<br />-Borda da barra de comando<br />-Sombras menu<br />-Ferramenta de borda da guia janela padrão e passe o mouse e separador<br />-Bem documento plano de fundo de botão de estouro<br />-Borda de glifo de destino encaixe |
| ControlDarkDark |-Janela de guia do documento foco, selecionado |
| ControlLight |-Borda de guia ocultar automaticamente<br />-Borda da lista suspensa e de caixa de combinação<br />-Encaixar a borda e o plano de fundo de destino |
| ControlLightLight | -Borda provisional focada selecionada |
| ControlText | -Glifo de lista suspensa e de caixa de combinação<br />-Texto da guia ferramenta janela desmarcada |
| Texto cinza |-Caixa de combinação e a lista suspensa desabilitadas borda, glifos de lista suspensa, texto e texto do item de menu<br />-Texto do menu desabilitado<br />-Texto do cabeçalho pesquisa controle 'Opções de pesquisa'<br />-Separador de seção de controle pesquisa |
| Realçar | -Todos os hover e planos de fundo pressionados e bordas, exceto combinação botão suspenso em segundo plano e documento bem estouro botão borda da caixa<br />-Planos de fundo de item selecionado |
| Texto realçado | -Todas as em foco e pressionados foregrounds (texto e glifos)<br />-Ferramenta focada janela e documento guia janela controle em primeiro plano<br />-Borda de barra de título de janela de ferramenta focada<br />-Primeiro plano de guia provisional focada, selecionada<br />-Botão border documento bem estouro no hover e pressione<br />-Borda de ícone selecionado|
| HotTrack | -Barra de rolagem thumb em segundo plano e pressione a borda<br />-Barra de rolagem glifos de seta em pressione |
| Legenda inativa | -IDE inativo e glifos de botão de janela rafted em foco<br />-Plano de fundo do título barra do IDE e windows rafted<br />-Plano de fundo de controle de pesquisa desabilitado |
| Texto da legenda inativa | -Primeiro plano de barra de título rafted windows (texto e glifos) e IDE inativo<br />-Plano de fundo de botões de janela inativa e borda em foco<br />-Borda e plano de fundo do botão ferramenta foco janela<br />-Primeiro plano de controle de pesquisa desabilitado |
| Menu | -Plano de fundo de menu suspenso<br />-Marca de seleção Check e desabilitados em segundo plano |
| MenuText | -Borda de menu suspenso<br />-Marcas de seleção<br />-Glifos menu<br />-Texto do menu suspenso<br />-Borda de ícone selecionado |  
| Barra de Rolagem | -Role barra e barra de plano de fundo de seta, todos os estados de rolagem |
| Janela | -Ocultar automaticamente em segundo plano de guia<br />-Menu barra e plano de fundo de validade de comando<br />-Plano de fundo do documento foco ou desmarcado janela guia e a borda de documento, para as guias abertas e provisionais<br />-Plano de fundo barra título de janela de ferramenta foco<br />-Ferramenta janela guia em segundo plano, selecionados e desmarcados |
| Moldura da janela | -Borda IDE |
| WindowText | -Primeiro plano de guia ocultar automaticamente<br />-Primeiro plano de guia de janela de ferramenta selecionada<br />-Guia da janela de documento foco e plano de fundo de guia provisional foco ou não selecionado<br />-Árvore em primeiro plano do modo de exibição padrão e passe o mouse sobre glifo não selecionado<br />-Borda da janela de ferramenta guia selecionada<br />-Barra de rolagem thumb em segundo plano, borda e glifo |
  
##  <a name="BKMK_ExposingColorsForEndUsers"></a>Exposição de cores para os usuários finais  
  
### <a name="overview"></a>Visão Geral  
Às vezes, convém permitir que o usuário final personalizar a interface do usuário, como quando você estiver criando um editor de código ou a superfície de design. É a maneira mais comum de fazer isso usando o **ferramentas &gt; opções** caixa de diálogo. A menos que você tenha altamente especializada da interface do usuário que requer controles especiais, a maneira mais fácil para apresentar a personalização é por meio de **fontes e cores** página dentro de **ambiente** seção da caixa de diálogo. Para cada elemento que você expõe para personalização, o usuário pode optar por alterar a cor de primeiro plano, cor de plano de fundo ou ambos.

### <a name="building-a-vspackage-for-your-customizable-colors"></a>Criar um VSPackage para as cores personalizadas  
Um VSPackage pode controlar as fontes e cores por meio de categorias personalizadas e exibir os itens na página de propriedades de fontes e cores. Ao usar esse mecanismo, VSPackages deve implementar o [IVsFontAndColorDefaultsProvider](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.ivsfontandcolordefaultsprovider.aspx) interface e suas interfaces associadas.  
  
Em princípio, esse mecanismo pode ser usado para modificar todos os itens de exibição existente e as categorias que as contém. No entanto, ele não deve ser usado para modificar a categoria do Editor de texto ou seus itens de exibição. Para obter mais informações sobre a categoria do Editor de texto, consulte [visão geral de cor e de fonte](https://msdn.microsoft.com/en-us/library/bb165065.aspx).  
  
Para implementar categorias personalizadas ou exibir itens, um VSPackage deve:  
  
-   **Crie ou identifique categorias no registro.** A implementação do IDE do **fontes e cores** página de propriedades usa essas informações para consultar corretamente para o serviço de suporte a uma determinada categoria.  
  
-   **Criar ou identificar grupos no registro (opcional).** Pode ser útil definir um grupo, que representa a união de duas ou mais categorias. Se um grupo é definido, o IDE automaticamente mescla subcategorias e distribui os itens de exibição dentro do grupo.  
  
-   **Implementa o suporte do IDE.**  
  
-   **Controlar as alterações de fonte e cor.**  
  
#### <a name="to-create-or-identify-categories"></a>Para criar ou identificar categorias  
Construir um tipo especial de entrada de registro de categoria em `[HKLM\SOFTWARE\Microsoft \Visual Studio\\<Visual Studio version\>\FontAndColors\\<Category\>]` onde `<Category>` é o nome da categoria não localizada.
  
Preencha o registro com dois valores:  

| Nome | Tipo | Dados | Descrição |
| --- | --- | --- | --- |
| Categoria | REG_SZ | GUID | Um GUID criado para identificar a categoria |
| Pacote | REG_SZ | GUID | O GUID do serviço VSPackage que oferece suporte a categoria |
  
 O serviço especificado no registro deve fornecer uma implementação de [IVsFontAndColorDefaults](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.ivsfontandcolordefaults.aspx) para a categoria correspondente.  
  
#### <a name="to-create-or-identify-groups"></a>Para criar ou identificar grupos  
Construir um tipo especial de entrada de registro de categoria em `[HKLM\SOFTWARE\Microsoft \Visual Studio\\<Visual Studio version\>\FontAndColors\\<group\>]` onde `<group>` é o nome do grupo não localizada.  
  
Preencha o registro com dois valores:

| Nome | Tipo | Dados | Descrição |
|--- | --- | --- | --- |
| Categoria | REG_SZ | GUID | Um GUID criado para identificar a categoria |
| Pacote | REG_SZ | GUID | O GUID do serviço VSPackage que oferece suporte a categoria |
  
O serviço especificado no registro deve fornecer uma implementação de `T:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup` para o grupo correspondente.

![Implementação de interface IVsFontAndColorGroup](../../extensibility/ux-guidelines/media/0304-a_fontandcolorgroup.png "0304-a_FontAndColorGroup")<br />Implementação de`IVsFontAndColorGroup`
  
### <a name="to-implement-ide-support"></a>Para implementar o suporte IDE  
Implementar [GetObject](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.ivsfontandcolordefaultsprovider.getobject.aspx), que retorna um uma [IVsFontAndColorDefaults](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.ivsfontandcolordefaults.aspx) interface ou um `T:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup` interface IDE para cada categoria ou grupo GUID fornecida.  
  
Para cada categoria que oferece suporte a ele, um VSPackage implementa uma instância separada do [IVsFontAndColorDefaults](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.ivsfontandcolordefaults.aspx) interface.  
  
Os métodos implementados por meio de [IVsFontAndColorDefaults](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.ivsfontandcolordefaults.aspx) deve fornecer o IDE com:  
  
-   Listas de itens de exibição na categoria  
  
-   Nomes localizáveis para itens de exibição  
  
-   Informações de exibição para cada membro da categoria  
  
 > **Observação:** cada categoria deve conter pelo menos um item de exibição.
  
O IDE usa o `T:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup` interface para definir uma união de várias categorias.

Sua implementação fornece o IDE com:

-   Uma lista das categorias que compõem um grupo específico  
  
-   Acesso a instâncias de [IVsFontAndColorDefaults](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.ivsfontandcolordefaults.aspx) cada categoria dentro do grupo de suporte  
  
-   Nomes de grupo localizável  
  
#### <a name="updating-the-ide"></a>Atualizando o IDE  
O IDE armazena informações sobre configurações de fonte e cor. Portanto, após qualquer modificação da configuração de IDE fontes e cores, garantindo que o cache seja atualizado é uma prática recomendada.  
  
Atualizando o cache é feito por meio de [IvsFontAndColorCacheManager](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.ivsfontandcolorcachemanager.aspx) interface e pode ser executados itens selecionados globalmente ou apenas em.  
  
### <a name="handling-font-and-color-changes"></a>Tratando alterações de fonte e cor  
Para suporte a coloração de texto que exibe um VSPackage corretamente, o serviço de colorização que suporta o VSPackage deve responder às alterações iniciada pelo usuário feitas através da página de propriedades de fontes e cores.  
  
Para fazer isso, um VSPackage deve:  
  
-   **manipular eventos gerados pelo IDE** Implementando o [IVsFontAndColorEvents](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.ivsfontandcolorevents.aspx) interface. O IDE chama o método apropriado seguindo as modificações do usuário da página de fontes e cores. Por exemplo, ele chama o [OnFontChanged](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.ivsfontandcolorevents.onfontchanged.aspx) método se uma nova fonte é selecionada.  
  
 **OR**  
  
-   **sondar o IDE para que as alterações**. Isso pode ser feito por meio do sistema implementado [IVsFontAndColorStorage](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.ivsfontandcolorstorage.aspx) interface. Embora principalmente para suporte de persistência, o [GetItem](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.ivsfontandcolorstorage.getitem.aspx) método pode obter informações de fontes e cores para exibir itens. Para obter mais informações sobre configurações de fonte e cor, consulte o artigo do MSDN [acessar fonte armazenado e as configurações de cor](https://msdn.microsoft.com/en-us/library/bb166382.aspx).  
  
> **Observação:** para garantir que os resultados da pesquisa estão corretos, use o [IVsFontAndColorCacheManager](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.ivsfontandcolorcachemanager.aspx) interface para determinar se uma liberação de cache e atualização são necessárias antes de chamar os métodos de recuperação do [IVsFontAndColorStorage](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.ivsfontandcolorstorage.aspx) interface.
  
#### <a name="registering-custom-font-and-color-category-without-implementing-interfaces"></a>Registrar fonte personalizada e a categoria de cor sem implementar interfaces  
O exemplo de código a seguir demonstra como registrar a fonte personalizada e categoria de cores sem implementar interfaces:  
  
```  
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\FontAndColors\CSharp Tool Window]  
"Package"="{F5E7E71D-1401-11D1-883B-0000F87579D2}"  
"Category"="{9FF46859-A47E-47bf-8AC5-EC3DBE69D1FE}"  
"ToolWindowPackage"="{7259e420-6241-4e0d-b535-5b820671d183}"  
  
    "NameID"=dword:00000064  
```  

Para este exemplo de código:   
-   `"NameID"` = a ID de recurso do nome da categoria localizada no pacote
-   `"ToolWindowPackage"` = GUID do pacote
-   `"Category"="{9FF46859-A47E-47bf-8AC5-EC3DBE69D1FE}"`é apenas um exemplo e o valor real pode ser um novo GUID fornecido, o implementador.  
  
### <a name="set-the-font-and-color-property-category-guid"></a>Defina a categoria de propriedade fonte e cor GUID  
O exemplo de código a seguir demonstra a configuração de GUIDs de categoria.  
  
```  
// m_pView is your IVsTextView  
IVsTextEditorPropertyCategoryContainer spPropCatContainer =  
(IVsTextEditorPropertyCategoryContainer)m_pView;  
if (spPropCatContainer != null)  
{  
IVsTextEditorPropertyContainer spPropContainer;  
Guid GUID_EditPropCategory_View_MasterSettings =  
new Guid("{D1756E7C-B7FD-49a8-B48E-87B14A55655A}");  
hr = spPropCatContainer.GetPropertyCategory(  
ref GUID_EditPropCategory_View_MasterSettings,  
out spPropContainer);  
if(hr == 0)  
{  
hr =  
spPropContainer.SetProperty(  
VSEDITPROPID.VSEDITPROPID_ViewGeneral_FontCategory,  
catGUID);  
hr =  
spPropContainer.SetProperty(  
VSEDITPROPID.VSEDITPROPID_ViewGeneral_ColorCategory,  
catGUID);  
}  
}  
```  
  
##  <a name="BKMK_DaytonaAndWebUI"></a>Daytona e interface da web  
  
### <a name="overview"></a>Visão Geral  
"Daytona" é um conjunto de APIs, ferramentas e serviços que permitem que um usuário crie plug-ins com HTML, CSS e JavaScript que pode ser usado em uma variedade de hosts, como o Visual Studio ou F12. Plug-ins são compostos de um componente portátil, que é escrito em HTML, CSS e JavaScript, e os componentes opcionais de host específico. Cada host Daytona pode ter seu próprio conjunto de convenções de interface do usuário, implícitas ou explícitas, se um plug-in deve obedecer para aparecer nativo para seu ambiente. Alguns dos hosts, como o Visual Studio, permitir que os usuários finais fazer alterações para o tema"padrão", de forma que os aspectos visuais do host não podem ser estaticamente direcionados ao criar uma folha de estilos. Isso representa um desafio para os desenvolvedores que criam plug-ins portátil. Este tópico explica como criar web da interface do usuário no Visual Studio usando o host Daytona de forma que oferece suporte a temas e alto contraste corretamente.  
  
### <a name="daytona-theming-mechanism"></a>Mecanismo de temas Daytona  
O tempo de execução Daytona fornece um conjunto de serviços que resume as convenções de interface do usuário e recursos de temas do host. Esses serviços Verifique se o plug-ins automaticamente atende às expectativas de visual do usuário com base no ambiente que são hospedados em. Esse comportamento é fornecido por três recursos principais:  
  
1.  Uma folha de estilos injetado em tempo de execução (plugin.css) que se aplica a um conjunto de regras CSS a interface de usuário do plug-in de forma transparente e estilos o conjunto padrão de controles HTML (por exemplo, HTMLInputElement e HTMLButtonElement  
  
2.  Um conjunto de tokens fornecida pelo host que podem ser usadas para elementos de interface do usuário de estilo usando os valores que são baseados em tema em vez de codificados  
  
    -  uma sintaxe declarativa para acessar esses tokens com CSS  
  
    -  uma API para acessar programaticamente os tokens de tema do JavaScript  
  
3.  Notificação de alterações de tema  
  
#### <a name="runtime-injected-style-sheet"></a>Folha de estilos injetado em tempo de execução  
As coordenadas de tempo de execução Daytona com o host para injetar um estilo que automaticamente folha temas os elementos de interface do usuário padrão de um plug-in. Isso inclui o estilo para os seguintes conceitos:  
  
-   Fonte de ambiente  
  
-   Cores de plano de fundo  
  
-   Hiperlinks  
  
-   Controles de formulário (por exemplo: `<select>`, `<input>`,`<button>`  
  
-   Tabelas  
  
-   Títulos  
  
-   Barras de rolagem  
  
Isso significa que se a interface do usuário é composto de controles de interface do usuário HTML padrão, em seguida, nenhum trabalho adicional será necessária corretamente responder a alterações de tema e para dar suporte a alto contraste.  
  
#### <a name="custom-ui"></a>Personalizar a interface do usuário  
Em quase todos os casos não trivial, o padrão de controles de interface do usuário HTML será suficiente para fornecer uma experiência completa para um plug-in e deve ser introduzida a interface do usuário personalizada. Para oferecer suporte ao uso de opção e a cor de fonte correta, **tokens de tema** devem ser usados declarativamente no CSS ou imperativa por meio da API de JavaScript descrito abaixo. O tempo de execução Daytona cuidará de atualizar as folhas de estilo que usam esses tokens no carregamento do plug-in e alterações de tema.  
  
##### <a name="theme-tokens"></a>Tokens de tema  
Ambos os tokens de tema padrão e específica de host estão disponíveis. Tokens padrão são injetados pelo host e está sempre disponível. É preferível usar os tokens padrão sempre que possível. Tokens padrão têm garantia de ser fornecido por todos os hosts Daytona e usá-los torna o plug-in inerentemente mais portáteis. O conjunto de tokens padrão está sujeita a alterações, embora somente novos tokens devem ser adicionadas e nenhum deve ser removida. A versão do Visual Studio 2013 está documentada abaixo:  
  
| Nome do token | Descrição |
| --- | --- |
| `plugin-background-color` | A cor de plano de fundo padrão para o plug-in |
| `plugin-color` | A cor de primeiro plano padrão para o plug-in |
| `plugin-contextmenu-active-color` | A cor de seleção de primeiro plano padrão para os menus de contexto quando estiverem ativas (tem foco) |
| `plugin-contextmenu-background-color` | A cor de plano de fundo padrão para os menus de contexto |
| `plugin-contextmenu-border-color` | A cor de borda padrão para os menus de contexto |
| `plugin-contextmenu-color` | A cor de primeiro plano padrão para os menus de contexto |
| `plugin-contextmenu-hover-color` | A cor de fundo padrão em foco para menus de contexto |
| `plugin-contextmenu-hover-text-color` | A cor de primeiro plano de foco padrão para os menus de contexto |
| `plugin-contextmenu-icon-checkbox` | A cor do ícone de caixa de seleção padrão para os menus de contexto |
| `plugin-contextmenu-inactive-text-color` | A cor de seleção de primeiro plano padrão para os menus de contexto quando estão inativos |
| `plugin-contextmenu-separator-color` | A cor do separador padrão para os menus de contexto |
| `plugin-font-family` | A família de fontes padrão a ser usado para o plug-in |
  
No Visual Studio, o seguinte `plugin-font` tokens são com base nas configurações de fonte de ambiente:  
  
-   `plugin-font-size`  
  
-   `plugin-font-weight`  
  
-   `plugin-highlight-background-color`  
  
-   `plugin-highlight-color`  
  
-   `plugin-inactive-color` 
  
O seguinte `plugin-link` tokens são usados para o estilo `HTMLElements` (hiperlinks):
  
-   `plugin-link-color`  
  
-   `plugin-link-active-color`  
  
-   `plugin-link-hover-color`  
  
Plugin.CSS estilos barras de rolagem por padrão, usando os seguintes tokens para dar um suporte melhor os temas em vários hosts (em especial, o Visual Studio):
  
-   `plugin-scrollbar-arrow-color`  
  
-   `plugin-scrollbar-background-color`  
  
-   `plugin-scrollbar-face-color`  
  
O seguinte `plugin-select` tokens são usados para o estilo de `HTMLSelectElement` (combinação caixa suspensa):  
  
-   `plugin-select-option-background-color` 
  
-   `plugin-select-option-color`  
  
-   `plugin-select-option-checked-background-color`  
  
-   `plugin-select-option-checked-border-color`  
  
-   `plugin-select-option-checked-foreground-color`  
  
-   `plugin-select-option-hover-background-color`  
  
-   `plugin-select-option-hover-border-color`  
  
-   `plugin-select-option-hover-foreground-color`  
  
-   `plugin-select-border-color`  
  
-   `plugin-select-background-color`  
  
-   `plugin-select-foreground-color`  
  
-   `plugin-select-hover-background-color`  
  
-   `plugin-select-hover-border-color`  
  
-   `plugin-select-hover-foreground-color`  
  
-   `plugin-table-border-color`  
  
-   `plugin-table-header-background-color`  
  
-   `plugin-table-header-color`  
  
-   `plugin-textbox-border-color`  
  
-   `plugin-textbox-background-color`  
  
-   `plugin-textbox-color`  
  
-   `plugin-textbox-disabled-background-color`  
  
-   `plugin-textbox-disabled-border-color`  
  
-   `plugin-textbox-disabled-color`  
  
Esses tokens devem ser usados para *todos os* , as tabelas e exibições de árvore porque eles têm os padrões corretos definidos em vários hosts para dar suporte a alto contraste e temas:  
  
-   `plugin-treeview-content-background-color`  
  
-   `plugin-treeview-content-color` 
  
-   `plugin-treeview-content-inactive-selected-color`  
  
-   `plugin-treeview-content-mouseover-background-color`  
  
-   `plugin-treeview-content-mouseover-color`  
  
-   `plugin-treeview-content-inactive-selected-color`  
  
-   `plugin-treeview-content-selected-background-color`  
  
-   `plugin-treeview-content-selected-border-color`  
  
-   `plugin-treeview-content-selected-color`  
  
##### <a name="host-specific-tokens"></a>Tokens de host específico  
Além de oferecer suporte o conjunto padrão de tokens, os hosts também podem fornecer tokens não padrão. O host do Visual Studio faz isso, permitindo que o plug-in especificar aliases de token do tema em uma seção do Visual Studio específicos do manifesto. Por exemplo:
  
```  
"vs": {  
    "theme_token_aliases": {   
        "diagnostics-host-border": {   
            "category": "f8a8b2a5-dd35-43f6-a382-fd6a61325c22",   
            "key_type": "BackgroundColor",   
            "name": "Border"   
        },   
        ...   
    }   
}    
```  
  
 Este exemplo apresenta um token de tema, denominado `diagnostics-host-border`, que pode ser referenciado idêntico aos tokens de padrão mencionados acima. O `category`, `key_type`, e `name` são usadas para resolver a cor do `IVsFontAndColorStorage` interface. Em muitos casos, é possível localizar cores apropriadas (juntamente com o `category`, `key_type`, e `name` informações) dos arquivos XML localizado em `VSCommonContent\themes`. O mesmo mecanismo é usado se o seu pacote apresenta novas cores configuráveis: corresponder o `category`, `key_type`, e `name` para a cor que você deseja usar. Autores de plug-in devem tentar usar tokens padrão sempre que possível e usar apenas os tokens de host específicos quando absolutamente necessário.  
  
##### <a name="using-theme-tokens-in-css"></a>Uso de tokens de tema no CSS  
 Tokens de tema são chamados por meio de uma sintaxe de comentário especificamente formatado. As regras de análise do token:  
  
1.  A expressão de comentário deve ser colocada entre colchetes (`[ ]`).  
  
2.  Todos os espaços em branco dentro do comentário, mas fora da expressão, é ignorado.  
  
3.  A expressão de comentário deve seguir diretamente a propriedade que ele substitui.  
  
4.  Qualquer espaço em branco à esquerda ou à direita na expressão será cortado.  
  
5.  Cada nome de token dentro da expressão deve ser colocado entre chaves (por exemplo, `{font-family}` e `{button-hover-color}`). Caso contrário, ele será tratado como um valor literal.  
  
 Os seguintes são exemplos de como o analisador token substituirão os valores CSS, supondo que o `plugin-background-color` token tem o valor de `#000` e `plugin-font-family` token tem o valor de `Verdana`.
  
| CSS criados | CSS analisada | Observações |  
| --- | --- | --- |
| `background-color: #fff; /*[{plugin-background-color}]*/` | `background-color: #000;` | O valor padrão é substituído pelo valor dinâmico específica do host. |  
| `background-color: #fff; /*   [{plugin-background-color}]   */` | `background-color: #000;` | O espaço em branco fora da expressão é ignorado. |  
| `background-color: #fff; /*[   {plugin-background-color}   ]*/` | `background-color: #000;` | O espaço em branco à esquerda e à direita na expressão é fragmentado. |
| `background-color: #fff; /*{plugin-background-color}*/` | `background-color: #fff;` | A expressão não está entre colchetes e, portanto, o comentário será ignorado. |
| `background-color: #fff; /*[plugin-background-color]*/` | `background-color: plugin-background-color;` | O token não está entre chaves e, portanto, é tratado como um valor literal. |
| `/*[{plugin-background-color}]*/ background-color: #fff;` | `background-color: #fff;` | O comentário não segue o valor da propriedade e, portanto, é ignorado. |
| `background-color: #fff;  /*[{plugin-background-color}]*/` | `background-color: #fff;`| *Mesmo que acima* |
| `/*[{plugin-background-color}]*/  background-color: #fff;` | `background-color: #fff;` | *Mesmo que acima* |
| `font-family: Arial, sans-serif; /*[{plugin-font-family}, sans-serif]*/` | `font-family: Verdana, sans-serif;` | O token é substituído e o conteúdo literal é mantido. |
| `background-image: linear-gradient(0% #000, 100% #ccc); /*[linear-gradient(0% #000, 100% {plugin-background-color})]*/` | `background-image: linear-gradient(0% #000, 100% #000);` | *Mesmo que acima* |
  
Se um arquivo CSS inclui tokens de tema deve ser marcado pelo `data-plugin-theme` atributo no `link` elemento no arquivo HTML. Por exemplo:  
  
```  
<link href="default.css" rel="stylesheet" data-plugin-theme="true" />  
```

##### <a name="using-theme-tokens-from-javascript"></a>Uso de tokens de tema do JavaScript  
Enquanto a interface do usuário personalizada deve ser com tema por CSS sempre que possível, há situações quando o valor de um tema de token precisa ser acessado por meio de programação. Por exemplo, se a interface do usuário personalizada que está sendo desenhado em um `CanvasElement` que não herda o estilo de CSS, ou se um elemento de interface do usuário é criado dinamicamente como contrário fazendo referência a folhas de estilo. Os cenários habilitados usando a API Daytona `Plugin.Theme.getValue`. Essa função retorna um valor de tema fornecida pelo host quando é fornecido um nome de token.  
  
| Não com tema | Com tema |
| --- | --- |
| `var surface = document.getElementById("surface").getContext("2d");  surface.fillStyle = "#ccc";  surface.fillRect(0, 0, 200, 200);` | `var surface = document.getElementById("surface").getContext("2d");  surface.fillStyle = ("plugin-background-color");  surface.fillRect(0, 0, 200, 200);` |
| `var el = document.createElement("div");  el.style.backgroundColor = "#ccc";` | `var el = document.createElement("div");  el.style.backgroundColor = Plugin.Theme.getValue("plugin-background-color");` |  
  
Se os tokens são usados de JavaScript **deve ser tratado o evento de alteração de tema para responder a atualizações**. Isto é desnecessário para tokens de tema usados declarativamente no CSS, como o tempo de execução Daytona cuida para o plug-in. O evento de tema pode ser tratado da seguinte maneira:

**Membro (único manipulador)**
```
Plugin.Theme.onchange = function () 
{
    // re-draw dynamic UI here
}
```

**Evento de DOM (vários manipuladores)**
```
Plugin.Theme.addEventListener("change", function () 
{
    // re-draw dynamic UI here
});
```
  
Nesse caso, seria muito comum para chamar novamente `Plugin.Theme.getValue` nesses manipuladores, como o valor dos tokens do tema provavelmente alterado quando o tema alterado.  
  
##### <a name="standard-token-mapping"></a>Mapeamento de token padrão  
Os tokens padrão são mapeados para as cores do ambiente e o Shell. A lista a seguir fornece um tipo de quais são esses mapeamentos.  
  
| Nome do token | VS mapeamento (`EnvironmentColors`) |  
| --- | --- |  
| `plugin-color` | `ToolWindowTextColorKey` |
| `plugin-background-color` | `ToolWindowBackgroundColorKey` |
| `plugin-link-color` | `ControlLinkTextColorKey` |
| `plugin-link-hover-color` | `ControlLinkTextHoverColorKey` |
| `plugin-link-active-color` | `ControlLinkTextPressedColorKey` |
| `plugin-highlight-color` | `HighlightTextColorKey` |
| `plugin-highlight-background-color` | `HighlightColorKey` |
| `plugin-table-header-background-color` | `GridHeadingBackgroundColorKey` |
| `plugin-table-header-color` | `GridHeadingTextColorKey` |
| `plugin-table-border-color` | `GridLineColorKey` |
| `plugin-button-background-color` | `ButtonFaceColorKey` |
| `plugin-button-hover-background-color` | `ButtonHighlightColorKey` | 
| `plugin-button-color` | `ButtonTextColorKey` |
| `plugin-button-border-color` | `ButtonBorderColorKey` |
  
##### <a name="theme-changes"></a>Alterações de tema  
As Visual Studio host gatilhos plug-in tema as alterações quando um usuário final faz alterações para as seguintes configurações:  
  
**Tema de cores:**  
  
![Alterações de tema de cores](~/docs/extensibility/ux-guidelines/media/0305-a_colortheme.png "0305-a_ColorTheme")<br />Alterações de tema de cores  
  
**Tema de ambiente:**  
  
![Alterações de tema do ambiente](~/docs/extensibility/ux-guidelines/media/0305-b_environmenttheme.png "0305-b_EnvironmentTheme")<br />Alterações de tema do ambiente  
  
**Tema do sistema operacional** (somente quando alterar para e de alto contraste):  
  
![Alterações de tema do sistema operacional](../../extensibility/ux-guidelines/media/0305-c_ostheme.png "0305-c_OSTheme")<br />Alterações de tema do sistema operacional
