---
title: "In&#237;cio R&#225;pido: an&#225;lise de c&#243;digo para C/C++ | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "análise de código C/C++"
  - "análise de código, C/C++"
ms.assetid: 6110b8ba-0af6-4acd-b1ba-bb0551f90e44
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# In&#237;cio R&#225;pido: an&#225;lise de c&#243;digo para C/C++
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Você pode melhorar a qualidade do seu aplicativo ao executar a análise de código regularmente em código C ou C\+\+.  Isso pode ajudá\-lo a localizar problemas comuns de violações de boa prática de programação ou defeitos são difíceis de serem descobertas por meio de testes.  Avisos da análise de código diferem de avisos e erros do compilador porque a análise de código procura por padrões de código específicos que são válidos, mas ainda podem criar problemas para você ou outras pessoas que usam seu código.  
  
## Neste tópico  
  
-   [Configurar conjuntos de regras para um projeto](../code-quality/quick-start-code-analysis-for-c-cpp.md#BKMK_ConfigureRuleSets)  
  
-   [Executar análise de código](../code-quality/quick-start-code-analysis-for-c-cpp.md#BKMK_Run)  
  
-   [Analisar e resolver avisos da análise de código](../code-quality/quick-start-code-analysis-for-c-cpp.md#BKMK_Analyze)  
  
-   [Suprimindo avisos da análise de código](../code-quality/quick-start-code-analysis-for-c-cpp.md#BKMK_Suppress)  
  
-   [Criando itens de trabalho para o código avisos de análise](../code-quality/quick-start-code-analysis-for-c-cpp.md#BKMK_Creating_work_items_for_code_analysis_warnings)  
  
-   [Pesquisando e filtrando resultados da análise de código](../code-quality/quick-start-code-analysis-for-c-cpp.md#BKMK_Search)  
  
##  <a name="BKMK_ConfigureRuleSets"></a> Configurar conjuntos de regras para um projeto  
  
1.  Em **Solution Explorer**, abra o menu de atalho para o nome do projeto e escolha **propriedades**.  
  
2.  As etapas a seguir são opcionais:  
  
    1.  No **configuração** e **plataforma** listas, escolha a plataforma de destino e a configuração de compilação.  
  
    2.  Por padrão, a análise de código não relata avisos do código que é gerado automaticamente por ferramentas externas.  Para exibir avisos do código gerado, desmarque o **Suprimir resultados do código gerado** caixa de seleção.  
  
        > [!NOTE]
        >  Essa opção não suprime erros de análise de código e avisos do código gerado quando os erros e avisos são exibidos em formulários e modelos.  Você pode exibir e manter o código\-fonte para um formulário ou um modelo.  
  
3.  Para executar análise de código sempre que o projeto é compilado usando a configuração selecionada, selecione o **habilitar análise de código para C\/C\+\+ na compilação** caixa de seleção.  Você também pode executar a análise de código manualmente abrindo o **Analisar** menu e, em seguida, escolhendo **Executar análise de código na** *ProjectName*.  
  
4.  No **executar esse conjunto de regras** lista, siga um destes procedimentos:  
  
    -   Escolha o conjunto de regras que você deseja usar.  
  
    -   Escolha **\< Browse... \>** especificar uma regra personalizada existente definido que não está na lista.  
  
    -   Defina um conjunto de regras personalizadas.  
  
         Para obter mais informações, consulte [Criando conjuntos de regras personalizados](../code-quality/creating-custom-code-analysis-rule-sets.md).  
  
### Conjuntos de regra padrão C\/C\+\+  
 O Visual Studio inclui dois conjuntos de regras para código nativo padrão:  
  
|Conjunto de Regras|Descrição|  
|------------------------|---------------|  
|Nativo do Microsoft mínimo recomendado de regras|Esse conjunto de regras enfoca os problemas mais críticos no seu código nativo, incluindo possíveis falhas de segurança e falhas do aplicativo.  Você deve incluir esse conjunto de regras em qualquer conjunto de regras personalizado que criar para seus projetos nativos.|  
|Regras Nativas Recomendadas da Microsoft|Esse conjunto de regras abrange uma ampla gama de problemas.  Ele inclui todas as regras no Microsoft Native mínimo recomendado regras.|  
  
##  <a name="BKMK_Run"></a> Executar análise de código  
 Na página de análise de código das páginas de propriedades do projeto, você pode configurar a análise de código para ser executado sempre que você compilar seu projeto.  Você também pode executar a análise de código manualmente.  
  
 Para executar análise de código em uma solução:  
  
-   Sobre o **criar** menu, escolha **Executar análise de código na solução**.  
  
 Para executar análise de código em um projeto:  
  
-   No Solution Explorer, escolha o nome do projeto.  
  
-   Sobre o **criar** menu, escolha **Executar análise de código na** *nome do projeto*.  
  
 A solução ou projeto é compilada e análise de código é executado.  Resultados aparecem na janela de análise de código.  
  
##  <a name="BKMK_Analyze"></a> Analisar e resolver avisos da análise de código  
 Para analisar um aviso específico, escolha o título do aviso na janela análise de código.  O aviso se expande para exibir informações adicionais sobre o problema.  Quando possível, análise de código exibe os números de linha e a lógica de análise que levou ao aviso.  Para obter informações detalhadas sobre o aviso, incluindo soluções possíveis para o problema, escolha a identificação de aviso para exibir o tópico da Ajuda na biblioteca de MSND para a mensagem.  
  
 Quando você expande um aviso, a linha de código que causou o aviso é realçada no editor de código do Visual Studio.  
  
 Depois de entender o problema, você pode resolvê\-lo em seu código.  Em seguida, execute novamente a análise de código para certificar\-se de que o aviso não aparece mais na janela análise de código e que a correção não gerou novos avisos.  
  
> [!TIP]
>  Você pode executar novamente a análise de código na janela de análise de código.  Escolha o **Analisar** botão e escolha o escopo da análise.  Você pode executar novamente a análise na solução inteira ou em um projeto selecionado.  
  
##  <a name="BKMK_Suppress"></a> Suprimindo avisos da análise de código  
 Há momentos em que você pode decidir não corrigir um aviso de análise de código.  Você pode decidir que resolver o aviso exige recodificação demais a probabilidade de que o problema ocorrerá em qualquer implementação real do seu código.  Ou você pode achar que a análise é usada no aviso é inadequada nesse contexto específico.  Você pode suprimir avisos individuais para que eles não aparecem mais na janela análise de código.  
  
 Para suprimir um aviso:  
  
1.  Se as informações detalhadas não for exibidas, escolha o título do aviso para expandi\-la.  
  
2.  Escolha o **ações** link na parte inferior do aviso.  
  
3.  Escolha **suprimir mensagem** e, em seguida, escolha **na origem**.  
  
 Suprimir uma mensagem insere `#pragma warning (disable:`*ID do aviso*`)` que suprime o aviso para a linha de código.  
  
##  <a name="BKMK_Creating_work_items_for_code_analysis_warnings"></a> Criando itens de trabalho para o código avisos de análise  
 Você pode usar o recurso de rastreamento de item de trabalho para registrar bugs do Visual Studio.  Para usar esse recurso, você deve se conectar a uma instância do Team Foundation Server.  
  
 **Para criar um item de trabalho para um ou mais avisos de código C\/C\+\+**  
  
1.  Na janela de análise de código, expanda e selecione os avisos  
  
2.  No menu de atalho para os avisos, escolha **Criar Item de trabalho**, e, em seguida, escolha o tipo de item de trabalho.  
  
3.  Visual Studio cria um único item de trabalho para os avisos selecionados e exibe o item de trabalho em uma janela de documento do IDE.  
  
4.  Adicione qualquer informação adicional e, em seguida, escolha **Salvar Item de trabalho**.  
  
##  <a name="BKMK_Search"></a> Pesquisando e filtrando resultados da análise de código  
 Você pode pesquisar listas longas de mensagens de aviso e você pode filtrar avisos em soluções multiprojeto.  
  
1.  **Para filtrar avisos por título ou identificação de aviso**: insira a palavra\-chave no **filtro** caixa de texto.  
  
2.  **Para filtrar avisos pelo projeto**: em uma solução multiprojeto, escolha um ou mais projetos na lista na parte superior direita da janela de análise de código.  Escolha o nome da solução para exibir todos os avisos.  
  
3.  **Para filtrar avisos por severidade**: por padrão, mensagens de análise de código são atribuídas a severidade **Aviso**.  Você pode atribuir a gravidade de uma ou mais mensagens como **erro** em uma regra personalizada definida.  Escolha **Aviso** ou **erro** para exibir apenas as mensagens que são atribuídas a severidade respectiva.  Escolha **todas as** para exibir todas as mensagens.