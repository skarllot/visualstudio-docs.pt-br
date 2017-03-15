---
title: "Fontes e formatação para o Visual Studio | Documentos do Microsoft"
ms.custom: 
ms.date: 11/04/2016
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
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 60affb10656f5f9a6f4f7ddf45db06857abe8d93
ms.lasthandoff: 02/22/2017

---
# <a name="fonts-and-formatting-for-visual-studio"></a>Fontes e formatação para o Visual Studio
##  <a name="a-namebkmktheenvironmentfonta-the-environment-font"></a><a name="BKMK_TheEnvironmentFont"></a>A fonte de ambiente  
 Todas as fontes dentro do Visual Studio devem ser expostas ao usuário para personalização. Isso é feito principalmente por meio de **fontes e cores** página o **Ferramentas > opções** caixa de diálogo. As três principais categorias de configurações de fonte são:  
  
-   **Fonte do ambiente** — a fonte primária para o IDE (ambiente de desenvolvimento integrado), usada para todos os elementos da interface, incluindo caixas de diálogo, menus, janelas de ferramentas e janelas de documento. Por padrão, a fonte de ambiente é vinculada a uma fonte de sistema que aparece como 9 pt Segoe da interface do usuário nas versões atuais do Windows. Usando uma fonte para todos os elementos de interface ajuda a garantir uma aparência consistente fonte por meio do IDE.  
  
-   **Editor de texto** — página de elementos que superfície em código e outros editores de texto podem ser personalizadas no Editor de texto em **Ferramentas > opções**.  
  
-   **Coleções específicas** — designers windows que oferecem a personalização de seus elementos de interface do usuário pode expor fontes específicas para o design da superfície na própria página de configurações no **Ferramentas > opções**.  
  
### <a name="editor-font-customization-and-resizing"></a>Personalização do Editor de fonte e redimensionamento  
 Os usuários geralmente ampliar ou reduzir o tamanho e/ou a cor do texto no editor de acordo com suas preferências, independente da interface do usuário geral. Como a fonte de ambiente é usada em elementos que podem aparecer dentro ou como parte de um editor/designer, é importante observar o comportamento esperado quando uma destas classificações de fonte é alterada.  
  
 Ao criar elementos de interface do usuário que aparecem no editor, mas são não fazem parte do *conteúdo*, é importante usar a fonte de ambiente e não a fonte do texto para que redimensionar elementos de uma maneira previsível.  
  
1.  Para texto de código no editor, redimensionada com a definição de fonte de texto de código e responder ao nível de zoom do texto do editor.  
  
2.  Todos os outros elementos da interface devem estar vinculados a configuração de fonte do ambiente e respondem às alterações no ambiente global. Isso inclui (mas não está limitado a):  
  
    -   Texto nos menus de contexto  
  
    -   Texto em um adorno de editor, como texto de menu lâmpada, rápido localizar o painel do editor e navegue até o painel  
  
    -   Rótulo de texto nas caixas de diálogo, como localizar em arquivos ou Refatorar  
  
### <a name="accessing-the-environment-font"></a>Acessar a fonte de ambiente  
 No código nativo ou WinForms, a fonte de ambiente pode ser acessada chamando o método **IUIHostLocale::GetDialogFont** depois de consultar a interface do serviço SID_SUIHostLocale.  
  
 Para o Windows Presentation Foundation (WPF), derivar a classe de janela de diálogo do shell **DialogWindow** classe em vez do WPF **janela** classe.  
  
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
  
 Para exibir a caixa de diálogo, chamada "**ShowModal()**" na classe sobre **ShowDialog()**. **ShowModal()** define o estado modal correto no shell, garante que a caixa de diálogo é centralizada na janela pai e assim por diante.  
  
 O código é da seguinte maneira:  
  
```  
MyWindow window = new MyWindow();  
window.ShowModal()  
  
```  
  
 **ShowModal** retorna um bool? (booleano anulável) com o **DialogResult**, que pode ser usado se necessário. O valor de retorno será true se a caixa de diálogo foi fechada com **Okey**.  
  
 Se você precisa exibir alguns UI WPF que não é uma caixa de diálogo e é hospedado em sua própria **HwndSource**, como uma janela pop-up ou janela WPF filha de uma janela do Win32/WinForms pai, você precisará definir o **FontFamily** e **FontSize** no elemento raiz do elemento do WPF. (O shell define as propriedades na janela principal, mas eles não serão herdados após um HWND). O shell fornece recursos para que as propriedades podem ser associadas, como este:  
  
```  
<Setter property="FontFamily" Value="{DynamicResource VsFont.EnvironmentFontFamily}" />  
<Setter property="FontSize" Value="{DynamicResource VsFont.EnvironmentFontSize}" />  
  
```  
  
###  <a name="a-namebkmkformattinga-formatting-scalingbolding-reference"></a><a name="BKMK_Formatting"></a>Formatação de referência (dimensionamento/negrito)  
 Algumas caixas de diálogo exigem texto em negrito ou um tamanho diferente de fonte de ambiente. Anteriormente, fontes maiores do que a fonte de ambiente eram semelhantes ou codificado como "fonte de ambiente +&2;". Usar os trechos de código fornecido, monitores de DPI alto e certifique-se de que o texto de exibição aparece sempre no tamanho correto e peso (como luz ou Semilight).  
  
> **Observação: Antes de aplicar formatação, certifique-se você estiver seguindo as diretrizes encontradas [estilo de texto](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TextStyle).**  
  
 Para dimensionar a fonte de ambiente, defina o estilo de TextBlock ou Label, conforme indicado. Cada esses trechos de código usados corretamente, irá gerar a fonte correta, incluindo as variações de tamanho e peso apropriadas.  
  
 Onde "vsui" é uma referência ao namespace Microsoft.VisualStudio.Shell:  
  
```  
xmlns:vsui="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.14.0"  
  
```  
  
#### <a name="375-environment-font--light"></a>Fonte de ambiente %&375; + Light  
 **Aparece como:** pt 34 Segoe UI Light  
  
 **Uso:** (raro) exclusivo com marca interface do usuário, como a página inicial  
  
 **Código procedural:** onde "textBlock" é um TextBlock previamente definido e "label" é um rótulo definido anteriormente.  
  
```  
textBlock.SetResourceReference(TextBlock.StyleProperty,    
        VsResourceKeys.TextBlockEnvironment375PercentFontSizeStyleKey);   
label.SetResourceReference(Label.StyleProperty,    
        VsResourceKeys.LabelEnvironment375PercentFontSizeStyleKey);  
  
```  
  
 **XAML:** definir o estilo de TextBlock ou Label, conforme mostrado.  
  
```  
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironment375PercentFontSizeStyleKey}}">TextBlock: 375 Percent Scaling</TextBlock>   
<Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironment375PercentFontSizeStyleKey}}">Label: 375 Percent Scaling</Label>  
  
```  
  
#### <a name="310-environment-font--light"></a>Fonte de ambiente %&310; + Light  
 **Aparece como:** pt 28 Segoe UI Light  
  
 **Uso:** títulos de caixa de diálogo assinatura grande, principais em relatórios  
  
 **Código procedural:** onde "textBlock" é um TextBlock previamente definido e "label" é um rótulo definido anteriormente.  
  
```  
textBlock.SetResourceReference(TextBlock.StyleProperty,    
        VsResourceKeys.TextBlockEnvironment310PercentFontSizeStyleKey);   
label.SetResourceReference(Label.StyleProperty,    
        VsResourceKeys.LabelEnvironment310PercentFontSizeStyleKey);  
  
```  
  
 **XAML:** definir o estilo de TextBlock ou Label, conforme mostrado.  
  
```  
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironment310PercentFontSizeStyleKey}}">TextBlock: 310 Percent Scaling</TextBlock>   
<Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironment310PercentFontSizeStyleKey}}">Label: 310 Percent Scaling</Label>  
  
```  
  
#### <a name="200-environment-font--semilight"></a>Fonte do ambiente&200;% + Semilight  
 **Aparece como:** 18 pt Segoe UI Semilight  
  
 **Uso:** subtítulos, títulos em caixas de diálogo de pequenas e médias  
  
 **Código procedural:** onde "textBlock" é um TextBlock previamente definido e "label" é um rótulo definido anteriormente.  
  
```  
textBlock.SetResourceReference(TextBlock.StyleProperty,    
        VsResourceKeys.TextBlockEnvironment200PercentFontSizeStyleKey);   
label.SetResourceReference(Label.StyleProperty,    
        VsResourceKeys.LabelEnvironment200PercentFontSizeStyleKey);  
  
```  
  
 **XAML:** definir o estilo de TextBlock ou Label, conforme mostrado.  
  
```  
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironment200PercentFontSizeStyleKey}}">TextBlock: 200 Percent Scaling</TextBlock>   
<Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironment200PercentFontSizeStyleKey}}">Label: 200 Percent Scaling</Label>  
  
```  
  
#### <a name="155-environment-font"></a>Fonte de ambiente %&155;  
 **Aparece como:** 14 pt Segoe UI  
  
 **Uso:** títulos de seção no documento bem relatórios ou interface do usuário  
  
 **Código procedural:** onde "textBlock" é um TextBlock previamente definido e "label" é um rótulo definido anteriormente.  
  
```  
textBlock.SetResourceReference(TextBlock.StyleProperty,    
        VsResourceKeys.TextBlockEnvironment155PercentFontSizeStyleKey);   
label.SetResourceReference(Label.StyleProperty,    
        VsResourceKeys.LabelEnvironment155PercentFontSizeStyleKey);  
  
```  
  
 **XAML:** definir o estilo de TextBlock ou Label, conforme mostrado.  
  
```  
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironment155PercentFontSizeStyleKey}}">TextBlock: 155 Percent Scaling</TextBlock>   
<Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironment155PercentFontSizeStyleKey}}">Label: 155 Percent Scaling</Label>  
  
```  
  
#### <a name="133-environment-font"></a>Fonte de ambiente %&133;  
 **Aparece como:** 12 pt Segoe UI  
  
 **Uso:** subtítulos menores no documento e caixas de diálogo de assinatura bem da interface do usuário  
  
 **Código procedural:** onde "textBlock" é um TextBlock previamente definido e "label" é um rótulo definido anteriormente.  
  
```  
textBlock.SetResourceReference(TextBlock.StyleProperty,    
        VsResourceKeys.TextBlockEnvironment133PercentFontSizeStyleKey);   
label.SetResourceReference(Label.StyleProperty,    
        VsResourceKeys.LabelEnvironment133PercentFontSizeStyleKey);  
  
```  
  
 **XAML:** definir o estilo de TextBlock ou Label, conforme mostrado.  
  
```  
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironment133PercentFontSizeStyleKey}}">TextBlock: 133 Percent Scaling</TextBlock>   
<Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironment133PercentFontSizeStyleKey}}">Label: 133 Percent Scaling</Label>  
  
```  
  
#### <a name="122-environment-font"></a>Fonte de ambiente %&122;  
 **Aparece como:** 11 pt Segoe UI  
  
 **Uso:** seção títulos em caixas de diálogo de assinatura, superior de nós na exibição de árvore, navegação de tabulação vertical  
  
 **Código procedural:** onde "textBlock" é um TextBlock previamente definido e "label" é um rótulo definido anteriormente.  
  
```  
textBlock.SetResourceReference(TextBlock.StyleProperty,    
        VsResourceKeys.TextBlockEnvironment122PercentFontSizeStyleKey);   
label.SetResourceReference(Label.StyleProperty,    
        VsResourceKeys.LabelEnvironment122PercentFontSizeStyleKey);  
  
```  
  
 **XAML:** definir o estilo de TextBlock ou Label, conforme mostrado.  
  
```  
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironment122PercentFontSizeStyleKey}}">TextBlock: 122 Percent Scaling</TextBlock>   
<Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironment122PercentFontSizeStyleKey}}">Label: 122 Percent Scaling</Label>  
  
```  
  
#### <a name="environment-font--bold"></a>Fonte de ambiente + em negrito  
 **Aparece como:** em negrito 9 pt Segoe UI  
  
 **Uso:** rótulos e subtítulos em caixas de diálogo de assinatura, relatórios e documentos bem da interface do usuário  
  
 **Código procedural:** onde "textBlock" é um TextBlock previamente definido e "label" é um rótulo definido anteriormente.  
  
```  
textBlock.SetResourceReference(TextBlock.StyleProperty,    
        VsResourceKeys.TextBlockEnvironmentBoldStyleKey);   
label.SetResourceReference(Label.StyleProperty,    
        VsResourceKeys.LabelEnvironmentBoldStyleKey);  
  
```  
  
 **XAML:** definir o estilo de TextBlock ou Label, conforme mostrado.  
  
```  
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironmentBoldStyleKey}}"> Bold TextBlock</TextBlock>   
<Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironmentBoldStyleKey}}"> Bold Label</Label>  
  
```  
  
### <a name="localizable-styles"></a>Estilos localizáveis  
 Em alguns casos, os localizadores precisam modificar estilos de fonte para localidades diferentes, como a remoção de negrito do texto para idiomas do Leste Asiático. Para possibilitar a localização dos estilos de fonte, esses estilos devem estar dentro do arquivo. resx. É a melhor maneira de fazer isso e ainda Editar estilos de fonte no designer de formulários do Visual Studio definir explicitamente os estilos de fonte em tempo de design. Embora isso cria um objeto de fonte completa e pode parecer que quebrem a herança de fontes do pai, apenas a propriedade FontStyle é usada para definir a fonte.  
  
 A solução é vincular o formulário diálogo **FontChanged** eventos. No **FontChanged** evento, percorrer todos os controles e verificar se a fonte é definida. Se estiver definido, mude para uma nova fonte com base na fonte do formulário e estilo de fonte do controle anterior. Um exemplo no código é:  
  
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
  
 Usando este código garante que quando a fonte do formulário for atualizada, as fontes de controles atualizará também. Esse método também deve ser chamado de construtor do formulário, porque a caixa de diálogo pode falhar obter uma instância de **IUIService** e **FontChanged** evento nunca será acionado. Interceptação **FontChanged** permitirá que as caixas de diálogo Selecionar a nova fonte dinamicamente mesmo se a caixa de diálogo já está aberta.  
  
### <a name="testing-the-environment-font"></a>Teste a fonte de ambiente  
 Para garantir que a interface do usuário está usando a fonte de ambiente e respeita as configurações de tamanho, abra **Ferramentas > opções > ambiente > fontes e cores** e selecione "Fonte de ambiente" sob a "Mostrar configurações de:" menu suspenso.  
  
 ![Página de fontes e cores nas ferramentas > caixa de diálogo Opções](../../extensibility/ux-guidelines/media/0201-a_optionsfonts.png "a_OptionsFonts&0201;")  
  
 **Configurações de fontes e cores nas ferramentas de > caixa de diálogo Opções**  
  
 Defina a fonte para algo muito diferente do padrão. Para deixar claro que não atualizar a interface do usuário, escolha uma fonte com serifas (como "Times New Roman") e defina um tamanho muito grande. A interface do usuário para garantir que ele respeita o ambiente de teste. Aqui está um exemplo usando a caixa de diálogo de licença:  
  
 ![Exemplo de caixa de diálogo não usando a fonte de ambiente](../../extensibility/ux-guidelines/media/0201-b_wrongfontdialog.png "b_WrongFontDialog&0201;")  
  
 **Exemplo de texto de interface do usuário que respeitam a fonte de ambiente**  
  
 Nesse caso, "Informações do usuário" e "Informações do produto" são não respeitar a fonte. Em alguns casos, isso pode ser uma escolha de design explícita, mas pode ser um erro se a fonte explícita não é especificada como parte das especificações de redline.  
  
 Para redefinir a fonte, clique em "Usar padrões" em **Ferramentas > opções > ambiente > fontes e cores**.  
  
##  <a name="a-namebkmktextstylea-text-style"></a><a name="BKMK_TextStyle"></a>Estilo de texto  
 Estilo de texto refere-se maiusculas e minúsculas, peso e tamanho da fonte. Para obter diretrizes de implementação, consulte [a fonte de ambiente](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TheEnvironmentFont).  
  
### <a name="text-casing"></a>Maiusculas e minúsculas do texto  
  
#### <a name="all-caps"></a>Todas em maiusculas  
 Não use todas em maiusculas para títulos ou rótulos no Visual Studio.  
  
#### <a name="all-lowercase"></a>Todas as minúsculas  
 Não use letras minúsculas para títulos ou rótulos no Visual Studio.  
  
#### <a name="sentence-and-title-case"></a>Caso oração e título  
 Texto do Visual Studio deve usar maiusculas/minúsculas ou sentença inteira, dependendo da situação.  
  
|Use letras maiusculas para:|Sentença de caso de uso:|  
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
 Capitalização de título é um estilo no qual as primeiras letras da maioria ou todas as palavras em uma frase estão em maiusculas. No Visual Studio, maiusculas/minúsculas é usada para vários itens, incluindo:  
  
-   **Dicas de ferramenta.** Exemplo: "Visualizar itens selecionados"  
  
-   **Cabeçalhos de coluna.** Exemplo: "resposta do sistema"  
  
-   **Itens de menu.** Exemplo: "Salvar tudo"  
  
 Ao usar maiusculas/minúsculas, estas são as diretrizes para quando capitalizar palavras e deixá-los em minúsculas:  
  
|Maiúsculas|Comentários e exemplos|  
|---------------|---------------------------|  
|Todos os substantivos||  
|Todos os verbos|Incluindo outras formas de "ser" e "É"|  
|Todos os advérbios|Incluindo "De" e "Quando"|  
|Todos os adjetivos|Incluindo "This" e "Que"|  
|Todos os pronomes|Incluindo o caso seja "Seu", bem como "É," uma contração do Pronome "-" e o verbo "é"|  
|Primeira e última palavras, independentemente de partes da fala||  
|Preposições que fazem parte de uma frase verbal|"Fechar todos os Windows" ou "Desligamento do sistema"|  
|Todas as letras de um acrônimo|HTML, XML, URL, IDE, RGB|  
|A segunda palavra em uma palavra composta se é um substantivo ou adjetivo apropriado, ou se as palavras têm o mesmo peso|Acesso de leitura/gravação de referência cruzada, Software de pré-lançamento do Microsoft, tempo de execução|  
  
|Minúsculas|Exemplos|  
|---------------|--------------|  
|A segunda palavra em uma palavra composta se ele for um participle modificando a primeira palavra ou outra parte da fala|Instruções, derivado|  
|Artigos, a menos que um é a primeira palavra no título|um, uma, o|  
|Coordenar associações|e, mas, nem, ou|  
|Preposições com palavras de quatro ou menos letras fora de uma frase verbal|em, em, como para fora do, na parte superior do|  
|"Para" quando usada em uma frase infinita|"Como formatar o disco rígido"|  
  
##### <a name="sentence-case"></a>Sentença inteira  
 Sentença inteira é o método padrão de maiusculas e minúsculas para gravação no qual a primeira palavra da sentença está em maiusculas, junto com qualquer substantivos e o Pronome "I". Em geral, a sentença inteira é mais fácil para um público internacional de ler, especialmente quando o conteúdo será convertido por uma máquina. Sentença de caso de uso:  
  
1.  **Mensagens da barra de status.** Essas são simples e curtas e fornecem apenas informações de status. Exemplo: "carregar arquivo de projeto"  
  
2.  **Todos os outros elementos de interface do usuário**, incluindo rótulos, caixas de seleção, botões e itens de caixa de lista. Exemplo: "Selecionar todos os itens na lista"  
  
### <a name="text-formatting"></a>Formatação de texto  
 Formatação no Visual Studio 2013 de texto padrão é controlado por um [a fonte de ambiente](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TheEnvironmentFont). Esse serviço ajuda a garantir uma aparência consistente de fonte em todo o IDE (ambiente de desenvolvimento integrado), e você deve usá-lo para garantir uma experiência consistente para seus usuários.  
  
 O tamanho padrão usado pelo serviço da fonte do Visual Studio é fornecido pelo Windows e aparece como 9 pontos.  
  
 Você pode aplicar formatação a fonte de ambiente. Este tópico aborda como e onde usar estilos. Para obter informações sobre implementação, consulte [a fonte de ambiente](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TheEnvironmentFont).  
  
#### <a name="bold-text"></a>Texto em negrito  
 Texto em negrito é usado com moderação no Visual Studio e deve ser reservado para:  
  
-   rótulos de pergunta em assistentes  
  
-   designando o projeto ativo no Gerenciador de soluções  
  
-   valores substituídos na janela da ferramenta de propriedades  
  
-   determinados eventos em listas suspensas Visual Basic editor  
  
-   conteúdo gerado pelo servidor na estrutura de tópicos de documento para páginas da web  
  
-   cabeçalhos de seção na caixa de diálogo complexa ou designer de interface do usuário  
  
#### <a name="italics"></a>Itálico  
 Visual Studio não usa o texto em itálico itálico ou negrito.  
  
#### <a name="color"></a>Cor  
  
-   Azul é reservado para hiperlinks (navegação e comandos) e nunca deve ser usado para a orientação.  
  
-   Títulos maiores (fonte de ambiente x 155% ou maior) podem ser coloridos para essas finalidades:  
  
    -   Para fornecer o apelo visual a assinatura de IU do Visual Studio  
  
    -   Para chamar a atenção para uma área específica  
  
    -   Para oferecer alívio da cor do texto ambiente preto/cinza escuro padrão  
  
-   Cor do cabeçalho deve aproveitar o Visual Studio marca cores existentes, principalmente o principal roxo, #FF68217A.  
  
-   Ao usar cores nos cabeçalhos, você deve seguir o [diretrizes de cores do Windows](https://msdn.microsoft.com/en-us/library/dn742482.aspx), incluindo a taxa de contraste e outras considerações de acessibilidade.  
  
### <a name="font-size"></a>Tamanho da fonte  
 Design do Visual Studio da interface do usuário possui uma aparência mais clara com mais espaço em branco. Sempre que possível, barras de título e chrome foram reduzidas ou removidas. Enquanto a densidade de informações é um requisito no Visual Studio, tipografia continua sendo importante, com ênfase em espaçamento mais aberto e uma variação de pesos e tamanhos de fonte.  
  
 As tabelas a seguir inclui detalhes de design e exemplos visuais para as fontes de exibição usados no Visual Studio. Algumas variações de fonte de exibição tem o tamanho e o peso, como Semilight ou luz, codificados em sua aparência.  
  
 Trechos de código de implementação para todas as fontes de vídeo podem ser encontrados em [formatação referência (dimensionamento/negrito)](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_Formatting).  
  
#### <a name="375-environment-font--light"></a>Fonte de ambiente %&375; + Light  
  
|||  
|-|-|  
|**Uso:** raros. Exclusivo da marca apenas da interface do usuário.<br /><br /> **Faça:**<br /><br /> -Use sentença inteira<br />-Sempre usar leve<br /><br /> **Não:**<br /><br /> -Use a interface do usuário diferente de assinatura da interface do usuário como página inicial<br />-Em negrito, itálico ou negrito itálico<br />-Use para corpo de texto<br />-Use em janelas de ferramenta|**Aparece como:** pt 34 Segoe UI Light<br /><br /> **Exemplo de Visual:**<br /><br /> *Atualmente não usado. Pode ser usado na página de início.*|  
  
#### <a name="310-environment-font--light"></a>Fonte de ambiente %&310; + Light  
  
|||  
|-|-|  
|**Uso:**<br /><br /> -Título maior nas caixas de diálogo de assinatura<br />-Título do relatório principal<br /><br /> **Faça:**<br /><br /> -Use sentença inteira<br />-Sempre usar leve<br /><br /> **Não:**<br /><br /> -Use a interface do usuário diferente de assinatura da interface do usuário como página inicial<br />-Em negrito, itálico ou negrito itálico<br />-Use para corpo de texto<br />-Use em janelas de ferramenta|**Aparece como:** pt 28 Segoe UI Light<br /><br /> **Exemplo de Visual:**<br /><br /> ![Exemplo de fonte de ambiente % 310 + título leve](../../extensibility/ux-guidelines/media/0202-a_ef310.png "0202-a_EF310")|  
  
#### <a name="200-environment-font--semilight"></a>Fonte do ambiente&200;% + Semilight  
  
|||  
|-|-|  
|**Uso:**<br /><br /> -Subtítulos<br />-Títulos em caixas de diálogo de pequenas e médias<br /><br /> **Faça:**<br /><br /> -Use sentença inteira<br />-Sempre usar Semilight peso<br /><br /> **Não:**<br /><br /> -Em negrito, itálico ou negrito itálico<br />-Use para corpo de texto<br />-Use em janelas de ferramenta|**Aparece como:** 18 pt Segoe UI Semillight<br /><br /> **Exemplo de Visual:**<br /><br /> ![Exemplo de fonte de ambiente 200% + Semilight](../../extensibility/ux-guidelines/media/0202-b_ef200.png "0202-b_EF200")|  
  
#### <a name="155-environment-font"></a>Fonte de ambiente %&155;  
  
|||  
|-|-|  
|**Uso:**<br /><br /> -Os títulos de seção documento bem da interface do usuário<br />-Relatórios<br /><br /> **Como fazer:** sentença caso de uso<br /><br /> **Não:**<br /><br /> -Em negrito, itálico ou negrito itálico<br />-Use para corpo de texto<br />-Use controles padrão do Visual Studio<br />-Use em janelas de ferramenta|**Aparece como:** 14 pt Segoe UI<br /><br /> **Exemplo de Visual:**<br /><br /> ![Exemplo de título de fonte de ambiente % 155](../../extensibility/ux-guidelines/media/0202-c_ef155.png "0202-c_EF155")|  
  
#### <a name="133-environment-font"></a>Fonte de ambiente %&133;  
  
|||  
|-|-|  
|**Uso:**<br /><br /> -Subtítulos menores nas caixas de diálogo de assinatura<br />-Subtítulos menores no documento bem da interface do usuário<br /><br /> **Como fazer:** sentença caso de uso<br /><br /> **Não:**<br /><br /> -Em negrito, itálico ou negrito itálico<br />-Use para corpo de texto<br />-Use controles padrão do Visual Studio<br />-Use em janelas de ferramenta|**Aparece como:** 12 pt Segoe UI<br /><br /> **Exemplo de Visual:**<br /><br /> ![Exemplo de título de fonte de ambiente % 133](../../extensibility/ux-guidelines/media/0202-d_ef133.png "0202-d_EF133")|  
  
#### <a name="122-environment-font"></a>Fonte de ambiente %&122;  
  
|||  
|-|-|  
|**Uso:**<br /><br /> -Títulos de seção nas caixas de diálogo de assinatura<br />-Nós superior no modo de exibição de árvore<br />-Navegação por guias vertical<br /><br /> **Como fazer:** sentença caso de uso<br /><br /> **Não:**<br /><br /> -Em negrito, itálico ou negrito itálico<br />-Use para corpo de texto<br />-Use controles padrão do Visual Studio<br />-Use em janelas de ferramenta|**Aparece como:** 11 pt Segoe UI<br /><br /> **Exemplo de Visual:**<br /><br /> ![Exemplo de título de fonte de ambiente % 122](../../extensibility/ux-guidelines/media/0202-e_ef122.png "0202-e_EF122")|  
  
#### <a name="environment-font--bold"></a>Fonte de ambiente + em negrito  
  
|||  
|-|-|  
|**Uso:**<br /><br /> -Rótulos e subtítulos nas caixas de diálogo de assinatura<br />-Rótulos e subtítulos em relatórios<br />-Rótulos e subtítulos no documento da interface do usuário<br /><br /> **Faça:**<br /><br /> -Use sentença inteira<br />-Use o peso em negrito<br /><br /> **Não:**<br /><br /> -Itálico ou negrito itálico<br />-Use para corpo de texto<br />-Use controles padrão do Visual Studio<br />-Use em janelas de ferramenta|**Aparece como:** em negrito 9 pt Segoe UI<br /><br /> **Exemplo de Visual:**<br /><br /> ![Exemplo de fonte de ambiente + título em negrito](../../extensibility/ux-guidelines/media/0202-f_efb.png "0202-f_EFB")|  
  
#### <a name="environment-font"></a>Fonte do ambiente  
  
|||  
|-|-|  
|**Uso:** todos os outros textos<br /><br /> **Como fazer:** sentença caso de uso<br /><br /> **Não:** itálico ou negrito itálico|**Aparece como:** Segoe 9 pontos da interface do usuário<br /><br /> **Exemplo de Visual:**<br /><br /> ![Exemplo de fonte de ambiente](../../extensibility/ux-guidelines/media/0202-g_ef.png "0202-g_EF")|  
  
### <a name="padding-and-spacing"></a>Preenchimento e espaçamento  
 Títulos exigem espaço em torno delas para dar-lhes a ênfase apropriada. Esse espaço varia dependendo do tamanho do ponto e o que mais é quase o título, como uma régua horizontal ou uma linha de texto na fonte de ambiente.  
  
-   O preenchimento ideal para um título por si só deve ser 90% do espaço de altura de caractere maiusculo. Por exemplo, um título de luz de IU Segoe pt 28 possui uma altura de limite de 26 pt e o preenchimento deve ser aproximadamente 23 pt ou aproximadamente 31 pixels.  
  
-   O espaço mínimo em torno de um título deve ser 50% da altura do caractere maiusculo. Menos espaço pode ser usado quando um cabeçalho é acompanhado por uma regra ou outro elemento de ajuste rígida.  
  
-   Texto da fonte em negrito ambiente deve seguir o preenchimento e o espaçamento de altura de linha padrão.  
  
## <a name="see-also"></a>Consulte também  
 [MSDN: Fontes (Windows)](https://msdn.microsoft.com/en-us/library/windows/desktop/dn742483\(v=vs.85\).aspx)   
 [MSDN: Texto da Interface do usuário (Windows)](https://msdn.microsoft.com/en-us/library/windows/desktop/dn742478\(v=vs.85\).aspx)
