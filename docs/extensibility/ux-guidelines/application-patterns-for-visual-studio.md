---
title: "Padrões de aplicativo para o Visual Studio | Microsoft Docs"
ms.custom: 
ms.date: 04/26/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8ed68602-4e28-46fe-b39f-f41979b308a2
caps.latest.revision: 7
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
ms.openlocfilehash: 7c2612cb537a6f3197cf9f99a0dc11981dfc73e1
ms.contentlocale: pt-br
ms.lasthandoff: 05/04/2017

---
# <a name="application-patterns-for-visual-studio"></a>Padrões de aplicativo para o Visual Studio
##  <a name="BKMK_WindowInteractions"></a>Interações de janela  
  
### <a name="overview"></a>Visão Geral  
Os dois tipos de janela principal usados no Visual Studio são editores de documento e janelas de ferramenta. Raras, mas possível, é grandes caixas de diálogo sem janela restrita. Embora essas sejam tudo sem janela restrita no shell, seus padrões são fundamentalmente diferentes. Esta seção aborda a diferença entre janelas de documentos, janelas de ferramentas e caixas de diálogo sem janela restrita. Padrões da caixa de diálogo modal são abordadas em [caixas de diálogo](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_Dialogs).  
  
### <a name="comparing-window-usage-patterns"></a>Comparando os padrões de uso de janela  
**Documento windows** quase sempre são exibidos dentro do documento bem. Isso permite que o editor de documentos um "estágio center" para organizar as janelas de ferramentas complementares ao redor.  
  
Um **janela da ferramenta** geralmente é exibido como uma janela separada, menor recolhida com a borda do IDE. Isso pode ser visível, oculto ou ocultas automaticamente. No entanto, às vezes, janelas de ferramentas são apresentadas no documento bem, desmarcando a **janela/encaixe** propriedade na janela. Isso resulta em mais espaço, mas também uma comum decisão de design: ao tentar integrar o Visual Studio, você deve decidir se o recurso deve exibir uma janela de ferramenta ou em uma janela de documento.  
  
**Caixas de diálogo sem janela restrita** são desaconselhável no Visual Studio. Caixas de diálogo sem janela restrita mais são, por definição, janelas de ferramentas flutuantes e devem ser implementadas dessa maneira. Caixas de diálogo sem janela restrita são permitidas em casos em que o tamanho de uma janela normal de ferramenta encaixada na lateral do shell seria seja muito limitado. Eles também são permitidos em casos em que o usuário seria provavelmente mover a caixa de diálogo para um monitor secundário.  
  
Pense cuidadosamente sobre que tipo de contêiner que você precisa. Considerações de padrão de uso comuns de design de interface do usuário estão na tabela a seguir.  
  
||Janela de documento|Janela de ferramenta|Caixa de diálogo sem janela restrita|  
|-|---------------------|-----------------|---------------------|  
| **Posição** | Sempre posicionado dentro do documento bem e não encaixar ao redor das bordas do IDE. Ele pode ser "bem-sucedido" para que ele flutua separadamente do shell principal. | Geralmente guia ancoradas ao redor das bordas do IDE, mas pode ser personalizado para ser flutuante, ocultas automaticamente (desafixada) ou encaixado dentro do documento bem.|Grande janela flutuante separada do IDE. |  
| **Confirmar o modelo** | *Confirmação atrasada*<br /><br /> Para salvar os dados em um documento, o usuário deve emitir a **arquivo &gt; salvar**, **Salvar como**, ou **Salvar tudo** comando. Uma janela de documento tem o conceito de dados nela sendo "sujas" confirmado para um Salvar comandos. Ao fechar uma janela de documento, todos os conteúdos são salvas em disco ou perdidos. | *Confirmação imediata*<br /><br /> Não há nenhum Salvar modelo. Inspetor janelas de ferramentas que ajudam a edição de um arquivo, o arquivo deve ser aberto no editor ativo ou no designer e o editor ou designer possui o salvamento. | *Confirmação atrasada ou imediata*<br /><br /> Geralmente, uma caixa de diálogo sem janela restrita grande requer uma ação para confirmar as alterações e permite uma operação "Cancelar", que reverte todas as alterações feitas na sessão de diálogo.  Isso faz a diferenciação uma caixa de diálogo sem janela restrita em uma janela de ferramenta no qual janelas de ferramentas sempre terá um modelo de confirmação imediata. |  
| **Visibilidade** | *Abrir/criar (arquivo) e fechar*<br /><br /> Abrir uma janela de documento é feito por meio da abertura de um documento existente ou usando um modelo para criar um novo documento. Não há nenhuma "abrir \<editor específico >" comando. | *Ocultar e mostrar*<br /><br /> Janelas de ferramentas de única instância podem ser ocultadas ou exibidas. Mantêm o conteúdo e os estados dentro da janela de ferramenta se no modo de exibição ou oculto. Janelas de ferramentas de várias instâncias podem ser fechadas e como ocultadas. Quando uma janela de ferramenta com várias instâncias é fechada, o conteúdo e o estado dentro da janela de ferramenta serão descartados. | *Iniciado a partir de um comando*<br /><br /> Caixas de diálogo são iniciadas a partir de um comando baseado em tarefas. |  
| **Instâncias** | *Várias instâncias*<br /><br /> Vários editores podem ser abertos no mesmo momento e edição de arquivos diferente, embora alguns editores também permitem que o mesmo arquivo para ser aberto em mais de um editor (usando o **janela &gt; nova janela** comando).<br /><br /> Um único editor pode estar editando um ou vários arquivos ao mesmo tempo (Designer de projeto). | *Único ou vários instance*<br /><br /> Conteúdo alterado para refletir o contexto (como o navegador de propriedade) ou enviar por push o foco/contexto para outras janelas (lista de tarefas, o Gerenciador de soluções).<br /><br /> Janelas de ferramentas de instância única e várias instâncias devem ser associadas à janela do documento ativo a menos que haja um motivo convincente não para. | *Instância única* |  
| **Exemplos** | **Editores de texto**, como o editor de códigos<br /><br /> **Superfícies de design**, como o designer de formulários ou uma superfície de modelagem<br /><br /> **Controlar layouts semelhantes a caixas de diálogo**, como o Designer de manifesto | O **Solution Explorer** fornece uma solução e projetos contidos dentro da solução<br /><br /> O **Server Explorer** fornece uma exibição hierárquica de servidores e conexões de dados que o usuário opta por abrir na janela. Abrindo um objeto da hierarquia de banco de dados, como uma consulta, abre uma janela de documento e permite que o usuário editar a consulta.<br /><br /> O **navegador de propriedade** exibe propriedades para o objeto selecionado em uma janela de documento ou outra janela de ferramenta. As propriedades são apresentadas em uma exibição hierárquica de grade ou em controles de caixa de diálogo semelhante complexos e permitir que o usuário definir os valores dessas propriedades. | |  
  
##  <a name="BKMK_ToolWindows"></a>Janelas de ferramentas  
  
### <a name="overview"></a>Visão Geral  
Janelas de ferramentas oferecem suporte a um trabalho do usuário que ocorre em janelas de documento. Eles podem ser usados para exibir uma hierarquia que representa um objeto raiz fundamental que o Visual Studio fornece e pode manipular.  
  
Ao considerar uma nova janela de ferramenta no IDE, os autores devem:  
  
-   Usar janelas de ferramenta existente apropriado de tarefa e não criar novos com funcionalidade semelhante. Novas janelas de ferramenta devem ser criadas apenas se eles oferecem um "ferramenta" significativamente diferente ou funcionalidade que não pode ser integrada em uma janela semelhante ou ao transformar uma janela existente em um hub de dinamização.  
  
-   Use uma barra de comando padrão, se necessário, na parte superior da janela de ferramentas.  
  
-   Ser consistente com padrões já está presentes nas outras janelas de ferramenta para controlar a navegação de teclado e apresentação.  
  
-   Ser consistente com a apresentação de controle em outras janelas de ferramenta.  
  
-   Verifique janelas de ferramenta específica do documento automaticamente visíveis quando possível, para que eles aparecem somente quando o documento pai é ativado.  
  
-   Certifique-se de que seu conteúdo da janela é passível de navegação pelo teclado (teclas de direção de suporte).  
  
#### <a name="tool-window-states"></a>Estados de janela de ferramenta  
Janelas de ferramentas do Visual Studio têm diferentes estados, alguns dos quais são ativados por usuário (como o recurso de ocultar automaticamente). Outros estados, como o auto visíveis, permitir janelas de ferramenta aparecer no contexto correto e ocultar quando não é necessário. Há cinco estados de janela de ferramenta no total.  
  
-   **Encaixado/fixado** janelas de ferramentas podem ser anexadas a qualquer um dos quatro lados da área do documento. O ícone de pino é exibido na barra de título da janela de ferramenta. A janela de ferramentas pode ser encaixada horizontal ou verticalmente ao longo da borda do shell e outras janelas de ferramenta e também pode ser vinculada por guia.  
  
-   **Auto-oculto** janelas de ferramentas estejam fixadas. A janela pode deslizar ficará oculta, deixando uma guia (com o nome da janela de ferramenta e seu ícone) na borda da área do documento. A janela da ferramenta desliza quando um usuário passar o mouse sobre a guia.  
  
-   **Autovisível** janelas de ferramentas será exibida automaticamente quando a outra parte da interface do usuário, como um editor, é iniciado ou ganha o foco.  
  
-   **Flutuante** janelas de ferramenta passe o mouse fora do IDE. Isso é útil para configurações de vários monitores.  
  
-   **Documentos com guias** janelas de ferramentas podem ser bem encaixadas dentro do documento. Isso é útil para janelas de ferramenta grandes, como o Pesquisador de objetos, que precisam de mais imóveis que permite até as bordas do quadro de encaixe.  
  
![Estados de janela de ferramenta no Visual Studio](~/extensibility/ux-guidelines/media/0702-01_toolwindowstates.png "0702-01_ToolWindowStates")<br />Estados de janela de ferramenta no Visual Studio
  
#### <a name="single-instance-and-multi-instance"></a>Instância única e várias instâncias  
Janelas de ferramentas são instância única ou várias instâncias. Algumas janelas de ferramenta de instância única podem ser associadas com a janela do documento ativo, enquanto as janelas de ferramentas de várias instâncias não podem. Janelas de ferramentas de várias instâncias respondem a **janela &gt; nova janela** comando criando uma nova instância da janela. A imagem a seguir ilustra uma janela de ferramenta, permitindo que o comando nova janela quando uma instância da janela está ativa:  
  
![Janela de ferramenta permitindo que o comando 'Nova janela' quando uma instância da janela está ativa](~/extensibility/ux-guidelines/media/0702-02_toolwindowenablingcommand.png "0702-02_ToolWindowEnablingCommand")<br />Janela de ferramenta permitindo que o comando 'Nova janela' quando uma instância da janela está ativa  
  
Janelas de ferramentas de única instância podem ser ocultadas ou exibidas, enquanto as janelas de ferramentas de várias instâncias podem ser fechadas, bem como ocultadas. Todas as janelas de ferramentas podem ser encaixadas, vinculada por guia, flutuante ou definida como uma janela filho de Interface de documentos múltiplos (MDI) (semelhante a uma janela de documento). Todas as janelas de ferramenta devem responder para os comandos de gerenciamento de janela apropriada no menu da janela:  
  
![Comandos de gerenciamento de janela no menu janela do Visual Studio](~/extensibility/ux-guidelines/media/0702-03_windowmanagementcontrols.png "0702-03_WindowManagementControls")<br />Comandos de gerenciamento de janela no menu janela do Visual Studio
  
#### <a name="document-specific-tool-windows"></a>Janelas de ferramentas de documento específico  
Algumas janelas de ferramenta são projetadas para mudar de acordo com um determinado tipo de documento. Essas janelas continuamente atualizados para refletir a funcionalidade aplicável para a janela do documento ativo no IDE.  
  
A caixa de ferramentas e a estrutura de tópicos do documento são exemplos de janelas de ferramenta cujo conteúdo é alterado para refletir o editor selecionado. Essas janelas mostram uma marca d'água quando um editor tem foco que não oferecem o contexto para a janela.  
  
#### <a name="navigable-list-tool-windows"></a>Janelas de ferramentas de lista navegável  
Algumas janelas de ferramenta exibem uma lista de itens navegáveis que o usuário pode interagir com. Esse tipo de janela, deve haver sempre comentários para o item atual na lista, mesmo se a janela está inativa. A lista deve responder para o **GoToNextLocation** e **GoToPrevLocation** comandos alterando também o item atualmente selecionado na janela  
  
O Gerenciador de soluções e a janela localizar resultados são exemplos de janelas de ferramentas de lista navegável.  
  
### <a name="tool-window-types"></a>Tipos de janelas de ferramenta  
  
#### <a name="common-tool-windows-and-their-functions"></a>Janelas de ferramentas comuns e suas funções

**Janelas de ferramentas hierárquica**
| Janela de ferramenta | Função | 
| --- | --- | 
| Gerenciador de Soluções | Uma árvore hierárquica que exibe uma lista de documentos contidos em projetos e arquivos diversos itens de solução. A exibição de itens dentro de projetos é definida pelo pacote que possui o tipo de projeto (por exemplo, tipos de base de referência, com base no diretório ou modo misto). | 
| Exibição de Classe | Uma árvore hierárquica das classes e vários elementos no conjunto de trabalho de documentos, independentes dos próprios arquivos. | 
| conexões de servidor | Uma árvore hierárquica que exibe todas as conexões de servidores e dados na solução. | 
| Estrutura de Tópicos do Documento | A estrutura hierárquica do documento ativo. | 

**Janelas de ferramentas de grade**
| Janela de ferramenta | Função | 
| --- | --- | 
| Propriedades | Uma grade que exibe uma lista de propriedades do objeto selecionado, junto com os seletores de valor para editar essas propriedades. | 
| Lista de Tarefas | Uma grade que permite ao usuário para criar/editar/excluir tarefas e comentários. | 

**Janelas de ferramentas de conteúdo**
| Janela de ferramenta | Função | 
| --- | --- | 
| Ajuda | Uma janela que permite aos usuários acesso a vários métodos de obter ajuda, de "Como fazer?" vídeos nos fóruns do MSDN. | 
| Ajuda Dinâmica | Uma janela de ferramenta que exibe links para tópicos aplicáveis à seleção atual da Ajuda. | 
| Pesquisador de Objetos | Um conjunto de quadros de duas colunas com uma lista de componentes de objeto hierárquica no painel esquerdo e o objeto propriedades e métodos na coluna à direita. | 

**Janelas de ferramentas da caixa de diálogo**
| Janela de ferramenta | Função | 
| --- | --- | 
| Localizar | Uma caixa de diálogo que permite ao usuário localizar ou localizar e substituir em arquivos diversos dentro da solução. |
| Localização avançada | Uma caixa de diálogo que permite ao usuário localizar ou localizar e substituir em arquivos diversos dentro da solução. | 

**Outras janelas de ferramenta**
| Janela de ferramenta | Função | 
| --- | --- | 
| Caixa de Ferramentas | A janela da ferramenta usada para armazenar elementos que serão removidos em superfícies de design, fornecendo uma fonte de arrastar consistente para todos os designers. |
| Start Page | Portal do usuário para o Visual Studio, com acesso a feeds de notícias do desenvolvedor, a Ajuda do Visual Studio e projetos recentes. Os usuários também podem criar páginas de início personalizados, copiando o arquivo StartPage.xaml o "Common7\IDE\StartPages\" diretório de arquivos de programa do Visual Studio para a pasta StartPages o diretório de documentos do Visual Studio e, em seguida, editando o XAML manualmente ou abri-lo no Visual Studio ou em outro editor de código. | 

**Janelas de ferramentas do depurador**
| Janela de ferramenta | Função | 
| --- | --- |
| Autos ||  
| Imediato ||  
| Saída | A janela de saída pode ser usada sempre que você tiver o status para declarar ou eventos textuais. |  
| Memória ||  
| Pontos de interrupção ||  
| Em execução ||  
| Documentos ||  
| Pilha de chamadas ||  
| Locais ||  
| Inspeções ||  
| Desmontagem ||  
| Registros ||  
| Threads ||  
  
##  <a name="BKMK_DocumentEditorConventions"></a>Convenções de editor do documento  
  
### <a name="document-interactions"></a>Interações de documento  
O "documento bem" é o maior espaço dentro do IDE e onde o usuário geralmente concentrou atenção para concluir suas tarefas, assistidas por janelas de ferramentas complementares. Editores de documento representam as unidades fundamentais de trabalho que o usuário é aberta e salva no Visual Studio. Eles mantêm um forte senso de seleção associado ao Gerenciador de soluções ou outras janelas de hierarquia ativo. O usuário deve ser capaz de apontar para uma dessas janelas de hierarquia e saber onde o documento está contido e sua relação para a solução, o projeto ou outro objeto raiz fornecido por um pacote do Visual Studio.  
  
Edição de documentos requer uma experiência de usuário consistente. Para permitir que o usuário a se concentrar na tarefa à mão, em vez de no gerenciamento de janela e Localizando comandos, selecione uma estratégia de exibição de documento que melhor atende as tarefas do usuário para esse tipo de documento de edição.  
  
#### <a name="common-interactions-for-the-document-well"></a>Interações comuns para o documento bem  
  
-   Manter um modelo de interação consistente em comum **novo arquivo** e **abrir arquivo** experiências.  
  
-   Atualize funcionalidades relacionadas em menus e janelas relacionadas quando a janela do documento é aberto.  
  
-   Comandos de menu estão integrados adequadamente menus comuns como **editar**, **formato**, e **exibição** menus. Se houver uma quantidade significativa de comandos especializadas, um novo menu pode ser criado. Esse novo menu deve ser visível apenas quando o documento tem o foco.  
  
-   Uma barra de ferramentas inserida pode ser colocada na parte superior do editor. Isso é preferível ter uma barra de ferramentas separada que aparece fora do editor.  
  
-   Sempre manter uma seleção no Gerenciador de soluções ou ativo semelhante janela hierarquia.  
  
-   Clicando duas vezes em um documento no Gerenciador de soluções deve executar a mesma ação que **abrir**.  
  
-   Se mais de um editor pode ser usado em um tipo de documento, o usuário deve ser capaz de substituir ou redefinir a ação padrão em um tipo de documento específico usando o **abrir com** caixa de diálogo clicando duas vezes no arquivo e selecionando **abrir com** no menu de atalho.  
  
-   Não crie também um assistente em um documento.  
  
### <a name="user-expectations-for-specific-document-types"></a>Expectativas dos usuários para os tipos de documento específico  
Há vários tipos diferentes de básicos de editores de documento e cada um tem um conjunto de interações que são consistentes com outros usuários do mesmo tipo.  
  
-   **Editor de texto:** editor de códigos, arquivos de log  
  
-   **Superfície de design:** WPF forms designer, do Windows forms  
  
-   **Editor de caixa de diálogo de estilo:** Designer de manifesto, propriedades do projeto  
  
-   **Designer de modelo:** designer de fluxo de trabalho, codemap, diagrama de arquitetura, progressão  
  
Também há vários tipos de editor não que usam o documento também. Embora eles não editam próprios documentos, eles precisam execute interações padrão para janelas de documento.  
  
-   **Relatórios:** relatório do IntelliTrace, Hyper-V de relatórios, relatórios do criador de perfil  
  
-   **Painel:** Hub de diagnóstico  
  
#### <a name="text-based-editors"></a>Editores de texto  
  
-   O documento participa no modelo de guia de visualização, permitindo a visualização do documento sem abri-lo.  
  
-   A estrutura do documento pode ser representada em uma janela de ferramenta complementar, como uma estrutura de tópicos do documento.  
  
-   IntelliSense (se apropriado) irão se comportar consistente com outros editores de códigos.  
  
-   Pop-ups ou interface de usuário assistencial siga estilos e padrões semelhantes para existente semelhante da interface do usuário, como CodeLens.  
  
-   Mensagens sobre o status do documento serão exibidas em um controle de barra de informações na parte superior do documento ou na barra de status.  
  
-   O usuário deve ser capaz de personalizar a aparência de fontes e cores usando um **Ferramentas > Opções** página, a página de fontes e cores compartilhada ou um específico para o editor.  
  
#### <a name="design-surfaces"></a>Superfícies de design  
  
-   Um designer vazio deve ter uma marca d'água na superfície de indicando como começar.  
  
-   Mecanismos de alternância de exibição seguirão os padrões existentes, como clicar duas vezes para abrir um editor de códigos ou guias na janela do documento, que permite a interação com os dois painéis.  
  
-   A adição de elementos na superfície de design deve ser feita por meio da caixa de ferramentas, a menos que uma janela de ferramenta altamente específica é necessária.  
  
-   Itens na superfície de seguirá um modelo consistente de seleção.  
  
-   Barras de ferramentas inseridas contêm comandos apenas, não comum de comandos específicos do documento como **salvar**.  
  
#### <a name="dialog-style-editors"></a>Editores de estilo de caixa de diálogo  
  
-   Layout de controle deverá seguir as convenções de layout da caixa de diálogo normal.  
  
-   Guias dentro do editor não devem corresponder a aparência das guias do documento, eles devem corresponder a um dos dois estilos de guia interior permitidos.  
  
-   Os usuários devem ser capazes de interagir com os controles usando o teclado. qualquer um, ativando o editor e por meio de controles ou de tabulação usando mnemônicos padrão.  
  
-   O designer deve usar comuns Salvar modelo. Sem salvar geral ou confirmação botões devem ser colocados na superfície, embora outros botões podem ser apropriados.  
  
#### <a name="model-designers"></a>Designers de modelo  
  
-   Um designer vazio deve ter uma marca d'água na superfície de indicando como começar.  
  
-   A adição de elementos na superfície de design deve ser feita por meio da caixa de ferramentas.  
  
-   Itens na superfície de seguirá um modelo consistente de seleção.  
  
-   Barras de ferramentas inseridas contêm comandos apenas, não comum de comandos específicos do documento como **salvar**.  
  
-   Uma legenda pode aparecer na superfície, indicativo ou uma marca d'água.  
  
-   O usuário deve ser capaz de personalizar a aparência das fontes/cores usando um **Ferramentas > Opções** página, a página de fontes e cores compartilhada ou um específico para o editor.  
  
#### <a name="reports"></a>Relatórios  
  
-   Relatórios são normalmente somente informações e não participarem no modelo de salvar. No entanto, eles podem incluir interação como links para outras informações relevantes ou seções expandir e recolher.  
  
-   A maioria dos comandos na superfície de deve ser hiperlinks, e não os botões.  
  
-   Layout deve incluir um cabeçalho e siga as diretrizes de layout de relatório padrão.  
  
#### <a name="dashboards"></a>Painéis  
  
-   Painéis de controle não tem um modelo de interação si, mas servem como um meio de oferecer uma variedade de outras ferramentas.  
  
-   Eles não participam no modelo de salvar.  
  
-   Usuários devem ser capazes de interagir com os controles usando o teclado, ativando o editor e percorrer controles ou mnemônico padrão.  
  
##  <a name="BKMK_Dialogs"></a>Caixas de diálogo  
  
### <a name="introduction"></a>Introdução  
Caixas de diálogo no Visual Studio normalmente devem dar suporte a uma unidade discreta de trabalho do usuário e, em seguida, ser descartadas.  
  
Se você tiver determinado que você precisa de uma caixa de diálogo, você tem três opções, na ordem de preferência:  
  
1.  Integre os recursos em uma das caixas de diálogo compartilhadas no Visual Studio.  
  
2.  Crie sua própria caixa de diálogo usando um padrão encontrado em uma caixa de diálogo semelhante existente.  
  
3.  Crie uma nova caixa de diálogo, seguinte interação e diretrizes de layout.  
  
Esta seção descreve como escolher o padrão de diálogo corretas nos fluxos de trabalho do Visual Studio e as convenções comuns para o design da caixa de diálogo.  
  
### <a name="themes"></a>Temas  
Caixas de diálogo no Visual Studio execute um dos dois estilos básicos:  
  
#### <a name="standard-unthemed"></a>Padrão (unthemed)  
A maioria das caixas de diálogo são caixas de diálogo do utilitário padrão e deve ser unthemed. Não não controles comuns do novo modelo ou tentativa de criar botões "modernos" estilizado ou controles. Controles e a aparência de cromo siga [as diretrizes de interação de área de trabalho do Windows padrão para caixas de diálogo](https://msdn.microsoft.com/en-us/library/windows/desktop/dn742499\(v=vs.85\).aspx).  
  
#### <a name="themed"></a>Com tema  
Caixas de diálogo especialidade "assinatura" podem ser com tema. Caixas de diálogo com tema tem uma aparência distinta, que também tem alguns padrões de interação especial associadas ao estilo. Tema a caixa de diálogo somente se ele atende aos seguintes requisitos:  
  
-   A caixa de diálogo é uma experiência comum que serão Vista e usada com frequência ou por muitos usuários (por exemplo, o **novo projeto** caixa de diálogo.  
  
-   A caixa de diálogo contém elementos de marca de produto destacados (por exemplo, o **configurações de conta** caixa de diálogo).  
  
-   A caixa de diálogo é exibida como parte integrante de um fluxo maior que inclui outras caixas de diálogo com tema (por exemplo, o **Adicionar serviço conectado** caixa de diálogo).  
  
-   A caixa de diálogo é uma parte importante de uma experiência que desempenha um papel estratégico em promover ou diferenciando uma versão do produto.  
  
Ao criar uma caixa de diálogo com tema, use as cores do ambiente apropriado e siga o layout correto e os padrões de interação. (Consulte [Layout para o Visual Studio](../../extensibility/ux-guidelines/layout-for-visual-studio.md).)  
  
### <a name="dialog-design"></a>Design de caixa de diálogo  
Caixas de diálogo bem projetadas consideram os seguintes elementos:  
  
-   A tarefa de usuário que está sendo com suporte  
  
-   O estilo de texto da caixa de diálogo, o idioma e terminologia  
  
-   Opção de controle e convenções de interface do usuário  
  
-   Alinhamento de especificação e controle de layout Visual  
  
-   Acesso pelo teclado  
  
#### <a name="content-organization"></a>Organização do conteúdo  
Considere as diferenças entre esses tipos básicos de caixas de diálogo:  
  
-   [Caixas de diálogo simples](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_SimpleDialogs) apresentar controles em uma única janela modal. A apresentação pode incluir variações de padrões de controle complexo, incluindo um seletor de campo ou uma barra de ferramentas.  
  
-   [Em camadas de caixas de diálogo](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_LayeredDialogs) são usados para fazer a maior parte do espaço na tela quando uma única parte da interface do usuário consiste em vários grupos de controles. Agrupamentos da caixa de diálogo são "em camadas" por meio de controles de guia, controles de lista de navegação ou botões para que o usuário pode escolher qual o agrupamento para ver a qualquer momento.  
  
-   [Assistentes](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_Wizards) são úteis para direcionar o usuário por meio de uma sequência lógica de etapas para a conclusão de uma tarefa. Uma série de opções é oferecida em painéis sequenciais, às vezes, introduzindo diferentes fluxos de trabalho ("branches") dependentes de uma escolha feita no painel anterior.  
  
####  <a name="BKMK_SimpleDialogs"></a>Caixas de diálogo simples  
Uma caixa de diálogo é uma apresentação de controles em uma única janela modal. Esta apresentação pode incluir variações dos padrões de controle complexo, como um seletor de campo. Para caixas de diálogo simples, siga o layout geral padrão, bem como qualquer layout específicas necessárias para agrupamentos de controle complexo.
  
![> criar chave de nome forte é um exemplo de uma caixa de diálogo simple no Visual Studio.](~/extensibility/ux-guidelines/media/0704-01_createstrongnamekey.png "0704-01_CreateStrongNameKey")<br />Criar chave de nome forte é um exemplo de uma caixa de diálogo simple no Visual Studio.
  
####  <a name="BKMK_LayeredDialogs"></a>Caixas de diálogo em camadas  
Caixas de diálogo em camadas incluem guias, painéis e árvores incorporados. Eles são usados para maximizar imóveis quando há vários grupos de controles oferecidos em uma única parte da interface do usuário. Os agrupamentos são colocadas em camadas para que o usuário pode escolher qual o agrupamento para ver a qualquer momento.  
  
No caso mais simples, o mecanismo para alternar entre agrupamentos é um controle guia. Há várias alternativas disponíveis. Consulte priorizar e camadas de como escolher o estilo mais apropriado.  
  
O **ferramentas &gt; opções** caixa de diálogo é um exemplo de uma caixa de diálogo em camadas, usando uma árvore inserida:  
  
![Ferramentas > Opções é um exemplo de uma caixa de diálogo em camadas no Visual Studio.](~/extensibility/ux-guidelines/media/0704-02_toolsoptions.png "0704-02_ToolsOptions")<br />Ferramentas > Opções é um exemplo de uma caixa de diálogo em camadas no Visual Studio.
  
####  <a name="BKMK_Wizards"></a>Assistentes  
Assistentes são úteis para direcionar o usuário por meio de uma sequência lógica de etapas na conclusão de uma tarefa. Uma série de opções oferecidas nos painéis sequenciais, e o usuário deve continuar em cada etapa antes de prosseguir para a próxima. Depois que os padrões suficientes estiverem disponíveis, o **concluir** botão é habilitado.  
  
 Modais assistentes são usados para tarefas que:  
  
-   Contém a ramificação, onde os diferentes caminhos são oferecidos dependendo das opções de usuário  
  
-   Contém dependências entre as etapas, onde as etapas subsequentes dependem de entrada do usuário das etapas anteriores  
  
-   Suficientemente complexas que a interface do usuário deve ser usado para explicar as opções oferecidas e os possíveis resultados de cada etapa  
  
-   São transacionais, que requerem um conjunto de etapas para ser concluída em sua totalidade antes que as alterações sejam confirmadas  
  
### <a name="common-conventions"></a>Convenções comuns  
Para obter o melhor design e funcionalidade com as caixas de diálogo, siga estas convenções no tamanho da caixa de diálogo, posição, padrões, configuração de controle e alinhamento, interface do usuário texto, barras de título, os botões de controle e chaves de acesso.  
  
Para obter diretrizes específicas do layout, consulte [Layout para o Visual Studio](../../extensibility/ux-guidelines/layout-for-visual-studio.md).  
  
#### <a name="size"></a>Tamanho  
Caixas de diálogo devem se ajustar dentro de uma resolução de tela de 1024 x 768 mínimo e tamanho da caixa de diálogo inicial não deve exceder 900 x 700 pixels. Caixas de diálogo podem ser redimensionadas, mas não é um requisito.  
  
Há dois recomendações para caixas de diálogo redimensionáveis:  
  
1.  Se um tamanho mínimo é definido para a caixa de diálogo otimizar para o controle definido sem recorte e ajustar para acomodar o crescimento de localização razoável.  
  
2.  Se o tamanho da escala de usuário persiste a cada sessão. Por exemplo, se o usuário pode ser dimensionado para 150% em uma caixa de diálogo, uma inicialização subsequente da caixa de diálogo exibirá 150%.  
  
#### <a name="position"></a>Posição  
Caixas de diálogo devem aparecer centralizadas dentro do IDE na primeira inicialização. A última posição de caixas de diálogo não redimensionável não precisa ser persistentes, para que eles serão exibidos em inicializações subsequentes. 

Para caixas de diálogo redimensionáveis, o tamanho deve ser persistido em inicializações subsequentes. Para caixas de diálogo modais redimensionáveis, a posição não precisa ser persistente. Exibi-los centralizado dentro do IDE impede a possibilidade da caixa de diálogo que aparece em uma posição imprevisível ou inutilizável quando a configuração de exibição do usuário foi alterada. 

Para caixas de diálogo sem janela restrita que podem ser reposicionadas, a posição do usuário deve ser mantida em inicializações subsequentes, como a caixa de diálogo pode ser usada com frequência como parte integrante de um fluxo de trabalho maior.  
  
Quando as caixas de diálogo devem gerar outras caixas de diálogo, a caixa de diálogo mais alta deve propagar à direita e inferior do pai de forma que ele claro para o usuário você navegar até um novo local.  
  
#### <a name="modality"></a>Modalidade  
Sendo modal significa que os usuários são necessários para concluir ou cancelar a caixa de diálogo antes de continuar. Como caixas de diálogo modais impedem o usuário de interagir com outras partes do ambiente, o fluxo de tarefas do recurso deve usá-los moderadamente possível. Quando uma operação restrita for necessária, o Visual Studio tem um número de caixas de diálogo compartilhadas, em que você pode integrar seus recursos. Se você deve criar uma nova caixa de diálogo, seguem o padrão de interação de uma caixa de diálogo existente com funcionalidade semelhante.  
  
Quando os usuários precisam executar duas atividades ao mesmo tempo, como **localizar** e **substituir** ao escrever novo código, a caixa de diálogo deve ser restrita para que o usuário pode alternar facilmente entre eles. Geralmente, o Visual Studio usa janelas de ferramentas para esse tipo de suporte de editor de tarefa vinculada.  
  
#### <a name="control-configuration"></a>Configuração de controle  
Ser consistente com as configurações de controle existentes que realizam a mesma coisa no Visual Studio.  
  
#### <a name="title-bars"></a>Barras de título  
  
-   O texto na barra de título deve refletir o nome do comando que o iniciou.  
  
-   Nenhum ícone deve ser usado em barras de título da caixa de diálogo. Em casos em que o sistema exige um, use o logotipo do Visual Studio.  
  
-   Caixas de diálogo não devem ter minimizar ou maximizar botões.  
  
-   Botões de ajuda na barra de título foram preteridos. Não adicione-os para novas caixas de diálogo. Quando existirem, eles devem iniciar um tópico de Ajuda que é conceitualmente relevantes para a tarefa.  
  
 ![Especificações de diretriz das barras de título nas caixas de diálogo do Visual Studio](~/extensibility/ux-guidelines/media/0704-03_titlebarspecs.png "0704-03_TitleBarSpecs")<br />Especificações de diretriz das barras de título nas caixas de diálogo do Visual Studio
  
#### <a name="control-buttons"></a>Botões de controle  
Em geral, **Okey**, **Cancelar**, e **ajuda** botões devem ser organizados horizontalmente no canto inferior direito da caixa de diálogo. A pilha vertical alternativa é permitida se uma caixa de diálogo tem vários outros botões na parte inferior da caixa de diálogo que fornece confusão visual com os botões de controle.  
  
![Configurações aceitáveis para os botões de controle nas caixas de diálogo do Visual Studio](~/extensibility/ux-guidelines/media/0704-04_controlbuttonconfig.png "0704-04_ControlButtonConfig")<br />Configurações aceitáveis para os botões de controle nas caixas de diálogo do Visual Studio
  
A caixa de diálogo deve incluir um botão de controle padrão. Para determinar o comando recomendado para usar como padrão, escolha uma das opções a seguir (listadas em ordem de precedência):  
  
-   Escolha o comando mais seguro e mais seguro como padrão. Isso significa que o comando mais provável evitar perda de dados e evitar o acesso ao sistema não intencionais.  
  
-   Se a segurança e a perda de dados não são fatores, em seguida, escolha o comando de padrão com base em sua conveniência. Incluindo o comando provavelmente como padrão melhorará o fluxo de trabalho do usuário quando a caixa de diálogo oferece suporte a tarefas repetitivas ou frequentes.  
  
Evite escolher uma ação destrutiva permanentemente para o comando padrão. Se esse comando estiver presente, escolha um comando mais seguro como padrão.  
  
#### <a name="access-keys"></a>Chaves de acesso  
Não use as teclas de acesso para **Okey**, **Cancelar**, ou **ajuda** botões. Por padrão, esses botões são mapeados a teclas de atalho:  
  
| Nome do botão | Atalho de teclado |  
| --- | --- |  
| OK | Enter |  
| Cancelar | Esc |  
| Ajuda | F1 |  
  
#### <a name="imagery"></a>Imagens  
Use imagens moderadamente em caixas de diálogo. Não use ícones grandes em caixas de diálogo para usar o espaço. Use imagens somente se eles são uma parte importante de transmitir a mensagem para o usuário, como ícones de aviso ou animações de status.  
  
###  <a name="BKMK_PrioritizingAndLayering"></a>Priorize e divisão em camadas  
  
#### <a name="prioritizing-your-ui"></a>Priorizando a interface do usuário  
Talvez seja necessário trazer certos elementos de interface do usuário para o forefront e coloque comportamento mais avançado e as opções (incluindo comandos obscuros) em caixas de diálogo. Coloque funcionalidades mais comumente usadas para o forefront fazer espaço para ele e torná-lo visível por padrão na interface de usuário com um rótulo de texto quando a caixa de diálogo é exibida.  
  
#### <a name="layering-your-ui"></a>Dispondo em camadas sua interface do usuário  
Se você tiver determinado que uma caixa de diálogo é necessária, mas a funcionalidade relacionada que você quiser apresentar ao usuário ultrapassa o que pode ser exibido em uma caixa de diálogo, você precisa de camada sua interface do usuário. Os métodos mais comuns de camadas que usa o Visual Studio são guias e corredores ou painéis. Em alguns casos, as regiões que podem expandir e recolher podem ser apropriados. Interface do usuário adaptável geralmente não é recomendável no Visual Studio.  
  
Há vantagens e desvantagens de métodos diferentes de dispondo em camadas da interface do usuário por meio de controles de guia. Examine a lista a seguir para garantir que você está escolhendo uma técnica de camadas que é apropriada para sua situação.  
  
##### <a name="tabbing"></a>Tabulação  
  
| Mecanismo de troca | Vantagens e uso apropriado | Uso inadequado e desvantagens |  
| --- | --- | --- |  
| Controle de guia | Agrupar logicamente páginas de diálogo em conjuntos relacionados<br /><br />Útil para menos de cinco (ou o número de guias que cabem em uma linha na caixa de diálogo) páginas de controles relacionados na caixa de diálogo<br /><br />Rótulos de guia devem ser curtos: uma ou duas palavras que podem identificar facilmente o conteúdo<br /><br />Um estilo de caixa de diálogo comuns do sistema<br /><br />Exemplo: **Explorador de arquivos &gt; propriedades de itens** | Pode ser difícil fazer descritivos rótulos curtos<br /><br />Em geral não dimensionado para mais de cinco guias em uma caixa de diálogo<br /><br />Inadequado se você tiver muitos guias para uma linha (use uma técnica alternativa camadas)<br /><br />Não é extensível |  
| Navegação de barra lateral | Dispositivo de alternância Simple que pode acomodar mais categorias de guias<br /><br />Lista simples de categorias (nenhuma hierarquia)<br /><br />Extensível<br /><br />Exemplo: **personalizar... &gt; Adicionar comando** | Não um bom uso de espaço horizontal se houver menos de três grupos<br /><br />Tarefa pode ser melhor adequada para uma lista suspensa |  
| Controle de árvore | Permite categorias ilimitadas<br /><br />Permite o agrupamento e/ou a hierarquia de categorias<br /><br />Extensível<br /><br />Exemplo: **ferramentas &gt; opções** | Hierarquias aninhadas muito podem causar a rolagem horizontal excessiva<br /><br />O Visual Studio tem um overabundance dos modos de exibição de árvore |  
| Wizard | Ajuda na conclusão de tarefas por guiar o usuário pelas etapas sequenciais, com base em tarefa: o assistente representa uma tarefa de alto nível e os painéis individuais representam subtarefas necessárias para realizar a tarefa geral<br /><br />Útil quando a tarefa cruza os limites de interface do usuário, como quando o usuário caso contrário, teria que usar vários editores e janelas para concluir a tarefa de ferramentas<br /><br />Útil quando a tarefa requer ramificação<br /><br />Útil quando a tarefa contém dependências entre as etapas<br /><br />Útil quando várias tarefas semelhantes com bifurcação de uma decisão podem ser apresentadas em uma caixa de diálogo para reduzir o número de caixas de diálogo semelhantes diferentes | Apropriado para qualquer tarefa que não requer um fluxo de trabalho sequencial<br /><br />Os usuários podem se tornar sobrecarregado e confundido por um assistente com muitas etapas<br /><br />Assistentes inerentemente limitaram espaço na tela |  
  
##### <a name="hallways-or-dashboards"></a>Corredores ou painéis  
Corredores e painéis são caixas de diálogo ou painéis que servem como iniciar o aponta para outras caixas de diálogo e janelas. "Entrada" bem projetada imediatamente revela somente as mais comuns opções, comandos e configurações, permitindo que o usuário realizar rapidamente tarefas comuns. Como um corredor reais fornece entradas de acesso para acessar as salas por trás deles, aqui a interface do usuário menos comuns é coletado em separado "salas" (geralmente outras caixas de diálogo) de funcionalidades relacionadas que podem ser acessados de entrada principal.  
  
Como alternativa, uma interface de usuário que oferece todos os recursos disponíveis em uma única coleção em vez da funcionalidade de menos comuns em locais separados de refatoração é simplesmente um painel.  
  
![Conceito de corredor para expor a interface de usuário adicional no Outlook](~/extensibility/ux-guidelines/media/0704-08_hallway.png "0704-08_Hallway")<br />Conceito de corredor para expor a interface de usuário adicional no Outlook
  
##### <a name="adaptive-ui"></a>Interface do usuário adaptável  
Mostrar ou ocultar a interface do usuário com base no uso ou a experiência do usuário automaticamente relatado é outra maneira de apresentar necessária da interface do usuário enquanto oculta a outras partes. Isso não é recomendado no Visual Studio, como os algoritmos para decidir quando mostrar ou ocultar a interface do usuário podem ser complicados e as regras sempre serão incorreta do mesmo conjunto de casos.  
  
##  <a name="BKMK_Projects"></a>Projetos  
  
### <a name="projects-in-the-solution-explorer"></a>Projetos no Gerenciador de soluções  
A maioria dos projetos são classificadas como base de referência, com base no diretório ou misto. Todos os três tipos de projetos têm suporte simultaneamente no Gerenciador de soluções. A raiz da experiência do usuário ao trabalhar com projetos ocorre dentro desta janela. Embora nós diferentes de projeto são projetos de tipo de modo misto, diretório ou referência, há um padrão de interação comum que deve ser aplicado como um ponto de partida antes divergentes em padrões do usuário específica do projeto.  
  
Projetos devem sempre:  
  
-   Suporte a capacidade de adicionar pastas de projeto para organizar o conteúdo do projeto  
  
-   Manter um modelo consistente para a persistência de projeto  
  
Projetos também devem manter os modelos de interação consistente para:  
  
-   Removendo itens de projeto  
  
-   Salvando documentos  
  
-   Edição de propriedade do projeto  
  
-   Editar o projeto em um modo de exibição alternativo  
  
-   Operações de arrastar e soltar  
  
### <a name="drag-and-drop-interaction-model"></a>Modelo de interação de arrastar e soltar  
Projetos normalmente classificam si como referência com base em (capaz de manter apenas referências a itens de projeto no armazenamento), (persistir somente itens de projeto fisicamente armazenados na hierarquia do projeto), com base no diretório ou misto (capaz de manter referências ou itens físicos). O IDE acomode todos os três tipos de projetos simultaneamente dentro de **Gerenciador de soluções**.  
  
De uma perspectiva de arrastar e soltar, as seguintes características devem ser aplicados a cada tipo de projeto dentro de **Solution Explorer**:  
  
-   **Projeto de referência:** o ponto principal é que o projeto está arrastando em torno de uma referência a um item no armazenamento. Quando um projeto de referência com base em atua como uma fonte para uma operação de movimentação, ele só deve remover a referência ao item do projeto. O item, na verdade, não deve ser excluído do disco rígido. Quando um projeto de referência com base em atua como um destino para uma operação de mover (ou cópia), ele deve adicionar uma referência para o item de origem original sem fazer uma cópia particular do item.  
  
-   **Com base no diretório de projeto:** de um ponto de vista de arrastar e soltar, o projeto está arrastando ao redor do item físico em vez de uma referência. Quando um projeto baseado no diretório atua como uma fonte para uma operação de movimentação, ele deve terminar excluindo o item físico do disco rígido, bem como removê-lo do projeto. Quando um projeto baseado no diretório atua como um destino para uma operação de mover (ou cópia), ele deve fazer uma cópia do item de origem em seu local de destino.  
  
-   **Projeto de destino misto:** de um ponto de vista de arrastar e soltar, o comportamento desse tipo de projeto é com base na natureza do item que está sendo arrastado (uma referência a um item no armazenamento) ou o próprio item. O comportamento correto para referências e itens físicos são descritos acima.  
  
Se houver apenas um tipo de projeto no **Solution Explorer**, operações de arrastar e soltar será simples. Como cada sistema de projeto tem a capacidade de definir seu próprio comportamento de arrastar e soltar, determinadas diretrizes (com base no comportamento de arrastar e soltar do Windows Explorer) devem ser seguidas para garantir uma experiência de usuário mais previsível:  
  
-   Arraste um inalterado operação **Solution Explorer** (quando não Ctrl nem teclas Shift mantidos) devem resultar em uma operação de movimentação.  
  
-   A operação de arrastar SHIFT deve resultar em uma operação de movimentação.  
  
-   A operação de arrastar CTRL deve resultar em uma operação de cópia.  
  
-   Sistemas de projeto misto e de referência com base em oferece suporte à noção de adicionar um link (ou uma referência) para o item de origem. Quando esses projetos são o destino de uma operação de arrastar e soltar (quando **Ctrl + Shift** é mantido pressionado), ele deve resultar em uma referência para o item que está sendo adicionado ao projeto  
  
Nem todas as operações de arrastar e soltar são sensatas em combinações de projetos baseados em referências, com base no diretório e mistos. Em particular, é problemático para fingir permitir que uma operação de movimentação entre um projeto com base no diretório de origem e o projeto de destino de referência com base em como o projeto com base no diretório de origem será preciso excluir o item de origem após a conclusão da mudança. O projeto de referência com base em destino deve terminar com uma referência a um item excluído.  
  
Também é enganosa fingem permitir que uma operação de cópia entre esses tipos de projetos, porque o projeto de referência com base em destino não deve fazer uma cópia independente do item de origem. Da mesma forma, Ctrl + Shift arrastando a um projeto com base no diretório de destino não permitir porque não é possível manter referências de um projeto com base no diretório. Em casos onde não há suporte para a operação de arrastar e soltar, o IDE deve impedir o descarte e mostrar ao usuário o cursor não soltar (mostrado na tabela ponteiro abaixo).  
  
Para implementar corretamente o comportamento de arrastar e soltar, o projeto de origem de drag deve se comunicar sua natureza do projeto de destino. (Por exemplo, é baseada em referência ou directory?) Esta informação é indicada pelo formato de área de transferência que é oferecido pela origem. Como a origem de arrastar (ou operação de cópia da área de transferência), um projeto deve oferecer um `CF_VSREFPROJECTITEMS` ou `CF_VSSTGPROJECTITEMS` respectivamente, dependendo se o projeto é baseada no diretório ou referência. Esses formatos têm o mesmo conteúdo de dados, que é semelhante do Windows `CF_HDROP` Formatar exceto que a lista de cadeias de caracteres, em vez de ser nomes de arquivos é um duplo -`NULL` encerrada lista de `Projref` cadeias de caracteres (como retornado pelo `IVsSolution::GetProjrefOfItem` ou `::GetProjrefOfProject` conforme apropriado).  
  
Como o destino de soltar (ou operação de colagem da área de transferência), um projeto deve aceitar os dois `CF_VSREFPROJECTITEMS` e `CF_VSSTGPROJECTITEMS`, embora o tratamento exato da operação de arrastar e soltar varia dependendo da natureza do projeto de destino e o projeto de origem. O projeto de origem declara sua natureza, se ele oferece `CF_VSREFPROJECTITEMS` ou `CF_VSSTGPROJECTITEMS`. O destino de soltar compreende sua própria natureza e, portanto, tem informações suficientes para tomar decisões e se a mover, copiar, ou link deve ser executado. O usuário também modifica a operação de arrastar e soltar que deve ser executada, pressionando a tecla Ctrl, Shift, ou as teclas Ctrl e Shift. É importante para o destino de soltar indicar corretamente a operação que será executada com antecedência no seu `DragEnter` e `DragOver` métodos. O **Solution Explorer** sabe automaticamente se o projeto de origem e o projeto de destino são o mesmo projeto.  
  
Especificamente, não há suporte para a arrastando os itens de projeto entre instâncias do Visual Studio (por exemplo, de uma instância do devenv.exe para outro). O **Solution Explorer** desabilita isso também diretamente.  
  
O usuário sempre deve ser capaz de determinar o efeito de uma operação de arrastar e soltar selecionando um item, arrastando-a para o local de destino, e observando qual dos seguintes ponteiros do mouse aparece antes do item é removido:  
  
| Ponteiro do mouse | Comando | Descrição |  
| :---: | --- | --- |  
| ![Mouse "sem soltar" ícone](~/extensibility/ux-guidelines/media/0706-01_mousenodrop.png "0706 01_MouseNoDrop") | Nenhum drop | Item não pode ser solto no local especificado. |  
| ![Ícone de "cópia" mouse](~/extensibility/ux-guidelines/media/0706-02_mousecopy.png "0706 02_MouseCopy") | Copiar | Item será copiado para o local de destino. |  
| ![Ícone de mouse "move"](~/extensibility/ux-guidelines/media/0706-03_mousemove.png "0706 03_MouseMove") | Mover | Item será movido para o local de destino. |  
| ![Ícone de "Adicionar referência" mouse](~/extensibility/ux-guidelines/media/0706-04_mouseaddref.png "0706 04_MouseAddRef") | Adicionar referência | Uma referência para o item selecionado será adicionada ao local de destino. |

#### <a name="reference-based-projects"></a>Referência com base em projetos  
 A tabela a seguir resume as operações de arrastar e soltar (bem como Recortar/copiar/colar) que devem ser executadas com base na natureza das chaves de item e o modificador de origem pressionado para projetos de destino com base em referenciada:  
  
| Modificador | Categoria | Item de origem: / Link de referência | Item de origem: sistema físico do item ou arquivo (`CF_HDROP`) |  
| --- | --- | --- | --- |  
| Nenhum modificador | Ação | Mover | Link |  
| Nenhum modificador | Destino | Adiciona a referência ao item original | Adiciona a referência ao item original |  
| Nenhum modificador | Origem | Referência de exclusões para o item original | Retém o item original |  
| Nenhum modificador | Resultado | `DROPEFFECT_MOVE`é retornado como a ação de `::Drop` e item permanece no local original no armazenamento | `DROPEFFECT_LINK`é retornado como a ação de `::Drop` e item permanece no local original no armazenamento |  
| SHIFT + arrastar | Ação | Mover | Nenhum drop |  
| SHIFT + arrastar | Destino | Adiciona a referência ao item original | Nenhum drop |  
| SHIFT + arrastar | Origem | Referência de exclusões para o item original | Nenhum drop |  
| SHIFT + arrastar | Resultado | `DROPEFFECT_MOVE`é retornado como a ação de `::Drop` e item permanece no local original no armazenamento | Nenhum drop |  
| CTRL + arrastar | Ação | Copiar | Nenhum drop |  
| CTRL + arrastar | Destino | Adiciona a referência ao item original | Nenhum drop |  
| CTRL + arrastar | Origem | Mantém a referência ao item original | Nenhum drop |  
| CTRL + arrastar | Resultado | `DROPEFFECT_COPY`é retornado como a ação de `::Drop` e item permanece no local original no armazenamento | Nenhum drop |  
| Ctrl + Shift + arrastar | Ação | Link | Link |  
| Ctrl + Shift + arrastar | Destino | Adiciona a referência ao item original | Adiciona a referência ao item original |  
| Ctrl + Shift + arrastar | Origem | Mantém a referência ao item original | Retém o item original |  
| Ctrl + Shift + arrastar | Resultado | `DROPEFFECT_LINK`é retornado como a ação de `::Drop` e item permanece no local original no armazenamento | `DROPEFFECT_LINK`é retornado como a ação de `::Drop` e item permanece no local original no armazenamento |  
| Ctrl + Shift + arrastar | Observação | Mesmo que o comportamento de arrastar e soltar para atalhos no Windows Explorer. ||  
| Recortar/colar | Ação | Mover | Link |  
| Recortar/colar | Destino | Adiciona a referência ao item original | Adiciona a referência ao item original |  
| Recortar/colar | Origem | Mantém a referência ao item original|Retém o item original |  
| Recortar/colar | Resultado | Item permanece no local original no armazenamento | Item permanece no local original no armazenamento |  
| Copiar/colar | Ação | Copiar | Link |  
| Copiar/colar | Origem | Adiciona a referência ao item original | Adiciona a referência ao item original |  
| Copiar/colar | Resultado | Mantém a referência ao item original | Retém o item original |  
| Copiar/colar | Ação | Item permanece no local original no armazenamento | Item permanece no local original no armazenamento |  
  
#### <a name="directory-based-projects"></a>Projetos baseados em diretório  
A tabela a seguir resume as operações de arrastar e soltar (bem como Recortar/copiar/colar) que devem ser executadas com base na natureza das chaves de item e o modificador de origem pressionado para projetos de destino com base no diretório:  
  
| Modificador | Categoria | Item de origem: / Link de referência | Item de origem: sistema físico do item ou arquivo (`CF_HDROP`) |  
| --- | --- | --- | --- |  
| Nenhum modificador | Ação | Mover | Mover |  
| Nenhum modificador | Destino | Item de cópias para local de destino | Item de cópias para local de destino |  
| Nenhum modificador | Origem | Referência de exclusões para o item original | Referência de exclusões para o item original | | Nenhum modificador | Resultado | `DROPEFFECT_MOVE`é retornado como a ação de `::Drop` e item permanece no local original no armazenamento | `DROPEFFECT_MOVE`é retornado como a ação de `::Drop` e item permanece no local original no armazenamento |  
| SHIFT + arrastar | Ação | Mover | Mover |  
| SHIFT + arrastar | Destino | Item de cópias para local de destino | Item de cópias para local de destino |  
| SHIFT + arrastar | Origem | Referência de exclusões para o item original | Exclui o item do local original |
| SHIFT + arrastar | Resultado | `DROPEFFECT_MOVE`é retornado como a ação de `::Drop` e item permanece no local original no armazenamento | `DROPEFFECT_MOVE`é retornado como a ação de `::Drop` e item permanece no local original no armazenamento |  
| CTRL + arrastar | Ação | Copiar | Copiar |  
| CTRL + arrastar | Destino | Item de cópias para local de destino | Item de cópias para local de destino |  
| CTRL + arrastar | Origem | Mantém a referência ao item original | Mantém a referência ao item original |  
| CTRL + arrastar | Resultado | `DROPEFFECT_COPY`é retornado como a ação de `::Drop` e item permanece no local original no armazenamento | `DROPEFFECT_COPY`é retornado como a ação de `::Drop` e item permanece no local original no armazenamento |  
| Ctrl + Shift + arrastar | | Nenhum drop | Nenhum drop |  
| Recortar/colar | Ação | Mover | Mover |  
| Recortar/colar | Destino | Item de cópias para local de destino | Item de cópias para local de destino |  
| Recortar/colar | Origem | Referência de exclusões para o item original | Exclui o item do local original |  
| Recortar/colar | Resultado | Item permanece no local original no armazenamento | Item é excluído do local original no armazenamento |  
| Copiar/colar | Ação | Copiar | Copiar |  
| Copiar/colar | Destino | Adiciona a referência ao item original | Item de cópias para local de destino |  
| Copiar/colar | Origem | Retém o item original | Retém o item original |  
| Copiar/colar | Resultado | Item permanece no local original no armazenamento | Item permanece no armazenamento de ins local original |
  
#### <a name="mixed-target-projects"></a>Projetos de destino misto  
A tabela a seguir resume as operações de arrastar e soltar (bem como Recortar/copiar/colar) que devem ser executadas com base na natureza das chaves de item e o modificador de origem pressionado para projetos de destino misto:  
  
| Modificador | Categoria | Item de origem: / Link de referência | Item de origem: sistema físico do item ou arquivo (`CF_HDROP`) |  
| --- | --- | --- | --- |
| Nenhum modificador | Ação | Mover | Mover |
| Nenhum modificador | Destino | Adiciona a referência ao item original | Item de cópias para local de destino |
| Nenhum modificador | Origem | Referência de exclusões para o item original | Referência de exclusões para o item original |
| Nenhum modificador | Resultado | `DROPEFFECT_ MOVE`é retornado como a ação de `::Drop` e item permanece no local original no armazenamento | `DROPEFFECT_ MOVE`é retornado como a ação de `::Drop` e o item é excluído do local original no armazenamento |
| SHIFT + arrastar | Ação | Mover | Mover |
| SHIFT + arrastar | Destino | Adiciona a referência ao item original | Item de cópias para local de destino |
| SHIFT + arrastar | Origem | Referência de exclusões para o item original | Exclui o item do local original | 
| SHIFT + arrastar | Resultado | `DROPEFFECT_ MOVE`é retornado como a ação de `::Drop` e item permanece no local original no armazenamento | `DROPEFFECT_ MOVE`é retornado como a ação de `::Drop` e o item é excluído do local original no armazenamento |
| CTRL + arrastar | Ação | Copiar | Copiar |
| CTRL + arrastar | Destino | Adiciona a referência ao item original | Item de cópias para local de destino |
| CTRL + arrastar | Origem | Mantém a referência ao item original | Retém o item original |
| CTRL + arrastar | Resultado | `DROPEFFECT_ COPY`é retornado como a ação de `::Drop` e item permanece no local original no armazenamento | `DROPEFFECT_ COPY`é retornado como a ação de `::Drop` e item permanece no local original no armazenamento |
| Ctrl + Shift + arrastar | Ação | Link | Link |
| Ctrl + Shift + arrastar | Destino | Adiciona a referência ao item original | Adiciona a referência ao item de origem original |
| Ctrl + Shift + arrastar | Origem | Mantém a referência ao item original | Retém o item original |
| Ctrl + Shift + arrastar | Resultado | `DROPEFFECT_ LINK`é retornado como a ação de `::Drop` e item permanece no local original no armazenamento | `DROPEFFECT_ LINK`é retornado como a ação de `::Drop` e item permanece no local original no armazenamento |
| Recortar/colar | Ação | Mover | Mover |
| Recortar/colar | Destino | Item de cópias para local de destino | Item de cópias para local de destino |
| Recortar/colar | Origem | Referência de exclusões para o item original | Exclui o item do local original |
| Recortar/colar | Resultado | Item permanece no local original no armazenamento | Item é excluído do local original no armazenamento |
| Copiar/colar | Ação | Copiar | Copiar |
| Copiar/colar | Destino | Adiciona a referência ao item original | Item de cópias para local de destino |
| Copiar/colar | Origem | Retém o item original | Retém o item original |
| Copiar/colar | Resultado | Item permanece no local original no armazenamento | Item permanece no local original no armazenamento |
  
Esses detalhes devem ser levadas em consideração ao implementar a arrastar o **Solution Explorer**:  
  
-   Design para vários cenários de seleção.  
  
-   Nomes de arquivo (caminho completo) devem ser exclusivos entre o projeto de destino ou o descarte não deve ser permitido.  
  
-   Nomes de pasta devem ser exclusivos (diferencia maiusculas de minúsculas) no nível do qual eles são descartados.  
  
-   Há diferenças de comportamento entre arquivos que são abertos ou fechados em tempo de arrastar (não mencionada em cenários acima).  
  
-   Arquivos de nível superior se comportam de forma ligeiramente diferente do que os arquivos em pastas.  
  
Outro problema estar atento é como lidar com operações de movimentação em itens que têm editores ou designers abertos. O comportamento esperado é da seguinte maneira (isso se aplica a todos os tipos de projeto):  
  
1.  Se o editor aberto/designer não tem alterações não salvas, em seguida, a janela de designer do editor deve ser silenciosamente fechada.  
  
2.  Se o editor aberto/designer tem alterações não salvas, a origem de drag deve esperar para o descarte ocorrer e, em seguida, peça ao usuário para salvar as alterações não confirmadas nos documentos abertos antes de fechar a janela com um aviso semelhante ao seguinte:  
  
    ```  
    ==========================================================   
         One or more open documents have unsaved changes.  
    Do you want to save uncommitted changes before proceeding?   
                      [Yes]  [No]  [Cancel]   
    ==========================================================  
    ```  
  
Isso dá ao usuário a oportunidade de salvar o trabalho em andamento antes do destino faz com que as cópias. Um novo método `IVsHierarchyDropDataSource2::OnBeforeDropNotify` foi adicionado para habilitar esse tratamento.  
  
O destino, em seguida, copiar o estado do item como ele está no armazenamento (não incluindo as alterações não salvas no editor, se o usuário escolheu **não**). Depois que o destino concluiu sua cópia (em `IVsHierarchyDropDataSource::Drop`), a fonte tem a oportunidade para concluir a parte de exclusão da operação de movimentação (em `IVsHierarchyDropDataSource::OnDropNotify`).  
  
Qualquer editores com alterações não salvas deverá ser deixados abertos. Para esses documentos com alterações não salvas, isso significa que a parte de cópia da operação de movimentação será executada, mas a parte de exclusão será anulada. Em um cenário de seleção de vários quando o usuário escolhe **não**, esses documentos com alterações não salvas não devem ser fechados ou removidos, mas aqueles sem alterações não salvas devem ser fechados e removidos.
