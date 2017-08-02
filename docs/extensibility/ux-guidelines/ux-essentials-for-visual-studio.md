---
title: "Conceitos básicos UX para o Visual Studio | Microsoft Docs"
ms.custom: 
ms.date: 04/26/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a793cf7a-f230-43ce-88d0-fa5d6f1aa9c7
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
ms.openlocfilehash: 19db4e41ef35ddbec4f43823d4bf66bb148a854f
ms.contentlocale: pt-br
ms.lasthandoff: 05/04/2017

---
# <a name="ux-essentials-for-visual-studio"></a>Conceitos básicos UX para o Visual Studio
## <a name="best-practices"></a>Práticas recomendadas  
  
### <a name="1-be-consistent-within-the-visual-studio-environment"></a>1. Ser consistente dentro do ambiente do Visual Studio.  
  
-   Siga existente [padrões de interação](interaction-patterns-for-visual-studio.md) dentro do shell.  
  
-   Criar recursos para ser consistente com a linguagem visual do shell e [requisitos de habilidade](evaluation-tools-for-visual-studio.md).  
  
-   Use compartilhadas comandos e controles quando eles existem.  
  
-   Compreenda a hierarquia do Visual Studio e como ele estabelece um contexto e unidades de interface do usuário.  
  
### <a name="2-use-the-environment-service-for-fonts-and-colors"></a>2. Use o serviço de ambiente para fontes e cores.  
  
-   Interface do usuário deve respeitar atual [fonte de ambiente](fonts-and-formatting-for-visual-studio.md) , a menos que ela é exposta para personalização na página de fontes e cores na caixa de diálogo Opções de configuração.  
  
-   Elementos de interface do usuário devem usar o [VSColor Service](colors-and-styling-for-visual-studio.md), usar compartilhado tokens de ambiente ou tokens de recurso específico.  
  
### <a name="3-make-all-imagery-consistent-with-the-new-vs-style"></a>3. Verifique todas as imagens consistente com o novo estilo VS.  
  
-   Siga os princípios de design do Visual Studio para ícones, glifos e outros gráficos.  
  
-   Não coloque o texto em elementos gráficos.  
  
### <a name="4-design-from-a-user-centric-perspective"></a>4. Design de uma perspectiva centrado no usuário.  
  
-   Crie o fluxo de tarefas antes dos recursos individuais dentro dele.  
  
-   Familiarize-se com os usuários e tornar esse conhecimento explícito em sua especificação.  
  
-   Ao revisar a interface do usuário, avalie a experiência completa, bem como os detalhes.  
  
-   Crie sua interface do usuário para que ele permaneça funcional e atraente, independentemente do idioma ou localidade.  
  
## <a name="screen-resolution"></a>Resolução de tela  
  
### <a name="minimum-resolution"></a>Resolução mínima  
 - A resolução mínima Dev14 do Visual Studio é **1280x720**. Isso significa que ele é *possíveis* para usar o Visual Studio nessa resolução, embora não seja uma excelente experiência do usuário. Não há nenhuma garantia de que todos os aspectos poderá ser usados com resoluções inferiores 1280x720.  
  
 - A resolução de destino para o Visual Studio é **1366x768**. Esta é a menor resolução em que prometemos um *bom* experiência do usuário.

 - Altura da caixa de diálogo inicial deve ser **menor do que 700 pixels**, de modo que ele se ajuste na resolução mínima do quadro IDE a 96 dpi.
  
### <a name="high-density-displays"></a>Vídeos de alta densidade  
 Interface do usuário no Visual Studio deve funcionar bem em DPI todos os fatores que o Windows oferece suporte pronto para uso de dimensionamento: 150%, 200% e % de 250.  
  
## <a name="anti-patterns"></a>Anti-padrões de  
 O Visual Studio contém vários exemplos de interface do usuário que siga nossas diretrizes e práticas recomendadas. Em um esforço para ser consistente, os desenvolvedores geralmente emprestam padrões de design de interface do usuário de produto semelhantes ao que está criando. Embora essa seja uma boa abordagem que ajuda a nós unidade consistência na interação do usuário e o design visual, ocasionalmente Fornecemos recursos com alguns detalhes que não atender às nossas diretrizes devido a restrições de agendamento ou remover priorização. Nesses casos, não queremos equipes para copiar um dos seguintes anti-""padrões porque elas proliferam inválido ou está inconsistente de interface de usuário no ambiente do Visual Studio.  
  
### <a name="required-fieldssettings-shown-in-error-state-by-default"></a>Campos/configurações necessárias mostradas em estado de erro por padrão  
  
#### <a name="feature-team-goals"></a>Metas da equipe de recursos  
  
-   Avise os usuários que eles adicionou um elemento que deve ser configurado.  
  
-   Chame a atenção do usuário para as áreas que precisam de entrada.  
  
#### <a name="anti-pattern-solution"></a>Solução de antipadrão  
 Assim que o usuário iniciou uma ação e antes da tarefa estiver concluída, coloque imediatamente parada crítica ícones ao lado de áreas que precisam de configuração.  
  
#### <a name="example-manifest-designer-declarations"></a>Exemplo: Declarações de Designer de manifesto  
 Adicionar uma declaração à lista imediatamente o coloca em um estado de erro, que persiste até que o usuário define as propriedades necessárias.  
  
 Nesse caso, há uma preocupação adicional porque contém o ícone usado para o alerta um "&times;" ícone, portanto não pode ser usado no ícone Remover comuns ao lado dela. Como resultado, a interface do usuário utiliza um botão Remover, um controle mais complexa.  
  
 ![Colocação de interface do usuário em um estado de erro por padrão é um padrão de um Visual Studio.](~/docs/extensibility/ux-guidelines/media/manifestdesignererrordeclarationsanti-pattern.png "ManifestDesignererrordeclarationsanti-pattern")<br />Colocação de interface do usuário em um estado de erro por padrão é um padrão de um Visual Studio.
  
#### <a name="alternatives"></a>Alternativas  
 A melhor solução para esse problema seria:  
  
-   Permitir que o usuário adicione uma declaração sem aviso e, em seguida, mover imediatamente para definir as propriedades do item.  
  
-   Adicionar o ícone de aviso (triângulo gold) quando foco é movido do item, como para adicionar outra declaração à lista ou tente alterar guias dentro do designer.  
  
-   Se o usuário tentar alterar guias antes de definir propriedades em qualquer declaração, pop explicando que o aplicativo não criará uma caixa de diálogo (ou qualquer as implicações) até que os avisos sejam resolvidos. Se o usuário fecha a caixa de diálogo e guias de alterações assim mesmo, em seguida, um ícone (crítico ou aviso, conforme apropriado) é adicionado à guia declarações.  
  
### <a name="multiple-clicks-to-dismiss-ui"></a>Vários cliques para ignorar a interface do usuário  
  
#### <a name="feature-team-goals"></a>Metas da equipe de recursos  
 Não permitir que o usuário ignore a interface do usuário sem primeiro ver o texto de explicação.  
  
#### <a name="anti-pattern"></a>Um padrão  
 A equipe inserindo os links de vídeos em vários locais dentro da interface do usuário VS decidiu contra o padrão comum dos "&times;" Fechar explicação botão e dica de ferramenta, como especificado pelo UX e implementado em vez disso, uma lista suspensa e vincular a "Não mostrar novamente".  

#### <a name="example-video-links-in-team-explorer"></a>Exemplo: links de vídeo no Team Explorer
Forçar o usuário leia texto explicativo antes de ignorar a interface do usuário é um antidentro padrão de do Visual Studio. Links de vídeo corretamente projetado deve exibir uma dica de ferramenta com informações adicionais no hover e clicando na "&times;" deve ignorar a mensagem sem necessidade de interação adicional.


 ![Explicação texto anti #45; padrão &#45; incorreto](~/docs/extensibility/ux-guidelines/media/incorrectuseofmultipleclicks.png "Incorrectuseofmultipleclicks")<br />Padrão de link de vídeo incorreto
  
#### <a name="result"></a>Resultado  
 Em vez de um botão Fechar simple (um clique), o usuário será forçado a usar dois cliques para simplesmente ignorar a interface do usuário em cada local que os links de vídeos aparecem.  
  
#### <a name="alternatives"></a>Alternativas  
 O design correto para essa situação seria seguem o padrão comum para o Internet Explorer, o Office e o Visual Studio: no foco, o usuário pode ver a descrição de dica de ferramenta e um clique oculta a interface do usuário.  
  
 ![Explicação texto anti #45; padrão &#45; corrigir](~/docs/extensibility/ux-guidelines/media/explanatorytextanti-pattern-correct.png "Explanatorytextanti-pattern-correct")<br />Padrão de link de vídeo correto
  
### <a name="using-command-bars-for-settings"></a>Usando as barras de comando para configurações  
 **A Figura** representa esse anti-padrão: colocar uma configuração abaixo de um botão de comando que se aplica a mais do que apenas o comando. Nesse esboço, há comandos além de iniciar depuração — como o modo de exibição no navegador, iniciar sem depurar e intervir — que respeitará a configuração selecionada.  

  ![R: de figura Padrão contra da barra de comando](~/docs/extensibility/ux-guidelines/media/commandbaranti-pattern-figurea.png "Commandbaranti-pattern-FigureA")<br />R: de figura Padrão contra da barra de comando
  
 Ligeiramente melhor, mas ainda indesejável, é colocar as configurações deste tipo em barras de ferramentas, conforme mostrado no **Figura B**. Enquanto os botões de divisão levar menos de espaço e, portanto, uma melhoria em listas suspensas, ambos os designs ainda estiver usando uma barra de ferramentas para promover a algo que não é realmente um comando.  
 
 ![Figura b: melhor, mas ainda um antide padrão de barra de comando](~/docs/extensibility/ux-guidelines/media/commandbaranti-pattern-figureb.png "Commandbaranti-pattern-FigureB")<br />Figura b: melhor, mas ainda um antide padrão de barra de comando
 
  A abordagem correta mostrado na **Figura C**, a configuração está associada a uma série de comandos. Não há nenhuma configuração global que está sendo definida e podemos simplesmente alterna entre quatro comandos. Essa é a única situação em que os comandos na barra de ferramentas são aceitáveis. 

 ![Uso correto de c: de figura de padrão de barra de comando do Visual Studio](~/docs/extensibility/ux-guidelines/media/commandbaranti-pattern-figurec.png "Commandbaranti-pattern-FigureC")<br />Uso correto de c: de figura de padrão de barra de comando do Visual Studio
   
### <a name="control-anti-patterns"></a>Padrões de um controle  
 Alguns antisão padrões de uso simplesmente incorreto ou apresentação de um controle ou um grupo de controles.  
  
#### <a name="underlining-used-as-a-group-label-not-a-hyperlink"></a>Sublinhado usado como um rótulo de grupo, não um hiperlink  
 Texto sublinhado deve ser usado apenas para hiperlinks.  
  
 **Inválido:**    
 ![Texto sublinhado e não é um hiperlink é um padrão de um Visual Studio.](~/docs/extensibility/ux-guidelines/media/0102-g_grouplabelincorrect.png "0102-g_GroupLabelIncorrect")<br />Texto sublinhado e não é um hiperlink é um padrão de um Visual Studio.
  
 **BOM:**   
 ![Estilo corretamente, o texto de hiperlink não aparece acrescido na fonte de ambiente.](~/docs/extensibility/ux-guidelines/media/0102-h_grouplabelcorrect.png "0102-h_GroupLabelCorrect")<br />Estilo corretamente, o texto de hiperlink não aparece acrescido na fonte de ambiente.
  
#### <a name="clicking-on-a-check-box-results-in-a-pop-up-dialog"></a>Clicando em resultados de uma caixa de seleção em uma caixa de diálogo pop-up  
 Clicando na caixa de seleção "Habilitar a área de trabalho remota para todas as funções" no Assistente "Publicar aplicativo do Windows Azure" imediatamente abre uma caixa de diálogo pop-up, um padrão de um Visual Studio. Além disso, o campo da caixa de seleção não preenche uma caixa de seleção após ser selecionado, outro anti-padrão de interação.  
  
 ![Colocar uma caixa de diálogo depois de clicar em uma caixa de seleção é um padrão de um Visual Studio.](~/docs/extensibility/ux-guidelines/media/0102-i_checkboxpopup.png "0102-i_CheckboxPopup")<br />Colocar uma caixa de diálogo depois de clicar em uma caixa de seleção é um padrão de um Visual Studio.
  
### <a name="hyperlink-anti-patterns"></a>Padrões de um hiperlink  
 O exemplo a seguir contém dois anti padrões de.  
  
1.  O primeiro plano ativar vermelho hover significa cor correta compartilhado do serviço da fonte não está sendo usado.  
  
2.  "Saiba mais" não é o texto apropriado para um link para um tópico conceitual. Objetivo do usuário não é saber mais, é compreender as implicações de sua escolha.  
  
 ![Ignorando o serviço de cor e usando "Saiba mais" para os hiperlinks são anti-padrões de Visual Studio.](~/docs/extensibility/ux-guidelines/media/0102-j_hyperlinkincorrect.png "0102-j_HyperlinkIncorrect")<br />Ignorando o serviço de cor e usando "Saiba mais" para os hiperlinks são anti-padrões de Visual Studio.  
  
 **Melhor solução:** representar a pergunta, o usuário deve estar se perguntando clicando no link.  
  
-   Como funcionam os serviços do Windows Azure?  
  
-   Quando é necessário um projeto de serviços móveis do Windows Azure?  
  
#### <a name="using-click-here-for-links"></a>Usando "Clique aqui" para links  
 Hiperlinks devem ser um. É um padrão de um para usar "Clique aqui" ou qualquer variação semelhante.  
  
 **Inválido:** "Clique aqui para obter instruções sobre como criar um novo projeto."
  
 **BOM:** "Como criar um novo projeto?"
