---
title: "Context Menus (XML Schema Explorer) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 42ab17ca-b8c1-40d7-beda-d033f66fe874
caps.latest.revision: 2
caps.handback.revision: 2
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Context Menus (XML Schema Explorer)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Os seguintes itens de menu de contexto são usados para executar pesquisas esquema\- específicas e outras operações.  
  
## Tipo de nó: Conjunto de esquema  
 A tabela a seguir descreve as opções que estão disponíveis para um nó do esquema.  
  
|Opção|Descrição|  
|-----------|---------------|  
|**Elementos de raiz mais provável de apresentação**|Localiza e realça todos os elementos globais não são referenciados de elementos globais diferentes de se.|  
|**Tipos globais de apresentação**|Os localiza e realça todos globais no conjunto de esquema.|  
|**Elementos globais de apresentação**|Localiza e realces todos elementos globais no conjunto de esquema.|  
|**Janela Propriedades**|Abre a janela de **Propriedades** \(se não estiver aberta\).  Esta janela exibe informações sobre o nó.|  
  
## Tipo de nó: Namespace  
 A tabela a seguir descreve as opções que estão disponíveis para um nó de namespace.  
  
|Opção|Descrição|  
|-----------|---------------|  
|**Mostrar todas as referências de entrada**|Localiza e ressalta os arquivos que importar o namespace selecionada.|  
|**Mostrar todas as referências de saída**|Para cada arquivo no namespace selecionado, localiza e ressalta o seguinte:<br /><br /> -   Quaisquer espaços para nome referenciados em instruções de importação sem um atributo de `schemaLocation` .<br />-   Todos os arquivos nos namespaces diferentes de selecionada que são especificados no atributo de `schemaLocation` na importação e incluem instruções.|  
|**Tipos globais de apresentação**|Os localiza e realça todos globais no namespace selecionada.|  
|**Elementos globais de apresentação**|Localiza e realces todos elementos globais no namespace selecionado.|  
|**Janela Propriedades**|Abre a janela de **Propriedades** \(se não estiver aberta\).  Esta janela exibe informações sobre o nó.|  
  
## Tipo de nó: Arquivo  
 A tabela a seguir descreve as opções que estão disponíveis para um nó de arquivo.  
  
|Opção|Descrição|  
|-----------|---------------|  
|**Mostrar todas as referências de entrada**|Localiza e realça todos os arquivos que especificam o arquivo selecionado em atributos de `schemaLocation` do incluem e importar instruções.|  
|**Mostrar todas as referências de saída**|Localiza e realces o seguinte:<br /><br /> -   Quaisquer namespaces especificados em atributos de namespace de quaisquer declarações de importação que não têm o atributo de `schemaLocation` .<br />-   Todos os arquivos especificados nos atributos de `schemaLocation` de qualquer importação e incluem instruções.|  
|**Tipos globais de apresentação**|Os localiza e realça todos globais neste arquivo.|  
|**Elementos globais de apresentação**|Os localiza e realça todos os elementos globais neste arquivo.|  
|**Código de exibição**|Abre o arquivo que contém o nó selecionado no editor XML.  O item selecionado em XML Schema Explorer também será selecionado no editor XML.|  
|**Janela Propriedades**|Abre a janela de **Propriedades** \(se não estiver aberta\).  Esta janela exibe informações sobre o nó.|  
  
## Todos os tipos de nós globais  
 A tabela a seguir descreve as opções que estão disponíveis para todos os nós globais.  
  
|Opção|Descrição|  
|-----------|---------------|  
|**Apresentação no modo de gráfico**|Abre a exibição do gráfico.  Se o nó selecionado não está no espaço de trabalho, adicione\-o ao espaço de trabalho e selecione o nó.|  
|**Apresentação no modo do modelo de conteúdo**|Abre a exibição do modelo de conteúdo.  Se o nó selecionado não está no espaço de trabalho, adicione\-o ao espaço de trabalho e selecione o nó.|  
|**Código de exibição**|Abre o arquivo que contém o nó selecionado no editor XML.  O item selecionado em XML Schema Explorer também será selecionado no editor XML.|  
|**Janela Propriedades**|Abre a janela de **Propriedades** \(se não estiver aberta\).  Esta janela exibe informações sobre o nó.|  
  
## Tipo de nó: Elemento  
 Além das opções do nó globais descritos acima, o menu de contexto para nós do elemento tem as seguintes opções:  
  
|Opção|Descrição|  
|-----------|---------------|  
|**Vá para a definição de tipo**|Navega para a definição de tipo do elemento selecionado.  Isso é aplicável quando o tipo que é usado para o elemento é um tipo global.|  
|**Vá para o elemento original**|Para referências de elemento, navega para a definição real do elemento.|  
|**Mostrar todas as referências**|Para elementos globais, localiza e realça todas as referências \(elementos que têm `ref="selectedElement"`\) ao elemento selecionado.|  
|**Membros de apresentação do grupo de substituição**|Para os cabeçotes de um grupo de substituição, localiza e realça todos os elementos que são membros do grupo de substituição de que o elemento selecionado é um membro.  Isso mostra participantes diretos e indiretos.|  
|**Chefes de grupo de substituição de apresentação**|Para elementos globais que são membros de um grupo de substituição, localiza e ressalta os cabeçotes qualquer diretos e indiretos para o elemento selecionado, como o seguinte:<br /><br /> -   Um chefe de grupo de substituição especificado no elemento selecionado.<br />-   Um chefe de grupo de substituição especificado no elemento principal.|  
|**Gerencia o exemplo XML**|Disponível somente para os elementos globais.  Gerencia um arquivo XML de exemplo para o elemento global.|  
  
## Tipo de nó: Tipos globais  
 Além das opções do nó globais descritos acima, o menu de contexto para nós globais do tipo tem as seguintes opções:  
  
|Opção|Descrição|  
|-----------|---------------|  
|**Tipo base de apresentação**|Se o tipo selecionado é derivado de um tipo global, navega para o tipo de base do tipo selecionado.|  
|**Mostrar todas as referências**|Localiza e realces todas as referências para o tipo selecionado.  Isso inclui os elementos e atributos de tipo e tipos derivados selecionados do tipo selecionado.|  
|**Mostrar todos os tipos derivados**|Localiza e realça todos os tipos que direta e indiretamente são derivados do tipo selecionado.|  
|**Mostrar todos os predecessores**|Mostrar todos os tipos de base pai \(\).|  
  
## Tipo de nó: Atributo  
 Além das opções do nó globais descritos acima, o menu de contexto para nós de atributo tem as seguintes opções:  
  
|Opção|Descrição|  
|-----------|---------------|  
|**Vá para a definição de tipo**|Quando o tipo que é usado para o atributo é um tipo global, navega para a definição de tipo do atributo selecionado.|  
|**Vá para o atributo original**|Para referências de atributo, navega para a definição real do atributo.|  
|**Mostrar todas as referências**|Para atributos globais, localiza e realça todas as referências \(outros atributos que têm `ref="selectedAttribute"`\) para o atributo selecionado.|  
  
## Tipo de nó: Grupo de atributo  
 Além das opções do nó globais descritos acima, o menu de contexto para nós do grupo de atributo tem as seguintes opções:  
  
|Opção|Descrição|  
|-----------|---------------|  
|**Ir para definição**|Para referências, navega para a definição real do atributo.|  
|**Mostrar todos os membros**|Localiza e realces todos os membros do grupo de atributo.|  
|**Mostrar todas as referências**|Localiza e realça todas as referências \(grupos de atributo que têm `ref="selectedAttributeGroup"`\) para o grupo selecionado de atributo.|  
  
## Tipo de nó: Grupo nomeado  
 Além das opções do nó globais descritos acima, o menu de contexto para nós nome de grupo tem as seguintes opções:  
  
|Opção|Descrição|  
|-----------|---------------|  
|**Ir para definição**|Para referências, navega para a definição real do atributo.|  
|**Mostrar todos os membros**|Localiza e realces todos os membros do grupo chamado.|  
|**Mostrar todas as referências**|Localiza e realça todas as referências \(grupos que têm `ref="selectedGroup"`\) para o grupo selecionado.|  
  
## Consulte também  
 [XML Schema Explorer](../xml-tools/xml-schema-explorer.md)   
 [Searching the Schema Set](../xml-tools/searching-the-schema-set.md)