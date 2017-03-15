---
title: Menus e comandos para o Visual Studio | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0a1ed675-2bd1-4603-ba3a-f40dfb5cfb69
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
ms.openlocfilehash: ab5a420cdde6a35d89f243c1a8067f32e0eebfd0
ms.lasthandoff: 02/22/2017

---
# <a name="menus-and-commands-for-visual-studio"></a>Menus e comandos para o Visual Studio
## <a name="command-usage"></a>Uso do comando  
  
### <a name="overview"></a>Visão Geral  
 Ao contrário do Microsoft Office, que é um pacote que inclui muitos produtos separados, o Visual Studio contém muitos produtos que cada contribuem seus conjuntos de comandos ao IDE do Visual Studio global. O IDE gerencia a complexidade de milhares de comandos filtrando a funcionalidade disponível para o usuário com base no contexto.  
  
 Quando altera um contexto do usuário – como alternar de uma janela de design para um janela de edição de código – funcionalidade não relacionada ao novo contexto desaparece. Ao mesmo tempo, junto com informações dinâmicas relacionadas, como opções de caixa de ferramentas e propriedades novas superfícies de funcionalidade. O usuário não verá a troca do conjunto de comandos disponíveis. Se o usuário é distraído ou confuso com comandos que aparecem ou desaparecem, o design de interface do usuário precisa ajuste. O contexto do usuário atual é sempre indicado em uma ou mais maneiras, como na barra de título do IDE, a janela Propriedades ou a caixa de diálogo Property Pages.  
  
 Barras de comando permitem flexibilidade na interface do usuário. O único comando estruturas inerentes ao Visual Studio ambiente estão o menu principal e a barra de comando principal, que pode tanto ser personalizada e até mesmo oculta. Outras barras de comando apareçam e desapareçam com base no estado do aplicativo. Janelas de ferramenta e editores de documento também podem conter barras de ferramentas inseridas dentro de suas bordas da janela.  
  
#### <a name="basic-guidelines"></a>Diretrizes básicas  
  
##### <a name="use-existing-shared-commands-command-groups-and-menus-whenever-possible"></a>Use comandos compartilhados existentes, grupos de comando e menus sempre que possível.  
 Como comandos normalmente são mostrados com base no contexto, o uso de menus compartilhados existentes e grupos de comando garante que a estrutura de comando permanecerá relativamente estável entre as alterações no contexto. Reutilizar comandos compartilhados e a inclusão de novos comandos próximos comandos compartilhados relacionados também reduz a complexidade do IDE e cria uma experiência mais amigável. Se um novo comando precisa ser definida, tente colocá-lo em um grupo de comando compartilhado existente. Se um novo grupo precisa ser definido, coloque-o em um menu compartilhado existente perto de um grupo de comandos relacionados antes de criar um novo menu de nível superior.  
  
##### <a name="do-not-create-icons-for-every-command"></a>Não crie ícones para cada comando.  
 Pense cuidadosamente antes de criar um ícone do comando. Ícones devem ser criados somente para os comandos que:  
  
-   aparecem na barra de ferramentas padrão.  
  
-   devem ser adicionados por usuários para uma barra de ferramentas por meio de **personalizar...** caixa de diálogo.  
  
-   ter um ícone associado a mesma ação em outro produto da Microsoft.  
  
##### <a name="limit-the-addition-of-keyboard-shortcuts"></a>Limitar a adição dos atalhos de teclado  
 A maioria dos usuários empregar uma pequena fração de todos os atalhos disponíveis. Em caso de dúvida, não vincule o recurso a um atalho de teclado. Trabalhar com seu usuário experiência equipe antes de adicionar novos atalhos.  
  
##### <a name="give-commands-a-default-menu-placement"></a>Dar um posicionamento de menu padrão de comandos.  
 Lembre-se de que seus comandos serão personalizados por outras pessoas e criá-las adequadamente. Não há nenhum algo como um comando oculto. Todos os comandos do Visual Studio aparecem no **ferramentas > personalizar** caixa de diálogo, a janela de comando, preenchimento automático, o **Ferramentas > opções > teclado** caixa de diálogo e o desenvolvimento de ferramentas DTE (ambiente). Certifique-se de dar a seus comandos de um nome e uma dica de ferramenta no seu arquivo .ctc para que os usuários podem localizá-los facilmente.  
  
##### <a name="do-not-duplicate-shared-commands-on-an-embedded-toolbar"></a>Não duplicado compartilhados comandos em uma barra de ferramentas inserida.  
 É útil colocar os comandos em proximidade com a área de foco do usuário. Uma maneira de fazer isso é criar uma barra de ferramentas inserida na parte superior do documento ou janela de ferramentas editor. Os comandos colocados na barra de ferramentas devem ser específicos para a região do conteúdo dentro da janela. Não duplicado compartilhados comandos essas barras de ferramentas. Por exemplo, nunca coloque um ícone de "Salvar" dentro de uma barra de ferramentas inserida.  
  
### <a name="content-and-command-visibility"></a>Visibilidade do conteúdo e comando  
 Comandos existem os seguintes escopos: **ambiente**, **hierarquia**, e **documento**. Conhecer cada escopo para ter confiança no posicionamento de comando.  
  
 Comandos no **ambiente** escopo estabelecer contexto primário e são compartilhados entre vários contextos. Eles alteram a visibilidade ou a organização de documentos e janelas de ferramenta. Entre os comandos no ambiente do escopo são **novo projeto**, **conectar ao servidor**, **anexar processo**, **Recortar**, **cópia**, **colar**, **localizar**, **opções**, **personalizar**, **nova janela**, e **exibir ajuda**.  
  
 Comandos no **hierarquia** escopo gerenciar hierarquias de Visual Studio, incluindo **projeto**, **equipe**, e **dados**. Eles se relacionam com o contexto do projeto – por exemplo, **depurar**, **criar**, **teste**, **arquitetura**, ou **analisar**. Entre os comandos na hierarquia de escopo são **Adicionar Novo Item**, **nova consulta**, **configurações do projeto**, **Add New Data Source**, **Launch Performance Wizard**, e **novo diagrama**.  
  
 Comandos no **documento** ato de escopo no conteúdo de um documento, como código, design ou uma consulta de item de trabalho (WIQ). Eles também funcionar no modo de exibição de uma janela de ferramenta ou caso contrário são específicos para essa janela de ferramenta. Comandos de escopo do documento também atuam sobre os objetos de arquivo que são específicas à hierarquia, como **remover do projeto**. Entre os comandos no documento de escopo são **refatorar > Renomear**, **criar cópia do Item de trabalho**, **Expandir tudo**, **Recolher tudo**, e **criar tarefa de usuário**.  
  
### <a name="command-placement-decisions"></a>Decisões de posicionamento de comando  
 Depois de decidir criar um comando, você precisará determinar o posicionamento adequado e se deseja criar um atalho de teclado. Siga este caminho de decisão para estabelecer onde colocar o comando:  
  
 ![Gráfico de decisão de posicionamento do comando](../../extensibility/ux-guidelines/media/0501-a_commandplacement.png "0501 a_CommandPlacement")  
  
 **Caminho de decisão para o posicionamento de comando no Visual Studio**  
  
### <a name="command-placement-in-menus"></a>Posicionamento de comando nos menus  
  
#### <a name="main-menu-bar"></a>Barra de menus principal  
 A barra de menus principal deve ser o local padrão para comandos de quaisquer pacotes de menu de contexto específico que contribuem para a interface do usuário. A barra de menus principal é diferente de outras estruturas de comando, o ambiente usa para controlar quais comandos estão visíveis. Todas as barras de comando simplesmente desativar comandos que estão fora do contexto, eles são colocados em um menu ou uma barra de ferramentas.  
  
 O ambiente define um conjunto de comandos incorporados a barra de menus principal que são comuns em todo o IDE e vários domínios de tarefa. Esses comandos são sempre visíveis independentemente dos quais os VSPackages são carregados no ambiente. Embora os VSPackages pode estender este conjunto de comandos, o conjunto de cada produto e o posicionamento dos seus comandos de comandos é responsabilidade de cada equipe.  
  
 A estrutura do menu principal do Visual Studio pode ser dividida nas seguintes categorias de menu:  
  
##### <a name="core-menus"></a>Menus principais  
  
-   Arquivo  
  
-   Editar  
  
-   Exibir  
  
-   Ferramentas  
  
-   Janela  
  
-   Ajuda  
  
##### <a name="project-specific-menus"></a>Menus específicos de projeto  
  
-   Projeto  
  
-   Build  
  
-   Depurar  
  
##### <a name="context-specific-menus"></a>Menus de contexto específico  
  
-   Equipe  
  
-   Dados  
  
-   Teste  
  
-   Arquitetura  
  
-   Analisar  
  
##### <a name="document-specific-menus"></a>Menus específicos de documento  
  
-   Formatar  
  
-   Tabela  
  
##### <a name="when-designing-main-menus-adhere-to-these-rules"></a>Durante a criação de menus principais, seguem estas regras:  
  
-   Não exceder 25 itens de nível superior em um determinado contexto  
  
-   Menus nunca devem exceder 600 pixels de altura.  
  
-   Avalie um menu principal em vários contextos, como a SKU Ultimate e o perfil geral.  
  
-   Menus suspensos são aceitáveis.  
  
-   Menus suspensos devem conter pelo menos três itens e não mais do que sete.  
  
-   Menus suspensos devem ir somente um nível de profundidade – alguns itens de menu do Visual Studio têm submenus em cascata, mas não é incentivado a esse padrão.  
  
-   Use separadores não mais de seis. Agrupamentos devem aderir a ilustração a seguir:  
  
     ![Diretrizes para agrupamento de menu principal](../../extensibility/ux-guidelines/media/0501-b_mainmenus.png "0501 b_MainMenus")  
  
-   Embora ele não é necessária para que cada agrupamento na figura, adicionando agrupamentos adicionais é restrito.  
  
-   Cada agrupamento deve ter de dois a sete itens de menu.  
  
#### <a name="main-menu-ordering"></a>Ordenação de menu principal  
 Antes de adicionar um novo item de nível superior, considere colocar o comando em um menu de nível superior existente. Ao adicionar um novo menu de nível superior, certifique-se de colocá-lo no local correto. Decida se o menu é específico ao projeto, o contexto ou o documento. Mantenha o nome do menu de nível superior concisa e use apenas uma palavra.  
  
 Os menus principais devem delimitador o restante dos comandos. Arquivo, editar e exibir sempre devem ser à esquerda e ferramentas, janela, e ajuda deve ser sempre à direita.  
  
#### <a name="context-menus"></a>Menus de contexto  
 Colocar muita funcionalidade em menus de contexto resulta em uma interface difíceis de aprender. Todas as principais funcionalidades devem estar disponíveis por meio da barra de menus principal. Posicionamento de comandos deve ser reconciliado com comandos existentes para evitar comandos duplicados. Menus de contexto, o shell define os grupos de menus padrão que devem ser incluídos, dependendo se o menu de contexto é a solução, um nó de projeto ou um item de projeto.  
  
 Durante a criação de menus de contexto, siga as mesmas regras para o menu principal e, além disso:  
  
-   Não exceda 25 itens de menu de nível superior.  
  
-   Menus suspensos são aceitáveis, mas deve não exceder um nível de profundidade – nunca use submenus em cascata.  
  
-   Use separadores não mais de seis.  
  
### <a name="command-placement-in-toolbars"></a>Posicionamento de comando nas barras de ferramentas  
  
#### <a name="general-toolbars"></a>Barras de ferramentas gerais  
 Ao criar e organizar barras de ferramentas, siga esses padrões:  
  
-   Não use mais de um verbo por botão. Um botão = uma ação.  
  
-   Use texto ao lado do ícone somente se ele precisa ser reforçada com o rótulo.  
  
-   Use uma caixa de combinação exclusivamente para propriedades que serão trocadas várias vezes em uma sessão. Caso contrário, expõem a propriedade em outro lugar.  
  
-   A largura de uma caixa de combinação deve ser igual a largura do item mais longo na caixa + 30%. Por exemplo, se o item mais longo é 200 pixels, a caixa de combinação deve ser 260 pixels de largura.  
  
-   Limite o uso de separadores. O uso de um separador ao lado de uma lista suspensa é um antipadrão porque a forma do menu suspenso em si atua como um separador visual.  
  
-   Grupos de ícone devem conter de três a seis ícones.  
  
-   Se qualificadores resultarem em vários comandos úteis, use um botão de divisão que armazena a última configuração:  
  
     ![Dividir botões no Visual Studio](../../extensibility/ux-guidelines/media/0501-c_splitbuttons.png "0501 c_SplitButtons")  
  
     **Exemplo de um botão de divisão. Em vez disso, ajustar os seis comandos à esquerda em um único botão.**  
  
#### <a name="product-specific-toolbars"></a>Barras de ferramentas específicas do produto  
 Cada produto pode fornecer uma barra de ferramentas padrão que contém usados com frequência e comandos importantes e ferramentas padrão de cada produto devem aparecer na primeira vez em que o Visual Studio é iniciado depois que o produto foi instalado.  
  
 Produtos também devem aproveitar grupos do comando compartilhado e menus fornecidos pelo IDE. Cada grupo de comando compartilhado é colocado em um menu compartilhado deve organizar os comandos relacionados de forma significativa para o usuário. É importante aproveitar essa estrutura de comando compartilhado para reduzir a complexidade.  
  
#### <a name="global-toolbars"></a>Barras de ferramentas global  
 Barras de ferramentas global são necessárias para caber em uma linha prontos. Ao criar uma nova barra de ferramentas global, siga as diretrizes para esse tipo de barra de ferramentas.  
  
 **Diretrizes gerais de ferramentas:**  
  
-   Cada barra de ferramentas tem 24 pixels em controles comuns (garra, estouro).  
  
-   Cada botão da barra de ferramentas é 22 pixels de largura incluindo preenchimento. Tornar o ícone de um botão de divisão adiciona outro 11 pixels de largura.  
  
-   É permitida a duplicação de comandos em barras de ferramentas.  
  
 **Barras de ferramentas específicas de documentos** aparecem quando um determinado tipo de arquivo está ativo e desaparecem quando outro tipo de arquivo se torna ativo.  
  
-   Barras de ferramentas específicas de documento não podem ter mais de 12 botões.  
  
-   A largura total da barra de ferramentas não pode exceder 300 pixels.  
  
-   Cada tipo de arquivo pode ter uma barra de ferramentas incorporada ou um documento específico de ferramentas global, mas não ambos.  
  
 **Barras de ferramentas específicas de contexto** aparecem quando um determinado contexto é definido e tendem a permanecer ativas por longos períodos.  
  
-   O limite de botão para todas as barras de ferramentas específicas de contexto é 18.  
  
-   Se a maioria dos usuários não empregar consistentemente comandos essa barra de ferramentas quando o contexto está ativo, não associe essa barra de ferramentas com um contexto.  
  
-   Certifique-se de que a barra de ferramentas desaparecerá quando você sair do contexto. Nenhuma dessas barras de ferramentas deve aparecer na inicialização.  
  
 **Barras de ferramentas com nenhum contexto** nunca aparecem automaticamente. Elas aparecem somente quando o usuário os ativa. Mantenha a largura máxima abaixo de 200 pixels.  
  
### <a name="general-organization-and-shell-defined-groups"></a>Grupos definidos pelo shell e organização geral  
 Use comandos compartilhados existentes, grupos de comando e menus. Se um novo comando precisa ser definida, tente colocá-lo em um grupo de comando compartilhado existente. Se um novo grupo precisa ser definida, tente colocá-lo em um menu compartilhado existente perto de um grupo de comandos relacionados antes de criar um novo menu de nível superior. Isso reduz a complexidade do comando garantindo o posicionamento de comando consistente no IDE.  
  
 Compartilhado **formato** menu, geralmente mostrado no contexto de janelas de documento de estilo do designer, é ilustrado na imagem a seguir:  
  
 ![Menu do Visual Studio formato com textos explicativos](../../extensibility/ux-guidelines/media/0501-d_formatmenu.png "0501 d_FormatMenu")  
  
 **Grupos de menus no Visual Studio**  
  
### <a name="reducing-and-reusing-commands"></a>Reduzindo e reutilizar comandos  
 Comandos são normalmente mostrados com base no contexto, para reduzir o número de comandos que o usuário vê a qualquer momento. No entanto, você também deve reutilizar menus compartilhados existentes e grupos de comando para garantir que a estrutura de comando permanecerá relativamente estável entre as alterações no contexto.  
  
 Reutilizar comandos compartilhados e a inclusão de novos comandos próximos comandos compartilhados relacionados reduz a complexidade do IDE e cria uma experiência mais amigável.  
  
## <a name="naming-commands"></a>Comandos de nomenclatura  
  
### <a name="naming-conventions"></a>Convenções de nomenclatura  
 Comando consistente de nomenclatura é essencial para que os usuários podem localizar e executar comandos, usando a linha de comando ou associação a um atalho de teclado. Nomes de comando também ajudar o usuário a entender qual finalidade serve de um comando quando ele for exibido na barra de ferramentas ou em um menu de contexto ou em cascata.  
  
#### <a name="when-naming-commands"></a>Ao nomear comandos:  
  
-   Construa o texto para que ele seja facilmente localizável. Para obter mais informações sobre como localizar texto, consulte [preparação para o mundo para o Visual Studio](http://msdn.microsoft.com/en-us/1cc35051-8126-441f-bea9-059245a47b1d).  
  
-   Seja conciso. Comandos devem usar não mais do que três palavras.  
  
-   Usar a capitalização de título caso: a primeira letra de cada palavra deve estar em letras maiusculas. Para obter mais informações sobre formatação de texto no Visual Studio, consulte [estilo de texto](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TextStyle).  
  
-   Leve em consideração onde o comando será colocado. Está em um menu de nível superior ou um submenu? Por exemplo, quando os comandos de alinhamento de agrupamento em um submenu, o comando de nível superior devem ser "Alinhar" e os comandos de submenu deve ser "Left" "Right", "Centro", "justificar" e assim por diante. Seria redundante para nomear os comandos de submenu "Alinhar à esquerda" ou "Alinhar à direita."  
  
     ![Menu do Visual Studio formato](../../extensibility/ux-guidelines/media/0502-a_formatmenu.png "a_FormatMenu&0502;")  
  
### <a name="using-icons-with-commands"></a>Usando ícones com comandos  
 Ser econômico no uso de emparelhamento com comandos de ícone. Embora a associação de uma imagem exclusiva com um comando acelera muito a capacidade do usuário para identificar esse comando, ineficiência e desordem ocorrem com uso excessivo de imagem. As regras a seguir ajudam ao decidir se deseja criar um ícone do comando.  
  
#### <a name="use-an-icon-with-a-command-only-if"></a>Use um ícone com um comando apenas se:  
  
-   O mesmo comando tem um ícone associado a ele de outro produto proeminente da Microsoft, como um dos aplicativos do Microsoft Office.  
  
-   O comando será colocado em uma barra de ferramentas padrão.  
  
-   O comando é um comando de especialidade que os usuários podem adicionar uma barra de ferramentas usando o **"Personalizar..."** caixa de diálogo.  
  
## <a name="access-and-shortcut-keys"></a>Chaves de acesso e de atalho  
  
### <a name="overview"></a>Visão Geral  
 Há dois tipos de atribuições de tecla do teclado:  
  
-   **Chaves de acesso** (também conhecido como aceleradores) permitem o acesso de teclado por meio de menus para comandos e a cada rótulo na caixa de diálogo da interface do usuário. Teclas de acesso são principalmente para fins de acessibilidade, são atribuídas a todos os menus e a maioria dos controles de caixa de diálogo, não se destinam a ser memorizadas, afeta apenas a janela atual e estão localizadas.  
  
-   **Teclas de atalho** principalmente usar controle (Ctrl) e sequências de teclas de função (Fn). Eles são projetados mais para usuários avançados e auxiliam na produtividade. Eles são atribuídos apenas aos comandos usados com mais frequência e permitem o acesso rápido ao ignorar o menu principal. Teclas de atalho devem ser memorizadas e para que os motivo deve ser atribuído consistente com o esquema de perfil. Esquemas de teclas de atalho podem variar para cada perfil. Um usuário pode personalizar as teclas de atalho por meio de **Ferramentas > opções > teclado**.  
  
### <a name="assigning-access-keys"></a>Atribuindo teclas de acesso  
 Chaves de acesso consistem em chaves Alt mais alfanuméricos. Atribua uma chave de acesso para cada item de menu sem exceção. Siga as convenções comuns para a atribuição de chaves de acesso e Windows. Por exemplo, a chave de acesso para **arquivo > novo** deve ser sempre **Alt, F, N**.  
  
 Não use letras de largura de pixel único como 'i' (em maiusculas ou minúsculas) ou uma minúscula ' l'e evite usar caracteres com descendentes (g, j, p, q e y), conforme elas são difíceis de distinguir.  
  
 Evite usar chaves duplicadas quando possível. Em casos em que a eliminação de duplicação é inevitável, o sistema de menus trata conflitos, alternando entre todos os comandos que usam a chave. Por exemplo, para um controle de comando "Number" no menu arquivo que duplica a chave de acesso "N" **Alt, F, N** seria criar um novo arquivo, e **Alt, F, N, N** deve executar o comando "Number".  
  
### <a name="assigning-shortcut-keys"></a>Atribuindo teclas de atalho  
 Evite atribuir novas teclas de atalho, porque eles não são necessários para todos os comandos e se o uso excessivo de imposto do sistema (e a memória do usuário). Dados do programa de aperfeiçoamento de experiência para cliente (CEIP) indicam que os usuários do Visual Studio usam apenas um pequeno subconjunto dos atalhos integrados.  
  
 Ao definir atalhos, siga estas regras:  
  
-   **Usar o controle (Ctrl) e sequências de teclas de função (Fn).**  
  
-   **Preserve os atalhos usados com frequência.** Manter os atalhos mais populares.  
  
-   **Atalhos do editor tornam fácil de digitar.** Vincule para tipo atalhos para comandos que os desenvolvedores precisam mais enquanto escreve o código. Por exemplo, **Edit.InvokeSmartTag** deve ter uma tecla de atalho rápido como Ctrl c++ e não Alt + Shift + F10.  
  
-   **Se esforçar para atalhos de maneira consistente com temas.**  
  
-   **Siga as diretrizes do Windows para determinar quais modificador teclas empregar.** Use combinações de teclas Ctrl para comandos que têm efeitos em larga escala, como comandos que se aplicam a um documento inteiro. Use combinações de tecla Shift para comandos que estenderem ou complementam as ações a tecla de atalho padrão. Não use combinações de teclas Ctrl + Alt.  
  
-   **Remova atalhos estranhos.** Se você tiver um recurso herdado, considere remover atalhos que são usados com pouca frequência extreme a (menos de 10 horas de dados CEIP) ou pouca frequência moderada (menos de 100 vezes dos dados do CEIP) se uma chave de acesso fornece acesso rápido para o mesmo comando. Por exemplo: C Alt, H, abrirá/conteúdo da Ajuda.  
  
 Não há uma maneira simples de verificar a disponibilidade de atalho. Se você quiser adicionar um atalho, siga estas etapas:  
  
1.  Verifique a lista de [atalhos do Visual Studio 2013](http://visualstudioshortcuts.com/2013/) para determinar se há comandos semelhantes para agrupar sua com.  
  
2.  Vá para **Ferramentas > opções > ambiente > teclado** e testar seu atalho. Verifique cada esquema de mapeamento de teclado listados em "Aplicar o seguinte esquema de mapeamento de teclado adicionais". Verificar perfis geral, c#, VB e C++, como aqueles compartilhem atalhos exclusivos. O atalho está disponível se ele não está mapeado em qualquer um desses locais.
