---
title: Cores e estilos para o Visual Studio | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
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
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 49f72a7d7161cc4f9380072c45341b8afa5dd7fd
ms.lasthandoff: 02/22/2017

---
# <a name="colors-and-styling-for-visual-studio"></a>Cores e estilos para o Visual Studio
## <a name="using-color-in-visual-studio"></a>Usando cores no Visual Studio  
 No Visual Studio, a cor é usada principalmente como uma ferramenta de comunicação, não apenas como decoração. Usar cor minimamente e reservá-lo para situações em que você deseja:  
  
-   Comunicar significado ou afiliação (por exemplo, modificadores de plataforma ou idioma)  
  
-   Atrair a atenção (por exemplo, indicando uma alteração de status)  
  
-   Melhorar a legibilidade e fornecer pontos de referência para navegar a interface do usuário  
  
-   Finalidade de aumento  
  
 Existem várias opções para atribuir cores aos elementos de interface do usuário no Visual Studio. Às vezes, pode ser difícil de figura para qual opção você deverá para usar ou como usá-la corretamente. Este tópico o ajudará a:  
  
1.  Entenda os diferentes serviços e sistemas usados para definir cores no Visual Studio.  
  
2.  Selecione a opção correta para um determinado elemento.  
  
3.  Corretamente, use a opção escolhida.  
  
 **IMPORTANTE:** nunca codificar hexadecimal, RGB ou cores do sistema para os elementos de interface do usuário. Usando os serviços permite flexibilidade no ajuste de matiz. Além disso, sem o serviço, você não poderá aproveitar os recursos de troca de tema a [o serviço de VSColor](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_TheVSColorService).  
  
### <a name="methods-for-assigning-color-to-visual-studio-interface-elements"></a>Métodos para atribuir cores aos elementos de interface do Visual Studio  
 Escolha o método mais adequado para os elementos de interface do usuário.  
  
|A interface do usuário|Método|Quais são elas?|  
|-------------|------------|--------------------|  
|Você tiver inserido ou caixas de diálogo autônomo.|**Cores do sistema**|Nomes de sistema que permitem que o sistema operacional definir a cor e a aparência dos elementos da interface do usuário, como controles de caixa de diálogo comum.|  
|Você tem a interface do usuário personalizada que você deseja que sejam consistentes com o ambiente do VS geral e você tem elementos de interface do usuário que correspondem à categoria e o significado semântico dos tokens compartilhados.|**Cores compartilhadas comuns**|Nomes de cores predefinidas de token existente para elementos de interface do usuário específicos|  
|Você tem um recurso individual ou grupo de recursos e não há nenhuma cor compartilhado para elementos semelhantes.|**Cores personalizadas**|Nomes de token de cores que são específicos para uma área e não devem ser compartilhados com outro da interface do usuário|  
|Você deseja permitir que o usuário final personalizar a interface do usuário ou conteúdo (por exemplo, para editores de texto ou janelas de designer especializadas).|**Personalização do usuário final**<br /><br /> **(Ferramentas > caixa de diálogo Opções)**|As configurações definidas na página de "Fontes e cores" a **Ferramentas > opções** caixa de diálogo ou uma página especializada específica para um recurso da interface do usuário.|  
|Você tem a interface do usuário que é criado no HTML.|**Daytona**|Permite a interface do usuário criado em HTML para acessar o serviço de fonte e cor.|  
  
### <a name="visual-studio-themes"></a>Temas do Visual Studio  
 O Visual Studio apresenta três temas de cores diferentes: azul claro e escuro. Ele também detecta o modo de alto contraste, o que é um tema de cor de todo o sistema projetado para acessibilidade.  
  
 Usuários serão solicitados a selecionar um tema durante sua primeira utilização do Visual Studio e são capazes de alternar temas mais tarde, acessando a **Ferramentas > opções > ambiente > geral** e selecionando um novo tema no menu suspenso "tema de cores".  
  
 Usuários também podem usar o painel de controle para alternar os sistemas inteiros em um dos vários temas de alto contraste. Se um usuário selecionar um tema de alto contraste, em seguida, o seletor de tema de cores do Visual Studio não afeta mais cores no Visual Studio, embora as mudanças de tema são salvas para quando o usuário sai do modo de alto contraste. Para obter mais informações sobre o modo de alto contraste, consulte [cores de alto contraste escolhendo](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_ChoosingHighContrastColors).  
  
### <a name="the-vscolor-service"></a>O serviço VSColor  
 Visual Studio fornece um serviço de cor do ambiente, conhecido como o serviço VSColor, que permite que você vincule os valores de cor de seus elementos de interface do usuário a uma entrada nomeada que contém os valores de cor para cada tema do Visual Studio. Isso garante que suas cores serão alterado automaticamente para refletir o modo atual de alto contraste de sistema ou tema selecionado pelo usuário. Uso do serviço significa que a implementação de todas as alterações relacionadas de tema de cor é tratada em um local e, se você estiver usando cores comuns compartilhadas do serviço, a interface do usuário refletirá automaticamente os novos temas em versões futuras do Visual Studio.  
  
### <a name="implementation"></a>Implementação  
 O código-fonte Visual Studio inclui vários arquivos de definição de pacote que contêm listas de nomes de token e os valores de cor respectiva para cada tema. O serviço de cor lê o VSColors definidas nesses arquivos de definição de pacote. Essas cores são referenciadas na marcação XAML ou no código e, em seguida, carregadas por meio de **IVsUIShell5.GetThemedColor** método ou um mapeamento DynamicResource.  
  
### <a name="system-colors"></a>Cores do sistema  
 Controles comuns referenciar as cores do sistema por padrão. Se você quiser que a interface do usuário para usar cores do sistema, como quando você estiver criando uma caixa de diálogo incorporada ou autônomo, você não precisa fazer nada.  
  
### <a name="common-shared-colors-in-the-vscolor-service"></a>Cores comuns compartilhadas no serviço VSColor  
 Os elementos de interface devem refletir o ambiente geral do Visual Studio. Reutilizando as cores comuns compartilhadas que são apropriadas para o componente da interface do usuário que você está projetando, garanta que a interface seja consistente com outras interfaces do Visual Studio, e que as cores serão atualizadas automaticamente quando os temas são adicionados ou atualizados.  
  
 Antes de usar cores compartilhadas comuns, certifique-se de que você compreenda como usá-los corretamente. Uso incorreto de cores compartilhadas comuns pode resultar em uma experiência inconsistente, frustrante ou confusa para os usuários.  
  
### <a name="user-customizable-colors"></a>Cores personalizadas pelo usuário  
 Consulte: [expondo cores para os usuários finais](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_ExposingColorsForEndUsers)  
  
 Às vezes, convém permitir ao usuário final personalizar a interface do usuário, como quando você estiver criando um editor de código ou na superfície de design. Componentes de interface do usuário personalizáveis encontrados no **fontes e cores** seção o **Ferramentas > opções** caixa de diálogo, onde os usuários podem escolher para alterar a cor de primeiro plano, cor de plano de fundo ou ambos.  
  
 ![Ferramentas > caixa de diálogo de opções no Visual Studio](../../extensibility/ux-guidelines/media/0301-a_toolsoptionsdialog.png "0301 a_ToolsOptionsDialog")  
  
 **Ferramentas > caixa de diálogo Opções**  
  
### <a name="web-ui-colors"></a>Cores da interface do usuário da Web  
 Ele está se tornando comuns para criar componentes de interface do usuário usando HTML para que possa ser usados no Visual Studio Online e no Visual Studio. Interface do usuário escrita em HTML ainda deve usar o serviço VSColor ao ser executado no ambiente do Visual Studio. Para obter informações sobre Daytona e como usá-lo, consulte [Daytona e web da interface do usuário](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_DaytonaAndWebUI).  
  
##  <a name="a-namebkmkthevscolorservicea-the-vscolor-service"></a><a name="BKMK_TheVSColorService"></a>O serviço VSColor  
 Visual Studio fornece um serviço de cor do ambiente, também chamado do serviço de VSColor ou cor de shell. Esse serviço permite que você vincule os valores de cor de seus elementos de interface do usuário a um conjunto que contém cores para cada tema de cores de nome-valor. O serviço de VSColor deve ser usado para todos os elementos de interface do usuário, para que as cores automaticamente alterado para refletir o tema selecionado pelo usuário atual e para que a interface do usuário associado ao serviço de cor de ambiente se integrará ao novos temas em futuras versões do Visual Studio.  
  
### <a name="how-the-service-works"></a>Como funciona o serviço  
 O serviço de cor do ambiente lê que vscolors definido em pkgdef para o componente de interface do usuário. Esses VSColors, em seguida, são referenciados no código ou marcação XAML e são carregados por meio de **IVsUIShell5.GetThemedColor** ou um mapeamento DynamicResource.  
  
 ![Arquitetura de serviço de cor do ambiente](../../extensibility/ux-guidelines/media/0302-a_environmentcolorservicearchitecture.png "a_EnvironmentColorServiceArchitecture&0302;")  
  
 **Arquitetura de serviço de cor do ambiente**  
  
### <a name="accessing-the-service"></a>Acessando o serviço  
 Há várias maneiras diferentes de acesso usando o serviço do VSColor, dependendo de qual tipo de cor de tokens e que tipo de código que você tem.  
  
#### <a name="predefined-environment-colors"></a>Ambiente predefinido de cores  
  
##### <a name="from-native-code"></a>No código nativo  
 O shell fornece um serviço que fornece acesso ao COLORREF das cores. A interface de serviço/é:  
  
```  
IVsUIShell2::GetVSSysColorEx(VSSYSCOLOR dwSysColIndex, DWORD *pdwRGBval)  
```  
  
 No arquivo VSShell80.idl, a enumeração **__VSSYSCOLOREX** tem constantes de cor do shell. Para usá-lo, passar como o índice de valor de qualquer um dos valores da __VSSYSCOLOREX enum documentados no MSDN ou um índice regular número que o sistema Windows API, **GetSysColor**, aceita. Isso retorna o valor RGB da cor que deve ser usado no segundo parâmetro.  
  
 Se armazenar uma caneta ou um pincel com uma cor nova, você deve AdviseBroadcastMessages (fora do shell do Visual Studio) e escuta mensagens WM_SYSCOLORCHANGE e WM_THEMECHANGED.  
  
```  
// To access the color service in native code, you'll make a call that resembles this:  
pUIShell2->GetVSSysColorEx(VSCOLOR_COLOR_NAME, &rgbLOCAL_COLOR);  
  
```  
  
 **Observação:** os valores COLORREF retornados por **GetVSSysColorEx()** contêm apenas R, G, componentes de B de uma cor de tema. Se uma entrada de tema usa transparência, o valor de canal alfa é descartado antes de retornar. Portanto, se a cor do ambiente de interesse deve ser usada em um local em que o canal de transparência é importante, você deve usar IVsUIShell5.GetThemedColor em vez de IVsUIShell2::GetVSSysColorEx, conforme descrito posteriormente neste tópico.  
  
##### <a name="from-managed-code"></a>No código gerenciado  
 Acessando o serviço VSColor por meio de código nativo é bastante simples. Se você estiver trabalhando por meio de código gerenciado, no entanto, determinar como usar o serviço pode ser complicado. Com isso em mente, aqui está um trecho de código c# demonstra esse processo:  
  
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
 Você pode vincular a cores do Visual Studio por meio de valores exportados no dicionário de recurso do aplicativo. Abaixo está um exemplo de usando os recursos de tabela de cores, bem como a associação para os dados da fonte de ambiente em XAML.  
  
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
  
#### <a name="helper-classes-and-methods-for-managed-code"></a>Classes auxiliares e os métodos para código gerenciado  
 Para código gerenciado, a biblioteca de estrutura de pacote gerenciado do shell (Microsoft.VisualStudio.Shell.12.0.dll) contém algumas classes auxiliares que facilita o uso de cores de temas.  
  
 Os métodos auxiliares no **Microsoft.VisualStudio.Shell.VsColors** classe no MPF incluem **GetThemedGDIColor()** e **GetThemedWPFColor()**. Esses métodos auxiliares retornam o valor de cor de uma entrada de tema System.Drawing.Color ou System.Windows.Media.Color, para ser usado em WinForms ou WPF UI.  
  
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
  
 A classe também pode ser usada para obter identificadores VSCOLOR para uma determinada chave de recurso de cor WPF, ou vice-versa.  
  
```  
public static string GetColorBaseKey(int vsSysColor);  
public static bool TryGetColorIDFromBaseKey(string baseKey, out int vsSysColor);  
```  
  
 Os métodos de **VsColors** classe consultar o serviço de VSColor para retornar o valor de cor de cada vez que eles são chamados. Para obter um valor de cor como **System.Drawing.Color**, é uma alternativa com melhor desempenho usar os métodos do **Microsoft.VisualStudio.PlatformUI.VSThemeColor** classe, que armazena em cache os valores de cor obtidos do serviço VSColor. A classe internamente assina eventos de mensagens de difusão de shell e descartará o valor armazenado em cache quando ocorre um evento de alteração de tema. Além disso, a classe fornece um. Evento NET amigável para assinar as alterações de tema. Use o **ThemeChanged** eventos para adicionar um novo manipulador e usar o **GetThemedColor()** método obter cores valores para o **ThemeResourceKeys** de interesse. Um exemplo de código pode ter esta aparência:  
  
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
  
##  <a name="a-namebkmkchoosinghighcontrastcolorsa-choosing-high-contrast-colors"></a><a name="BKMK_ChoosingHighContrastColors"></a>Escolha de cores de alto contraste  
  
### <a name="overview"></a>Visão Geral  
 O Windows usa vários temas de nível de sistema de alto contraste que aumentam o contraste de cor de texto, planos de fundo e imagens, fazendo com que elementos são mais destacadas na tela. Por motivos de acessibilidade, é importante que os elementos de interface Visual Studio respondem corretamente quando os usuários alternar para um tema de alto contraste.  
  
 Apenas algumas poucas cores do sistema podem ser usada para temas de alto contraste. Ao escolher o sistema de nomes de cores, lembre-se as dicas a seguir:  
  
1.  **Escolher as cores do sistema que têm o mesmo significado semântico** como o elemento que são de cores. Por exemplo, se você escolher uma cor de alto contraste para o texto dentro de uma janela, use WindowText e não ControlText.  
  
2.  **Escolha primeiro e segundo plano pares** juntos ou pode não estar certo de que sua opção de cor funcionará em todos os temas de alto contraste.  
  
3.  **Determinar quais partes de sua interface do usuário são os mais importantes e certifique-se de que áreas de conteúdo destacará.** Você perderá muitos detalhes que normalmente seriam distinguir diferenças sutis de matiz da cor, portanto, o uso de cores de borda de alta segurança é comum definir áreas de conteúdo, porque não há nenhum variações de cor para diferentes áreas de conteúdo.  
  
### <a name="system-color-set"></a>Conjunto de cores do sistema  
 A tabela [Blog da equipe do WPF: referência SystemColors](http://blogs.msdn.com/b/wpf/archive/2010/11/30/systemcolors-reference.aspx) indica o conjunto completo de nomes de cores do sistema e os matizes correspondentes exibidos em cada tema.  
  
 Quando aplicar limitado o conjunto de cores para a interface do usuário, *é esperado que você perderá detalhes sutis que estavam presentes nos temas "normais"*. Aqui está um exemplo da interface do usuário com cores cinzas sutis que são usados para distinguir as áreas em uma janela de ferramenta. Quando combinado com a mesma janela exibida no modo de alto contraste, você pode ver que os planos de fundo são o mesmo matiz e as bordas dessas áreas são indicadas por borda sozinha:  
  
 ![Janela propriedades](../../extensibility/ux-guidelines/media/030303-a_propertieswindow.png "030303 a_PropertiesWindow")  
  
 **Exemplo de detalhes como sutis são perdidas quando em alto contraste**  
  
#### <a name="choosing-text-colors-in-an-editor"></a>Escolher cores de texto em um editor  
 Texto coloridos serão é usado em um editor ou em uma superfície de design para indicar o significado, como permitir que para facilitar a identificação dos grupos de itens semelhantes. Em um tema de alto contraste, no entanto, você não tem a capacidade de diferenciar entre mais de três cores de texto. WindowText, texto cinza e HotTrackText são apenas cores disponíveis nas superfícies de WindowBackground. Uma vez que não é possível usar mais de três cores, escolha cuidadosamente as diferenças mais importantes que você deseja exibir no modo de alto contraste.  
  
 Matizes para cada um dos nomes de token permitidos em uma superfície do editor, que aparecem em cada tema de alto contraste:  
  
 ![Comparação de editor alto contraste](../../extensibility/ux-guidelines/media/030303-b_hceditorcomparison.png "030303 b_HCEditorComparison")  
  
 **Comparação de editor alto contraste**  
  
 Exemplos da superfície do editor no tema azul:  
  
 ![Editor do tema azul](../../extensibility/ux-guidelines/media/030303-c_editorblue.png "030303 c_EditorBlue")  
  
 **Editor do tema azul**  
  
 ![Editor do tema de alto contraste](../../extensibility/ux-guidelines/media/030303-d_editorhc1.png "030303 d_EditorHC1")  
  
 **Editor do tema de alto contraste n º 1**  
  
### <a name="usage-patterns"></a>Padrões de uso  
 Vários elementos de interface do usuário comuns já definidas de cores de alto contraste. Você pode consultar esses padrões de uso ao escolher seu próprio sistema de nomes de cores, para que os elementos da interface são consistentes com os componentes similares.  
  
|Cor do sistema|Uso|  
|------------------|-----------|  
|Legenda ativa|-IDE ativa e a janela rafted glifos de botão em foco e pressione<br />-Plano de fundo do título barra do IDE e windows rafted<br />-Plano de fundo de barra de status padrão|  
|ActiveCaptionText|-IDE ativa e rafted janelas de primeiro plano da barra de título (texto e glifos)<br />-Plano de fundo e borda dos botões de janela ativa em foco e pressione|  
|Controle|-Caixa de combinação lista suspensa e pesquisa controle padrão e desabilitado em segundo plano, incluindo o botão suspenso<br />-Plano de fundo do botão Encaixar alvo<br />-Plano de fundo de barra de comando<br />-Plano de fundo de janela de ferramenta|  
|ControlDark|-Plano de fundo IDE<br />-Separadores de barra de menu e comando<br />-Borda da barra de comando<br />-Sombras menu<br />-Ferramenta borda da guia janela padrão e passe o mouse e o separador<br />-De documentos bem fundo do botão de estouro<br />-Borda de glifo de destino dock|  
|ControlDarkDark|-Janela de guia de documento foco, selecionado|  
|ControlLight|-Borda ocultar automaticamente<br />-Borda da lista suspensa e de caixa de combinação<br />-Encaixar o plano de fundo de destino e borda|  
|ControlLightLight|-Borda temporária focalizada selecionada|  
|ControlText|-Glifo de lista suspensa e de caixa de combinação<br />-Texto da guia ferramenta janela desmarcada|  
|Texto cinza|-Caixa de combinação e borda da lista desabilitada suspenso, suspenso glifo, texto e texto do item de menu<br />-Texto de menu desabilitado<br />-Texto do cabeçalho pesquisa controle 'Opções de pesquisa'<br />-Separador de seção de controle pesquisa|  
|Realçar|-All em foco e pressionado planos de fundo e bordas, exceto combinação caixa suspensa documento e plano de fundo do botão bem estouro de borda do botão<br />-Planos de fundo do item selecionado|  
|Texto realçado|-All em foco e pressionados primeiros planos (texto e glifos)<br />-Ferramenta focada janela e documento guia janela controle em primeiro plano<br />-Borda de barra de título de janela de ferramenta focada<br />-Primeiro plano guia provisória concentrado e selecionado<br />-Borda do botão de estouro bem documento em foco e pressione<br />-Borda de ícone selecionado|  
|HotTrack|-Plano de fundo Scrollbar thumb e pressione a borda<br />-Glifo de seta Scrollbar pressione|  
|Legenda inativa|-IDE inativo e janela rafted glifos de botão em foco<br />-Plano de fundo do título barra do IDE e windows rafted<br />-Plano de fundo de controle de pesquisa desabilitado|  
|Texto da legenda inativa|-IDE inativo e foreground de barra de título rafted windows (texto e glifos)<br />-Plano de fundo de botões de janela inativa e borda em foco<br />-Borda e plano de fundo do botão ferramenta foco janela<br />-Primeiro plano de controle de pesquisa desabilitado|  
|Menu|-Plano de fundo de menu suspenso<br />-Plano de fundo de marca de seleção verificado e desabilitado|  
|MenuText|-Borda do menu suspenso<br />-Seleção de marca de seleção<br />-Glifos menu<br />Lista suspensa texto de menu<br />-Borda de ícone selecionado|  
|Barra de Rolagem|-Plano de seta barra de rolagem e a barra de rolagem, todos os estados|  
|Janela|-Plano de fundo de guia ocultar automaticamente<br />-Menu barra e plano de fundo de prateleira de comando<br />-Plano de fundo do documento foco ou desmarcados janela guia e uma borda de documento, para guias abertas e temporária<br />-Segundo plano da janela da barra de título ferramenta foco<br />-Ferramenta janela guia plano de fundo, ambos marcadas e desmarcadas|  
|Quadro da janela|-Borda IDE|  
|WindowText|-Primeiro plano de guia ocultar automaticamente<br />-Primeiro plano de guia de janela de ferramenta selecionada<br />-Guia da janela de documento foco e de primeiro plano de foco ou desmarcados guia provisória<br />-Árvore em primeiro plano do modo de exibição padrão e passe o mouse sobre o glifo não selecionado<br />-Borda da janela de ferramenta guia selecionada<br />-Glifo, borda e plano de fundo de thumb Scrollbar|  
  
##  <a name="a-namebkmkexposingcolorsforendusersa-exposing-colors-for-end-users"></a><a name="BKMK_ExposingColorsForEndUsers"></a>Exposição de cores para os usuários finais  
  
### <a name="overview"></a>Visão Geral  
 Às vezes você desejará permitir ao usuário final personalizar a interface do usuário, como quando você estiver criando um editor de código ou na superfície de design. A maneira mais comum de fazer isso é usando o **Ferramentas > opções** caixa de diálogo. A menos que você tenha altamente especializada da interface do usuário que requer controles especiais, a maneira mais fácil para apresentar a personalização é por meio de **fontes e cores** página dentro do **ambiente** seção da caixa de diálogo. Para cada elemento que expõe para personalização, o usuário pode optar por alterar a cor de primeiro plano, cor de plano de fundo ou ambos.  
  
### <a name="building-a-vspackage-for-your-customizable-colors"></a>Criar um VSPackage para suas cores personalizáveis  
 Um VSPackage pode controlar as fontes e cores por meio de categorias personalizadas e exibir os itens na página de propriedades de fontes e cores. Ao usar esse mecanismo, VSPackages deve implementar o [IVsFontAndColorDefaultsProvider](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.ivsfontandcolordefaultsprovider.aspx) interface e suas interfaces associadas.  
  
 Em princípio, esse mecanismo pode ser usado para modificar todos os itens de exibição existentes e as categorias que os contêm. No entanto, ele não deve ser usado para modificar a categoria do Editor de texto ou seus itens de exibição. Para obter mais informações sobre a categoria do Editor de texto, consulte [visão geral de cor e fonte](https://msdn.microsoft.com/en-us/library/bb165065.aspx).  
  
 Para implementar categorias personalizadas ou exibir itens, um VSPackage deve:  
  
-   **Criar ou identificar categorias no registro.** Implementação do IDE do **fontes e cores** página de propriedades usa essas informações para consultar o serviço de suporte a uma determinada categoria corretamente.  
  
-   **Criar ou identificar grupos no registro (opcional).** Ele pode ser útil definir um grupo, que representa a união de duas ou mais categorias. Se um grupo estiver definido, o IDE automaticamente mescla subcategorias e distribui itens de exibição dentro do grupo.  
  
-   **Implementar o suporte do IDE.**  
  
-   **Lidar com alterações de fonte e cor.**  
  
#### <a name="to-create-or-identify-categories"></a>Para criar ou identificar categorias  
 Criar um tipo especial de entrada de registro de categoria em [HKLM\Software\Microsoft. \Visual Studio\\<Visual studio=""></Visual>\>\FontAndColors\\<>\>]. \<Categoria > é o nome da categoria não localizado.  
  
 Preencha o registro com dois valores:  
  
|Nome|Tipo|Dados|Descrição|  
|----------|----------|----------|-----------------|  
|Categoria|REG_SZ|GUID|Um GUID criado para identificar a categoria|  
|Pacote|REG_SZ|GUID|O GUID do serviço de VSPackage que ofereça suporte a categoria|  
  
 O serviço especificado no registro deve fornecer uma implementação de [IVsFontAndColorDefaults](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.ivsfontandcolordefaults.aspx) para a categoria correspondente.  
  
#### <a name="to-create-or-identify-groups"></a>Para criar ou identificar grupos  
 Criar um tipo especial de entrada de registro de categoria em [HKLM\Software\Microsoft. \Visual Studio\\<Visual studio=""></Visual>\>\FontAndColors\\<>\>]. \<grupo > é o nome do grupo não localizado.  
  
 Preencha o registro com dois valores:  
  
|Nome|Tipo|Dados|Descrição|  
|----------|----------|----------|-----------------|  
|Categoria|REG_SZ|GUID|Um GUID criado para identificar a categoria|  
|Pacote|REG_SZ|GUID|O GUID do serviço de VSPackage que ofereça suporte a categoria|  
  
 O serviço especificado no registro deve fornecer uma implementação de **T:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup** para o grupo correspondente.  
  
 ![Interface IVsFontAndColorGroup](../../extensibility/ux-guidelines/media/0304-a_fontandcolorgroup.png "a_FontAndColorGroup&0304;")  
  
### <a name="to-implement-ide-support"></a>Para implementar o suporte do IDE  
 Implementar [GetObject](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.ivsfontandcolordefaultsprovider.getobject.aspx), que retorna um [IVsFontAndColorDefaults](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.ivsfontandcolordefaults.aspx) interface ou uma **T:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup** interface ao IDE para cada categoria ou grupo GUID fornecida.  
  
 Para cada categoria oferece suporte a um VSPackage implementa uma instância separada do [IVsFontAndColorDefaults](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.ivsfontandcolordefaults.aspx) interface.  
  
 Os métodos implementados por meio de [IVsFontAndColorDefaults](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.ivsfontandcolordefaults.aspx) deve fornecer o IDE com:  
  
-   Listas de itens de exibição na categoria  
  
-   Nomes localizáveis para exibir itens  
  
-   Exibir informações de cada membro da categoria  
  
 **Observação:** cada categoria deve conter pelo menos um item de exibição.  
  
 O IDE usa o **T:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup** interface para definir uma união de várias categorias.  
  
 Sua implementação fornece o IDE com:  
  
-   Uma lista das categorias que compõem um grupo específico  
  
-   Acesso a instâncias de [IVsFontAndColorDefaults](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.ivsfontandcolordefaults.aspx) cada categoria dentro do grupo de suporte  
  
-   Nomes de grupo localizáveis  
  
#### <a name="updating-the-ide"></a>Atualizando o IDE  
 O IDE armazena informações sobre as configurações de fonte e cor. Portanto, depois de qualquer modificação da configuração do IDE fontes e cores, garantindo que o cache seja atualizado é uma prática recomendada.  
  
 Atualizando o cache é feito por meio de [IvsFontAndColorCacheManager](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.ivsfontandcolorcachemanager.aspx) de interface e pode ser realizados itens selecionados globalmente ou apenas em.  
  
### <a name="handling-font-and-color-changes"></a>Tratando alterações de fonte e cor  
 Para suporte a colorização de texto que exibe um VSPackage corretamente, o serviço de colorização suporta o VSPackage deve responder às alterações iniciadas pelo usuário feitas por meio da página de propriedades de fontes e cores.  
  
 Para fazer isso, um VSPackage deve:  
  
-   **tratar eventos gerados pelo IDE** Implementando o [IVsFontAndColorEvents](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.ivsfontandcolorevents.aspx) interface. O IDE chama o método apropriado seguindo as modificações do usuário da página fontes e cores. Por exemplo, ele chama o [OnFontChanged](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.ivsfontandcolorevents.onfontchanged.aspx) método se uma nova fonte é selecionada.  
  
 **OR**  
  
-   **sondar o IDE para que as alterações**. Isso pode ser feito por meio do sistema implementado [IVsFontAndColorStorage](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.ivsfontandcolorstorage.aspx) interface. Embora principalmente para suporte de persistência, o [GetItem](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.ivsfontandcolorstorage.getitem.aspx) método pode obter informações de fontes e cores para exibir itens. Para obter mais informações sobre configurações de fonte e cor, consulte o artigo do MSDN [acessar fonte armazenados e as configurações de cor](https://msdn.microsoft.com/en-us/library/bb166382.aspx).  
  
 **Observação:** para garantir que os resultados de pesquisa estão corretos, use o [IVsFontAndColorCacheManager](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.ivsfontandcolorcachemanager.aspx) interface para determinar se uma liberação de cache e a atualização são necessárias antes de chamar os métodos de recuperação do [IVsFontAndColorStorage](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.ivsfontandcolorstorage.aspx) interface.  
  
#### <a name="registering-custom-font-and-color-category-without-implementing-interfaces"></a>Registrar fonte personalizada e a categoria de cor sem implementar interfaces  
 O exemplo de código a seguir demonstra como registrar a fonte personalizada e categoria de cor sem implementar interfaces:  
  
```  
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\FontAndColors\CSharp Tool Window]  
"Package"="{F5E7E71D-1401-11D1-883B-0000F87579D2}"  
"Category"="{9FF46859-A47E-47bf-8AC5-EC3DBE69D1FE}"  
"ToolWindowPackage"="{7259e420-6241-4e0d-b535-5b820671d183}"  
  
    "NameID"=dword:00000064  
```  
  
 **OBSERVAÇÃO:**  
  
-   "NameID" = a ID de recurso do nome da categoria localizada no pacote  
  
-   "ToolWindowPackage" = GUID do pacote  
  
-   "Category" = "{9FF46859-A47E-47bf-8AC5-EC3DBE69D1FE}" é apenas um exemplo e o valor real pode ser um novo GUID fornecido pelo implementador.  
  
### <a name="set-the-font-and-color-property-category-guid"></a>Definir a categoria de propriedade fonte e cor GUID  
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
  
##  <a name="a-namebkmkdaytonaandwebuia-daytona-and-web-ui"></a><a name="BKMK_DaytonaAndWebUI"></a>Daytona e interface da web  
  
### <a name="overview"></a>Visão Geral  
 "Daytona" é um conjunto de APIs, ferramentas e serviços que permitem que um usuário crie plug-ins com HTML, CSS e JavaScript que pode ser usado em uma variedade de hosts, tais como o Visual Studio ou F12. Plug-ins são compostos de um componente portátil, que é escrito em HTML, CSS e JavaScript, e os componentes opcionais de host específico. Cada host Daytona pode ter seu próprio conjunto de convenções de interface do usuário, implícitas ou explícitas que um plug-in deve obedecer para aparecer nativo para seu ambiente. Alguns hosts, como o Visual Studio, permitem que os usuários finais alterar o tema"padrão" para que os aspectos visuais do host não podem ser alvo estaticamente ao criar uma folha de estilos. Isso representa um desafio para os desenvolvedores que criam plug-ins portátil. Este tópico explica como criar web da interface do usuário no Visual Studio usando o host Daytona de forma que oferece suporte a temas e alto contraste corretamente.  
  
### <a name="daytona-theming-mechanism"></a>Mecanismo de temas Daytona  
 O tempo de execução Daytona fornece um conjunto de serviços que abstrai as convenções de interface do usuário e recursos de temas do host. Esses serviços garantem que os plug-ins automaticamente em conformidade com as expectativas visual do usuário com base no ambiente que são hospedados em. Esse comportamento é fornecido por três recursos principais:  
  
1.  Uma folha de estilos inseridos em tempo de execução (plugin.css) que se aplica a um conjunto de regras CSS à interface do usuário do plug-in de forma transparente e estilos o conjunto padrão de controles HTML (por exemplo, HTMLInputElement e HTMLButtonElement  
  
2.  Um conjunto de tokens fornecidos pelo host que pode ser usado para elementos de interface do usuário de estilo usando valores que são baseados em tema em vez de codificados  
  
    1.  uma sintaxe declarativa para acessar esses símbolos com CSS  
  
    2.  uma API para acessar programaticamente os tokens de tema do JavaScript  
  
3.  Notificação de alterações de tema  
  
#### <a name="runtime-injected-style-sheet"></a>Folha de estilos inseridos em tempo de execução  
 As coordenadas de tempo de execução Daytona com o host para injetar um estilo de folha que automaticamente os elementos de interface do usuário padrão de um plug-in de temas. Isso inclui o estilo para os seguintes conceitos:  
  
-   Fonte do ambiente  
  
-   Cores de plano de fundo  
  
-   Hiperlinks  
  
-   Controles de formulário (por exemplo: \<selecione >, \<entrada >, \<botão >  
  
-   Tabelas  
  
-   Títulos  
  
-   Barras de rolagem  
  
 Isso significa que se a interface do usuário é composto de controles de interface do usuário HTML padrão, em seguida, nenhum trabalho adicional deve ser necessária responda corretamente a alterações de tema e oferecer suporte de alto contraste.  
  
#### <a name="custom-ui"></a>Interface do usuário personalizada  
 Em quase todos os casos não trivial, o padrão de controles de interface do usuário HTML será suficiente para fornecer uma experiência completa para um plug-in e interface do usuário personalizada deve ser introduzido. Para oferecer suporte a fonte correta use opções e cor, **tokens de tema** deve ser usado declarativamente em CSS ou imperativa por meio da API de JavaScript descrito abaixo. O tempo de execução Daytona cuidará de atualizar as folhas de estilos que usam esses tokens no carregamento de plug-in e alterações de tema.  
  
##### <a name="theme-tokens"></a>Tokens de tema  
 Ambos os tokens de tema padrão e específica de host estão disponíveis. Tokens padrão são injetadas host e está sempre disponível. É preferível usar os tokens padrão sempre que possível. Tokens padrão têm garantia de ser fornecido por todos os hosts Daytona e usá-los torna seu plug-in inerentemente mais portátil. O conjunto de tokens padrão está sujeitas a alterações, embora somente novos tokens devem ser adicionadas e nenhum deve ser removido. A versão do Visual Studio 2013 está documentada abaixo:  
  
|Nome de token|Descrição|  
|----------------|-----------------|  
|cor de plano de fundo de plug-in|A cor de plano de fundo padrão para o plug-in|  
|cor de plug-in|A cor de primeiro plano padrão para o plug-in|  
|plug-in contextmenu-ativo cores|A cor padrão do primeiro plano seleção menus de contexto quando eles estiverem ativos (tem o foco)|  
|plug-in-contextmenu-cor de plano de fundo|A cor de plano de fundo padrão para os menus de contexto|  
|plug-in-contextmenu-cor de borda|A cor de borda padrão para menus de contexto|  
|cor do plug-in contextmenu|A cor de primeiro plano padrão para menus de contexto|  
|plug-in-contextmenu-cor de foco|A cor de fundo em foco padrão para os menus de contexto|  
|plug-in-contextmenu-hover-cor do texto|A cor de primeiro plano de foco padrão para os menus de contexto|  
|plug-in-contextmenu ícone checkbox|A cor do ícone caixa de seleção padrão para os menus de contexto|  
|plug-in-contextmenu-inativo-cor do texto|A cor padrão do primeiro plano seleção menus de contexto quando estão inativos|  
|plug-in contextmenu-separador de cor|A cor do separador de padrão de menus de contexto|  
|família de fontes de plug-in|A família de fontes padrão a ser usado para o plug-in|  
  
 No Visual Studio, os seguintes tokens de plug-in de fonte baseiam-se nas configurações de fonte de ambiente:  
  
-   tamanho da fonte de plug-in  
  
-   espessura da fonte de plug-in  
  
-   plug-in-realce-cor de plano de fundo  
  
-   cor de realce de plug-in  
  
-   plug-in inativo cor  
  
 Os tokens de plug-in link a seguir são usados para estilo HTMLElements (hiperlinks):  
  
-   cor do link de plug-in  
  
-   plug-in-link ativo cor  
  
-   plug-in-link-cor de foco  
  
 Plugin.CSS estilos barras de rolagem por padrão, usando os seguintes tokens para melhor suporte os temas em vários hosts (em especial, Visual Studio):  
  
-   plug-in do scrollbar-seta cores  
  
-   plug-in-scrollbar-cor de plano de fundo  
  
-   plug-in do scrollbar-face cores  
  
 Os seguintes tokens de seleção de plug-in são usados para alterar o estilo de HTMLSelectElement (caixa de combinação suspensa):  
  
-   plug-in-Selecione-opção-cor de fundo  
  
-   plug-in-Selecionar opção de cor  
  
-   Plugin-Select-Option-checked-background-color  
  
-   Plugin-Select-Option-checked-Border-Color  
  
-   Plugin-Select-Option-checked-Foreground-Color  
  
-   Plugin-Select-Option-hover-background-color  
  
-   Plugin-Select-Option-hover-Border-Color  
  
-   Plugin-Select-Option-hover-Foreground-Color  
  
-   plug-in-Selecione-cor de borda  
  
-   plug-in-Selecione-cor de plano de fundo  
  
-   Selecione plug-in-cor do primeiro plano  
  
-   plug-in-selecione-hover-cor de fundo  
  
-   plug-in-selecione--borda-cor de foco  
  
-   plug-in-selecione-hover--cor de primeiro plano  
  
-   plug-in-tabela-cor de borda  
  
-   plug-in-tabela-cabeçalho-cor de fundo  
  
-   plug-in-tabela-cabeçalho-color  
  
-   plug-in-textbox-cor de borda  
  
-   plug-in-textbox-cor de plano de fundo  
  
-   cor do texto de plug-in  
  
-   plug-in-textbox-desabilitado-cor de fundo  
  
-   plug-in-textbox-desabilitado--cor da borda  
  
-   plug-in de texto-desabilitado cores  
  
 Esses tokens devem ser usados para *todas as* árvore exibições e tabelas, porque eles têm os padrões corretos definidos em vários hosts para dar suporte a temas e alto contraste:  
  
-   plug-in-treeview-conteúdo-cor de fundo  
  
-   plug-in treeview-conteúdo cores  
  
-   Plugin-TreeView-Content-inactive-Selected-Color  
  
-   Plugin-TreeView-Content-MouseOver-background-color  
  
-   plug-in treeview-conteúdo-mouseover-cores  
  
-   Plugin-TreeView-Content-inactive-Selected-Color  
  
-   Plugin-TreeView-Content-Selected-background-color  
  
-   Plugin-TreeView-Content-Selected-Border-Color  
  
-   plug-in-treeview-conteúdo--cor selecionada  
  
##### <a name="host-specific-tokens"></a>Tokens de host específico  
 Além de oferecer suporte o conjunto padrão de tokens, hosts também podem fornecer tokens não padrão. Host do Visual Studio faz isso permitindo que o plug-in especificar aliases de token do tema em uma seção do Visual Studio específicos do manifesto. Por exemplo:  
  
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
  
 Este exemplo apresenta um token de tema, chamado "diagnóstico-host-borda", que pode ser referenciado de forma idêntica aos tokens padrão mencionados acima. O nome, categoria e key_type são usados para resolver a cor por meio de **IVsFontAndColorStorage** interface. Em muitos casos, é possível localizar as cores apropriadas (juntamente com a categoria, key_type e informações de nome) nos arquivos XML localizados em vscommon\themes. O mesmo mecanismo é usado se o seu pacote introduzir novas cores configuráveis: corresponde a categoria, key_type e nome para a cor que você deseja usar. Autores de plug-in devem tentar usar tokens padrão sempre que possível e apenas usar tokens de host específicos quando absolutamente necessário.  
  
##### <a name="using-theme-tokens-in-css"></a>Usando tokens de tema em CSS  
 Tokens de tema são chamados por meio de uma sintaxe de comentário especificamente formatado. As regras de análise do token:  
  
1.  A expressão de comentário deve ser incluída dentro de colchetes (**[]**).  
  
2.  Todos os espaços em branco dentro do comentário, mas fora da expressão, é ignorado.  
  
3.  A expressão de comentário deve vir imediatamente após a propriedade substitui.  
  
4.  Nenhum espaço em branco à esquerda ou à direita da expressão será cortado.  
  
5.  Cada nome de token dentro da expressão deve ser colocado entre chaves (por exemplo, **{font-family}** e **{cor de foco botão}**). Caso contrário, ele será tratado como um valor literal.  
  
 Os seguintes são exemplos de como o analisador token substituirá os valores CSS, supondo que o **cor de plano de fundo de plug-in** token tem o valor #000 e **plug-in-font-family** token tem o valor de "Verdana".  
  
|CSS criados|CSS analisada|Observações|  
|------------------|----------------|-----------|  
|`background-color: #fff; /*[{plugin-background-color}]*/`|`background-color: #000;`|O valor padrão é substituído pelo valor específica de host dinâmico.|  
|`background-color: #fff; /*   [{plugin-background-color}]   */`|`background-color: #000;`|O espaço em branco fora da expressão é ignorado.|  
|`background-color: #fff; /*[   {plugin-background-color}   ]*/`|`background-color: #000;`|O espaço em branco à esquerda e à direita da expressão é cortado.|  
|`background-color: #fff; /*{plugin-background-color}*/`|`background-color: #fff;`|A expressão não está entre colchetes e, portanto, o comentário será ignorado.|  
|`background-color: #fff; /*[plugin-background-color]*/`|`background-color: plugin-background-color;`|O token não é colocado entre chaves e, portanto, é tratado como um valor literal.|  
|`/*[{plugin-background-color}]*/ background-color: #fff;`|`background-color: #fff;`|O comentário não segue o valor da propriedade e, portanto, será ignorado.|  
|`background-color: #fff;  /*[{plugin-background-color}]*/`|`background-color: #fff;`|*Mesmo que acima*|  
|`/*[{plugin-background-color}]*/  background-color: #fff;`|`background-color: #fff;`|*Mesmo que acima*|  
|`font-family: Arial, sans-serif; /*[{plugin-font-family}, sans-serif]*/`|`font-family: Verdana, sans-serif;`|O token é substituído e o conteúdo literal é mantido.|  
|`background-image: linear-gradient(0% #000, 100% #ccc); /*[linear-gradient(0% #000, 100% {plugin-background-color})]*/`|`background-image: linear-gradient(0% #000, 100% #000);`|*Mesmo que acima*|  
  
 Se um arquivo CSS inclui os tokens de tema que devem estar marcados pelo atributo de dados de plug-in de tema no elemento link no arquivo HTML. Por exemplo:  
  
```  
<link href="default.css" rel="stylesheet" data-plugin-theme="true" />  
```  
  
##### <a name="using-theme-tokens-from-javascript"></a>Uso de tokens de tema do JavaScript  
 Enquanto a interface do usuário personalizada deve ter tema por CSS sempre que possível, há situações em que o valor de um tema token precisam ser acessados por meio de programação. Por exemplo, se a interface do usuário personalizada que está sendo desenhado em um CanvasElement que não herda o estilo de CSS, ou se um elemento de interface do usuário está sendo dinamicamente criada em vez de fazer referência a folhas de estilo. Os cenários são habilitados usando a API Daytona **Plugin.Theme.getValue**. Essa função retorna um valor de tema fornecida pelo host quando é atribuído um nome de token.  
  
|Não com temas|Com temas|  
|----------------|------------|  
|`var surface = document.getElementById("surface").getContext("2d");  surface.fillStyle = "#ccc";  surface.fillRect(0, 0, 200, 200);`|`var surface = document.getElementById("surface").getContext("2d");  surface.fillStyle = ("plugin-background-color");  surface.fillRect(0, 0, 200, 200);`|  
|`var el = document.createElement("div");  el.style.backgroundColor = "#ccc";`|`var el = document.createElement("div");  el.style.backgroundColor = Plugin.Theme.getValue("plugin-background-color");`|  
  
 Se os tokens são usados no JavaScript**, o evento de alteração de tema deve ser manipulado para responder a atualizações**. Isso é desnecessário para tokens de tema usados declarativamente em CSS, como o tempo de execução Daytona cuida para o plug-in. O evento de tema pode ser tratado da seguinte maneira:  
  
|Membro (único manipulador)|Evento de DOM (vários manipuladores)|  
|-------------------------------|--------------------------------------|  
|`Plugin.Theme.onchange = function () {      // re-draw dynamic UI here  }`|`Plugin.Theme.addEventListener("change", function () {      // re-draw dynamic UI here  });`|  
  
 Nesse caso, seria muito comum para chamar novamente **Plugin.Theme.getValue** nesses manipuladores, como o valor dos tokens tema provavelmente alterado quando o tema alterado.  
  
##### <a name="standard-token-mapping"></a>Mapeamento de token padrão  
 Os tokens padrão são mapeados para as cores de ambiente e o Shell. A lista a seguir fornece um tipo de quais são esses mapeamentos.  
  
|Nome de token|VS mapeamento (EnvironmentColors)|  
|----------------|--------------------------------------|  
|cor de plug-in|ToolWindowTextColorKey|  
|cor de plano de fundo de plug-in|ToolWindowBackgroundColorKey|  
|cor do link de plug-in|ControlLinkTextColorKey|  
|plug-in-link-cor de foco|ControlLinkTextHoverColorKey|  
|plug-in-link ativo cor|ControlLinkTextPressedColorKey|  
|cor de realce de plug-in|HighlightTextColorKey|  
|plug-in-realce-cor de plano de fundo|HighlightColorKey|  
|plug-in-tabela-cabeçalho-cor de fundo|GridHeadingBackgroundColorKey|  
|plug-in-tabela-cabeçalho-color|GridHeadingTextColorKey|  
|plug-in-tabela-cor de borda|GridLineColorKey|  
|plug-in-botão-Cor de plano de fundo|ButtonFaceColorKey|  
|plug-in-botão-hover-cor de fundo|ButtonHighlightColorKey|  
|cor do botão de plug-in|ButtonTextColorKey|  
|plug-in-botão-Cor de borda|ButtonBorderColorKey|  
  
##### <a name="theme-changes"></a>Alterações de tema  
 O Visual Studio host gatilhos plug-in tema é alterado quando um usuário final faz alterações para as seguintes configurações:  
  
 **Tema de cor:**  
  
 ![Alterações de tema de cor](../../extensibility/ux-guidelines/media/0305-a_colortheme.png "a_ColorTheme&0305;")  
  
 **Tema do ambiente:**  
  
 ![Alterações de tema do ambiente](../../extensibility/ux-guidelines/media/0305-b_environmenttheme.png "b_EnvironmentTheme&0305;")  
  
 **Tema do sistema operacional** (somente ao alterar para e de alto contraste):  
  
 ![Alterações de tema do sistema operacional](../../extensibility/ux-guidelines/media/0305-c_ostheme.png "c_OSTheme&0305;")
