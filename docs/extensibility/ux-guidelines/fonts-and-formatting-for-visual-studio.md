---
title: "Fontes e formatação para o Visual Studio | Microsoft Docs"
ms.custom: 
ms.date: 04/26/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c3c3df69-83b4-4fd0-b5b1-e18c33f39376
caps.latest.revision: 5
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
ms.openlocfilehash: c55c135034f5b3b2dd09ccf94e22e56e8f04797e
ms.contentlocale: pt-br
ms.lasthandoff: 05/04/2017

---
# <a name="fonts-and-formatting-for-visual-studio"></a>Fontes e formatação para o Visual Studio
##  <a name="BKMK_TheEnvironmentFont"></a>A fonte de ambiente  
 Todas as fontes dentro do Visual Studio devem ser expostas ao usuário para personalização. Isso é feito principalmente através de **fontes e cores** página o **Ferramentas > Opções** caixa de diálogo. As três categorias principais de configurações de fonte são:  
  
-   **Fonte de ambiente** — a fonte principal para o IDE (ambiente de desenvolvimento integrado), usada para todos os elementos de interface, incluindo caixas de diálogo e janelas de documentos, janelas de ferramentas e menus. Por padrão, a fonte de ambiente é vinculada a uma fonte de sistema que aparece como 9 pt Segoe UI nas versões atuais do Windows. Usando uma fonte para todos os elementos de interface ajuda a garantir uma aparência consistente fonte em todo o IDE.  
  
-   **Editor de texto** — página de elementos que superfície no código e outros editores de texto podem ser personalizadas no Editor de texto em **Ferramentas > Opções**.  
  
-   **Coleções específicas** — designers windows que oferecem a personalização de seus elementos de interface do usuário pode expor fontes específicas para seu design de superfície em sua própria página de configurações em **Ferramentas > Opções**.  
  
### <a name="editor-font-customization-and-resizing"></a>Personalização do Editor de fonte e redimensionamento  
 Os usuários geralmente ampliar ou reduzir o tamanho e/ou a cor do texto no editor de acordo com sua preferência, independente da interface do usuário geral. Como a fonte de ambiente é usada em elementos que podem aparecer dentro ou como parte de um editor/designer, é importante observar o comportamento esperado quando um essas classificações de fonte é alterado.  
  
 Ao criar elementos de interface do usuário que aparecem no editor mas são não fazem parte do *conteúdo*, é importante usar a fonte de ambiente e não a fonte do texto para redimensionar elementos de maneira previsível.  
  
1.  Para texto de código no editor, redimensione com a definição de fonte do texto de código e responder ao nível de zoom do texto do editor.  
  
2.  Todos os outros elementos da interface devem ser vinculados à configuração de fonte de ambiente e respondem às alterações no ambiente global. Isso inclui (mas não está limitado a):  
  
    -   Texto nos menus de contexto  
  
    -   Texto em um adorno de editor, como o texto do menu de lâmpada, painel do editor de localização rápida e navegue até o painel  
  
    -   Rótulo de texto em caixas de diálogo, como **localizar nos arquivos** ou **Refatorar**  
  
### <a name="accessing-the-environment-font"></a>Acessar a fonte de ambiente  
 No código nativo ou WinForms, a fonte de ambiente pode ser acessada, chamando o método `IUIHostLocale::GetDialogFont` depois de consultar a interface do `SID_SUIHostLocale` service.  
  
 Para o Windows Presentation Foundation (WPF), derivar a classe de janela de diálogo do shell `DialogWindow` classe em vez do WPF `Window` classe.  
  
 Em XAML, o código tem esta aparência:  
  
```  
<ui:DialogWindow  
    x:Class"MyNameSpace.MyWindow"  
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"  
    xmlns:s="http://schemas.microsoft.com/winfx/2006/xaml"  
    xmlns:ui="clr-namespace:Microsoft.VisualStudio.PlatformUI;assembly=Microsoft.VisualStudio.Shell.11.0"  
    ShowInTaskbar="False"  
    WindowStartupLocation="CenterOwner"  
    Title="My Dialog">  
</ui:DialogWindow>  
  
code behind:  
  
internal partial class WebConfigModificationWindow : DialogWindow  
{  
}  
```  
  
 (Substitua `Microsoft.VisualStudio.Shell.11.0` com a versão atual da dll MPF.)  
  
 Para exibir a caixa de diálogo, chame "`ShowModal()`" na classe sobre `ShowDialog()`. `ShowModal()`Define o estado modal correto no shell, garante que a caixa de diálogo é centralizada na janela pai e assim por diante.  
  
 O código é da seguinte maneira:  
  
```  
MyWindow window = new MyWindow();  
window.ShowModal()  
```  
  
 `ShowModal`Retorna um bool? (booleano anulável) com o `DialogResult`, que pode ser usado se necessário. O valor de retorno será true se a caixa de diálogo foi fechada com **Okey**.  
  
 Se você precisar exibir algumas UI WPF que não é uma caixa de diálogo e está hospedado no seu próprio `HwndSource`, como uma janela pop-up ou uma janela filho WPF de uma janela do Win32/WinForms pai, você precisará definir o `FontFamily` e `FontSize` no elemento raiz do elemento WPF. (O shell define as propriedades na janela principal, mas eles não serão herdados após um `HWND`). O shell fornece recursos para o qual as propriedades podem ser associadas, como este:  
  
```  
<Setter property="FontFamily" Value="{DynamicResource VsFont.EnvironmentFontFamily}" />  
<Setter property="FontSize" Value="{DynamicResource VsFont.EnvironmentFontSize}" />  
```  
  
###  <a name="BKMK_Formatting"></a>Formatação de referência (dimensionamento/negrito)  
 Algumas caixas de diálogo exigem texto em negrito ou um tamanho diferente da fonte de ambiente. Anteriormente, as fontes maiores do que a fonte de ambiente foram codificadas como "`environment font +2`" ou semelhantes. Usar os trechos de código fornecido, monitores de alto DPI e certifique-se de que o texto de exibição sempre aparece no tamanho correto e peso (como luz ou Semilight).  
  
> **Observação: Antes de aplicar formatação, certifique-se de seguir as diretrizes encontradas [estilo de texto](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TextStyle).**  
  
 Para dimensionar a fonte de ambiente, defina o estilo do TextBlock ou rótulo conforme indicado. Cada um desses trechos de código, quando usados corretamente, gerará a fonte correta, incluindo as variações de tamanho e peso apropriadas.  
  
 Onde "`vsui`" é uma referência ao namespace `Microsoft.VisualStudio.Shell`:  
  
```  
xmlns:vsui="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.14.0" 
```  
  
#### <a name="375-environment-font--light"></a>Fonte de ambiente % 375 + luz  
 **Aparece como:** pt 34 Segoe UI Light  
 **Uso:** (raro) exclusivo da marca da interface do usuário, como na página de início

 **Código procedural:** onde `textBlock` é um TextBlock definido anteriormente e `label` é um rótulo definido anteriormente:  
  
```  
textBlock.SetResourceReference(TextBlock.StyleProperty,    
        VsResourceKeys.TextBlockEnvironment375PercentFontSizeStyleKey);   
label.SetResourceReference(Label.StyleProperty,    
        VsResourceKeys.LabelEnvironment375PercentFontSizeStyleKey);  
```  
  
 **XAML:** definir o estilo do rótulo ou TextBlock conforme mostrado.  
  
```  
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironment375PercentFontSizeStyleKey}}">TextBlock: 375 Percent Scaling</TextBlock>   
<Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironment375PercentFontSizeStyleKey}}">Label: 375 Percent Scaling</Label>  
```  
  
#### <a name="310-environment-font--light"></a>Fonte de ambiente % 310 + luz  
 **Aparece como:** pt 28 Segoe UI Light   
 **Uso:** títulos de caixa de diálogo assinatura grande, principais em relatórios  
  
 **Código procedural:** onde `textBlock` é um TextBlock definido anteriormente e `label` é um rótulo definido anteriormente:  
  
```  
textBlock.SetResourceReference(TextBlock.StyleProperty,    
        VsResourceKeys.TextBlockEnvironment310PercentFontSizeStyleKey);   
label.SetResourceReference(Label.StyleProperty,    
        VsResourceKeys.LabelEnvironment310PercentFontSizeStyleKey);    
```  
  
 **XAML:** definir o estilo do rótulo ou TextBlock conforme mostrado.  
  
```  
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironment310PercentFontSizeStyleKey}}">TextBlock: 310 Percent Scaling</TextBlock>   
<Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironment310PercentFontSizeStyleKey}}">Label: 310 Percent Scaling</Label>     
```  
  
#### <a name="200-environment-font--semilight"></a>Fonte de ambiente 200% + Semilight  
 **Aparece como:** 18 pt Segoe UI Semilight    
 **Uso:** subtítulos, títulos em caixas de diálogo de pequenos e médios  
  
 **Código procedural:** onde `textBlock` é um TextBlock definido anteriormente e `label` é um rótulo definido anteriormente: 
  
```  
textBlock.SetResourceReference(TextBlock.StyleProperty,    
        VsResourceKeys.TextBlockEnvironment200PercentFontSizeStyleKey);   
label.SetResourceReference(Label.StyleProperty,    
        VsResourceKeys.LabelEnvironment200PercentFontSizeStyleKey);    
```  
  
 **XAML:** definir o estilo do rótulo ou TextBlock conforme mostrado:  
  
```  
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironment200PercentFontSizeStyleKey}}">TextBlock: 200 Percent Scaling</TextBlock>   
<Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironment200PercentFontSizeStyleKey}}">Label: 200 Percent Scaling</Label>    
```  
  
#### <a name="155-environment-font"></a>Fonte de ambiente 155%  
 **Aparece como:** 14 pt Segoe UI    
 **Uso:** títulos de seção no documento bem relatórios ou interface do usuário  
  
 **Código procedural:** onde `textBlock` é um TextBlock definido anteriormente e `label` é um rótulo definido anteriormente:  
  
```  
textBlock.SetResourceReference(TextBlock.StyleProperty,    
        VsResourceKeys.TextBlockEnvironment155PercentFontSizeStyleKey);   
label.SetResourceReference(Label.StyleProperty,    
        VsResourceKeys.LabelEnvironment155PercentFontSizeStyleKey);    
```  
  
 **XAML:** definir o estilo do rótulo ou TextBlock conforme mostrado:  
  
```  
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironment155PercentFontSizeStyleKey}}">TextBlock: 155 Percent Scaling</TextBlock>   
<Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironment155PercentFontSizeStyleKey}}">Label: 155 Percent Scaling</Label>  
```  
  
#### <a name="133-environment-font"></a>Fonte de ambiente % 133  
 **Aparece como:** 12 pt Segoe UI    
 **Uso:** subtítulos menores em caixas de diálogo de assinatura e documento bem da interface do usuário  
  
 **Código procedural:** onde `textBlock` é um TextBlock definido anteriormente e `label` é um rótulo definido anteriormente:  
  
```  
textBlock.SetResourceReference(TextBlock.StyleProperty,    
        VsResourceKeys.TextBlockEnvironment133PercentFontSizeStyleKey);   
label.SetResourceReference(Label.StyleProperty,    
        VsResourceKeys.LabelEnvironment133PercentFontSizeStyleKey);    
```  
  
 **XAML:** definir o estilo do rótulo ou TextBlock conforme mostrado:  
  
```  
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironment133PercentFontSizeStyleKey}}">TextBlock: 133 Percent Scaling</TextBlock>   
<Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironment133PercentFontSizeStyleKey}}">Label: 133 Percent Scaling</Label>    
```  
  
#### <a name="122-environment-font"></a>Fonte de ambiente 122%  
 **Aparece como:** 11 pt Segoe UI    
 **Uso:** seção títulos em caixas de diálogo de assinatura, superior de nós na exibição de árvore, navegação de tabulação vertical  
  
 **Código procedural:** onde `textBlock` é um TextBlock definido anteriormente e `label` é um rótulo definido anteriormente:  
  
```  
textBlock.SetResourceReference(TextBlock.StyleProperty,    
        VsResourceKeys.TextBlockEnvironment122PercentFontSizeStyleKey);   
label.SetResourceReference(Label.StyleProperty,    
        VsResourceKeys.LabelEnvironment122PercentFontSizeStyleKey);    
```  
  
 **XAML:** definir o estilo do rótulo ou TextBlock conforme mostrado:  
  
```  
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironment122PercentFontSizeStyleKey}}">TextBlock: 122 Percent Scaling</TextBlock>   
<Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironment122PercentFontSizeStyleKey}}">Label: 122 Percent Scaling</Label>    
```  
  
#### <a name="environment-font--bold"></a>Fonte de ambiente + em negrito  
 **Aparece como:** em negrito 9 pt Segoe UI    
 **Uso:** rótulos e subtítulos em caixas de diálogo de assinatura, relatórios e documento bem da interface do usuário  
  
 **Código procedural:** onde `textBlock` é um TextBlock definido anteriormente e `label` é um rótulo definido anteriormente:  
  
```  
textBlock.SetResourceReference(TextBlock.StyleProperty,    
        VsResourceKeys.TextBlockEnvironmentBoldStyleKey);   
label.SetResourceReference(Label.StyleProperty,    
        VsResourceKeys.LabelEnvironmentBoldStyleKey);    
```  
  
 **XAML:** definir o estilo do rótulo ou TextBlock conforme mostrado:  
  
```  
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironmentBoldStyleKey}}"> Bold TextBlock</TextBlock>   
<Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironmentBoldStyleKey}}"> Bold Label</Label>    
```  
  
### <a name="localizable-styles"></a>Estilos localizáveis  
 Em alguns casos, os localizadores precisará modificar os estilos de fonte para localidades diferentes, como a remoção de negrito do texto para idiomas do Leste Asiático. Para possibilitar a localização de estilos de fonte, esses estilos devem estar dentro do arquivo. resx. É a melhor maneira de fazer isso e ainda Editar estilos de fonte no designer de formulário do Visual Studio definir explicitamente os estilos de fonte em tempo de design. Embora isso cria um objeto de fonte completa e pode parecer interromper a herança de fontes de pai, apenas a propriedade FontStyle é usada para definir a fonte.  
  
 A solução é conectar-se com o formulário de caixa de diálogo `FontChanged` eventos. No `FontChanged` mostram todos os controles de evento e verificar se a fonte está definida. Se estiver definido, mude para uma nova fonte com base na fonte do formulário e o estilo de fonte do controle anterior. Um exemplo no código é:  
  
```  
private void Form1_FontChanged(object sender, System.EventArgs e)  
{  
          SetFontStyles();  
}  
  
/// <summary>  
/// SetFontStyles - This function will iterate all controls on a page  
/// and recreate their font with the desired fontstyle.  
/// It should be called in the OnFontChanged handler (and also in the constructor  
/// in case the IUIService is not available so OnFontChange doesn't fire).  
/// This way, when the VS shell font is given to us the controls that have  
/// a different style for the font (bolded for example) will recreate their font  
/// and use the VS shell font but with a style variation (bolded ...).  
/// </summary>   
protected void SetFontStyles()  
{  
     SetFontStyles(this, this, this.Font);  
}  
  
protected static void SetFontStyles(Control topControl, Control parent, Font referenceFont)  
{  
     foreach(Control c in parent.Controls)  
     {  
          if (c.Controls != null && c.Controls.Count > 0) {  
               SetFontStyles(topControl, c, referenceFont);  
          }  
          if (c.Font != topControl.Font) {  
               c.Font = new Font(referenceFont, c.Font.Style);  
          }  
     }  
}  
```  
  
 Usar esse código, você garante que, quando a fonte do formulário é atualizada, as fontes de controles serão atualizados também. Esse método também deve ser chamado do construtor do formulário, porque a caixa de diálogo pode falhar obter uma instância de `IUIService` e `FontChanged` evento nunca será acionado. Capturando `FontChanged` permitirá caixas de diálogo Selecionar a nova fonte dinamicamente mesmo se a caixa de diálogo já estiver aberta.  
  
### <a name="testing-the-environment-font"></a>A fonte do ambiente de teste  
 Para garantir que a interface do usuário está usando a fonte de ambiente e respeita as configurações de tamanho, abra **Ferramentas > Opções > ambiente > fontes e cores** e selecione "Fonte de ambiente" sob a "Mostrar configurações de:" menu suspenso.  
  
 ![Configurações de fontes e cores nas ferramentas de &gt; caixa de diálogo Opções](../../extensibility/ux-guidelines/media/0201-a_optionsfonts.png "0201-a_OptionsFonts")<br />Configurações de fontes e cores nas ferramentas de &gt; caixa de diálogo Opções
  
 Defina a fonte para algo muito diferente do padrão. Para deixar claro que não atualizar a interface do usuário, escolha uma fonte com serifas (como "Times New Roman") e definir um tamanho muito grande. A interface do usuário para garantir que ele respeita o ambiente de teste. Aqui está um exemplo usando a caixa de diálogo de licença:  
  
 ![Exemplo de texto de interface do usuário que não respeita a fonte de ambiente](../../extensibility/ux-guidelines/media/0201-b_wrongfontdialog.png "0201-b_WrongFontDialog")<br />Exemplo de texto de interface do usuário que não respeita a fonte de ambiente
  
 Nesse caso, "Informações de usuário" e "Informações de produto" são não respeitar a fonte. Em alguns casos, isso pode ser uma opção de design explícito, mas pode ser um erro se a fonte explícita não for especificada como parte das especificações redline.  
  
 Para redefinir a fonte, clique em "Usar padrões" em **Ferramentas > Opções > ambiente > fontes e cores**.  
  
##  <a name="BKMK_TextStyle"></a>Estilo de texto  
 Estilo de texto refere-se maiusculas e minúsculas, peso e tamanho da fonte. Para obter diretrizes de implementação, consulte [a fonte de ambiente](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TheEnvironmentFont).  
  
### <a name="text-casing"></a>Uso de maiusculas e minúsculas do texto  
  
#### <a name="all-caps"></a>Todas em maiusculas  
 Não use tampas de todos os títulos ou rótulos no Visual Studio.  
  
#### <a name="all-lowercase"></a>Todas as minúsculas  
 Não use letras minúsculas para títulos ou rótulos no Visual Studio.  
  
#### <a name="sentence-and-title-case"></a>Caso oração e título  
 Texto do Visual Studio deve usar maiusculas/minúsculas ou maiusculas sentença, dependendo da situação.  
  
|Use capitalização de título para:|Use a capitalização de frase para:|  
|-------------------------|----------------------------|  
|Títulos de caixa de diálogo|Rótulos|  
|Caixas de grupo|Caixas de seleção|  
|Itens de menu|Botões de opção|  
|Itens de menu de contexto|Itens de caixa de lista|  
|Botões|Barras de status|  
|Rótulos de tabela||  
|Cabeçalhos de coluna||  
|Dicas de ferramenta||  
  
##### <a name="title-case"></a>Capitalização de título  
 Capitalização de título é um estilo no qual as primeiras letras da maioria ou todas as palavras dentro de uma frase estão em maiusculas. No Visual Studio, maiusculas/minúsculas é usada para vários itens, incluindo:  
  
-   **Dicas de ferramenta.** Exemplo: "visualização itens selecionados"  
  
-   **Cabeçalhos de coluna.** Exemplo: "resposta do sistema"  
  
-   **Itens de menu.** Exemplo: "Salvar tudo"  
  
 Ao usar a capitalização de título, estas são as diretrizes para quando aproveitar palavras e deixá-los em minúsculas:  
  
|Maiúsculas|Comentários e exemplos|  
|---------------|---------------------------|  
|Todos os substantivos||  
|Todos os verbos|Incluindo "É" e outras formas de "ser"|  
|Todos os advérbios|Incluindo "De" e "Quando"|  
|Todos os adjetivos|Incluindo "Isso" e "Que"|  
|Todos os pronomes|Incluindo o caso seja "Seu", bem como "É", uma contração do Pronome "-" e o verbo "é"|  
|Primeira e última palavras, independentemente de partes da fala||  
|Preposições que fazem parte de uma frase de verbo|"Fechar todos os Windows" ou "Desligamento do sistema"|  
|Todas as letras de um acrônimo|HTML, XML, URL, IDE, RGB|  
|A segunda palavra em uma palavra composta, se é um substantivo ou um adjetivo próprio, ou se as palavras têm o mesmo peso|Acesso de leitura/gravação de referência cruzada, Software de pré-lançamento do Microsoft, tempo de execução|  
  
|Minúsculas|Exemplos|  
|---------------|--------------|  
|A segunda palavra em uma palavra composta, se for um participle modificando a primeira palavra ou outra parte da fala|Como derivado|  
|Artigos, a menos que um seja a primeira palavra no título|um, um, o|  
|Conjunções coordenadas|e, mas, para, nem, ou|  
|Preposições com as palavras de quatro ou menos letras fora de uma frase de verbo|em, em, como para fora da, na parte superior do|  
|"Para" quando usada em uma frase infinita|"Como formatar o disco rígido"|  
  
##### <a name="sentence-case"></a>Sentença inteira  
 Sentença inteira é o método padrão de maiusculas e minúsculas para gravação no qual a primeira palavra da frase está em letras maiusculas, juntamente com qualquer substantivos e o Pronome "I". Em geral, a sentença inteira é mais fácil para um público mundial de ler, especialmente quando o conteúdo será convertido em uma máquina. Use a capitalização de frase para:  
  
1.  **Mensagens da barra de status.** Essas são simples, o resumo e fornecem apenas informações de status. Exemplo: "carregar arquivo de projeto"  
  
2.  **Todos os outros elementos de interface do usuário**, incluindo rótulos, caixas de seleção, botões e itens de caixa de lista. Exemplo: "Selecionar todos os itens na lista"  
  
### <a name="text-formatting"></a>Formatação de texto  
 Formatação no Visual Studio 2013 de texto padrão é controlado pelo [a fonte de ambiente](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TheEnvironmentFont). Esse serviço ajuda a garantir uma aparência consistente fonte em todo o IDE (ambiente de desenvolvimento integrado), e você deve usá-lo para garantir uma experiência consistente para os usuários.  
  
 O tamanho padrão usado pelo serviço da fonte do Visual Studio é fornecido pelo Windows e aparece como 9 pt.  
  
 Você pode aplicar formatação a fonte de ambiente. Este tópico aborda como e onde usar estilos. Para obter informações sobre implementação, consulte [a fonte de ambiente](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TheEnvironmentFont).  
  
#### <a name="bold-text"></a>Texto em negrito  
 Texto em negrito é usado com moderação no Visual Studio e deve ser reservado para:  
  
-   rótulos de pergunta nos assistentes  
  
-   Designa o projeto ativo no Gerenciador de soluções  
  
-   valores substituídos na janela da ferramenta de propriedades  
  
-   certos eventos nas listas de lista suspensa de editor do Visual Basic  
  
-   conteúdo gerado pelo servidor na estrutura de tópicos de documento para páginas da web  
  
-   cabeçalhos de seção na caixa de diálogo complexas ou designer de interface do usuário  
  
#### <a name="italics"></a>Itálico  
 Visual Studio não usar texto em itálico itálico ou em negrito.  
  
#### <a name="color"></a>Cor  
  
-   Azul é reservado para hiperlinks (navegação e comandos) e nunca deve ser usado para a orientação.  
  
-   Títulos maior (fonte de ambiente x 155% ou superior) podem ser coloridos para esses fins:  
  
    -   Para fornecer apelo visual a assinatura de interface de usuário do Visual Studio  
  
    -   Para chamar a atenção para uma área específica  
  
    -   Para oferecer alívio da cor do texto padrão ambiente preto/cinza escuro  
  
-   Cor nos títulos deve aproveitar o Visual Studio marca cores existentes, principalmente o roxo principal FF68217A #.  
  
-   Ao usar cor nos cabeçalhos, você deve cumprir a [diretrizes de cores do Windows](https://msdn.microsoft.com/en-us/library/dn742482.aspx), incluindo contraste e outras considerações de acessibilidade.  
  
### <a name="font-size"></a>Tamanho da fonte  
 Design do Visual Studio da interface do usuário tem uma aparência mais clara com mais espaço em branco. Sempre que possível, as barras de título e o chrome foram reduzidas ou removidas. Enquanto a densidade de informações é um requisito no Visual Studio, tipografia continua a ser importante, com ênfase em espaçamento mais aberto e uma variação de tamanhos de fonte e pesos.  
  
 As tabelas a seguir inclui detalhes de design e exemplos de visual para as fontes de vídeo usadas no Visual Studio. Algumas variações de fonte de exibição tem o tamanho e o peso, como Semilight ou luz, codificados em sua aparência.  
  
 Trechos de código de implementação para todas as fontes de exibição podem ser encontrados em [formatação referência (dimensionamento/negrito)](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_Formatting).  
  
#### <a name="375-environment-font--light"></a>Fonte de ambiente % 375 + luz  
  
|||  
|-|-|  
|**Uso:** raros. Unique da marca somente da interface do usuário.<br /><br /> **Fazer:**<br /><br /> -Usar a capitalização de frase<br />-Use sempre leve<br /><br /> **Não:**<br /><br /> -Use para a interface do usuário que não seja de assinatura da interface do usuário como página inicial<br />-Em negrito, itálico ou negrito, itálico<br />-Use para corpo de texto<br />-Usar em janelas de ferramentas|**Aparece como:** pt 34 Segoe UI Light<br /><br /> **Exemplo de Visual:**<br /><br /> *Atualmente não usado. Pode ser usado na página de início.*|  
  
#### <a name="310-environment-font--light"></a>Fonte de ambiente % 310 + luz  
  
|||  
|-|-|  
|**Uso:**<br /><br /> -Título maior em caixas de diálogo de assinatura<br />-Título do relatório principal<br /><br /> **Fazer:**<br /><br /> -Usar a capitalização de frase<br />-Use sempre leve<br /><br /> **Não:**<br /><br /> -Use para a interface do usuário que não seja de assinatura da interface do usuário como página inicial<br />-Em negrito, itálico ou negrito, itálico<br />-Use para corpo de texto<br />-Usar em janelas de ferramentas|**Aparece como:** pt 28 Segoe UI Light<br /><br /> **Exemplo de Visual:**<br /><br /> ![Exemplo de fonte de ambiente % 310 &#43; Título da luz](../../extensibility/ux-guidelines/media/0202-a_ef310.png "0202-a_EF310")|  
  
#### <a name="200-environment-font--semilight"></a>Fonte de ambiente 200% + Semilight  
  
|||  
|-|-|  
|**Uso:**<br /><br /> -Subtítulos<br />-Títulos em caixas de diálogo de pequenas e médias<br /><br /> **Fazer:**<br /><br /> -Usar a capitalização de frase<br />-Use sempre Semilight peso<br /><br /> **Não:**<br /><br /> -Em negrito, itálico ou negrito, itálico<br />-Use para corpo de texto<br />-Usar em janelas de ferramentas|**Aparece como:** 18 pt Segoe UI Semillight<br /><br /> **Exemplo de Visual:**<br /><br /> ![Exemplo de fonte de ambiente 200% &#43; Semilight](../../extensibility/ux-guidelines/media/0202-b_ef200.png "0202-b_EF200")|  
  
#### <a name="155-environment-font"></a>Fonte de ambiente 155%  
  
|||  
|-|-|  
|**Uso:**<br /><br /> -Títulos seção documento bem da interface do usuário<br />-Relatórios<br /><br /> **Tarefas pendentes:** sentença caso de uso<br /><br /> **Não:**<br /><br /> -Em negrito, itálico ou negrito, itálico<br />-Use para corpo de texto<br />-Usar em controles padrão do Visual Studio<br />-Usar em janelas de ferramentas|**Aparece como:** 14 pt Segoe UI<br /><br /> **Exemplo de Visual:**<br /><br /> ![Exemplo de título de fonte de ambiente 155%](../../extensibility/ux-guidelines/media/0202-c_ef155.png "0202-c_EF155")|  
  
#### <a name="133-environment-font"></a>Fonte de ambiente % 133  
  
|||  
|-|-|  
|**Uso:**<br /><br /> -Menores subtítulos nas caixas de diálogo de assinatura<br />-Menores subtítulos no documento bem da interface do usuário<br /><br /> **Tarefas pendentes:** sentença caso de uso<br /><br /> **Não:**<br /><br /> -Em negrito, itálico ou negrito, itálico<br />-Use para corpo de texto<br />-Usar em controles padrão do Visual Studio<br />-Usar em janelas de ferramentas|**Aparece como:** 12 pt Segoe UI<br /><br /> **Exemplo de Visual:**<br /><br /> ![Exemplo de título de fonte de ambiente % 133](../../extensibility/ux-guidelines/media/0202-d_ef133.png "0202-d_EF133")|  
  
#### <a name="122-environment-font"></a>Fonte de ambiente 122%  
  
|||  
|-|-|  
|**Uso:**<br /><br /> -Títulos de seção nas caixas de diálogo de assinatura<br />-Nós superior na exibição de árvore<br />-Navegação de guia vertical<br /><br /> **Tarefas pendentes:** sentença caso de uso<br /><br /> **Não:**<br /><br /> -Em negrito, itálico ou negrito, itálico<br />-Use para corpo de texto<br />-Usar em controles padrão do Visual Studio<br />-Usar em janelas de ferramentas|**Aparece como:** 11 pt Segoe UI<br /><br /> **Exemplo de Visual:**<br /><br /> ![Exemplo de título de fonte de ambiente 122%](../../extensibility/ux-guidelines/media/0202-e_ef122.png "0202-e_EF122")|  
  
#### <a name="environment-font--bold"></a>Fonte de ambiente + em negrito  
  
|||  
|-|-|  
|**Uso:**<br /><br /> -Rótulos e subtítulos nas caixas de diálogo de assinatura<br />-Rótulos e subtítulos em relatórios<br />-Rótulos e subtítulos documento bem da interface do usuário<br /><br /> **Fazer:**<br /><br /> -Usar a capitalização de frase<br />-Use peso em negrito<br /><br /> **Não:**<br /><br /> -Itálico ou negrito itálico<br />-Use para corpo de texto<br />-Usar em controles padrão do Visual Studio<br />-Usar em janelas de ferramentas|**Aparece como:** em negrito 9 pt Segoe UI<br /><br /> **Exemplo de Visual:**<br /><br /> ![Exemplo de fonte de ambiente &#43; Título em negrito](../../extensibility/ux-guidelines/media/0202-f_efb.png "0202-f_EFB")|  
  
#### <a name="environment-font"></a>Fonte de ambiente  
  
|||  
|-|-|  
|**Uso:** todos os outros texto<br /><br /> **Tarefas pendentes:** sentença caso de uso<br /><br /> **Não:** itálico ou negrito itálico|**Aparece como:** 9 pt Segoe UI<br /><br /> **Exemplo de Visual:**<br /><br /> ![Exemplo de fonte de ambiente](../../extensibility/ux-guidelines/media/0202-g_ef.png "0202-g_EF")|  
  
### <a name="padding-and-spacing"></a>Preenchimento e espaçamento  
 Títulos exigem espaço ao redor deles para dar-lhes a ênfase apropriada. Esse espaço varia dependendo do tamanho do ponto e o que é quase o título, como uma régua horizontal ou uma linha de texto na fonte de ambiente.  
  
-   O preenchimento ideal para um título por si só deve ser 90% do espaço de altura de caractere maiusculo. Por exemplo, um título de Segoe UI Light pt 28 possui uma altura de limite de 26 pt, e o preenchimento deve ser aproximadamente 23 pt ou sobre 31 pixels.  
  
-   O espaço mínimo em torno de um título deve ser 50% da altura do caractere maiusculo. Menos espaço pode ser usado quando um cabeçalho é acompanhado por uma regra ou outro elemento de ajuste total.  
  
-   Texto de fonte em negrito ambiente deve seguir preenchimento e espaçamento de altura de linha padrão.  
  
## <a name="see-also"></a>Consulte também  
 [MSDN: Fontes (Windows)](https://msdn.microsoft.com/en-us/library/windows/desktop/dn742483\(v=vs.85\).aspx)   
 [MSDN: Texto de Interface de usuário (Windows)](https://msdn.microsoft.com/en-us/library/windows/desktop/dn742478\(v=vs.85\).aspx)
