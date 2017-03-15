---
title: "Graph View | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 5881afde-3f24-4eb9-bff8-6cb3fc8aade7
caps.latest.revision: 3
caps.handback.revision: 3
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Graph View
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

A exibição do gráfico fornece uma representação gráfica de nós globais do esquema e relações entre os nós.  Observe que a exibição do gráfico não permite que você alterar o layout do esquema definido na superfície de design.  A exibição do gráfico também inclui a barra de ferramentas do designer de esquema XML e a barra de rastreamento.  
  
 A imagem a seguir mostra a visualização de gráfico com seis nós globais na superfície de design.  
  
 ![XML Schema Designer Graph View](../xml-tools/media/xsddesigner_graphview.gif "XSDDesigner\_GraphView")  
  
## A superfície de design  
 A superfície de design do modo de gráfico exibe o conteúdo de [O espaço de trabalho do designer de esquema XML](../xml-tools/xml-schema-designer-workspace.md).  Se o espaço de trabalho contém quaisquer nós globais do conjunto de esquema, os nós são mostrados na superfície de design do modo de gráfico e as setas são desenhadas entre os nós que possuem relações.  
  
 Clique duas vezes em um nó no modo de gráfico trará anterior o editor XML.  
  
 Para excluir selecionou nós de espaço de trabalho, usa a barra de ferramentas do designer XSD ou a tecla DELETE.  
  
 Se a superfície de design está em branco, o editor XML, XML Schema Explorer, e a marca de agua são mostrados.  *A marca de agua* é uma lista de links para todas as exibições de designer XSD.  
  
 ![XSD Designer; Graph View](../xml-tools/media/xsdgraphviewwatermark.gif "XSDGraphViewWatermark")  
  
 Se o esquema tem erros, o seguinte texto é exibido no fim da lista: “Use Lista de erros para exibir e corrigir erros no conjunto.”  
  
## Barra de rastreamento  
 A barra de rastreamento na parte inferior do modo de figura a seguir mostra onde o nó selecionado é localizado no conjunto de esquema.  Se vários itens são selecionados, a barra de rastreamento será em branco.  
  
## O menu de contexto  
 A tabela a seguir descreve as opções que estão disponíveis para todos os nós na superfície de design do modo de gráfico.  
  
|Opção|Descrição|  
|-----------|---------------|  
|**Apresentação em XML Schema Explorer**|Coloca o foco no esquema Explorer e ressalta o nó do esquema.|  
|**Apresentação no modo de gráfico**|Alterna para o modo de exibição gráfico \(desativada\).|  
|**Gerencia o exemplo XML**|Disponível somente para os elementos globais.  Gerencia um arquivo XML de exemplo para o elemento global.|  
|**O espaço de trabalho claro**|Limpa o espaço de trabalho e a superfície de design.|  
|**Remova de espaço de trabalho**|Removes selecionou nós de espaço de trabalho e da superfície de design.|  
|**Remova todos com exceção de seleção de espaço de trabalho**|Remove os nós que não são selecionados de espaço de trabalho e da superfície de design.|  
|**Diagrama de exportação como a imagem…**|Salva a superfície de design para um arquivo XPS.|  
|**Selecionar Tudo**|Selecionar todos os nós na superfície de design.|  
|**Código de exibição**|Abre o arquivo que contém o nó selecionado no editor XML.  O item selecionado em XML Schema Explorer também será selecionado no editor XML.|  
|**Janela Propriedades**|Abre a janela de **Propriedades** \(se não estiver aberta\).  Esta janela exibe informações sobre o nó.|  
  
 Além das opções comuns descritas anterior, o menu de contexto para elementos globais também tem as seguintes opções:  
  
|Opção|Descrição|  
|-----------|---------------|  
|**Adicionar Definição de Tipo**|Adiciona o tipo base no diagrama.|  
|**Adicionar Todas as Referências**|Adiciona todos os nós que se referem ao elemento e desenha setas para indicar relações entre eles.|  
|**Adicionar Membros do Grupo de Substituição**|Adiciona todos os membros do grupo de substituição.  Essa opção aparece na exibição se o elemento é o início ou membro de um grupo de substituição.|  
|**Gerencia o exemplo XML**|Gerencia um arquivo XML de exemplo para o elemento global.|  
  
 Além das opções comuns descritas anterior, o menu de contexto para tipos complexos simples e globais globais também tem as seguintes opções:  
  
|Opção|Descrição|  
|-----------|---------------|  
|**Adicione o tipo base**|Se o tipo selecionado é derivado de um tipo global, adiciona o tipo base do tipo selecionado.|  
|**Adicionar Todas as Referências**|Adiciona todas as referências de tipo selecionado.  Isso inclui os elementos e atributos do tipo selecionado, e tipos derivados do tipo selecionado.|  
|**Adicionar Todos os Tipos Derivados**|Adiciona todos os tipos que direta e indiretamente são derivados do tipo selecionado.|  
|**Adicionar Todos os Ancestrais**|Adiciona todos os tipos de base pai \(\).|  
  
 Além das opções comuns descritas anterior, o menu de contexto para grupos globais e grupos de atributo também tem as seguintes opções:  
  
|Opção|Descrição|  
|-----------|---------------|  
|**Adicionar Todas as Referências**|Adiciona todos os nós que se referem ao grupo e desenha setas para indicar relações entre eles.|  
|**Adicionar Todos os Membros**|Adiciona todos os membros do grupo e desenha setas para indicar relações entre eles.|  
  
 No addtion em padrões comuns descritas anterior, o menu de contexto para atributos globais também tem as seguintes opções:  
  
|Opção|Descrição|  
|-----------|---------------|  
|**Adicionar Todas as Referências**|Adiciona todos os nós que se referem ao grupo e desenha setas para indicar relações entre eles.|  
  
## Janela Propriedades  
 Use o menu de contexto para abrir inicialmente a janela de **Propriedades** .  Por padrão, a janela de **Propriedades** aparece no canto inferior direito do Visual Studio.  Quando você clica em um nó que é processado no modo do modelo de conteúdo, as propriedades do nó serão exibidas na janela de **Propriedades** .  
  
## Barra de ferramentas XSD  
 Os seguintes botões da barra de ferramentas XSD são ativados quando a exibição do gráfico está ativo.  
  
 ![XML Schema Designer Toolbar](../xml-tools/media/xsdgraphviewtoolbar.gif "XSDGraphViewToolbar")  
  
|Opção|Descrição|  
|-----------|---------------|  
|**Mostrar Exibição Inicial**|Alterna a [O modo de Início](../xml-tools/start-view.md).  Esta exibição pode ser acessada usando o atalho de teclado: **CTRL \+ 1**.|  
|**Mostrar Exibição de Modelo de Conteúdo**|Alterna a [O modo do modelo de conteúdo](../xml-tools/content-model-view.md).  Esta exibição pode ser acessada usando o atalho de teclado: **CTRL \+ 2**.|  
|**Mostrar Exibição de Gráfico**|Alterna a [O modo de gráfico](../xml-tools/graph-view.md).  Esta exibição pode ser acessada usando o atalho de teclado: **CTRL \+ 3**.|  
|**O espaço de trabalho claro**|Limpa o espaço de trabalho e a superfície de design.|  
|**Remova de espaço de trabalho**|Removes selecionou nós de espaço de trabalho e serface de design.|  
|**Remova todos com exceção de seleção de espaço de trabalho**|Remove os nós que não são selecionados de espaço de trabalho e serface de design.  Essa opção é ativada no modo do modelo de conteúdo e no modo de gráfico.|  
|**Da Esquerda para a Direita**|Altera o layout no modo de gráfico a uma representação hierárquica esquerda para a direita de nós.  Essa opção pode ser acessada usando o atalho de teclado: **Alt \+ seta para a direita**.|  
|**Da Direita para a Esquerda**|Altera o layout no modo de gráfico a uma representação hierárquica da direita para a esquerda de nós.  Essa opção pode ser acessada usando o atalho de teclado: **Alt \+ seta para a esquerda**.|  
|**De Cima para Baixo**|Altera o layout no modo de gráfico a uma representação hierárquica de cima para baixo de nós.  Essa opção pode ser acessada usando o atalho de teclado: **Alt \+ seta para baixo**.|  
|**De Baixo para Cima**|Altera o layout no modo de gráfico a uma representação hierárquica de parte inferior\-à\- parte superior dos nós.  Essa opção pode ser acessada usando o atalho de teclado: **Alt \+ seta para cima**.|  
  
## Bandeja\/rolagem  
 Você pode filtrar a superfície de design usando barras de rolagem ou mantendo a tecla CTRL quando você clique e arraste o mouse.  Quando você filtra a superfície de design usando o clique e o arrastar, o cursor será alterado a quatro setas cruzadas apontando em quatro direções.  
  
## Desfazer\/refazer  
 Desfazer\/refaz o recurso é habilitado no modo de gráfico para as seguintes ações:  
  
-   Adicionando um único nó arrastando e soltando\-se.  
  
-   Adicionando mais nós da janela de resultados de pesquisa no esquema Explorer ou em consultas de exibição de Início.  
  
-   Excluindo única ou mais nós.  
  
## Aplicar Zoom  
 O zoom está disponível no canto inferior direito do modo de gráfico.  
  
 O zoom pode ser controlado das seguintes maneiras:  
  
-   Mantendo a tecla CTRL e girar o mouse rode quando o mouse está sobre a superfície de exibição de gráfico.  
  
-   Usando o controle deslizante.  O controle deslizante mostra o nível atual de zoom.  
  
 O controle deslizante de zoom é opaco ao selecionar, o passa sobre ele, ou utiliza o CTRL com a roda do mouse para aplicar zoom; em quaisquer outros vezes, é transparente.  
  
## Integração de editor XML  
 Você pode alternar para frente e para trás entre o modo de gráfico e o editor XML clicando em um nó e usando o menu de contexto de código de exibição.  
  
 Se você alterar o esquema definido no editor XML, as alterações serão sincronizadas no modo de gráfico.  Para obter mais informações, consulte [Integration with XML Editor](../xml-tools/integration-with-xml-editor.md).  
  
## Consulte também  
 [A superfície de design](../xml-tools/xml-schema-designer-workspace.md)