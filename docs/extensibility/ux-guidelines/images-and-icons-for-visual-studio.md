---
title: "Imagens e ícones para o Visual Studio | Documentos do Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f410325e-9cf2-4f39-b6d7-b672121c2691
caps.latest.revision: 11
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
ms.openlocfilehash: f59add27269e24a7673e8b78afc35a9d5e4b46c5
ms.lasthandoff: 02/22/2017

---
# <a name="images-and-icons-for-visual-studio"></a>Imagens e ícones para o Visual Studio
##  <a name="a-namebkmkimageuseinvisualstudioa-image-use-in-visual-studio"></a><a name="BKMK_ImageUseInVisualStudio"></a>Uso da imagem no Visual Studio  
 Antes de criar a arte final, considere fazer uso de mais de 1.000 imagens no [biblioteca de imagens do Visual Studio](http://www.microsoft.com/en-my/download/details.aspx?id=35825).  
  
### <a name="types-of-images"></a>Tipos de imagens  
  
-   **Ícones**. Imagens pequenas que aparecem em comandos, hierarquias, modelos e assim por diante. O tamanho do ícone padrão usado no Visual Studio é um arquivo 16x16 PNG. Ícones produzidas pelo serviço de imagem automaticamente geram o formato XAML para suporte HDPI.  
  
     **Observação:** enquanto imagens são usadas no sistema de menu, você não deve criar um ícone para cada comando. Consulte [Menus e comandos para o Visual Studio](../../extensibility/ux-guidelines/menus-and-commands-for-visual-studio.md) para ver se o comando deve obter um ícone.  
  
-   **Miniaturas.** Imagens usadas na área de visualização da caixa de diálogo, como a caixa de diálogo Novo projeto.  
  
-   **Imagens da caixa de diálogo.** Imagens que aparecem em caixas de diálogo ou assistentes, como gráficos descritivos ou indicadores de mensagem. Use raramente e somente quando necessário para ilustrar um conceito difícil ou obter a atenção do usuário (aviso de alerta,).  
  
-   **Imagens animadas.** Usada em caixas de diálogo de operação, barras de status e indicadores de progresso.  
  
-   **Cursores.** Usado para indicar se uma operação é permitida com o mouse, em que um objeto pode ser removido e assim por diante.  
  
##  <a name="a-namebkmkicondesigna-icon-design"></a><a name="BKMK_IconDesign"></a>Design de ícone  
  
### <a name="overview"></a>Visão Geral  
 O Visual Studio usa ícones moderna, que têm geometria limpa e 50/50 equilibrar positivos/negativos (claro/escuro) e usam metáforas diretas e legível. Design de ícone crucial pontos giram em torno de clareza, simplificação e contexto.  
  
-   **Clareza:** enfocar a metáfora de núcleo que oferece um ícone de seu significado e individualidade.  
  
-   **Simplificação:** reduzir o ícone para seu significado principais – transmitir o tema com o elemento necessário e sem sofisticações.  
  
-   **Contexto:** considerar todos os aspectos da função de um ícone durante o desenvolvimento do conceito, que é essencial ao decidir quais elementos constituem a metáfora de núcleo do ícone.  
  
 Com ícones, há um número de pontos de design para evitar:  
  
-   Não use os ícones que representam os elementos de interface do usuário, exceto quando apropriado. Escolha uma abordagem mais abstrata ou simbólica quando o elemento de interface do usuário não é comum, evidente, nem exclusivo.  
  
-   Não uso excessivo de elementos comuns, como documentos, pastas, setas e a Lupa. Use esses elementos quando essencial para o significado do ícone. Por exemplo, a Lupa para a direita deve indicar somente pesquisar, procurar e localizar.  
  
-   Embora alguns elementos de ícone herdado mantém o uso de perspectiva, não crie novos ícones com perspectiva, a menos que o elemento não tem a clareza sem ele.  
  
-   Não espremer muitas informações em um ícone. Uma imagem simples que pode ser facilmente reconhecida ou aprendeu como um símbolo reconhecível é muito mais útil que uma imagem excessivamente complexa. Um ícone não contam a história toda.  
  
### <a name="icon-creation"></a>Criação de ícone  
  
#### <a name="concept-development"></a>Desenvolvimento do conceito  
 Visual Studio tem dentro de sua interface do usuário uma ampla variedade de tipos de ícones. Considere cuidadosamente o tipo de ícone durante o desenvolvimento. Não use objetos de interface do usuário obscuro ou incomuns para elementos de ícone. Optar por simbólico nesses casos, como com o ícone de marca inteligente. Observe que o significado da marca abstrata à esquerda é mais óbvio do que a versão vaga da interface do usuário à direita:  
  
|||  
|-|-|  
|**Uso correto de imagens simbólico**|**Uso incorreto de imagens simbólico**|  
|![Ícone de marca inteligente correto](../../extensibility/ux-guidelines/media/0404-01_smarttagcorrect.png "01_SmartTagCorrect&0404;")|![Ícone de marca inteligente incorreto](../../extensibility/ux-guidelines/media/0404-02_smarttagincorrect.png "02_SmartTagIncorrect&0404;")|  
  
 Há situações em que os elementos de interface do usuário padrão, facilmente reconhecíveis funcionam bem para ícones. Adicione que janela é um exemplo:  
  
|||  
|-|-|  
|**Elemento de interface do usuário correto em um ícone**|**Elemento de interface de usuário incorreto em um ícone**|  
|![Ícone de janela Adicionar correto](../../extensibility/ux-guidelines/media/0404-03_addwindowcorrect.png "03_AddWindowCorrect&0404;")|![Ícone de janela Adicionar incorreto](../../extensibility/ux-guidelines/media/0404-04_addwindowincorrect.png "04_AddWindowIncorrect&0404;")|  
  
 Não use um documento como um elemento base a menos que seja essencial para o significado do ícone. Sem o documento de elemento no documento de adicionar (o significado abaixo) é perdido, enquanto a atualização o elemento do documento é desnecessário informar o significado.  
  
|||  
|-|-|  
|**Uso correto do ícone do documento**|**Uso incorreto do ícone do documento**|  
|![Ícone de documento correto](../../extensibility/ux-guidelines/media/0404-05_documenticoncorrect.png "05_DocumentIconCorrect&0404;")|![Ícone de documento incorreto](../../extensibility/ux-guidelines/media/0404-06_documenticonincorrect.png "06_DocumentIconIncorrect&0404;")|  
  
 O conceito de "apresentação" deve ser representado pelo ícone que ilustra melhor o que está sendo mostrado, tais como ocorre com o exemplo de mostrar todos os arquivos. Uma metáfora de Lente pode ser usada para indicar o conceito de "exibição", se necessário, como o exemplo de exibição de recurso.  
  
|||  
|-|-|  
|**"Mostrar"**|**"View"**|  
|![Mostrar ícone de](../../extensibility/ux-guidelines/media/0404-07_show.png "07_Show&0404;")|![Ícone do modo de exibição](../../extensibility/ux-guidelines/media/0404-08_view.png "08_View&0404;")|  
  
 O para a direita ampliar o ícone de deve representar apenas pesquisar, localizar e procurar. A variante voltada para a esquerda com o sinal de mais ou menos deve representar apenas zoom em / zoom.  
  
|||  
|-|-|  
|**"Pesquisar"**|**"Zoom"**|  
|![Ícone de pesquisa](../../extensibility/ux-guidelines/media/0404-09_search.png "09_Search&0404;")|![Ícone de zoom](../../extensibility/ux-guidelines/media/0404-10_zoom.png "10_Zoom&0404;")|  
  
 Nos modos de exibição de árvore, não use o ícone de pasta e um modificador. Quando disponível, use apenas o modificador.  
  
|||  
|-|-|  
|**Ícones de exibição de árvore correto**|**Ícones de exibição de árvore incorreto**|  
|![Ícone do modo de exibição de árvore correto (1)](../../extensibility/ux-guidelines/media/0404-11_treeviewcorrect1.png "0404&11;_TreeViewCorrect1") ![ícone do modo de exibição de árvore correto (2)](../../extensibility/ux-guidelines/media/0404-12_treeviewcorrect2.png "12_TreeViewCorrect2&0404;")|![Ícone do modo de exibição de árvore incorreto (1)](../../extensibility/ux-guidelines/media/0404-13_treeviewincorrect1.png "0404&13;_TreeViewIncorrect1") ![ícone do modo de exibição de árvore incorreto (2)](../../extensibility/ux-guidelines/media/0404-14_treeviewincorrect2.png "14_TreeViewIncorrect2&0404;")|  
  
### <a name="style-details"></a>Detalhes de estilo  
  
#### <a name="layout"></a>Layout  
 Elementos da pilha conforme mostrado para os ícones de 16x16 padrão:  
  
 ![Pilha de layout para os ícones de 16x16](../../extensibility/ux-guidelines/media/0404-15_layoutstack.png "15_LayoutStack 0404")  
  
 **Pilha de layout para os ícones de 16x16**  
  
 Elementos de notificação de status são mais usados como ícones autônomo. Há contextos, no entanto, no qual uma notificação deve ser empilhada no elemento base, como com o ícone de tarefa concluída:  
  
 ![Notificações de autônomo no Visual Studio](../../extensibility/ux-guidelines/media/0404-16_standalonenotificationicons.png "16_StandaloneNotificationIcons&0404;")  
  
 **Ícones de notificação autônomo**  
  
 ![Ícone de tarefa concluída](../../extensibility/ux-guidelines/media/0404-17_taskcomplete.png "17_TaskComplete&0404;")  
  
 **Ícone de tarefa concluída**  
  
 Ícones de projeto geralmente são arquivos. ico que contêm vários tamanhos. A maioria dos ícones de 16x16 contêm os mesmos elementos. As versões de 32 x 32 têm mais detalhes, incluindo o tipo de projeto, quando aplicável.  
  
 ![Projeto ícones no Visual Studio](../../extensibility/ux-guidelines/media/0404-18_iconprojectthreesizes.png "18_IconProjectThreeSizes&0404;")  
  
 **Ícones de projeto de biblioteca de controle do Windows VB, 16 x 16 e 32 x 32**  
  
 Centro de um ícone dentro do quadro pixel. Se isso não for possível, alinhe o ícone na parte superior e/ou à direita do quadro.  
  
 ![Ícone centralizado dentro do quadro de pixel](../../extensibility/ux-guidelines/media/0404-19_iconcentered.png "19_IconCentered&0404;")  
  
 **Ícone centralizado dentro do quadro de pixel**  
  
 ![Ícone alinhado à parte superior direita do quadro de pixel](../../extensibility/ux-guidelines/media/0404-20_icontopright.png "20_IconTopRight&0404;")  
  
 **Ícone alinhado na parte superior direita do quadro**  
  
 ![Ícone centralizada e alinhado à parte superior do quadro de pixel](../../extensibility/ux-guidelines/media/0404-21_icontopalign.png "21_IconTopAlign&0404;")  
  
 **Ícone centralizada e alinhado à parte superior do quadro**  
  
 Para alcançar o equilíbrio e alinhamento ideal, evite obstruindo o elemento base do ícone glifos de ação. Coloque o glifo na parte superior esquerdo do elemento base. Ao adicionar um elemento adicional, considere o alinhamento e o saldo do ícone.  
  
|||  
|-|-|  
|**Saldo e alinhamento correto**|**Saldo e alinhamento incorreto**|  
|![Corrija o saldo de ícone e alinhamento](../../extensibility/ux-guidelines/media/0404-22_alignbalancecorrect.png "22_AlignBalanceCorrect&0404;")|![Saldo de ícone incorreto e alinhamento](../../extensibility/ux-guidelines/media/0404-23_alignbalanceincorrect.png "23_AlignBalanceIncorrect&0404;")|  
  
 Certifique-se de paridade de tamanho dos ícones que compartilham elementos e são usados em conjuntos. Observe que no emparelhamento incorreto, o círculo e seta forem muito grandes e não correspondem.  
  
|||  
|-|-|  
|**Paridade de tamanho correto**|**Paridade de tamanho incorreto**|  
|![Corrigir o tamanho de ícone e paridade](../../extensibility/ux-guidelines/media/0404-24_sizeparitycorrect.png "24_SizeParityCorrect&0404;")|![Tamanho do ícone incorreto e paridade](../../extensibility/ux-guidelines/media/0404-25_sizeparityincorrect.png "25_SizeParityIncorrect&0404;")|  
  
 Use linhas consistente e pesos visual. Avalie como o ícone que você está criando se compara aos outros ícones usando uma comparação lado a lado. Nunca use toda a estrutura de 16x16, use 15 x 15 ou menor. A taxa de (escuro para claro) negativo para positivo deve ser 50/50.  
  
|||  
|-|-|  
|**Taxa de negativo para positivo correta**|**Taxa de negativo para positivo incorreta**|  
|![Peso visual correto de ícones (1)](../../extensibility/ux-guidelines/media/0404-26_visualweightcorrect1.png "0404-26_VisualWeightCorrect1")<br /><br /> ![Peso visual correto de ícones (2)](../../extensibility/ux-guidelines/media/0404-27_visualweightcorrect2.png "0404-27_VisualWeightCorrect2")<br /><br /> ![Peso visual correto de ícones (3)](../../extensibility/ux-guidelines/media/0404-28_visualweightcorrect3.png "0404-28_VisualWeightCorrect3")|![Peso visual incorreto para ícones](../../extensibility/ux-guidelines/media/0404-29_visualweightincorrect.png "29_VisualWeightIncorrect&0404;")|  
  
 Use formas simples, comparáveis e ângulos complementares para criar os elementos sem sacrificar a integridade do elemento. Use os ângulos de 45° ou 90° sempre que possível.  
  
 ![Corrija os ângulos de ícone](../../extensibility/ux-guidelines/media/0404-30_iconanglescorrect.png "30_IconAnglesCorrect&0404;")  
  
#### <a name="perspective"></a>Perspectiva  
 Mantenha o ícone claro e compreensível. Use a perspectiva e uma fonte de luz somente quando necessário. Embora usando perspectiva em elementos de ícone deve ser evitado, alguns elementos são irreconhecíveis sem ele. Nesses casos, uma perspectiva estilizada se comunica a clareza do elemento.  
  
 ![perspectiva de ponto&3;](../../extensibility/ux-guidelines/media/0404-31_3pointperspective.png "31_3PointPerspective&0404;")  
  
 **perspectiva de ponto&3;**  
  
 ![1 ponto perspectiva](../../extensibility/ux-guidelines/media/0404-32_1pointperspective.png "32_1PointPerspective&0404;")  
  
 **perspectiva de&1; ponto**  
  
 A maioria dos elementos deve ficar voltado ou diagonal à direita.  
  
 ![Ícones angular direito](../../extensibility/ux-guidelines/media/0404-33_angledright.png "33_AngledRight&0404;")  
  
 Use fontes de luz somente ao adicionar clareza necessária a um objeto.  
  
|||  
|-|-|  
|**Fonte de luz correto**|**Fonte de luz incorreto**|  
|![Corrija as fontes de luz para ícones](../../extensibility/ux-guidelines/media/0404-34_lightsourcescorrect.png "34_LightSourcesCorrect&0404;")|![Fontes de luz incorretos para ícones](../../extensibility/ux-guidelines/media/0404-35_lightsourcesincorrect.png "35_LightSourcesIncorrect&0404;")|  
  
 Use contornos somente para melhorar a legibilidade ou comunicar melhor a metáfora. Saldo negativo positivo (claro-escuro) deve ser 50/50.  
  
|||  
|-|-|  
|**Uso correto de estruturas de tópicos**|**Uso incorreto de estruturas de tópicos**|  
|![Corrigir contornos](../../extensibility/ux-guidelines/media/0404-36_outlinescorrect.png "36_OutlinesCorrect&0404;")|![Contornos incorretos](../../extensibility/ux-guidelines/media/0404-37_outlinesincorrect.png "37_OutlinesIncorrect&0404;")|  
  
#### <a name="icon-types"></a>Tipos de ícone  
 **Barra de comandos e shell** ícones consistem em não mais do que três dos seguintes elementos: uma base, um modificador, uma ação ou um status.  
  
 ![Shell e ícones de barra de comandos](../../extensibility/ux-guidelines/media/0404-38_shellicons.png "38_ShellIcons&0404;")  
  
 **Exemplos de shell e ícones de barra de comandos**  
  
 **Barra de comandos de janela de ferramenta** ícones consistem em não mais do que três dos seguintes elementos: uma base, um modificador, uma ação ou um status.  
  
 ![Ícones da barra de comando janela de ferramenta](../../extensibility/ux-guidelines/media/0404-39_toolwindowcommandbaricons.png "39_ToolWindowCommandBarIcons&0404;")  
  
 **Exemplos de ícones da barra de ferramenta janela comando**  
  
 **Disambiguator de exibição de árvore** ícones consistem em não mais do que três dos seguintes elementos: uma base, um modificador, uma ação ou um status.  
  
 ![Ícones de disambiguator de exibição de árvore](../../extensibility/ux-guidelines/media/0404-40_treeviewicons.png "40_TreeViewIcons&0404;")  
  
 **Exemplos de árvore exibir ícones disambiguator**  
  
 **Taxonomia de valor com base no estado** ícones existem nos seguintes estados: ativo, ativo desativado e desabilitado inativo.  
  
 ![Ícones de valor de taxonomia baseada em estado](../../extensibility/ux-guidelines/media/0404-41_statebasedtaxonomy.png "41_StateBasedTaxonomy&0404;")  
  
 **Exemplos de ícones de taxonomia de valor com base no estado**  
  
 **IntelliSense** ícones consistem em não mais do que três dos seguintes elementos: uma base, um modificador e um status.  
  
 ![Ícones de IntelliSense](../../extensibility/ux-guidelines/media/0404-42_intellisenseicons.png "42_IntelliSenseIcons&0404;")  
  
 **Exemplos de ícones do IntelliSense**  
  
 **Pequeno (16x16) projeto** ícones devem ter não mais do que dois elementos: uma base e um modificador.  
  
 ![ícone de projeto de&16;x16 (1)](../../extensibility/ux-guidelines/media/0404-43_16x16project1.png "0404&43;_16x16Project1") ![ícone do projeto de&16;x16 (2)](../../extensibility/ux-guidelines/media/0404-44_16x16project2.png "0404&44;_16x16Project2") ![ícone do projeto de&16;x16 (3)](../../extensibility/ux-guidelines/media/0404-45_16x16project3.png "45_16x16Project3&0404;")  
  
 **Exemplos de ícones pequenos do projeto (16x16)**  
  
 **Grande (32 x&32;) projeto** ícones consistem em não mais do que quatro dos seguintes elementos: uma base, um ou dois modificadores e uma linguagem de sobreposição.  
  
 ![ícones de projeto de&32; x&32;](../../extensibility/ux-guidelines/media/0404-46_32x32project.png "46_32x32Project&0404;")  
  
 **Exemplos de ícones grandes de projeto (32 x&32;)**  
  
### <a name="production-details"></a>Detalhes da produção  
 Todos os novos elementos de interface do usuário devem ser criados usando o Windows Presentation Foundation (WPF) e todos os novos ícones para WPF devem estar no formato PNG de 32 bits. O PNG de 24 bits é um formato herdado que não oferece suporte a transparência e, portanto, não é recomendado para os ícones.  
  
 Salve a resolução de 96 DPI.  
  
#### <a name="file-types"></a>Tipos de arquivo  
  
-   **PNG de&32; bits:** o formato preferencial para ícones. Um formato de arquivo de compactação sem perda de dados que pode armazenar uma imagem de varredura única (pixels). arquivos PNG de&32; bits suportam transparência de canal alfa, a correção gama e o entrelaçamento.  
  
-   **32 bits BMP:** para controles do WPF não. Também chamado XP ou colorido, 32 bits BMP é um formato de imagem RGB/A, uma imagem true color com transparência de uma canal alfa. O canal alfa é uma camada de transparência designada do Adobe Photoshop que é salvo dentro do bitmap como um adicional (quarta) canal de cor. Um plano de fundo preto é adicionado durante a produção de arte a todos os arquivos BMP de 32 bits para fornecer uma indicação visual rápida sobre a intensidade de cor. Este plano de fundo preto representa a área a ser ocultada na interface do usuário.  
  
-   **ICO de&32; bits:** de ícones de projeto e Adicionar Item. Todos os arquivos ICO são cor verdadeiro de 32 bits com transparência de canal alfa (RGB/A). Como os arquivos ICO podem armazenar vários tamanhos e intensidades de cor, ícones do Vista costumam em um formato ICO contendo 16x16, 32x32, 48x48 e 256 x 256 tamanhos de imagem. Para exibir corretamente no Windows Explorer, arquivos ICO devem ser salvo para baixo a intensidade de cor de 24 bits e de 8 bits para cada tamanho de imagem.  
  
-   **XAML:** para superfícies de design e os adornos do Windows. Ícones XAML são arquivos de imagem baseada em vetor que oferecem suporte a dimensionar, girar, arquivamento e transparência. Eles não são comuns no Visual Studio hoje, mas estão se tornando mais populares devido à sua flexibilidade.  
  
-   **SVG**  
  
-   **24 bits BMP:** para a barra de comando do Visual Studio. Um formato de imagem true color RGB, BMP 24 bits é uma convenção de ícone que cria uma camada de transparência usando magenta (R = 255, G = 0, B = 255) como uma chave de cor para uma camada de transparência de limite crítica. Em um BMP de 24 bits, todas as superfícies magenta são exibidas usando a cor de plano de fundo.  
  
-   **24 bits GIF:** para a barra de comando do Visual Studio. Um formato de imagem RGB true color que oferece suporte à transparência. Arquivos GIF são geralmente usados em arte final do assistente e animações de GIF.  
  
### <a name="icon-construction"></a>Construção de ícone  
 O menor tamanho de ícone no Visual Studio é 16x16. O maior em comum o uso é 32 x 32. Tenha em mente não podem ocupar todo o quadro de 16x16, 24 x 24 ou 32 x 32 durante a criação de um ícone. Construção de ícone uniforme, legível, é essencial para reconhecimento do usuário. Cumprir os seguintes pontos ao criar ícones.  
  
-   Ícones devem ser clara, consistente e compreensível.  
  
-   É melhor usar os elementos de notificação de status como ícones únicos e não para organizá-las na parte superior de um elemento de ícone base. Em determinados contextos, a interface do usuário pode exigir que o elemento de status a ser combinado com um elemento base.  
  
-   Ícones de projeto geralmente são arquivos. ico que contêm vários tamanhos. Apenas os ícones de 16 x 16, 24 x 24 e 32 x 32 estão sendo atualizados. A maioria dos ícones de 16x16 e 24 x 24 conterá os mesmos elementos. Os ícones de 32 x 32 contêm mais detalhes, incluindo o tipo de idioma do projeto quando aplicável.  
  
-   Para 32 x 32 ícones, elementos base geralmente têm uma espessura de linha 2 pixels. Uma espessura de linha de pixel de 1 ou 2 pode ser usada para elementos de detalhe. Use o bom senso para determinar qual é mais adequado.  
  
-   Ter pelo menos um espaçamento 1 pixel entre elementos de 16x16 e os ícones de 24 x 24. Ícones de 32 x 32, use 2 pixels espaçamento entre elementos e entre o elemento base e o modificador.  
  
 ![Espaçamento de elementos para os ícones de 16 x 16, 24 x 24 e 32 x 32](../../extensibility/ux-guidelines/media/0404-47_elementspacing.png "47_ElementSpacing 0404")  
  
 **Espaçamento de elementos para ícones em tamanho 16x16, 24 x 24 e 32 x 32**  
  
#### <a name="color-and-accessibility"></a>Cor e acessibilidade  
 Diretrizes de conformidade do Visual Studio exigem que todos os ícones no produto passam os requisitos de acessibilidade para a cor e o contraste. Isso é obtido por meio de inversão de ícone, e quando você está criando, você deve estar ciente que será ser invertidas programaticamente no produto.  
  
 Para obter mais informações sobre como usar cores de ícones do Visual Studio, consulte [usando cores nas imagens](../../extensibility/ux-guidelines/images-and-icons-for-visual-studio.md#BKMK_UsingColorInImages).  
  
##  <a name="a-namebkmkusingcolorinimagesa-using-color-in-images"></a><a name="BKMK_UsingColorInImages"></a>Usando cores em imagens  
  
### <a name="overview"></a>Visão Geral  
 Ícones no Visual Studio são principalmente monocromáticos. Cor é reservada para transmitir informações específicas e nunca para a decoração. Cor é usada:  
  
-   para indicar uma ação  
  
-   para alertar o usuário para uma notificação de status  
  
-   para designar a afiliação de linguagem  
  
-   para diferenciar os itens no IntelliSense  
  
### <a name="accessibility"></a>Acessibilidade  
 Diretrizes de conformidade do Visual Studio exigem que todos os ícones verificadas para a passagem de produto os requisitos de acessibilidade para a cor e o contraste. Cores da paleta de linguagem visual foram testadas e atendem a esses requisitos.  
  
#### <a name="color-inversion-for-dark-themes"></a>Inversão de cores de temas escuros  
 Para exibir ícones com a taxa de contraste correto no tema escuro Visual Studio, uma inversão é aplicada por meio de programação. As cores deste guia foram escolhidas em parte para que eles Inverter corretamente. Restringir o uso de cores a essa paleta, ou você obterá resultados imprevisíveis quando é aplicada a inversão.  
  
 ![Exemplos de ícones cujas cores tiveram sido invertidos](../../extensibility/ux-guidelines/media/0405-01_darkthemeinversion.png "01_DarkThemeInversion&0405;")  
  
 **Exemplos de ícones que tiveram suas cores invertidas**  
  
### <a name="base-palette"></a>Paleta de base  
 Todos os ícones padrão contêm três cores base. Ícones não contenham nenhuma gradientes ou sombras, com uma ou duas exceções para os ícones de ferramenta 3D.  
  
|Uso|Nome|Valor (tema no claro)|Amostra de|Exemplo|  
|-----------|----------|---------------------------|------------|-------------|  
|Plano de fundo/escuro|VS BG|424242 / 66,66,66|![Amostra 424242](../../extensibility/ux-guidelines/media/0405_424242.png "0405_424242")|![Exemplo de paleta base](../../extensibility/ux-guidelines/media/0405-02_basepaletteexample.png "02_BasePaletteExample&0405;")|  
|Primeiro plano/leve|FG VS|F0EFF1 / 240,239,241|![Amostra F0EFF1](../../extensibility/ux-guidelines/media/0405_f0eff1.png "0405_F0EFF1")||  
|Contorno|VS-Out|F6F6F6 / 246,246,246|![Amostra F6F6F6](../../extensibility/ux-guidelines/media/0405_f6f6f6.png "0405_F6F6F6")||  
  
 Além das cores base, cada ícone pode conter adicionais em uma cor de paleta estendida.  
  
### <a name="extended-palette"></a>Paleta estendida  
  
#### <a name="action-modifiers"></a>Modificadores de ação  
 Quatro cores indicam os tipos de ações requeridas modificadores de ação:  
  
|Uso|Nome|Valor (todos os temas)|Amostra de|  
|-----------|----------|--------------------------|------------|  
|Positivo|Verde de ação do VS|388A34 / 56,138,52|![Amostra 388A34](../../extensibility/ux-guidelines/media/0405_388a34.png "0405_388A34")|  
|Negativo|VS ação vermelho|A1260D / 161,38,13|![Amostra A1260D](../../extensibility/ux-guidelines/media/0405_a1260d.png "0405_A1260D")|  
|Neutro|VS ação azul|C 00539 / 0,83,156|![Amostra de C 00539](../../extensibility/ux-guidelines/media/0405_00539c.png "0405_00539C")|  
|Criar/novo|VS ação laranja|C27D1A / 194,156,26|![Amostra C27D1A](../../extensibility/ux-guidelines/media/0405_c27d1a.png "0405_C27D1A")|  
  
##### <a name="examples"></a>Exemplos  
 Verde é usado para modificadores de ação positiva como "Adicionar", "Executar", "Reproduzir" e "Validar".  
  
|||||  
|-|-|-|-|  
|![Ícone executar](../../extensibility/ux-guidelines/media/0405-03_actionmodifierrun.png "0405&03;_ActionModifierRun") **executar**|![Ícone de consulta executar](../../extensibility/ux-guidelines/media/0405-04_executequery.png "0405&04;_ExecuteQuery") **executar consulta**|![Executar todos os ícone de etapas](../../extensibility/ux-guidelines/media/0405-05_playallsteps.png "0405&05;_PlayAllSteps") **executar todas as etapas**|![Ícone de controle Adicionar](../../extensibility/ux-guidelines/media/0405-06_addcontrol.png "0405&06;_AddControl") **adicionar controle**|  
  
 Vermelho é usado para modificadores de ação negativo como "Excluir," "Stop", "Cancelar" e "Fechar".  
  
|||||  
|-|-|-|-|  
|![Excluir relação ícone](../../extensibility/ux-guidelines/media/0405-07_deleterelationship.png "0405&07;_DeleteRelationship") **Excluir relação**|![Excluir coluna ícone](../../extensibility/ux-guidelines/media/0405-08_deletecolumn.png "0405&08;_DeleteColumn") **excluir coluna**|![Ícone de consulta de parada](../../extensibility/ux-guidelines/media/0405-09_stopquery.png "0405&09;_StopQuery") **parar consulta**|![Ícone de Conexão offline](../../extensibility/ux-guidelines/media/0405-10_connectionoffline.png "0405&10;_ConnectionOffline") **Conexão Offline**|  
  
 Azul é aplicada à ação neutra modificadores mais comumente representadas como setas, como "Open," "Próximo", "Anterior", "Importar" e "Exportar".  
  
|||||  
|-|-|-|-|  
|![Vá para o ícone de campo](../../extensibility/ux-guidelines/media/0405-11_gotofield.png "0405&11;_GoToField") **ir para o campo**|![Ícone de verificação Batched](../../extensibility/ux-guidelines/media/0405-12_batchedcheckin.png "0405&12;_BatchedCheckIn") **em lotes Check-In**|![Ícone do editor de endereço](../../extensibility/ux-guidelines/media/0405-13_addresseditor.png "0405&13;_AddressEditor") **Editor de endereço**|![Ícone do editor de associação](../../extensibility/ux-guidelines/media/0405-14_associationeditor.png "0405&14;_AssociationEditor") **Editor de associação**|  
  
 Ouro escuro é usado principalmente para o modificador de "Novo".  
  
|||||  
|-|-|-|-|  
|![Ícone do novo projeto](../../extensibility/ux-guidelines/media/0405-15_newproject.png "0405&15;_NewProject") **novo projeto**|![Ícone de gráfico Create new](../../extensibility/ux-guidelines/media/0405-16_createnewgraph.png "0405&16;_CreateNewGraph") **criar um novo gráfico**|![Novo ícone de teste de unidade](../../extensibility/ux-guidelines/media/0405-17_newunittest.png "0405&17;_NewUnitTest") **novo teste de unidade**|![Ícone de item de lista de novos](../../extensibility/ux-guidelines/media/0405-18_newlistitem.png "0405&18;_NewListItem") **Novo Item de lista**|  
  
#### <a name="special-cases"></a>Casos especiais  
 Em alguns casos, um modificador de ação colorido pode ser usado independentemente como um ícone autônomo. A cor usada para o ícone reflete as ações que o ícone está associado. Esse uso é limitado a um pequeno subconjunto de ícones, incluindo:  
  
||||||  
|-|-|-|-|-|  
|![Ícone executar](../../extensibility/ux-guidelines/media/0405-03_actionmodifierrun.png "0405&03;_ActionModifierRun") **executar**|![Ícone de interrupção](../../extensibility/ux-guidelines/media/0405-19_stop.png "0405&19;_Stop") **parar**|![Ícone Excluir](../../extensibility/ux-guidelines/media/0405-20_delete.png "0405&20;_Delete") **excluir**|![Salvar o ícone](../../extensibility/ux-guidelines/media/0405-21_save.png "0405&21;_Save") **salvar**|![Ícone de voltar Navigate](../../extensibility/ux-guidelines/media/0405-22_navigateback.png "0405&22;_NavigateBack") **navegue novamente**|  
  
### <a name="code-hierarchy-palette"></a>Paleta de hierarquia de código  
  
#### <a name="folder"></a>Pasta  
  
|Uso|Nome|Valor (todos os temas)|Amostra de|Exemplo|  
|-----------|----------|--------------------------|------------|-------------|  
|Pastas|Pasta|DCB67A / 220,182,122|![Amostra DCB67A](../../extensibility/ux-guidelines/media/0405_dcb67a.png "0405_DCB67A")|![Ícone de cor da pasta](../../extensibility/ux-guidelines/media/0405-23_foldercolor.png "23_FolderColor&0405;")|  
  
#### <a name="visual-studio-languages"></a>Idiomas do Visual Studio  
 Cada um dos idiomas comum ou plataformas disponíveis no Visual Studio tem uma cor associada. Essas cores são usadas no ícone de base, ou em modificadores de linguagem que aparecem no canto superior direito dos ícones compostas.  
  
|Uso|Nome|Valor (todos os temas)|Amostra de|  
|-----------|----------|--------------------------|------------|  
|ASP, HTML, WPF|ASP HTML WPF azul|7 0095D / 0,149,215|![Amostra 0095 D 7](../../extensibility/ux-guidelines/media/0405_0096d7.png "0405_0096D7")|  
|C++|Roxo CPP|9B4F96 / 155,79,150|![Amostra 9B4F96](../../extensibility/ux-guidelines/media/0405_9b4f96.png "0405_9B4F96")|  
|C#|CS Green (verde de ação do VS)|388A34 / 56,138,52|![Amostra 388A34](../../extensibility/ux-guidelines/media/0405_388a34.png "0405_388A34")|  
|CSS|Vermelho CSS|BD1E2D / 189,30,45|![Amostra BD1E2D](../../extensibility/ux-guidelines/media/0405_bd1e2d.png "0405_BD1E2D")|  
|F#|FS roxo|672878 / 103,40,120|![Amostra 672878](../../extensibility/ux-guidelines/media/0405_672878.png "0405_672878")|  
|JavaScript|JS laranja|F16421 / 241,100,33|![Amostra F16421](../../extensibility/ux-guidelines/media/0405_f16421.png "0405_F16421")|  
|VB|VB azul (VS ação azul)|C 00539 / 0,83,156|![Amostra de C 00539](../../extensibility/ux-guidelines/media/0405_00539c.png "0405_00539C")|  
|TypeScript|TS laranja|E04C06 / 224,76,6|![Amostra E04C06](../../extensibility/ux-guidelines/media/0405_e04c06.png "0405_E04C06")|  
|Python|Aj verde|879636 / 135,150,54|![Amostra 879636](../../extensibility/ux-guidelines/media/0405_879636.png "0405_879636")|  
  
##### <a name="examples-of-icons-with-language-modifiers"></a>Exemplos de ícones com modificadores de linguagem  
  
|||||||  
|-|-|-|-|-|-|  
|![Ícone de Visual Basic](../../extensibility/ux-guidelines/media/0405-25_vb.png "0405&25;_VB") **VB**|![Ícone de c#](../../extensibility/ux-guidelines/media/0405-26_csharp.png "0405&26;_CSharp") **c#**|![Ícone de C++](../../extensibility/ux-guidelines/media/0405-27_cplusplus.png "0405&27;_CPlusPlus") **C++**|![Ícone de F #](../../extensibility/ux-guidelines/media/0405-28_fsharp.png "0405&28;_FSharp") **F #**|![Ícone de JavaScript](../../extensibility/ux-guidelines/media/0405-29_javascript.png "0405&29;_JavaScript") **JavaScript**|![Ícone de Python](../../extensibility/ux-guidelines/media/0405-30_python.png "0405&30;_Python") **Python**|  
|![Ícone HTML](../../extensibility/ux-guidelines/media/0405-31_html.png "0405&31;_HTML") **HTML**|![Ícone do WPF](../../extensibility/ux-guidelines/media/0405-32_wpf.png "0405&32;_WPF") **WPF**|![Ícone ASP](../../extensibility/ux-guidelines/media/0405-33_asp.png "0405&33;_ASP") **ASP**|![Ícone CSS](../../extensibility/ux-guidelines/media/0405-34_css.png "0405&34;_CSS") **CSS**|![Ícone de typeScript](../../extensibility/ux-guidelines/media/0405-35_typescript.png "0405&35;_TypeScript") **TypeScript**||  
  
#### <a name="intellisense"></a>IntelliSense  
 Ícones de IntelliSense usam uma paleta de cores exclusivas. Essas cores são usadas para ajudar os usuários a diferenciar rapidamente os itens diferentes na lista pop-up do IntelliSense.  
  
|Uso|Nome|Valor (todos os temas)|Amostra de|  
|-----------|----------|--------------------------|------------|  
|Classe de evento|VS ação laranja|C27D1A / 194,125,26|![Amostra C27D1A](../../extensibility/ux-guidelines/media/0405_c27d1a.png "0405_C27D1A")|  
|Método de extensão, o delegado de método, o módulo|VS ação roxo|652D 90 / 101,45,144|![Amostra de 90 652D](../../extensibility/ux-guidelines/media/0405_652d90.png "0405_652D90")|  
|Campo, Item de Enum, Macro, estrutura, tipo de valor de união, operador, Interface|VS ação azul|C 00539 / 0,83,156|![Amostra de C 00539](../../extensibility/ux-guidelines/media/0405_00539c.png "0405_00539C")|  
|Objeto|Verde de ação do VS|388A34 / 56,138,52|![Amostra 388A34](../../extensibility/ux-guidelines/media/0405_388a34.png "0405_388A34")|  
|Constante, exceção, Item de Enum, mapa, Item de mapa, Namespace, modelo, definição de tipo|Plano de fundo (VS BG)|424242 / 66,66,66|![Amostra 424242](../../extensibility/ux-guidelines/media/0405_424242.png "0405_424242")|  
  
##### <a name="examples-of-intellisense-icons"></a>Exemplos de ícones do IntelliSense  
  
||||||  
|-|-|-|-|-|  
|![Ícone de classe IntelliSense](../../extensibility/ux-guidelines/media/0405-36_intellisenseclass.png "0405&36;_IntelliSenseClass") **classe**|![Ícone de evento particular IntelliSense](../../extensibility/ux-guidelines/media/0405-37_intellisenseprivateevent.png "0405&37;_IntelliSensePrivateEvent") **evento particular**|![Ícone de delegado IntelliSense](../../extensibility/ux-guidelines/media/0405-38_intellisensedelegate.png "0405&38;_IntelliSenseDelegate") **delegar**|![Ícone de amigo do IntelliSense método](../../extensibility/ux-guidelines/media/0405-39_intellisensemethodfriend.png "0405&39;_IntelliSenseMethodFriend") **método Friend**|![Ícone de campo](../../extensibility/ux-guidelines/media/0405-40_field.png "0405&40;_Field") **campo**|  
|![IntelliSense protegido ícone do item de enum](../../extensibility/ux-guidelines/media/0405-41_intellisenseprotectedenumitem.png "0405&41;_IntelliSenseProtectedEnumItem") **Item protegido de Enum**|![Ícone do objeto IntelliSense](../../extensibility/ux-guidelines/media/0405-42_intellisenseobject.png "0405&42;_IntelliSenseObject") **objeto**|![Ícone de modelo do IntelliSense](../../extensibility/ux-guidelines/media/0405-43_intellisensetemplate.png "0405&43;_IntelliSenseTemplate") **modelo**|![Ícone de atalho do IntelliSense exceção](../../extensibility/ux-guidelines/media/0405-44_intellisenseexceptionshortcut.png "0405&44;_IntelliSenseExceptionShortcut") **atalho de exceção**||  
  
### <a name="notifications"></a>Notificações  
 Notificações no Visual Studio são usadas para indicar o status. A paleta de notificação usa os seguintes quatro cores, bem como opções de preenchimento de primeiro plano preto ou branco, para definir notificações com os seguintes níveis de status.  
  
|Uso|Nome|Valor (todos os temas)|Amostra de|  
|-----------|----------|--------------------------|------------|  
|Status: neutro|Notificação Blue (azul VS)|1BA1E2 / 27,161,226|![Amostra 1BA1E2](../../extensibility/ux-guidelines/media/0405_1ba1e2.png "0405_1BA1E2")|  
|Status: positivo|Notificação verde (VS verde)|339933 / 51,153,51|![Amostra 339933](../../extensibility/ux-guidelines/media/0405_339933.png "0405_339933")|  
|Status: negativo|Notificação vermelho (VS vermelho)|E51400 / 229,20,0|![Amostra E51400](../../extensibility/ux-guidelines/media/0405_e51400.png "0405_E51400")|  
|Status: aviso|Notificação amarelo (VS laranja)|FFCC00 / 255,204,0|![Amostra FFCC00](../../extensibility/ux-guidelines/media/0405_ffcc00.png "0405_FFCC00")|  
|Preenchimento de primeiro plano|Notificação Black (preto)|000000 / 0,0,0|![Amostra de&#00000;0](../../extensibility/ux-guidelines/media/0405_000000.png "0405_000000")|  
|Preenchimento de primeiro plano|Notificação branco (branco)|FFFFFF / 255,255,255|![Amostra FFFFFF](../../extensibility/ux-guidelines/media/0405_ffffff.png "0405_FFFFFF")|  
  
#### <a name="examples-of-notification-icons"></a>Exemplos de ícones de notificação  
  
|||||  
|-|-|-|-|  
|![Ícone de alerta](../../extensibility/ux-guidelines/media/0405-45_alert.png "0405&45;_Alert") **alerta**|![Ícone de aviso](../../extensibility/ux-guidelines/media/0405-48_warning.png "0405&48;_Warning") **aviso**|![Ícone concluído](../../extensibility/ux-guidelines/media/0405-46_complete.png "0405&46;_Complete") **concluída**|![Ícone de interrupção](../../extensibility/ux-guidelines/media/0405-47_stop.png "0405&47;_Stop") **parar**|  
  
### <a name="visual-studio-online"></a>Visual Studio Online  
 Em geral, o Visual Studio Online consiste em recursos hospedados em um navegador. Varia a cor em ambientes diferentes, mas o estilo permanece o mesmo.  
  
|Grupo|Uso|Nome|Valor (todos os temas)|Amostra de|  
|-----------|-----------|----------|--------------------------|------------|  
|TFS|Informações preliminares|TFSO BG|656565/ 101, 101, 101|![Amostra 656565](../../extensibility/ux-guidelines/media/0405_656565.png "0405_656565")|  
|TFS|Contorno|TFSO-OUT|FFFFFF / 255, 255, 255|![Amostra FFFFFF](../../extensibility/ux-guidelines/media/0405_ffffff.png "0405_FFFFFF")|  
|Napa|Informações preliminares|Branco|FFFFFF / 255, 255, 255|![Amostra FFFFFF](../../extensibility/ux-guidelines/media/0405_ffffff.png "0405_FFFFFF")|  
|Monaco|Informações preliminares|Branco|FFFFFF / 255, 255, 255|![Amostra FFFFFF](../../extensibility/ux-guidelines/media/0405_ffffff.png "0405_FFFFFF")|  
|F12|Informações preliminares|Branco|FFFFFF / 255, 255, 255|![Amostra FFFFFF](../../extensibility/ux-guidelines/media/0405_ffffff.png "0405_FFFFFF")|  
|F12|Normal|Grey_Primary F12|555555 / 85, 85, 85|![Amostra 555555](../../extensibility/ux-guidelines/media/0405_555555.png "0405_555555")|  
|F12|Focalizar|Blue_Hover F12|2279BF / 34,121,191|![Amostra 2279BF](../../extensibility/ux-guidelines/media/0405_2279bf.png "0405_2279BF")|  
|F12|Disabled|LtGrey_Disabled F12|ABABAC / 171,171,172|![Amostra ABABAC](../../extensibility/ux-guidelines/media/0405_ababac.png "0405_ABABAC")|  
|F12|Plano de fundo em foco|Passe o mouse bg|D9EBF7 / 217,235,247|![Amostra D9EBF7](../../extensibility/ux-guidelines/media/0405_d9ebf7.png "0405_D9EBF7")|  
|F12|Plano de fundo pressionado|Bg pressionado|B2D7F0 / 178,215,240|![Amostra B2D7F0](../../extensibility/ux-guidelines/media/0405_b2d7f0.png "0405_B2D7F0")|  
|F12|Contorno|VS-OUT|F6F6F6 / 246,246,246|![Amostra F6F6F6](../../extensibility/ux-guidelines/media/0405_f6f6f6.png "0405_F6F6F6")|  
|F12|Informações|Informações|00BCF2 / 0,188,242|![Amostra 00BCF2](../../extensibility/ux-guidelines/media/0405_00bcf2.png "0405_00BCF2")|  
|F12|Aviso|Aviso|F28300 / 242,131,0|![Amostra F28300](../../extensibility/ux-guidelines/media/0405_f28300.png "0405_F28300")|  
|F12|Erro / negativo|Error_Negative|E81123 / 232,17,35|![Amostra E81123](../../extensibility/ux-guidelines/media/0405_e81123.png "0405_E81123")|  
|F12|Iniciar / positivo|Start_Positive|009E49 / 0,158,73|![Amostra 009E49](../../extensibility/ux-guidelines/media/0405_009e49.png "0405_009E49")|  
|F12|Tipo de intervalo|Tipo de intervalo|9B4F96 / 155,79,150|![Amostra 9B4F96](../../extensibility/ux-guidelines/media/0405_9b4f96.png "0405_9B4F96")|  
|F12|Marca de evento|Marca de evento|A51F00 / 165,31,0|![Amostra A51F00](../../extensibility/ux-guidelines/media/0405_a51f00.png "0405_A51F00")|  
|F12|Marca do Usuário|Marca do Usuário|F16220 / 241,98,32|![Amostra F16220](../../extensibility/ux-guidelines/media/0405_f16220.png "0405_F16220")|  
  
#### <a name="examples-of-visual-studio-online-icons"></a>Exemplos de ícones Visual Studio Online  
  
|TFS Online||||  
|----------------|-|-|-|  
|![Ícone de equipe TFS Online](../../extensibility/ux-guidelines/media/0405-49_tfsonlineteam.png "0405&49;_TFSOnlineTeam") **equipe Online**|![Ícone de informações do TFS](../../extensibility/ux-guidelines/media/0405-50_tfsinformation.png "0405&50;_TFSInformation") **informações**|![Ícone de histórico do TFS](../../extensibility/ux-guidelines/media/0405-51_tfshistory.png "0405&51;_TFSHistory") **histórico**|![Ícone de ramificação do TFS](../../extensibility/ux-guidelines/media/0405-52_tfsbranch.png "0405&52;_TFSBranch") **ramificação**|  
  
|Napa||||  
|----------|-|-|-|  
|![Ícone de conteúdo Napa](../../extensibility/ux-guidelines/media/0405-53_napacontent.png "0405&53;_NapaContent") **conteúdo**|![Ícone de email do office Napa](../../extensibility/ux-guidelines/media/0405-54_napaofficemail.png "0405&54;_NapaOfficeMail") **email do Office**|![Ícone do SharePoint Napa](../../extensibility/ux-guidelines/media/0405-55_napasharepoint.png "0405&55;_NapaSharePoint") **SharePoint**|![Ícone do painel de tarefas Napa](../../extensibility/ux-guidelines/media/0405-56_napataskpane.png "0405&56;_NapaTaskPane") **painel de tarefas**|  
  
|Monaco||||  
|------------|-|-|-|  
|![Ícone de arquivos Monaco](../../extensibility/ux-guidelines/media/0405-57_monacofiles.png "0405&57;_MonacoFiles") **arquivos**|![Ícone de Mônaco gito](../../extensibility/ux-guidelines/media/0405-58_monacogit.png "0405&58;_MonacoGit") **Git**|![Ícone de pesquisa Monaco](../../extensibility/ux-guidelines/media/0405-59_monacosearch.png "0405&59;_MonacoSearch") **pesquisa**|![Ícone de texto Monaco](../../extensibility/ux-guidelines/media/0405-60_monacotext.png "0405&60;_MonacoText") **texto**|  
  
|F12||||  
|---------|-|-|-|  
|![Ícone de código muito F12](../../extensibility/ux-guidelines/media/0405-61_f12prettycode.png "0405&61;_F12PrettyCode") **muito código**|![Ícone de aviso F12](../../extensibility/ux-guidelines/media/0405-62_f12warning.png "0405&62;_F12Warning") **aviso**|![Ícone de F12 emular](../../extensibility/ux-guidelines/media/0405-63_f12emulate.png "0405&63;_F12Emulate") **Emulate**|
