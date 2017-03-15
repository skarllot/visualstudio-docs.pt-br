---
title: "Conceitos básicos de experiência do usuário para o Visual Studio | Documentos do Microsoft"
ms.custom: 
ms.date: 11/04/2016
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
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 7f10e2cefc0986a2457cc61945a60acfd1a4ef78
ms.lasthandoff: 02/22/2017

---
# <a name="ux-essentials-for-visual-studio"></a>Conceitos básicos de experiência do usuário do Visual Studio
## <a name="best-practices"></a>Práticas recomendadas  
  
### <a name="1-be-consistent-within-the-visual-studio-environment"></a>1. Ser consistente no ambiente do Visual Studio.  
  
-   Siga os padrões de interação existentes dentro do shell.  
  
-   Recursos para ser consistente com os requisitos de habilidade e da linguagem do visual do shell do design.  
  
-   Use controles e comandos compartilhados quando existirem.  
  
-   Compreenda a hierarquia do Visual Studio e como ele estabelece o contexto e unidades de interface do usuário.  
  
### <a name="2-use-the-environment-service-for-fonts-and-colors"></a>2. Use o serviço do ambiente de fontes e cores.  
  
-   Interface do usuário deve respeitar a configuração de fonte do ambiente atual, a menos que ele é exposto para personalização na página de fontes e cores na caixa de diálogo Opções.  
  
-   Elementos de interface do usuário devem usar o VSColor Service, usando o ambiente compartilhado ou tokens de recurso específico.  
  
### <a name="3-make-all-imagery-consistent-with-the-new-vs-style"></a>3. Verifique todas as imagens consistentes com o novo estilo VS.  
  
-   Siga os princípios de design do Visual Studio para ícones, glifos e outros elementos gráficos.  
  
-   Não coloque o texto em elementos gráficos.  
  
### <a name="4-design-from-a-user-centric-perspective"></a>4. Design de uma perspectiva centrada no usuário.  
  
-   Crie o fluxo de tarefas antes dos recursos individuais dentro dele.  
  
-   Estar familiarizado com os seus usuários e tornar esse conhecimento explícito em sua especificação.  
  
-   Ao revisar a interface do usuário, avalie a experiência completa, bem como os detalhes.  
  
-   Projete sua interface do usuário para que ele permaneça funcional e atraente, independentemente do idioma ou localidade.  
  
## <a name="screen-resolution"></a>Resolução de tela  
  
### <a name="minimum-resolution"></a>Resolução mínima  
 A resolução mínima para Visual Studio Dev14 é 1280 x 1024. Isso significa que ele é *possível* para usar o Visual Studio nessa resolução, embora não seja uma ótima experiência do usuário. Não há nenhuma garantia de que todos os aspectos poderá ser usados em resoluções inferiores 1280 x 1024.  
  
 Tamanho da caixa de diálogo inicial não deve exceder 1000 pixels de altura para caber dentro do quadro do IDE nessa resolução mínima de 96 dpi.  
  
### <a name="high-density-displays"></a>Monitores de alta densidade  
 Interface do usuário no Visual Studio deve funcionar bem em DPI todos os fatores que o Windows oferece suporte pronto para uso de dimensionamento: 150%, 200% e 250%.  
  
## <a name="anti-patterns"></a>Os antipadrões  
 Visual Studio contém muitos exemplos seguir nossas diretrizes e práticas recomendadas da interface do usuário. Em um esforço para ser consistente, os desenvolvedores geralmente emprestam de padrões de design de interface do usuário de produto semelhantes ao que está criando. Embora essa seja uma boa abordagem que ajuda a nos unidade consistência na interação do usuário e o design visual, ocasionalmente disponibilizarmos recursos com alguns detalhes que não atende às nossas diretrizes devido a restrições de agendamento ou defeito priorização. Nesses casos, não queremos que as equipes de copiar um desses "antipadrões" porque elas se proliferam inválido ou está inconsistente da interface do usuário dentro do ambiente do Visual Studio.  
  
### <a name="required-fieldssettings-shown-in-error-state-by-default"></a>Campos/configurações necessárias mostradas em estado de erro por padrão  
  
#### <a name="feature-team-goals"></a>Metas da equipe de recursos  
  
-   Avise os usuários que incluíram um elemento que deve ser configurado.  
  
-   Chame a atenção do usuário para as áreas que precisam de entrada.  
  
#### <a name="anti-pattern-solution"></a>Antipadrão de solução  
 Assim que o usuário iniciou uma ação e antes da tarefa estiver concluída, coloque imediatamente parada crítica ícones ao lado de áreas que precisam de configuração.  
  
#### <a name="example-manifest-designer-declarations"></a>Exemplo: Declarações de Designer de manifesto  
 Adicionar uma declaração à lista imediatamente o coloca em um estado de erro, que persiste até que o usuário define as propriedades necessárias.  
  
 Nesse caso, há uma preocupação adicional porque o ícone usado para o alerta contém um "x", então remover comuns ícone não pode ser usado ao lado dela. Como resultado, a interface do usuário usa um botão Remover, um controle mais complexa.  
  
 ![Manifesto Designer erro declaração antipadrão](../../extensibility/ux-guidelines/media/manifestdesignererrordeclarationsanti-pattern.png "ManifestDesignererrordeclarationsanti padrão")  
  
 **Colocar a interface do usuário em um estado de erro por padrão é um antipadrão do Visual Studio.**  
  
#### <a name="alternatives"></a>Alternativas  
 Uma melhor solução para esse problema seria:  
  
-   Permitir que o usuário adicione uma declaração sem aviso e, em seguida, mover imediatamente para definir as propriedades do item.  
  
-   Adicionar o ícone de aviso (triângulo gold) ao foco é movido do item, como para adicionar outra declaração para a lista ou tente alterar o guias dentro do designer.  
  
-   Se o usuário tentar alterar guias antes de definir propriedades em qualquer declaração, exibida uma caixa de diálogo explicando que o aplicativo não será compilado (ou qualquer das implicações) até que os avisos sejam resolvidos. Se o usuário fecha a caixa de diálogo e altera o guias mesmo assim um ícone (crítico ou aviso, conforme apropriado) é adicionado à guia declarações.  
  
### <a name="forcing-the-user-to-read-text-before-dismissing-ui"></a>Forçar o usuário a ler texto antes de ignorar a interface do usuário  
  
#### <a name="feature-team-goals"></a>Metas da equipe de recursos  
 Não permitir que o usuário ignorar a interface do usuário sem primeiro ver o texto de explicação.  
  
#### <a name="anti-pattern"></a>Antipadrão  
 A equipe inserindo os links de vídeo em vários locais dentro da interface do usuário VS decidimos contra o padrão comum de um X fecha botão e dica de ferramenta explicação conforme especificado pelo UX e implementado em vez disso, uma lista suspensa e o link "Não mostrar novamente".  
  
 ![Texto explicativo antipadrão-incorreto](../../extensibility/ux-guidelines/media/incorrectuseofmultipleclicks.png "Incorrectuseofmultipleclicks")  
  
 **Incorreto: forçar o usuário leia o texto explicativo antes de ignorar a interface do usuário é um antipadrão dentro do Visual Studio.**  
  
#### <a name="result"></a>Resultado  
 Em vez de um botão de fechamento simple (um clique), o usuário será forçado a usar dois cliques para simplesmente ignorar a interface do usuário em cada local que o vídeo links são exibidos.  
  
#### <a name="alternatives"></a>Alternativas  
 O design correto para essa situação seria seguem o padrão comum para Internet Explorer, do Office e do Visual Studio: no foco, o usuário pode ver a descrição de dica de ferramenta e um clique oculta a interface do usuário.  
  
 ![Texto explicativo antipadrão-correto](../../extensibility/ux-guidelines/media/explanatorytextanti-pattern-correct.png "Explanatorytextanti padrão correto")  
  
 **Correto: conforme projetado, links de vídeo deve exibir uma dica de ferramenta com informações adicionais em foco e clicando no "X" deve ignorar a mensagem sem necessidade de interação adicional.**  
  
### <a name="using-command-bars-for-settings"></a>Usando barras de comando para configurações  
 ![Comando barra antipadrão-Figura A](../../extensibility/ux-guidelines/media/commandbaranti-pattern-figurea.png "Commandbaranti de padrão de FigureA")  
  
 **Figura a: antipadrão comando barra**  
  
 **A Figura** representa esse antipadrão: colocar uma configuração sob um botão de comando que se aplica a mais do que apenas o comando. Nesse esboço, há comandos além de iniciar depuração — como o modo de exibição no navegador, iniciar sem depurar e Step Into — que respeita a configuração selecionada.  
  
 ![Comando barra antipadrão-Figura B](../../extensibility/ux-guidelines/media/commandbaranti-pattern-figureb.png "Commandbaranti de padrão de FigureB")  
  
 **Figura b: melhor, mas ainda um antipadrão de barra comando**  
  
 Um pouco melhor, mas ainda indesejável, é colocar as configurações desse tipo em barras de ferramentas, conforme mostrado na **Figura B**. Embora botões de divisão ocupar menos espaço e, portanto, são um aprimoramento em listas suspensas, ambos os designs ainda estão usando uma barra de ferramentas para promover algo que não é realmente um comando.  
  
 ![Comando barra antipadrão-Figura C](../../extensibility/ux-guidelines/media/commandbaranti-pattern-figurec.png "Commandbaranti de padrão de FigureC")  
  
 **Usar figura c correta do padrão de barra de comando do Visual Studio**  
  
 Em **Figura C**, a configuração está vinculada a uma série de comandos. Não há nenhuma configuração global que está sendo definida e estamos mudando apenas entre quatro comandos. Essa é a única situação em que os comandos na barra de ferramentas são aceitáveis.  
  
### <a name="control-anti-patterns"></a>Controle antipadrões  
 Alguns antipadrões são uso simplesmente incorreto ou apresentação de um controle ou um grupo de controles.  
  
#### <a name="underlining-used-as-a-group-label-not-a-hyperlink"></a>Sublinhar usado como um rótulo de grupo, não um hiperlink  
 Texto sublinhado deve ser usado apenas para hiperlinks.  
  
 **Ruim:**  
  
 ![Antipadrão sublinhado nos rótulos de grupo](../../extensibility/ux-guidelines/media/0102-g_grouplabelincorrect.png "g_GroupLabelIncorrect&0102;")  
  
 **Texto sublinhado que não é um hiperlink é um antipadrão do Visual Studio.**  
  
 **Boa:**  
  
 ![Antipadrão sublinhado nos rótulos de grupo (corretos)](../../extensibility/ux-guidelines/media/0102-h_grouplabelcorrect.png "h_GroupLabelCorrect&0102;")  
  
 **Estilo corretamente, texto de hiperlink não aparece acrescido da fonte de ambiente.**  
  
#### <a name="clicking-on-a-check-box-results-in-a-pop-up-dialog"></a>Clicar em uma caixa de seleção resulta em uma caixa de diálogo pop-up  
 Clicando na caixa de seleção "Habilitar a área de trabalho remota para todas as funções" no Assistente "Publicar aplicativo do Windows Azure" imediatamente abre uma caixa de diálogo pop-up, um antipadrão do Visual Studio. Além disso, o campo da caixa de seleção não seja preenchido com uma caixa de seleção após ser selecionado, antipadrão outra interação.  
  
 ![Caixa de seleção antipadrão de pop-up](../../extensibility/ux-guidelines/media/0102-i_checkboxpopup.png "i_CheckboxPopup&0102;")  
  
 **Colocar uma caixa de diálogo depois de clicar em uma caixa de seleção é um antipadrão do Visual Studio.**  
  
### <a name="hyperlink-anti-patterns"></a>Os antipadrões de hiperlink  
 O exemplo a seguir contém dois antipadrões.  
  
1.  Primeiro plano ativando vermelho hover significa que a cor compartilhada correta do serviço da fonte não está sendo usada.  
  
2.  "Saiba mais" não é o texto apropriado para um link para um tópico conceitual. Objetivo do usuário não é saber mais, é compreender as ramificações de sua escolha.  
  
 ![Os antipadrões hyperlink](../../extensibility/ux-guidelines/media/0102-j_hyperlinkincorrect.png "j_HyperlinkIncorrect&0102;")  
  
 **Ignorando o serviço de cor e usando "Saiba mais" hiperlinks são antipadrões do Visual Studio.**  
  
 **Melhor solução:** faça a pergunta que o usuário deve estar se perguntando, clicando no link.  
  
-   Como funcionam os serviços do Windows Azure?  
  
-   Quando é necessário um projeto de serviços móveis do Windows Azure?  
  
#### <a name="using-click-here-for-links"></a>Usando "Clique aqui" para links  
 Hiperlinks devem ser um. É um antipadrão usar "Clique aqui" ou qualquer variação semelhante.  
  
 **Inválido:** "Clique aqui para obter instruções sobre como criar um novo projeto."  
  
 **Boa:** "Como criar um novo projeto?"
