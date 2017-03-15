---
title: "Walkthrough: XSLT Profiler | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 87387c9a-2e89-4801-ad51-83740cd6ea25
caps.latest.revision: 2
caps.handback.revision: 2
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Walkthrough: XSLT Profiler
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

O profiler XSLT criar relatórios de desempenho detalhados XSLT que a medida da ajuda, avalia, e problemas de desempenho relacionados de destino no código XSLT.  O profiler XSLT inclui dicas úteis para XSL e otimizações de folha de estilos XSLT.  Para aplicativos que requerem XSLT máximo desempenho, essa ferramenta pode ser essencial.  
  
## Pré-requisitos  
 O seguinte explicação passo a passo requer a versão 4,0 do Visual Studio 2010 and.NET Framework.  O profiler XSLT só está disponível com a equipe do Microsoft Visual Studio o sistema com Ferramentas de design de Perfil instalado.  
  
### Crie o relatório de desempenho  
  
1.  Abrir um documento XSLT no Visual Studio.  
  
2.  Clique na opção de **Perfil XSLT** que está disponível no menu XML.  
  
3.  Fornecer um documento XML de entrada.  Se um documento XML ele já não estiver aberto, você será solicitado para o arquivo.  
  
4.  Inicia a análise, e uma barra de progresso exibem o progresso no editor.  
  
5.  A saída XSLT são visíveis no painel de saída.  
  
6.  Após extremidades de uma sessão de desempenho, verifique o relatório de desempenho.  Os dados salvos em um relatório de desempenho permitem que você exiba e analisar o desempenho XSLT.  
  
### Obter todos os modos disponíveis  
  
1.  Clique na lista suspensa de **Modo de exibição atual** para obter todos os modos disponíveis.  
  
2.  Selecione a opção de **Exibição de Resumo** na lista suspensa de **Modo de exibição atual** .  Por padrão, um relatório de desempenho é exibido em **Exibição de Resumo**.  Esta exibição é um ponto de partida para determinar problemas de desempenho com documentos XSLT.  **Exibição de Resumo** Lista os seguintes pontos de dados:  
  
    -   A maioria chamaram funções  
  
    -   Funções com a maioria de trabalho individual  
  
    -   Funções que usam o tempo os mais longa de executar  
  
3.  Por padrão, há três colunas para cada ponto de dados: o nome da função, o número de chamadas o valor absoluto, e um valor percentual de função chamado para chamadas de função total.  De cada ponto de dados em **Exibição de Resumo**, você pode navegar em uma exibição mais detalhadas clique com o botão direito do mouse nos pontos de dados de função.  
  
4.  Selecione a opção de **O modo de função** na lista suspensa de **Modo de exibição atual** .  Funções de listas de **O modo de função** chamadas durante a análise.  Você pode classificar os dados em um nome de coluna.  As colunas exibidas por padrão são:  
  
    -   **Nome de função**  
  
    -   **Tempo incluindo decorridos**  
  
    -   **Tempo exclusivos decorridos**  
  
    -   **Tempo do aplicativo incluindo**  
  
    -   **Tempo exclusivos do aplicativo**  
  
    -   **Número de chamadas**  
  
5.  Todas as colunas de tempo são exibidas em valores absolutos e em porcentagens.  O termo **Exclusivo** refere\-se ao momento que total executar gasta desacelerando função exclusivo de tempo passou por outras funções chamado durante a execução desta função.  
  
6.  O termo **Inclusivo** refere\-se ao tempo total para executar gasta desacelerando função, incluindo tempo de execução das funções que chamou e se qualquer uma das funções chamados chamaram outras funções.  
  
### O modo de seleção do chamador\/receptor  
  
1.  Selecione o modo de **Chamador\/receptor** na lista suspensa de **Modo de exibição atual** .  
  
2.  O modo de **Chamador\/receptor** tem as seguintes três partes distintas:  
  
    -   **Funções que chamaram**: Todas as funções que chamaram uma função particular são listadas na parte superior de exibição.  
  
    -   **Função atual**: A função específico que foi chamada é listada na parte média de exibição.  
  
    -   **Funções que foram chamados por**: Todas as funções que foram chamadas pela função particular são listadas na parte de fundo de exibição.  
  
3.  Se uma função chamada `SyncToNavigator` aparece na parte média de exibição, todas as funções que chamaram a função de `SyncToNavigator` aparecem na parte superior de exibição, e em todas as funções que foram chamados por `SyncToNavigator` aparecem na parte de fundo de exibição.  
  
4.  Você pode alterar a função na parte média de exibição clicando duas vezes em algumas das funções listadas em duas outras partes de exibição.  A exibição é atualizado para refletir automaticamente as alterações.  
  
5.  Você também pode classificar os dados clicando em nomes de coluna.  
  
### Selecione o modo de CallTree  
  
1.  **Modo de exibição de árvore de chamada** Selecione na lista suspensa de **Modo de exibição atual** .  Esta exibição é um modo de exibição de árvore de execução do programa.  
  
2.  **Modo de exibição de árvore de chamada** Mostra a raiz da árvore como o nome do processo.  As funções são os nós de árvore.  Esta exibição permite que você fure em rastreamentos específicos de chamada e analise que os rastreamentos têm o maior impacto de desempenho.  A exibição é semelhante a **Modo a pilha de chamadas** disponíveis durante a depuração.  Além das colunas em **O modo de função**, em **Modo de exibição de árvore de chamada**, há uma coluna extra para exibir **Nome do Módulo**.  
  
3.  **Marcas** Selecione na lista suspensa de **Modo de exibição atual** .  
  
4.  Com o profiler de SLT, há marcas que aparece no fluxo da coleção de dados com um comentário associado.  As marcas são locais no código que têm contadores.  Quando você indica que o profiler XSLT para coletar contadores de desempenho XSLT, os contadores obtém como cada vez que uma dessas marcas é executado.  Os dados são exibidos em uma tabela que contém **Identificação de marca**, **Nome de marca** \(**Iniciar Programa**, **Finalizar programa**\), e **Carimbo de Data\/Hora**.  As marcas não são agregadas e não aparecem em ordem cronológica em **Marcas de exibição** de relatório de desempenho.  
  
### Módulos selecionados na exibição atual  
  
1.  **Módulos** Selecione na lista suspensa de **Modo de exibição atual** .  
  
2.  Exibição de módulos é uma lista plana das funções agregadas para o nível de módulo.  Expandir ou recolher o nome do módulo para exibir ou fechar a exibição de dados de desempenho do módulo.  Você pode classificar os dados em um nome de coluna.  Por padrão, há valores absolutos e um números de porcentagem para **Tempo incluindo decorridos**, **Tempo exclusivos decorridos**, **Tempo do aplicativo incluindo**, **Tempo exclusivos do aplicativo**, e **Número de chamadas**.  
  
3.  **Processo** Selecione na lista suspensa de **Modo de exibição atual** .  
  
4.  A exibição do processo exibe uma tabela que inclui **Identificação do Processo**, **Nome do Processo**, **Inicie tempo**, e **Hora de Término**.  Os dados podem ser classificados clicando em nomes de coluna.  
  
## Consulte também  
 [Walkthrough: Using XSLT Hierarchy](../xml-tools/walkthrough-using-xslt-hierarchy.md)