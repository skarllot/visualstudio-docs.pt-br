---
title: "Padrões de aplicativo para o Visual Studio | Documentos do Microsoft"
ms.custom: 
ms.date: 11/04/2016
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
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 83b586273dcc60f56ad81fd451adce7860df4033
ms.lasthandoff: 02/22/2017

---
# <a name="application-patterns-for-visual-studio"></a>Padrões de aplicativo para o Visual Studio
##  <a name="a-namebkmkwindowinteractionsa-window-interactions"></a><a name="BKMK_WindowInteractions"></a>Interações de janela  
  
### <a name="overview"></a>Visão Geral  
 Os dois tipos de janela principal usados no Visual Studio são editores de documento e janelas de ferramenta. Rara, mas possível, é grandes caixas de diálogo sem janela restrita. Embora essas sejam tudo sem janela restrita no shell, seus padrões são fundamentalmente diferentes. Este tópico aborda a diferença entre as janelas de documentos, janelas de ferramentas e caixas de diálogo sem janela restrita. Padrões da caixa de diálogo modal são abordadas em [caixas de diálogo](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_Dialogs).  
  
### <a name="comparing-window-usage-patterns"></a>Comparando os padrões de uso de janela  
 **Janelas de documento** quase sempre são exibidas no documento também. Isso permite que o editor de documentos um "estágio center" para organizar as janelas de ferramentas complementares ao redor.  
  
 A **janela da ferramenta** geralmente é exibido como uma janela menores, que pode ser visível, oculto ou ocultas automaticamente – recolhido contra a borda do IDE. No entanto, às vezes, eles são apresentados no documento bem, desmarcando a **janela/encaixe** propriedade na janela. Isso resulta em um estado mais real, mas também uma comum decisão de design: ao tentar integrar o Visual Studio, você deve decidir se o recurso deve exibir uma janela de ferramenta ou em uma janela de documento.  
  
 **Caixas de diálogo sem janela restrita** não são incentivados no Visual Studio. Em grande parte, eles são – por definição – flutuante janelas de ferramenta e devem ser implementados como tal. Caixas de diálogo sem janela restrita são permitidas em casos onde o tamanho de uma janela de ferramenta normal ancorada ao lado do shell poderia ser muito limitado. Eles também são permitidos em casos onde o usuário seria provavelmente mover a caixa de diálogo para um monitor secundário.  
  
 Pense cuidadosamente sobre qual tipo de contêiner que você precisa. Considerações de padrão de uso comum para design de interface do usuário estão na tabela a seguir.  
  
||Janela de documento|Janela de ferramenta|Caixa de diálogo sem janela restrita|  
|-|---------------------|-----------------|---------------------|  
|**Posição**|Sempre posicionado dentro do documento bem e não encaixar ao redor das bordas do IDE. Ele pode ser "retirado" para que ela flutua separadamente do shell principal.|Geralmente guia integrada ao redor das bordas do IDE, mas pode ser personalizado para ser flutuante, oculta automaticamente (desafixada) ou encaixada bem dentro do documento.|Grande janela flutuante separada do IDE.|  
|**Modelo de confirmação**|*Confirmação atrasada*<br /><br /> Para salvar os dados em um documento, o usuário deve emitir o comando arquivo/salvar, salvar como ou salvar tudo. Uma janela de documento tem o conceito dos dados dentro dele sendo "sujas" confirmado para um Salvar comandos. Ao fechar uma janela de documento, todos os conteúdos são salvos em disco ou perdidos.|*Confirmação imediata*<br /><br /> Não há nenhum Salvar modelo. Para janelas de ferramenta de inspetor que ajudam na edição de um arquivo, o arquivo deve estar aberto no editor ativo ou no designer e editor ou designer possui o salvamento.|*Confirmação atrasada ou imediata*<br /><br /> Geralmente, uma caixa de diálogo sem janela restrita grande requer uma ação para confirmar as alterações e permite uma operação "Cancelar", que reverte todas as alterações feitas na sessão de diálogo.  Isso os diferencia uma caixa de diálogo sem janela restrita em uma janela de ferramenta que janelas de ferramentas sempre tem um modelo de confirmação imediata.|  
|**Visibilidade**|*Abrir/criar (arquivo) e fechar*<br /><br /> Abrir um documento do windows é feito por meio de abrir um documento existente ou usando um modelo para criar um novo documento. Não há nenhum "abrir \<editor específico >" comando.|*Ocultar e mostrar*<br /><br /> Janelas de ferramentas de instância única podem ser ocultadas ou exibidas. Conteúdo e estados dentro da janela de ferramenta persistirem se no modo de exibição ou oculto. Janelas de ferramentas de várias instâncias podem ser fechadas como ocultadas. Quando uma janela de ferramentas de várias instâncias é fechada, o conteúdo e o estado dentro da janela de ferramenta será descartada.|*Iniciado a partir de um comando*<br /><br /> Caixas de diálogo são lançadas a partir de um comando baseado em tarefas.|  
|**Instâncias**|*Várias instâncias*<br /><br /> Vários editores podem ser abertos ao mesmo tempo e edição de arquivos diferentes, embora alguns editores de também permitem o mesmo arquivo seja aberto em mais de um editor (usando o **janela > nova janela** comando).<br /><br /> Um editor de único pode estar editando um ou vários arquivos ao mesmo tempo (Designer de projeto).|*Único ou vários instance*<br /><br /> Conteúdo alterado para refletir o contexto (como o navegador de propriedade) ou enviar por push o foco/contexto para outras janelas (lista de tarefas, Gerenciador de soluções).<br /><br /> Janelas de ferramentas de instância única e várias instâncias devem ser associadas à janela do documento ativo, a menos que haja um motivo convincente não para.|*Instância única*|  
|**Exemplos**|**Editores de texto**, como o editor de código<br /><br /> **Superfícies de design**, como um designer de formulário ou uma superfície de modelagem<br /><br /> **Controlar layouts semelhantes a caixas de diálogo**, como o Designer de manifesto|O **Solution Explorer** oferece uma solução e projetos contidos dentro da solução<br /><br /> O **Server Explorer** fornece uma exibição hierárquica de servidores e conexões de dados que o usuário opta por abrir na janela. Abrindo um objeto da hierarquia de banco de dados, como uma consulta, abre uma janela de documento e permite que o usuário edite a consulta.<br /><br /> O **navegador de propriedade** exibe propriedades para o objeto selecionado em uma janela de documento ou em outra janela de ferramenta. As propriedades são apresentadas em uma exibição hierárquica de grade ou em controles de caixa de diálogo semelhante complexos e permitir que o usuário defina os valores dessas propriedades.||  
  
##  <a name="a-namebkmktoolwindowsa-tool-windows"></a><a name="BKMK_ToolWindows"></a>Janelas de ferramenta  
  
### <a name="overview"></a>Visão Geral  
 Ferramenta windows compatível com o trabalho do usuário que ocorre em janelas de documento. Eles podem ser usados para exibir uma hierarquia que representa um objeto raiz fundamental que o Visual Studio fornece e pode manipular.  
  
 Ao considerar uma nova janela de ferramenta no IDE, os autores devem:  
  
-   Usar janelas de ferramenta existente apropriado de tarefa e não criar novos com funcionalidade semelhante. Novas janelas de ferramenta devem ser criadas apenas se eles oferecem um "tool" significativamente diferente ou funcionalidade que não pode ser integrada em uma janela semelhante ou transformando uma janela existente em um hub de dinamização.  
  
-   Use uma barra de comando padrão, se necessário, na parte superior da janela de ferramenta.  
  
-   Ser consistente com padrões já presentes em outras janelas de ferramenta para controlar a navegação de teclado e de apresentação.  
  
-   Ser consistente com a apresentação de controle em outras janelas de ferramenta.  
  
-   Janelas de ferramenta específica do documento devem ser automaticamente visíveis quando possível para que eles aparecem somente quando o documento pai é ativado.  
  
-   Certifique-se de que o conteúdo da janela é navegado com um teclado (teclas de direção de suporte).  
  
#### <a name="tool-window-states"></a>Estados de janela de ferramenta  
 Janelas de ferramentas do Visual Studio têm diferentes estados, alguns dos quais são ativados por usuário (como o recurso de ocultar automaticamente). Outros estados, como auto visível, permitir janelas de ferramenta aparecem no contexto correto e ocultar quando não é necessário. Há cinco estados de janela de ferramenta no total.  
  
-   **Encaixado/fixado** janelas de ferramentas podem ser anexadas a qualquer um dos quatro lados da área do documento. O ícone de anotações aparece na barra de título da janela de ferramenta. A janela da ferramenta pode ser encaixada horizontal ou verticalmente ao longo da borda de shell e outras janelas de ferramenta e também pode ser vinculada por guia.  
  
-   **Auto-oculto** janelas de ferramenta serão desagregadas. A janela pode deslizar fora de Vista, deixando uma guia (com o nome da janela de ferramenta e seu ícone) na borda da área do documento. A janela da ferramenta desliza quando um usuário passar o mouse sobre a guia.  
  
-   **Autovisível** janelas de ferramenta será exibida automaticamente quando outra parte da interface do usuário, como um editor, é iniciado ou ganha o foco.  
  
-   **Flutuante** janelas de ferramenta passe fora do IDE. Isso é útil para configurações de vários monitores.  
  
-   **Documentos com guias** janelas de ferramenta podem ser bem encaixadas dentro do documento. Isso é útil para janelas de ferramenta grandes, como o Pesquisador de objetos, que precisam de mais imóveis que permite às bordas do quadro de encaixe.  
  
 ![Ferramenta de estados de janela no Visual Studio](../../extensibility/ux-guidelines/media/0702-01_toolwindowstates.png "0702&01;_ToolWindowStates")  
  
 **Estados de janela de ferramenta no Visual Studio**  
  
#### <a name="single-instance-and-multi-instance"></a>Instância única e várias instâncias  
 Janelas de ferramenta são instância única ou várias instâncias. Algumas janelas de ferramenta de instância única podem ser associadas com a janela do documento ativo, enquanto as janelas de ferramentas de várias instâncias não podem. Janelas de ferramentas de várias instâncias respondem ao comando janela/New Window, criando uma nova instância da janela. A imagem a seguir ilustra uma janela de ferramenta permitindo que a nova janela de comando quando uma instância da janela está ativa:  
  
 ![Janela de ferramenta permitindo comandos no Visual Studio](../../extensibility/ux-guidelines/media/0702-02_toolwindowenablingcommand.png "0702&02;_ToolWindowEnablingCommand")  
  
 **Janela de ferramenta permitindo que o comando 'Nova janela' quando uma instância da janela está ativa**  
  
 Janelas de ferramentas de instância única podem ser ocultadas ou exibidas, enquanto as janelas de ferramentas de várias instâncias podem ser fechadas, bem como ocultadas. Todas as janelas de ferramenta podem ser encaixadas, guia vinculada, flutuante ou definido como uma janela filho de Interface de documentos múltiplos (MDI) (semelhante a uma janela de documento). Todas as janelas de ferramenta devem responder para os comandos de gerenciamento de janela apropriada no menu da janela:  
  
 ![Comandos de gerenciamento de janela no Visual Studio](../../extensibility/ux-guidelines/media/0702-03_windowmanagementcontrols.png "0702&03;_WindowManagementControls")  
  
 **Comandos de gerenciamento de janela no menu janela do Visual Studio**  
  
#### <a name="document-specific-tool-windows"></a>Janelas de ferramentas específicas de documentos  
 Algumas janelas de ferramenta devem ser alteradas com base em um determinado tipo de documento. Essas janelas continuamente atualizado para refletir a funcionalidade aplicável à janela do documento ativo no IDE.  
  
 A caixa de ferramentas e a estrutura de tópicos do documento são exemplos de janelas de ferramenta cujo conteúdo é alterado para refletir o editor selecionado. Essas janelas mostram uma marca d'água quando um editor tem foco que não oferecem o contexto para a janela.  
  
#### <a name="navigable-list-tool-windows"></a>Janelas de ferramenta lista navegável  
 Algumas janelas de ferramenta exibem uma lista de itens navegáveis, com que o usuário pode interagir. Esse tipo de janela, deve sempre haver comentários para o item atual na lista, mesmo que a janela está inativa. A lista deve responder para o **GoToNextLocation** e **GoToPrevLocation** comandos alterando também o item atualmente selecionado na janela  
  
 O Gerenciador de soluções e a janela localizar resultados são exemplos de janelas de ferramenta lista navegável.  
  
### <a name="tool-window-types"></a>Tipos de janelas de ferramenta  
  
#### <a name="common-tool-windows-and-their-functions"></a>Janelas de ferramentas comuns e suas funções  
  
|Tipo|Janela de ferramenta|Função|  
|----------|-----------------|--------------|  
|**Hierarquia**|Gerenciador de Soluções|Uma árvore hierárquica que exibe uma lista dos documentos contidos em projetos e arquivos diversos itens de solução. A exibição de itens em projetos é definida pelo pacote que possui o tipo de projeto (por exemplo, tipos de base de referência, com base no diretório ou modo misto).|  
|**Hierarquia**|Exibição de Classe|Uma árvore hierárquica das classes e vários elementos no conjunto de trabalho de documentos, independentes dos próprios arquivos.|  
|**Hierarquia**|conexões de servidor|Uma árvore hierárquica que exibe todas as conexões de servidores e dados na solução.|  
|**Hierarquia**|Estrutura de Tópicos do Documento|A estrutura hierárquica do documento ativo.|  
|**Grade**|Propriedades|Uma grade que exibe uma lista de propriedades do objeto selecionado, junto com os seletores de valor para editar essas propriedades.|  
|**Grade**|Lista de Tarefas|Uma grade que permite ao usuário criar/editar/excluir tarefas e comentários.|  
|**Conteúdo**|Ajuda|Uma janela que permite aos usuários acesso a vários métodos para obter ajuda de "Como faço?" vídeos para os fóruns do MSDN.|  
|**Conteúdo**|Ajuda Dinâmica|Uma janela de ferramenta que exibe links para tópicos aplicáveis à seleção atual da Ajuda.|  
|**Conteúdo**|Pesquisador de Objetos|Um conjunto de quadros de duas colunas com uma lista de componentes de objeto hierárquica no painel esquerdo e o objeto propriedades e métodos na coluna à direita.|  
|**Caixa de diálogo**|Localização, localização avançada|Uma caixa de diálogo que permite ao usuário localizar ou localizar e substituir em vários arquivos dentro da solução.|  
|**Outros**|Caixa de Ferramentas|A janela da ferramenta usada para armazenar elementos que serão removidos em superfícies de design, fornecendo uma fonte de arrastar consistente para todos os designers.|  
|**Outros**|Start Page|Portal do usuário para o Visual Studio, com acesso aos feeds de notícias para desenvolvedores, Ajuda do Visual Studio e projetos recentes. Os usuários também podem criar páginas de início personalizados copiando o arquivo XAML da pasta arquivos de programa "Common7\IDE\StartPages\" Visual Studio para a pasta StartPages no diretório de documentos do Visual Studio e, em seguida, editando o XAML manualmente ou abri-lo no Visual Studio ou outro código de editor.|  
|**Depurador:** um grupo do windows específicas para tarefas de depuração e monitoramento de atividades|Autos||  
|**Depurador:** um grupo do windows específicas para tarefas de depuração e monitoramento de atividades|Imediato||  
|**Depurador:** um grupo do windows específicas para tarefas de depuração e monitoramento de atividades|Saída|A janela de saída pode ser usada sempre que houver eventos textuais ou status declarar.|  
|**Depurador:** um grupo do windows específicas para tarefas de depuração e monitoramento de atividades|Memória||  
|**Depurador:** um grupo do windows específicas para tarefas de depuração e monitoramento de atividades|Pontos de interrupção||  
|**Depurador:** um grupo do windows específicas para tarefas de depuração e monitoramento de atividades|Em execução||  
|**Depurador:** um grupo do windows específicas para tarefas de depuração e monitoramento de atividades|Documentos||  
|**Depurador:** um grupo do windows específicas para tarefas de depuração e monitoramento de atividades|Pilha de chamadas||  
|**Depurador:** um grupo do windows específicas para tarefas de depuração e monitoramento de atividades|Locais||  
|**Depurador:** um grupo do windows específicas para tarefas de depuração e monitoramento de atividades|Inspeções||  
|**Depurador:** um grupo do windows específicas para tarefas de depuração e monitoramento de atividades|Desmontagem||  
|**Depurador:** um grupo do windows específicas para tarefas de depuração e monitoramento de atividades|Registros||  
|**Depurador:** um grupo do windows específicas para tarefas de depuração e monitoramento de atividades|Threads||  
  
##  <a name="a-namebkmkdocumenteditorconventionsa-document-editor-conventions"></a><a name="BKMK_DocumentEditorConventions"></a>Convenções do documento editor  
  
### <a name="document-interactions"></a>Interações de documento  
 "Documento bem" é o maior espaço dentro do IDE e é onde o usuário geralmente tem se concentrado sua atenção para concluir suas tarefas, assistidas por janelas de ferramentas complementares. Editores de documento representam as unidades fundamentais de trabalho que o usuário abre e salva no Visual Studio. Eles mantêm um forte senso de seleção vinculada ao Gerenciador de soluções ou de outra hierarquia ativa. O usuário deve ser capaz de apontar para uma dessas janelas de hierarquia e saber onde o documento está contido e sua relação para a solução, o projeto ou outro objeto raiz fornecida por um pacote do Visual Studio.  
  
 Edição de documentos requer uma experiência de usuário consistente. Para permitir que o usuário a se concentrar na tarefa à mão, em vez de no gerenciamento de janela e Localizando comandos, selecione uma estratégia de exibição de documento que melhor atenda as tarefas do usuário para editar esse tipo de documento.  
  
#### <a name="common-interactions-for-the-document-well"></a>Interações comuns para o documento bem  
  
-   Manter um modelo consistente de interação comum **novo arquivo** e **abrir arquivo** experiências.  
  
-   Atualize a funcionalidade relacionada em menus e janelas relacionadas quando abre a janela do documento.  
  
-   Comandos de menu estão corretamente integrados menus comuns como **editar**, **formato**, e **exibição** menus. Se houver uma quantidade significativa de comandos especializados, então um novo menu pode ser criado que é visível somente quando o documento tem o foco.  
  
-   Uma barra de ferramentas inserida pode ser colocada na parte superior do editor. Isso é preferível ter uma barra de ferramentas separada que aparece fora do editor.  
  
-   Sempre manter uma seleção no Gerenciador de soluções ou ativo semelhante janela hierarquia.  
  
-   Clicar duas vezes em um documento no Gerenciador de soluções deve executar a mesma ação **abrir**.  
  
-   Se mais de um editor pode ser usado em um tipo de documento, o usuário deve ser capaz de substituir ou redefinir a ação padrão em um tipo de dado documento usando o **abrir com** caixa de diálogo clicando duas vezes no arquivo e selecionando **abrir com** no menu de atalho.  
  
-   Não crie também um assistente em um documento.  
  
### <a name="user-expectations-for-specific-document-types"></a>Expectativas do usuário para tipos específicos de documentos  
 Há vários tipos diferentes de básicos de editores de documento e cada um tem uma série de interações que são consistentes com outros usuários do mesmo tipo.  
  
-   **Editor de texto:** editor de código, arquivos de log  
  
-   **Superfície de design:** WPF forms designer, do Windows forms  
  
-   **Editor de estilos de caixa de diálogo:** Designer de manifesto, propriedades do projeto  
  
-   **Designer de modelo:** designer de fluxo de trabalho, codemap, diagrama de arquitetura, progressão  
  
 Também há vários tipos de editor não que usam o documento também. Embora eles não editam próprios documentos, eles precisam seguem interações padrão para janelas de documento.  
  
-   **Relatórios:** IntelliTrace relatório, relatório de Hyper-V, relatórios do criador de perfil  
  
-   **Painel:** Hub de diagnóstico  
  
#### <a name="text-based-editors"></a>Editores de texto  
  
-   O documento participa no modelo de guia de visualização, permitindo a visualização do documento sem abri-lo.  
  
-   A estrutura do documento pode ser representada em uma janela de ferramenta complementar, como uma estrutura de tópicos do documento.  
  
-   IntelliSense (se apropriado) irão se comportar consistentemente com outros editores de código.  
  
-   Pop-ups ou interface do usuário assistencial siga estilos e padrões semelhantes para existente semelhante da interface do usuário, como CodeLens.  
  
-   Mensagens sobre o status do documento serão apresentadas em um controle de barra de informações na parte superior do documento ou na barra de status.  
  
-   O usuário deve ser capaz de personalizar a aparência de fontes e cores usando um **Ferramentas > opções** página, a página de fontes e cores compartilhada ou um específico para o editor.  
  
#### <a name="design-surfaces"></a>Superfícies de design  
  
-   Um designer vazio deve ter uma marca d'água na superfície de indicando como começar.  
  
-   Mecanismos de alternância seguirão os padrões existentes, como clicar duas vezes para abrir um editor de código ou guias na janela do documento, permitindo que a interação com os dois painéis.  
  
-   Adicionando elementos à superfície de design deve ser feito por meio da caixa de ferramentas, a menos que uma janela de ferramenta altamente específica é necessária.  
  
-   Itens na superfície de segue um modelo consistente de seleção.  
  
-   Barras de ferramentas inseridas contêm comandos apenas; não comuns de comandos específicos do documento como **salvar**.  
  
#### <a name="dialog-style-editors"></a>Editores de estilo de caixa de diálogo  
  
-   Layout de controle deve seguir as convenções de layout de caixa de diálogo normal.  
  
-   Guias dentro do editor não devem corresponder a aparência de guias de documento, devem corresponder a um dos dois estilos de guia interiores permitidos.  
  
-   Os usuários devem ser capazes de interagir com os controles usando o teclado. pode ser feito ativando o editor e tabulações por meio de controles ou usando mnemônicos padrão.  
  
-   O designer deve usar comuns Salvar modelo. Não salvar geral ou botões de confirmação devem ser colocados na superfície, embora outros botões podem ser apropriados.  
  
#### <a name="model-designers"></a>Designers de modelo  
  
-   Um designer vazio deve ter uma marca d'água na superfície de indicando como começar.  
  
-   Adicionando elementos à superfície de design deve ser feito por meio da caixa de ferramentas.  
  
-   Itens na superfície de segue um modelo consistente de seleção.  
  
-   Barras de ferramentas inseridas contêm comandos apenas; não comuns de comandos específicos do documento como **salvar**.  
  
-   Uma legenda pode aparecer na superfície, indicativo ou uma marca d'água.  
  
-   O usuário deve ser capaz de personalizar a aparência das fontes/cores usando um **Ferramentas > opções** página, a página de fontes e cores compartilhada ou um específico para o editor.  
  
#### <a name="reports"></a>Relatórios  
  
-   Relatórios são normalmente somente informações e não participam no modelo de salvar. No entanto, eles podem incluir interação como links para outras informações relevantes ou seções expandir e recolher.  
  
-   A maioria dos comandos na superfície de deve ser hiperlinks, não os botões.  
  
-   Layout deve incluir um cabeçalho e siga as diretrizes de layout de relatório padrão.  
  
#### <a name="dashboards"></a>Painéis  
  
-   Painéis não têm um modelo de interação próprios, mas servem como um meio de oferecer uma variedade de outras ferramentas.  
  
-   Eles não participam no modelo de salvar.  
  
-   Os usuários devem ser capazes de interagir com os controles usando o teclado, ativando o editor e percorrer por controles ou mnemônico padrão.  
  
##  <a name="a-namebkmkdialogsa-dialogs"></a><a name="BKMK_Dialogs"></a>Caixas de diálogo  
  
### <a name="introduction"></a>Introdução  
 Caixas de diálogo no Visual Studio normalmente devem dar suporte a uma unidade separada do trabalho do usuário e, em seguida, ser descartadas.  
  
 Se você determinar que você precisa de uma caixa de diálogo, você tem três opções, na ordem de preferência:  
  
1.  Integre os recursos em uma das caixas de diálogo compartilhadas no Visual Studio.  
  
2.  Crie sua própria caixa de diálogo usando um padrão encontrado em uma caixa de diálogo semelhante existente.  
  
3.  Crie uma nova caixa de diálogo, interação a seguir e diretrizes de layout.  
  
 Este tópico descreve como escolher o padrão de diálogo corretas nos fluxos de trabalho do Visual Studio e as convenções comuns de design de caixa de diálogo.  
  
### <a name="themes"></a>Temas  
 Caixas de diálogo do Visual Studio execute um dos dois estilos básicos:  
  
#### <a name="standard-unthemed"></a>Padrão (unthemed)  
 A maioria das caixas de diálogo são caixas de diálogo do utilitário padrão e deve ser unthemed. Não não controles comuns do novo modelo ou tente criar botões de "moderna" estilizado ou controles. Controles e a aparência de cromo siga [diretrizes de interação de área de trabalho do Windows padrão para caixas de diálogo](https://msdn.microsoft.com/en-us/library/windows/desktop/dn742499\(v=vs.85\).aspx).  
  
#### <a name="themed"></a>Com temas  
 Caixas de diálogo especialidade "assinatura" podem ter um temas. Caixas de diálogo com temas têm uma aparência distinta, que também tem alguns padrões de interação especial associadas ao estilo. Tema a caixa de diálogo somente se ele atende a esses requisitos:  
  
-   A caixa de diálogo é uma experiência comum que será Vista e usada com frequência ou por muitos usuários (por exemplo, o **novo projeto** caixa de diálogo.  
  
-   A caixa de diálogo contém elementos de marca de produto de destaque (por exemplo, o **configurações de conta** caixa de diálogo).  
  
-   A caixa de diálogo é exibida como parte integrante de um fluxo maior que inclui outras temas caixas de diálogo (por exemplo, o **Adicionar serviço conectado** caixa de diálogo).  
  
-   A caixa de diálogo é uma parte importante de uma experiência que desempenha um papel estratégico em promover ou diferenciar uma versão do produto.  
  
 Ao criar uma caixa de diálogo com temas, use as cores de ambiente apropriado e siga o layout correto e os padrões de interação. (Consulte [Layout para o Visual Studio](../../extensibility/ux-guidelines/layout-for-visual-studio.md))  
  
### <a name="dialog-design"></a>Design da caixa de diálogo  
 Caixas de diálogo bem projetadas consideram os seguintes elementos:  
  
-   A tarefa de usuário suportada  
  
-   O estilo de texto da caixa de diálogo, idioma e terminologia  
  
-   Opção de controle e convenções de interface do usuário  
  
-   Alinhamento de especificação e controle de layout Visual  
  
-   Acesso de teclado  
  
#### <a name="content-organization"></a>Organização do conteúdo  
 Considere as diferenças entre esses tipos básicos de caixas de diálogo:  
  
-   [Caixas de diálogo simples](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_SimpleDialogs) apresentar controles em uma única janela modal. A apresentação pode incluir variações dos padrões de controle complexo, incluindo um seletor de campo ou uma barra de ferramentas.  
  
-   [Em camadas de caixas de diálogo](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_LayeredDialogs) são usados para obter o máximo de espaço na tela quando um único segmento de interface do usuário consiste em vários grupos de controles. Agrupamentos da caixa de diálogo são "em camadas" por meio de controles de guia, controles de navegação ou botões para que o usuário pode escolher qual o agrupamento para ver a qualquer momento.  
  
-   [Assistentes](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_Wizards) são úteis para direcionar o usuário por meio de uma sequência lógica de etapas para a conclusão de uma tarefa. Uma série de opções são oferecidos em painéis sequenciais, às vezes, introduzindo diferentes fluxos de trabalho ("ramificações") dependentes de uma escolha feita no painel anterior.  
  
####  <a name="a-namebkmksimpledialogsa-simple-dialogs"></a><a name="BKMK_SimpleDialogs"></a>Caixas de diálogo simples  
 Uma caixa de diálogo é uma apresentação dos controles em uma única janela modal. Esta apresentação pode incluir variações dos padrões de controle complexo, como um seletor de campo. Para caixas de diálogo simples, siga o layout geral padrão, bem como qualquer layout específico necessários para agrupamentos de controle complexo.  
  
 ![Caixa de diálogo Simple no Visual Studio](../../extensibility/ux-guidelines/media/0704-01_createstrongnamekey.png "01_CreateStrongNameKey&0704;")  
  
 **Criar chave de nome forte é um exemplo de uma caixa de diálogo simple no Visual Studio.**  
  
####  <a name="a-namebkmklayereddialogsa-layered-dialogs"></a><a name="BKMK_LayeredDialogs"></a>Caixas de diálogo em camadas  
 Caixas de diálogo em camadas incluem guias, painéis e árvores incorporados. Eles são usados para maximizar imóveis quando houver vários grupos de controles oferecidos em um único segmento de interface do usuário. Os agrupamentos são colocadas em camadas para que o usuário pode escolher qual o agrupamento para ver a qualquer momento.  
  
 No caso mais simples, o mecanismo para alternar entre agrupamentos é um controle guia. Há várias alternativas disponíveis. Consulte atribuir prioridades e camadas para como escolher o estilo mais apropriado.  
  
 O **Ferramentas > opções** caixa de diálogo é um exemplo de uma caixa de diálogo em camadas usando uma árvore inserida:  
  
 ![Caixa de diálogo em camadas no Visual Studio](../../extensibility/ux-guidelines/media/0704-02_toolsoptions.png "02_ToolsOptions&0704;")  
  
 **Ferramentas > opções é um exemplo de uma caixa de diálogo em camadas no Visual Studio.**  
  
####  <a name="a-namebkmkwizardsa-wizards"></a><a name="BKMK_Wizards"></a>Assistentes  
 Assistentes são úteis para direcionar o usuário por meio de uma sequência lógica de etapas na conclusão de uma tarefa. Uma série de opções oferecidas nos painéis sequenciais e o usuário deve continuar em cada etapa antes de prosseguir para a próxima. Depois de padrões suficientes estão disponíveis, o **concluir** botão é habilitado.  
  
 Assistentes modais são usados para tarefas que:  
  
-   Contém a ramificação, onde caminhos diferentes são oferecidos com as escolhas do usuário  
  
-   Contém dependências entre as etapas, onde as etapas subsequentes dependem de entrada do usuário das etapas anteriores  
  
-   São suficientemente complexa que a interface do usuário deve ser usado para explicar as opções oferecidas e os possíveis resultados de cada etapa  
  
-   São transacionais, exigindo um conjunto de etapas a serem concluídas em sua totalidade antes de quaisquer mudanças serem confirmadas  
  
### <a name="common-conventions"></a>Convenções comuns  
 Para fazer o design ideal e a funcionalidade com as caixas de diálogo, siga estas convenções diálogo tamanho, posição, padrões, configuração de controle e alinhamento, interface do usuário texto, barras de título, botões de controle, e chaves de acesso.  
  
 Para obter diretrizes específicas do layout, consulte [Layout para o Visual Studio](../../extensibility/ux-guidelines/layout-for-visual-studio.md).  
  
#### <a name="size"></a>Tamanho  
 Caixas de diálogo devem se ajustar dentro de uma resolução mínima de tela de 1024 x 768 e tamanho de caixa de diálogo inicial não deve exceder 900 x 700 pixels. Caixas de diálogo podem ser redimensionadas, mas não é um requisito.  
  
 Há dois recomendações para caixas de diálogo redimensionáveis:  
  
1.  Que tamanho mínimo é definido para a caixa de diálogo que otimizar para o conjunto de controles sem recorte e serão ajustadas para acomodar o crescimento de localização razoável.  
  
2.  Se o tamanho da escala de usuário persiste a cada sessão. Por exemplo, se o usuário dimensiona uma caixa de diálogo para 150%, uma inicialização subsequente da caixa de diálogo exibirá 150%.  
  
#### <a name="position"></a>Posição  
 Caixas de diálogo devem aparecer centralizadas no IDE na primeira inicialização. Para caixas de diálogo não redimensionável, não é necessário que a última posição da caixa de diálogo ser persistentes, para que ela aparecerá centralizada nas inicializações subsequentes. Para caixas de diálogo redimensionáveis, o tamanho deve ser persistido nas inicializações subsequentes. Para caixas de diálogo redimensionáveis que são modais, a posição não precisa ser mantido. Exibi-los centralizado dentro do IDE evita a possibilidade da caixa de diálogo que aparece em uma posição imprevisível ou inutilizável quando a configuração de exibição do usuário foi alterada. Para caixas de diálogo sem janela restrita que podem ser reposicionadas, a posição do usuário deve ser mantida nas inicializações subsequentes, como a caixa de diálogo pode ser usada com frequência, como parte integrante de um fluxo de trabalho maior.  
  
 Quando as caixas de diálogo devem gerar outras caixas de diálogo, a caixa de diálogo mais alta deve propagar para a direita e para baixo do pai para que ele seja claro para o usuário navegou para um novo local.  
  
#### <a name="modality"></a>Modalidade  
 Sendo modal significa que os usuários são necessários para concluir ou cancelar a caixa de diálogo antes de continuar. Como caixas de diálogo modais impedem que o usuário interaja com outras partes do ambiente, o fluxo de tarefas do recurso deve usá-los moderadamente possível. Quando uma operação restrita é necessária, o Visual Studio tem um número de caixas de diálogo compartilhados, em que você pode integrar os recursos. Se for necessário criar uma nova caixa de diálogo, siga o padrão de interação de uma caixa de diálogo existente com funcionalidade semelhante.  
  
 Quando os usuários precisam executar duas atividades ao mesmo tempo, como **localizar** e **substituir** ao escrever novo código, a caixa de diálogo deve ser restrita para que o usuário pode alternar facilmente entre elas. Geralmente, o Visual Studio usa janelas de ferramenta para esse tipo de suporte de editor de tarefa vinculada.  
  
#### <a name="control-configuration"></a>Configuração de controle  
 Ser consistente com as configurações de controle existentes que realizam a mesma coisa no Visual Studio.  
  
#### <a name="title-bars"></a>Barras de título  
  
-   O texto na barra de título deve refletir o nome do comando que o iniciou.  
  
-   Nenhum ícone deve ser usado em barras de título da caixa de diálogo. Em casos onde o sistema requer um, use o logotipo do Visual Studio.  
  
-   Caixas de diálogo não deve minimizar ou maximizar botões.  
  
-   Botões de ajuda na barra de título foram substituídos. Não adicione-os para novas caixas de diálogo. Quando existirem, eles devem iniciar um tópico da Ajuda que são conceitualmente relevantes para a tarefa.  
  
 ![Especificações do Visual Studio da barra de título](../../extensibility/ux-guidelines/media/0704-03_titlebarspecs.png "03_TitleBarSpecs&0704;")  
  
 **Especificações de diretriz para barras de título nas caixas de diálogo do Visual Studio.**  
  
#### <a name="control-buttons"></a>Botões de controle  
 Em geral, **Okey**/**Cancelar**/**ajuda** botões devem ser organizados horizontalmente no canto inferior direito da caixa de diálogo. A pilha vertical alternativa é permitida se uma caixa de diálogo tem vários outros botões na parte inferior da caixa de diálogo que poderia apresentar visual confusão com os botões de controle.  
  
 ![Controlar as configurações de botão no Visual Studio](../../extensibility/ux-guidelines/media/0704-04_controlbuttonconfig.png "04_ControlButtonConfig&0704;")  
  
 **Configurações aceitáveis para os botões de controle nas caixas de diálogo do Visual Studio**  
  
 A caixa de diálogo deve incluir um botão de controle padrão. Para determinar o comando recomendado para usar como padrão, escolha as opções seguintes (listadas em ordem de precedência):  
  
-   Escolha o comando mais seguro e mais seguro como o padrão. Isso significa que o comando mais provável evitar perda de dados e evitar o acesso ao sistema não intencionais.  
  
-   Se a segurança e a perda de dados não são fatores, escolha o comando padrão com base em sua conveniência. Incluindo o comando provavelmente como padrão melhorará o fluxo de trabalho do usuário quando a caixa de diálogo oferece suporte a tarefas repetitivas ou frequentes.  
  
 Evite escolher uma ação destrutiva permanentemente para o comando padrão. Se o comando estiver presente, escolha um comando mais seguro como o padrão.  
  
#### <a name="access-keys"></a>Teclas de acesso  
 Não use teclas de acesso para **Okey**/**Cancelar**/**ajuda** botões. Por padrão, esses botões são mapeados para as teclas de atalho:  
  
|Nome do botão|Atalho de teclado|  
|-----------------|-----------------------|  
|OK|Entrar|  
|Cancelar|ESC|  
|Ajuda|F1|  
  
#### <a name="imagery"></a>Imagens  
 Use imagens com moderação nas caixas de diálogo. Não use ícones grandes nas caixas de diálogo para usar o espaço. Use imagens somente se eles são uma parte importante de transmitir a mensagem para o usuário, como ícones de aviso ou animações de status.  
  
###  <a name="a-namebkmkprioritizingandlayeringa-prioritizing-and-layering"></a><a name="BKMK_PrioritizingAndLayering"></a>A priorização e a disposição em camadas  
  
#### <a name="prioritizing-your-ui"></a>Priorizando a interface do usuário  
 Pode ser necessário trazer certos elementos da interface do usuário para o forefront e colocar o comportamento mais avançado e opções (incluindo comandos obscuros) em caixas de diálogo. Trazer funcionalidades mais comumente usadas para o forefront fazer espaço para ele e torná-lo visível por padrão na interface do usuário com um rótulo de texto quando a caixa de diálogo é exibida.  
  
#### <a name="layering-your-ui"></a>Dispondo em camadas na interface do usuário  
 Se você tiver determinado que uma caixa de diálogo é necessária, mas a funcionalidade relacionada que deseja apresentar ao usuário vai além do que pode ser exibido em uma caixa de diálogo, você precisa camada de interface do usuário. Os métodos mais comuns de disposição em camadas que usa o Visual Studio são guias e corredores ou painéis. Em alguns casos, as regiões que podem expandir e recolher podem ser apropriados. Interface do usuário adaptável não costuma ser recomendada no Visual Studio.  
  
 Há vantagens e desvantagens diferentes métodos de disposição em camadas da interface do usuário por meio de controles de guia. Examine a lista a seguir para garantir que você está escolhendo uma técnica de disposição em camadas que é apropriada para sua situação.  
  
##### <a name="tabbing"></a>Tabulação  
  
|Mecanismo de comutação|Vantagens e uso apropriado|Uso indevido e desvantagens|  
|-------------------------|------------------------------------|-----------------------------------------|  
|Controle de guia|Agrupar logicamente páginas de diálogo em conjuntos relacionados<br /><br /> Útil para menos de cinco (ou o número de guias que caibam em uma linha na caixa de diálogo) páginas de controles relacionados na caixa de diálogo<br /><br /> Rótulos de guia devem ser curtos: uma ou duas palavras que podem identificar facilmente o conteúdo<br /><br /> Um estilo de caixa de diálogo comuns do sistema<br /><br /> Exemplo: **Explorador de arquivos > propriedades de Item**|Pode ser difícil fazer rótulos curtos descritivos<br /><br /> Geralmente não dimensionado para mais de cinco guias em uma caixa de diálogo<br /><br /> Inapropriado se você tiver muitos guias para uma linha; usar uma técnica alternativa de camadas<br /><br /> Não extensível|  
|Navegação da barra lateral|Dispositivo de alternância Simple que pode acomodar mais categorias de guias<br /><br /> Lista plana de categorias (nenhuma hierarquia)<br /><br /> Extensível<br /><br /> Exemplo: **personalizar... > Adicionar comando**|Não um bom uso de espaço horizontal se houver menos de três grupos<br /><br /> Tarefas podem ser mais adequadas para uma lista suspensa|  
|Controle de árvore|Permite categorias ilimitadas<br /><br /> Possibilita o agrupamento e/ou a hierarquia de categorias<br /><br /> Extensível<br /><br /> Exemplo: **Ferramentas > opções**|Hierarquias muito aninhadas podem causar excessiva de rolagem horizontal<br /><br /> O Visual Studio tem um overabundance dos modos de exibição de árvore|  
|Wizard|Auxilia na conclusão de tarefas, guiando pelas etapas sequenciais, baseado em tarefa. O assistente representa uma tarefa de alto nível e painéis individuais representam subtarefas necessárias para realizar a tarefa.<br /><br /> Útil quando a tarefa ultrapassa os limites da interface do usuário, como quando o usuário precisaria usar vários editores e janelas para concluir a tarefa de ferramentas<br /><br /> Útil quando a tarefa requer a ramificação<br /><br /> Útil quando a tarefa contém dependências entre as etapas<br /><br /> Útil quando várias tarefas semelhantes com bifurcação de uma decisão podem ser apresentadas em uma caixa de diálogo para reduzir o número de caixas de diálogo semelhante diferentes.|Apropriado para qualquer tarefa que não requer um fluxo de trabalho sequencial<br /><br /> Os usuários podem se tornar confuso com um assistente com muitas etapas e sobrecarregado<br /><br /> Assistentes inerentemente limitaram espaço na tela|  
  
##### <a name="hallways-or-dashboards"></a>Corredores ou painéis  
 Corredores e painéis são caixas de diálogo ou painéis que servem como iniciar aponta para outras caixas de diálogo e janelas. "Entrada" bem projetada imediatamente revela apenas as mais comuns opções, comandos e configurações, permitindo que o usuário realizar rapidamente tarefas comuns. Como um corredor reais fornece entradas de acesso para acessar as salas por trás delas, aqui a interface de usuário menos comuns é coletado em separado "salas" (geralmente outras caixas de diálogo) de funcionalidades relacionadas que podem ser acessados de entrada principal.  
  
 Como alternativa, uma interface de usuário que oferece toda a funcionalidade disponível em uma única coleção em vez da funcionalidade de menos comuns em locais separados de refatoração é simplesmente um painel.  
  
 ![Conceito do corredor no Outlook](../../extensibility/ux-guidelines/media/0704-08_hallway.png "08_Hallway&0704;")  
  
 **Conceito do corredor para expor a interface de usuário adicional no Outlook**  
  
##### <a name="adaptive-ui"></a>Interface do usuário adaptável  
 Mostrando ou ocultando a interface do usuário com base no uso ou a experiência do usuário automaticamente relatados é outra maneira de apresentar necessário da interface do usuário enquanto oculta a outras partes. Isso não é recomendado no Visual Studio como os algoritmos para decidir quando mostrar ou ocultar a interface do usuário podem ser complicados, e as regras sempre estará incorreta para um conjunto de casos.  
  
##  <a name="a-namebkmkprojectsa-projects"></a><a name="BKMK_Projects"></a>Projetos  
  
### <a name="projects-in-the-solution-explorer"></a>Projetos no Gerenciador de soluções  
 A maioria dos projetos são classificados como base de referência, com base no diretório ou misto. Todos os três tipos de projetos têm suporte simultaneamente no Gerenciador de soluções. A raiz da experiência do usuário ao trabalhar com projetos ocorre dentro desta janela. Embora nós diferentes de projeto são projetos de tipo de modo misto, diretório ou referência, há um padrão comum de interação que deve ser aplicado como um ponto de partida antes divergentes em padrões do usuário específicos do projeto.  
  
 Projetos devem sempre:  
  
-   Suporte a capacidade de adicionar pastas de projeto para organizar o conteúdo do projeto  
  
-   Manter um modelo consistente para persistência de projeto  
  
 Projetos também devem manter modelos de interação consistente para:  
  
-   Removendo itens de projeto  
  
-   Salvando documentos  
  
-   Edição de propriedade do projeto  
  
-   Editar o projeto em um modo de exibição alternativo  
  
-   Operações de arrastar e soltar  
  
### <a name="drag-and-drop-interaction-model"></a>Modelo de interação de arrastar e soltar  
 Projetos normalmente classificam próprios como base de referência (capaz de manter apenas referências a itens de projeto no armazenamento), (capaz de manter somente itens de projeto fisicamente armazenado na hierarquia do projeto), com base no diretório ou misto (capaz de manter referências ou itens físicas). O IDE acomoda todos os três tipos de projetos simultaneamente dentro do **Solution Explorer**.  
  
 De uma perspectiva de arrastar e soltar, as características a seguir devem ser aplicados a cada tipo de projeto dentro do **Solution Explorer**:  
  
-   **Projeto de referência:** o ponto principal é que o projeto está sendo arrastado em torno de uma referência a um item no armazenamento. Quando um projeto baseado em referência atua como uma fonte para uma operação de movimentação, ele só deve remover a referência para o item do projeto. O item, na verdade, não deve ser excluído do disco rígido. Quando um projeto baseado em referência atua como um destino para uma operação de movimentação (ou cópia), ele deve adicionar uma referência para o item de origem original sem fazer uma cópia particular do item.  
  
-   **Projetos baseados em diretório:** do ponto de vista do arrastar e soltar, o projeto está arrastando ao redor do item físico em vez de uma referência. Quando um projeto baseado em diretório atua como uma fonte para uma operação de movimentação, ele deve acabar excluindo o item físico do disco rígido, bem como para removê-la do projeto. Quando um projeto baseado em diretório atua como um destino para uma operação de movimentação (ou cópia), ele deve fazer uma cópia do item de origem no local de destino.  
  
-   **Projeto de destino misto:** do ponto de vista do arrastar e soltar, o comportamento desse tipo de projeto depende da natureza do item que está sendo arrastado (uma referência a um item no armazenamento) ou o próprio item. O comportamento correto para referências e itens físicos estão descritas acima.  
  
 Se houver apenas um tipo de projeto no **Solution Explorer**, operações de arrastar e soltar será simples. Como cada sistema de projeto tem a capacidade de definir seu próprio comportamento de arrastar e soltar, determinadas diretrizes (com base no comportamento de arrastar e soltar do Windows Explorer) devem ser seguidas para garantir uma experiência de usuário mais previsível:  
  
-   Arraste um inalterado operação **Solution Explorer** (quando Ctrl nem teclas Shift mantidos) devem resultar em uma operação de movimentação.  
  
-   A operação de arrastar SHIFT também deve resultar em uma operação de movimentação.  
  
-   A operação de arrastar CTRL deve resultar em uma operação de cópia.  
  
-   Sistemas baseados em referências e mistos projeto oferecem suporte a noção de adicionar um link (ou referência) o item de origem. Quando esses projetos são o destino de uma operação de arrastar e soltar (quando **Ctrl + Shift** for pressionado), ele deve resultar em uma referência para o item que está sendo adicionado ao projeto  
  
 Nem todas as operações de arrastar e soltar são sensatas entre combinações de projetos baseados em referências, com base no diretório e mistos. Em particular, é problemático fingir permitir que uma operação de movimentação entre um projeto com base no diretório de origem e o projeto de referência com base no destino, porque o projeto com base no diretório de origem será preciso excluir o item de origem após a conclusão da mudança. O projeto de referência com base no destino deve terminar com uma referência a um item excluído.  
  
 Também é enganoso fingir permitir que uma operação de cópia entre esses tipos de projetos como o projeto de referência com base no destino não deve fazer uma cópia independente do item de origem. Da mesma forma, Ctrl + Shift ao arrastar a um projeto com base no diretório de destino não permitir como um projeto com base no diretório é possível manter referências. Em casos onde não há suporte para a operação de arrastar e soltar, o IDE deve impedir o descarte e mostrar ao usuário o cursor não soltar (mostrado na tabela ponteiro abaixo).  
  
 Para implementar corretamente o comportamento de arrastar e soltar, o projeto de origem de arrastar precisa se comunicar sua natureza (por exemplo, é baseado em diretório ou referência?) para o projeto de destino. Esta informação é indicada pelo formato de área de transferência é oferecido pela origem. Como a origem de arrastar (ou operação de cópia da área de transferência), um projeto deve oferecer uma **CF_VSREFPROJECTITEM**S ou **CF_VSSTGPROJECTITEMS** respectivamente, dependendo se o projeto é baseado no diretório ou referência. Esses formatos têm o mesmo conteúdo de dados, que é semelhante do Windows **CF_HDROP** Formatar exceto que são listas de cadeias de caracteres, em vez de ser nomes de arquivo, um double -**nulo** encerrada a lista de **Projref** cadeias de caracteres (como retornado pelo **IVsSolution::GetProjrefOfItem** ou **:: GetProjrefOfProject** conforme apropriado).  
  
 Como o destino de soltar (ou operação de colagem da área de transferência), um projeto deve aceitar ambas **CF_VSREFPROJECTITEMS** e **CF_VSSTGPROJECTITEMS**, embora o tratamento exato da operação de arrastar e soltar varia dependendo da natureza do projeto de destino e o projeto de origem. O projeto de origem declara sua natureza, se ele oferece **CF_VSREFPROJECTITEMS** ou **CF_VSSTGPROJECTITEMS**. O destino de soltar compreende sua própria natureza e, portanto, tem informações suficientes para tomar decisões em se a mover, copiar ou link deve ser executado. O usuário também modifica qual operação arrastar-e-soltar deve ser executada ao pressionar o Ctrl, Shift, ou as teclas Ctrl e Shift. É importante para o destino de soltar indicar corretamente qual operação será executada com antecedência no seu **DragEnter** e **DragOver** métodos. O **Solution Explorer** sabe automaticamente se o projeto de origem e o projeto de destino são o mesmo projeto.  
  
 Especificamente, não há suporte para arrastar itens de projeto entre as instâncias do Visual Studio (por exemplo, de uma instância de devenv.exe para outro). O **Solution Explorer** desabilita isso diretamente.  
  
 O usuário deve sempre ser capaz de determinar o efeito de uma operação de arrastar e soltar, selecionando um item, arrastando-a para o local de destino e observando qual dos seguintes ponteiros do mouse aparece antes do item ser solto:  
  
|Ponteiro do mouse|Comando|Descrição|  
|-------------------|-------------|-----------------|  
|!["Sem queda" ícone de mouse](../../extensibility/ux-guidelines/media/0706-01_mousenodrop.png "0706&01;_MouseNoDrop")|Sem queda|Item não pode ser solto no local especificado.|  
|![Ícone de "cópia" de mouse](../../extensibility/ux-guidelines/media/0706-02_mousecopy.png "0706&02;_MouseCopy")|Copiar|Item será copiado para o local de destino.|  
|![Ícone de mouse "Mover"](../../extensibility/ux-guidelines/media/0706-03_mousemove.png "0706&03;_MouseMove")|Mover|Item será movido para o local de destino.|  
|![Ícone de "Adicionar referência" mouse](../../extensibility/ux-guidelines/media/0706-04_mouseaddref.png "0706&04;_MouseAddRef")|Adicionar referência|Uma referência para o item selecionado será adicionada ao local de destino.|  
  
#### <a name="reference-based-projects"></a>Projetos baseados em referências  
 A tabela a seguir resume as operações de arrastar e soltar (bem como Recortar/copiar/colar) que devem ser executadas com base na natureza das chaves de item e o modificador de origem pressionado para projetos de destino referenciado com base:  
  
|||Item de origem: referência/de Link|Item de origem: sistema de item ou arquivo físico (CF_HDROP)|  
|-|-|----------------------------------|-------------------------------------------------------------|  
|Nenhum modificador|Ação|Mover|Link|  
|Nenhum modificador|Destino|Adiciona a referência ao item original|Adiciona a referência ao item original|  
|Nenhum modificador|Origem|Exclusões de referência para o item original|Retém o item original|  
|Nenhum modificador|Resultado|**DROPEFFECT_MOVE** é retornado como a ação de **:: descartar** e item permanece no local original no armazenamento|**DROPEFFECT_LINK** é retornado como a ação de **:: descartar** e item permanece no local original no armazenamento|  
|SHIFT + arrastar|Ação|Mover|Sem queda|  
|SHIFT + arrastar|Destino|Adiciona a referência ao item original|Sem queda|  
|SHIFT + arrastar|Origem|Exclusões de referência para o item original|Sem queda|  
|SHIFT + arrastar|Resultado|**DROPEFFECT_MOVE** é retornado como a ação de **:: descartar** e item permanece no local original no armazenamento|Sem queda|  
|CTRL + arrastar|Ação|Copiar|Sem queda|  
|CTRL + arrastar|Destino|Adiciona a referência ao item original|Sem queda|  
|CTRL + arrastar|Origem|Mantém a referência ao item original|Sem queda|  
|CTRL + arrastar|Resultado|**DROPEFFECT_COPY** é retornado como a ação de **:: descartar** e item permanece no local original no armazenamento|Sem queda|  
|Ctrl + Shift + arrastar|Ação|Link|Link|  
|Ctrl + Shift + arrastar|Destino|Adiciona a referência ao item original|Adiciona a referência ao item original|  
|Ctrl + Shift + arrastar|Origem|Mantém a referência ao item original|Retém o item original|  
|Ctrl + Shift + arrastar|Resultado|**DROPEFFECT_LINK** é retornado como a ação de **:: descartar** e item permanece no local original no armazenamento|**DROPEFFECT_LINK** é retornado como a ação de **:: descartar** e item permanece no local original no armazenamento|  
|Ctrl + Shift + arrastar|Observação|Mesmo que o comportamento de arrastar e soltar para atalhos no Windows Explorer.||  
|Recortar/colar|Ação|Mover|Link|  
|Recortar/colar|Destino|Adiciona a referência ao item original|Adiciona a referência ao item original|  
|Recortar/colar|Origem|Mantém a referência ao item original|Retém o item original|  
|Recortar/colar|Resultado|Item permanece no local original no armazenamento|Item permanece no local original no armazenamento|  
|Copiar/colar|Ação|Copiar|Link|  
|Copiar/colar|Origem|Adiciona a referência ao item original|Adiciona a referência ao item original|  
|Copiar/colar|Resultado|Mantém a referência ao item original|Retém o item original|  
|Copiar/colar|Ação|Item permanece no local original no armazenamento|Item permanece no local original no armazenamento|  
  
#### <a name="directory-based-projects"></a>Projetos baseados em diretório  
 A tabela a seguir resume as operações de arrastar e soltar (bem como Recortar/copiar/colar) que devem ser executadas com base na natureza das chaves de item e o modificador de origem pressionado para projetos baseados em diretório de destino:  
  
|||Item de origem: referência/de Link|Item de origem: sistema de item ou arquivo físico (CF_HDROP)|  
|-|-|----------------------------------|-------------------------------------------------------------|  
|Nenhum modificador|Ação|Mover|Mover|  
|Nenhum modificador|Destino|Item de cópias para o local de destino|Item de cópias para o local de destino|  
|Nenhum modificador|Origem|Exclusões de referência para o item original|Exclusões de referência para o item original|  
|Nenhum modificador|Resultado|**Mover DROPEFFECT_** é retornado como a ação de **:: descartar** e item permanece no local original no armazenamento|**Mover DROPEFFECT_** é retornado como a ação de **:: descartar** e item permanece no local original no armazenamento|  
|SHIFT + arrastar|Ação|Mover|Mover|  
|SHIFT + arrastar|Destino|Item de cópias para o local de destino|Item de cópias para o local de destino|  
|SHIFT + arrastar|Origem|Exclusões de referência para o item original|Exclui o item do local original|  
|SHIFT + arrastar|Resultado|**Mover DROPEFFECT_** é retornado como a ação de **:: descartar** e item permanece no local original no armazenamento|**Mover DROPEFFECT_** é retornado como a ação de **:: descartar** e item permanece no local original no armazenamento|  
|CTRL + arrastar|Ação|Copiar|Copiar|  
|CTRL + arrastar|Destino|Item de cópias para o local de destino|Item de cópias para o local de destino|  
|CTRL + arrastar|Origem|Mantém a referência ao item original|Mantém a referência ao item original|  
|CTRL + arrastar|Resultado|**CÓPIA de DROPEFFECT_** é retornado como a ação de **:: descartar** e item permanece no local original no armazenamento|**CÓPIA de DROPEFFECT_** é retornado como a ação de **:: descartar** e item permanece no local original no armazenamento|  
|Ctrl + Shift + arrastar||Sem queda|Sem queda|  
|Recortar/colar|Ação|Mover|Mover|  
|Recortar/colar|Destino|Item de cópias para o local de destino|Item de cópias para o local de destino|  
|Recortar/colar|Origem|Exclusões de referência para o item original|Exclui o item do local original|  
|Recortar/colar|Resultado|Item permanece no local original no armazenamento|Item é excluído do local original no armazenamento|  
|Copiar/colar|Ação|Copiar|Copiar|  
|Copiar/colar|Destino|Adiciona a referência ao item original|Item de cópias para o local de destino|  
|Copiar/colar|Origem|Retém o item original|Retém o item original|  
|Copiar/colar|Resultado|Item permanece no local original no armazenamento|Item permanece no armazenamento de ins local original|  
  
#### <a name="mixed-target-projects"></a>Projetos de destino misto  
 A tabela a seguir resume as operações de arrastar e soltar (bem como Recortar/copiar/colar) que devem ser executadas com base na natureza das chaves de item e o modificador de origem pressionado para projetos de destino misto:  
  
|||Item de origem: referência/de Link|Item de origem: sistema de item ou arquivo físico (CF_HDROP)|  
|-|-|----------------------------------|-------------------------------------------------------------|  
|Nenhum modificador|Ação|Mover|Mover|  
|Nenhum modificador|Destino|Adiciona a referência ao item original|Item de cópias para o local de destino|  
|Nenhum modificador|Origem|Exclusões de referência para o item original|Exclusões de referência para o item original|  
|Nenhum modificador|Resultado|**Mover DROPEFFECT_** é retornado como a ação de **:: descartar** e item permanece no local original no armazenamento|**Mover DROPEFFECT_** é retornado como a ação de **:: descartar** e o item é excluído do local original no armazenamento|  
|SHIFT + arrastar|Ação|Mover|Mover|  
|SHIFT + arrastar|Destino|Adiciona a referência ao item original|Item de cópias para o local de destino|  
|SHIFT + arrastar|Origem|Exclusões de referência para o item original|Exclui o item do local original|  
|SHIFT + arrastar|Resultado|**Mover DROPEFFECT_** é retornado como a ação de **:: descartar** e item permanece no local original no armazenamento|**Mover DROPEFFECT_** é retornado como a ação de **:: descartar** e o item é excluído do local original no armazenamento|  
|CTRL + arrastar|Ação|Copiar|Copiar|  
|CTRL + arrastar|Destino|Adiciona a referência ao item original|Item de cópias para o local de destino|  
|CTRL + arrastar|Origem|Mantém a referência ao item original|Retém o item original|  
|CTRL + arrastar|Resultado|**CÓPIA de DROPEFFECT_** é retornado como a ação de **:: descartar** e item permanece no local original no armazenamento|**CÓPIA de DROPEFFECT_** é retornado como a ação de **:: descartar** e item permanece no local original no armazenamento|  
|Ctrl + Shift + arrastar|Ação|Link|Link|  
|Ctrl + Shift + arrastar|Destino|Adiciona a referência ao item original|Adiciona a referência ao item de origem original|  
|Ctrl + Shift + arrastar|Origem|Mantém a referência ao item original|Retém o item original|  
|Ctrl + Shift + arrastar|Resultado|**LINK de DROPEFFECT_** é retornado como a ação de **:: descartar** e item permanece no local original no armazenamento|**LINK de DROPEFFECT_** é retornado como a ação de **:: descartar** e item permanece no local original no armazenamento|  
|Recortar/colar|Ação|Mover|Mover|  
|Recortar/colar|Destino|Item de cópias para o local de destino|Item de cópias para o local de destino|  
|Recortar/colar|Origem|Exclusões de referência para o item original|Exclui o item do local original|  
|Recortar/colar|Resultado|Item permanece no local original no armazenamento|Item é excluído do local original no armazenamento|  
|Copiar/colar|Ação|Copiar|Copiar|  
|Copiar/colar|Destino|Adiciona a referência ao item original|Item de cópias para o local de destino|  
|Copiar/colar|Origem|Retém o item original|Retém o item original|  
|Copiar/colar|Resultado|Item permanece no local original no armazenamento|Item permanece no local original no armazenamento|  
  
 Esses detalhes devem ser levados em consideração ao implementar o arrastar para a **Solution Explorer**:  
  
-   Design para vários cenários de seleção.  
  
-   Nomes de arquivo (caminho completo) devem ser exclusivos no projeto de destino ou o descarte não deveria ter permissão.  
  
-   Nomes de pasta devem ser exclusivos (diferencia maiusculas de minúsculas) no nível do qual eles são descartados.  
  
-   Há diferenças de comportamento entre os arquivos que são abertas ou fechadas em tempo de arrastar (não mencionada nos cenários acima).  
  
-   Arquivos de nível superior se comportam de forma um pouco diferente do que os arquivos em pastas.  
  
 Outro problema que deve estar atento é como lidar com operações de movimentação de itens que têm editores ou abrir designers. O comportamento esperado é da seguinte maneira (isso se aplica a todos os tipos de projeto):  
  
1.  Se abrir editor/designer não tem alterações não salvas, em seguida, a janela editor/designer deve ser silenciosamente fechada.  
  
2.  Se abrir editor/designer tem alterações não salvas, a origem de arrastar deve esperar para a operação de soltar ocorrer e, em seguida, peça ao usuário para salvar as alterações não confirmadas em documentos abertos antes de fechar a janela com um aviso semelhante ao seguinte:  
  
    ```  
    ==========================================================   
         One or more open documents have unsaved changes.  
    Do you want to save uncommitted changes before proceeding?   
                      [Yes]  [No]  [Cancel]   
    ==========================================================  
    ```  
  
 Isso dá ao usuário a oportunidade de salvar o trabalho em andamento antes do destino torna suas cópias. Um novo método **IVsHierarchyDropDataSource2::OnBeforeDropNotify** foi adicionado para habilitar esse tratamento.  
  
 O destino, em seguida, copiar o estado do item como no armazenamento (não incluindo as alterações não salvas no editor, se o usuário escolher **não**). Depois que o destino concluiu sua cópia (em **IVsHierarchyDropDataSource::Drop**), a fonte tem a oportunidade para concluir a parte de exclusão da operação de movimentação (em **IVsHierarchyDropDataSource::OnDropNotify**).  
  
 Qualquer editores com alterações não salvas deverá ser deixados abertos. Para esses documentos com alterações não salvas, isso significa que a parte de cópia da operação de movimentação será executada, mas a parte de exclusão será anulada. Em um cenário de seleção de vários quando o usuário escolhe **não**, esses documentos com alterações não salvas não devem ser fechados ou removidos, mas aqueles sem alterações não salvas devem ser fechados e removidos.
