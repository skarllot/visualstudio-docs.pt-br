---
title: "Texto de interface do usuário e a Ajuda do Visual Studio | Documentos do Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e8747d07-6c90-46cc-b425-55b589f7e9e4
caps.latest.revision: 2
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
ms.openlocfilehash: 8d809ac7428440138f188e93df736ac947b8947e
ms.lasthandoff: 02/22/2017

---
# <a name="ui-text-and-help-for-visual-studio"></a>Texto de interface do usuário e a Ajuda do Visual Studio
##  <a name="a-namebkmkuitextandterminologya-ui-text-and-terminology"></a><a name="BKMK_UITextAndTerminology"></a>Texto de interface do usuário e terminologia  
 Texto abrangente é crucial para efetivo da interface do usuário. Os usuários de software tendem a ler rótulos em primeiro lugar, ou seja, aquelas mais relevantes para concluir a tarefa em questão. Texto estático é lido com menos frequência. Planejar para os usuários iniciarem suas sessões de trabalho com uma verificação rápida de toda a janela, seguida por uma leitura da interface do usuário nesta ordem aproximada:  
  
1.  Controles interativos no Centro  
  
2.  Confirmar botões  
  
3.  Controles interativos localizados em outro lugar  
  
4.  Instruções principais  
  
5.  Explicações complementares  
  
6.  Título da janela  
  
7.  Outro texto estático no corpo principal  
  
### <a name="usage-patterns-for-ui-text"></a>Padrões de uso para o texto da interface do usuário  
  
#### <a name="title-bar-text"></a>Texto da barra de título  
 Texto da barra de título deve corresponder o comando gerado da interface do usuário.  
  
#### <a name="instructional-text-helper-text"></a>Texto de instrução (texto auxiliar)  
 Em algumas caixas de diálogo, é útil fornecer instruções principais proeminentes para explicar o que fazer na janela ou na página. Isso às vezes é chamado de "texto de Ajuda".  
  
##### <a name="writing-style-rules-for-helper-text"></a>Escrever regras de estilo para o texto de ajuda  
  
-   Não explicaremos o óbvio. A menos que seja absolutamente necessário, não inclua texto de instrução.  
  
-   Texto de instrução sempre é colocado na parte superior da caixa de diálogo e deve se referir à tarefa que está sendo executada.  
  
-   Explique com precisão aos usuários que precisam fazer. Evite redundância e comunicação excessiva.  
  
-   Revise cada janela e eliminar palavras duplicadas e instruções.  
  
-   Mantenha instrutivo texto curto. Se informações mais são necessário para determinados usuários ou cenários, forneça um link para um tópico on-line conceitual detalhado.  
  
-   Escreva o texto para que cada palavra contém peso e é necessária.  
  
-   Siga as orientações Microsoft existente para [texto da Interface do usuário](https://msdn.microsoft.com/en-us/library/windows/desktop/dn742478\(v=vs.85\).aspx) e [estilo e o tom](https://msdn.microsoft.com/en-us/library/windows/desktop/dn742477\(v=vs.85\).aspx).  
  
#### <a name="supplemental-instructions"></a>Instruções suplementares  
 Instruções adicionais fornecem informações adicionais que ajuda o usuário a entender os controles ou controlar agrupamentos. Isso também pode incluir texto de dica necessário entender o formato que o controle de entrada está esperando. Use instruções complementares com moderação. Reservá-los para casos em que é provável que o usuário não compreender totalmente as implicações da opção que eles estão fazendo.  
  
 ![Texto complementar no Visual Studio](../../extensibility/ux-guidelines/media/0601-b_supplementaltext1.png "b_SupplementalText1&0601;")  
  
 **Texto complementar no Visual Studio**  
  
 ![Texto complementar no Visual Studio](~/docs/extensibility/ux-guidelines/media/0601-c_supplementaltext2.png "c_SupplementalText2&0601;")  
  
 **Texto complementar no Visual Studio**  
  
#### <a name="infotips"></a>InfoTips  
 Geralmente, o texto com instrução pode ser muito demorado para posicionar no local na interface do usuário ou pode ser útil somente para os novos usuários, pareçam resíduos para usuários experientes. Nesse caso, o texto das instruções informativas deve ser colocado como uma dica de ferramenta em uma InfoDica.  
  
 InfoTips devem ser colocados perto de controles que eles estão relacionados e devem usar o ícone InfoDica específico, que ainda não é invasivo perceptível.  
  
 ![InfoDica no Visual Studio](../../extensibility/ux-guidelines/media/0601-d_infotip.png "d_InfoTip&0601;")  
  
 **Exemplo de uma InfoDica no Visual Studio**  
  
##### <a name="writing-style-rules-for-infotips"></a>Regras de estilo de escrita para InfoTips  
  
-   Gravar InfoTips como frases. Eles exigem verbos específicos, sentença inteira e pontuação final.  
  
-   Use InfoTips para complementar a instrução principal ou informações. Se estiver usando apenas palavras diferentes para declarar novamente a ideia principal, não é necessário uma InfoDica.  
  
-   Manter InfoTips curto e bonito. Usar palavras pequeno e simples, linguagem cotidiana que oferece suporte e incentivo o usuário.  
  
-   Siga as orientações Microsoft existente para [texto da Interface do usuário](https://msdn.microsoft.com/en-us/library/windows/desktop/dn742478\(v=vs.85\).aspx) e [estilo e o tom](https://msdn.microsoft.com/en-us/library/windows/desktop/dn742477\(v=vs.85\).aspx).  
  
#### <a name="control-labels"></a>Rótulos de controle  
 Rótulos de controle devem ser curto, conciso e siga o [orientação de área de trabalho do Windows para controles](https://msdn.microsoft.com/en-us/library/windows/desktop/dn742399\(v=vs.85\).aspx).  
  
 Para obter mais informações sobre o formato do rótulo de controle e posicionamento dentro da interface do usuário, consulte [Layout para o Visual Studio](../../extensibility/ux-guidelines/layout-for-visual-studio.md).  
  
#### <a name="help-links"></a>Links da Ajuda  
 Links de Ajuda pode ser posicionado dentro do texto das instruções ou no corpo da interface do usuário. Eles podem ser links para a Ajuda ou abrem caixas de diálogo internas.  
  
##### <a name="visual-style-rules-for-help-links"></a>Regras de estilo visual para links de ajuda  
  
-   Use as cores do ambiente correto para hiperlinks. Um hiperlink corretamente com estilo não piscará brevemente vermelho quando clicado. Se você vir isso, é uma indicação de que as cores de ambiente não estão sendo usadas.  
  
-   Sublinhados só devem ser usados em foco ou quando o link é incorporado em um parágrafo.  
  
-   Para obter mais informações sobre estilos visuais e interação de hiperlinks, consulte botões e hiperlinks.  
  
##### <a name="writing-style-rules-for-help-links"></a>Escrever regras de estilo para links de ajuda  
  
-   Ao iniciar as caixas de diálogo, manter os padrões elipses: nenhum reticências para navegação, elipses, se a tarefa exigir adicional da interface do usuário.  
  
     ![Link de Ajuda no Visual Studio](~/docs/extensibility/ux-guidelines/media/0601-e_helplink.png "e_HelpLink&0601;")  
  
     **Reticências (...) em um link de ajuda indicam que a tarefa exigirá adicional da interface do usuário.**  
  
-   Links não deve começar com "Aprender", já que não é a intenção do usuário. O usuário deseja responder uma pergunta específica, não receberá um treinamento geral.  
  
-   Links de ajuda de frase para que eles fazer a pergunta que a resposta para o tópico.  
  
     Incorreto:  
     "Saiba mais sobre preços de serviços móveis do Windows Azure"  
  
     Corrigi:  
     "Quais opções de preços estão disponíveis para serviços móveis do Windows Azure?"  
  
-   Nunca use *clique em...* para o texto do link.  
  
-   Nunca link apenas a palavra "aqui". Isso é problemático para alguns leitores de tela, que serão apenas a palavra hiperlink de voz.  
  
     Incorreto:  
     "Para obter informações sobre o Windows Azure Mobile Services **aqui**"  
  
     Corrigi:  
     "Quais opções de preços estão disponíveis para serviços móveis do Windows Azure?"  
  
-   Para obter mais informações sobre o estilo de escrita correto para links de Ajuda, consulte o [diretrizes de área de trabalho do Windows para obter ajuda sobre](https://msdn.microsoft.com/en-us/library/windows/desktop/dn742494\(v=vs.85\).aspx).  
  
#### <a name="hint-text"></a>Texto de dica  
 Texto de dica aparece como uma marca d'água em um controle ou abaixo do controle. A formatação correta será aplicada usando o token VSColors apropriado, `Environment.GrayText`.  
  
 Ele pode aparecer em vários formulários.  
  
-   Em vez do rótulo de controle:  
  
     ![Dica de texto no Visual Studio](../../extensibility/ux-guidelines/media/0601-f_hinttext1.png "f_HintText1&0601;")  
  
-   Com um verbo, fornecendo instruções:  
  
     ![Dica de texto no Visual Studio](../../extensibility/ux-guidelines/media/0601-g_hinttext2.png "g_HintText2&0601;")  
  
-   Com texto indicando uma entrada necessária:  
  
     ![Dica de texto no Visual Studio](../../extensibility/ux-guidelines/media/0601-h_hinttext3.png "h_HintText3&0601;")  
  
#### <a name="watermark-text"></a>Texto de marca d'água  
 Em uma superfície de design vazio, o texto deve indicar o que fazer, bem como fornecer links para abrir outras janelas relacionadas, se apropriado:  
  
 ![Marca d'água de texto no Visual Studio](../../extensibility/ux-guidelines/media/0601-i_watermarktext.png "i_WatermarkText&0601;")  
  
 **Exemplo de texto de marca d'água no Visual Studio**  
  
### <a name="common-terminology"></a>Terminologia comum  
  
|Termo|Explicação|Comentário|  
|----------|-----------------|-------------|  
|Entrar / sair|Verbos usados como sinônimos com a web para representar uma autenticação em uma propriedade da web. Em clientes, usamos isso vez como uma noção de nível superior para entrar e sair da conexão de usuário do IDE, que representa uma identidade de nível superior que fornece recursos de nível mais alto, como roaming e licenciamento que não estão disponíveis em todas as outras conexões.|O usuário do IDE é o único recurso que deve representar uma entrada / sair verbo, pois ele representa o usuário IDE de nível superior.|  
|Conectar / desconectar|Use em lugares onde um recurso mantém uma única conexão para um serviço online.|Gerenciador de servidores, onde você pode ter apenas uma conexão do Azure ativa por vez, é um exemplo de como conectar/desconectar.|  
|Adicionar / remover|Não-destrutiva. Use quando estiver adicionando ou removendo algo em uma lista.|A caixa de diálogo de lista de servidor do Gerenciador de Conexão do TFS é um exemplo de como adicionar ou remover.|  
|Excluir|Destrutiva. Use somente quando o elemento que está sendo removido será descartada permanentemente ou excluído do disco.|"Delete" geralmente requer um prompt, se o resultado é excluir um arquivo do disco.|  
  
## <a name="error-messages"></a>Mensagens de erro  
  
### <a name="overview"></a>Visão Geral  
 Erros acontecem. Definir limitações sobre o que o usuário pode fazer é uma primeira etapa sensata impedindo que mensagens de erro pode ser evitado. No entanto, quando ocorre um erro, uma mensagem de erro bem escrito pode ir um longo caminho para atenuar o problema. Mensagens de erro são indiscutivelmente, um dos tipos mais importantes de notificação de que o usuário vê, porque eles são síncronos e indicam um problema que precisa ser resolvido. Mensagens de erro mal-escrito deixarem os usuários em suas próprias para decidir a causa dos erros e quaisquer soluções possíveis.  
  
 Os usuários podem parar prestando atenção ao uso excessivo ou confusas mensagens de erro para a experiência de mensagens necessário somente gravação que agregam valor ao usuário. Se a mensagem é simplesmente uma notificação, use uma apresentação alternativa.  
  
### <a name="rules-for-creating-an-error-message"></a>Regras para criar uma mensagem de erro  
  
-   Ao construir mensagens de erro, escolha o nível de erro apropriado para o público. O objetivo de resumos simples que fornecem uma ação que o usuário pode executar, se aplicável. Estado não tudo o que o usuário não precisa saber.  
  
-   Fornece assistência construtivas. É mais fácil de ler e agir sobre uma mensagem de erro que contém a instrução.  
  
-   Não use negativas duplas.  
  
-   Executar os dois um automatizados e um manual gramática e ortografia verificar qualquer mensagem de erro que você escreve.  
  
-   Para mensagens de erro complexo, evite comunicações sequenciais. Nunca use uma conexão de F1 para a mensagem de erro. A mensagem propriamente dita deve ser suficiente.  
  
-   Use o ícone correto.  
  
-   Faça perguntas fáceis de entender e usar os botões que desmarque as opções, como "Excluir" e "Cancelar".  
  
-   Para avisos, ser clara sobre a consequência de continuar. Os botões devem indicar as consequências.  
  
-   Para erros, descrevem o que o usuário pode fazer para corrigir o problema. Botões devem ser ações ou diga "Fechar". Não use um botão "Okey" para uma mensagem de erro.  
  
-   Algumas perguntas para perguntar ao construir uma mensagem de erro:  
  
    -   O usuário pode descobrir como solucionar o problema com esse erro sozinho?  
  
    -   O usuário usa o mesmo vocabulário como esse erro?  
  
    -   É esse erro ambigious ou compartilhados em várias situações? Nesse caso, como você orientar os usuários para a solução de que precisam?  
  
#### <a name="build-errors"></a>Erros de compilação  
 Como o Visual Studio é uma ferramenta de desenvolvimento de software, muitos de seus componentes têm uma compilação, converter ou codificação de etapa para converter o trabalho do desenvolvedor em formato binário. Essas conversões podem causar erros quando o compilador não pode processar arquivos criados de forma inadequada ou quando as opções de compilador não foram definidas corretamente.  
  
 Usuários do Visual Studio podem gastar um número enorme de horas de desenvolvimento Resolvendo erros de compilação. Esse tempo de resolução aumenta quando erros têm dependências ou quando as mensagens de erro são escritas incorretamente, o que pode dificultar a descobrir a origem do erro.  
  
 Os erros de compilação recomendados são aquelas que não ocorrem em primeiro lugar, é por isso que o Visual Studio fornece preenchimento automático e rabisca IntelliSense. Validadores de esquema e ferramentas semelhantes fornecem o mesmo tipo de comentários. Esses mecanismos proativamente guiar o usuário para construir o código bem formado, diminuindo a chance de erros de compilação.  
  
 O Visual Studio fornece uma janela de ferramenta onde os usuários podem ler e percorrer os erros que ocorreram em suas janelas de documento. Atalhos de teclado são fornecidos para que o usuário pode navegar grandes quantidades de código e ir diretamente para o local do problema rapidamente. O Visual Studio também permite que cada erro de compilação seja vinculada a uma determinada identificação de palavra-chave/contexto de ajuda para que o usuário pode ir diretamente para um tópico da Ajuda que fornece informações mais detalhadas sobre o erro.  
  
 Erros de compilação clara e concisa de gravação:  
  
-   **Use uma linguagem simples** que explica o problema com pouca ou nenhuma jargão do compilador. O texto de um erro de compilação não deve ser excessivamente técnico.  
  
-   **Descrever as possíveis causas.** Por exemplo, "faltando dois-pontos entre a propriedade e o valor de ' (propriedade): (valor)' declaração."  
  
-   Fornecer detalhes sobre possíveis correções. Se não houver espaço suficiente, detalhes adicionais podem ser colocados no tópico da Ajuda correspondente.  
  
### <a name="components-of-a-well-written-error-message"></a>Componentes de uma mensagem de erro bem escrita  
  
#### <a name="use-the-shell-dialog-service-for-error-messages"></a>Use o serviço de caixa de diálogo do shell para mensagens de erro.  
 Usando o serviço de diálogo shell permite que você controle a aparência da mensagem — fontes em particular — sem alterações importantes para elementos individuais. Use o **IErrorInfo** mecanismos e relatá-los usando **IVsUIShell::SetErrorInfo/ReportErrorInfo**.  
  
#### <a name="choose-an-effective-and-appropriate-notification-presentation"></a>Escolha uma apresentação de notificação efetivo e apropriado.  
 Use uma caixa de diálogo modal com um aviso crítico se uma ação imediata é necessária para evitar perda de dados (notificação síncrona). Ícones críticas são reservados para situações em que a mensagem sem leitura fechando pode levar a consequências negativas. Perda de dados é uma situação crítica que requer uma resposta de nível de alarme. Uso excessivo do ícone crítico desensitizes usuários à sua importância. Se a mensagem de erro informativa, considere as alternativas para uma caixa de diálogo modal (notificação assíncrona).  
  
#### <a name="provide-a-clean-succinct-explanation-of-why-the-problem-occurred-rather-than-a-technical-explanation"></a>Fornece uma explicação sucinta, limpeza porque o problema ocorreu em vez de uma explicação técnica.  
 Sobrecarregar os usuários com detalhes técnicos na explicação tornará mais provável ignorar mensagens de erro. Exemplos de bons mensagens:  
  
-   "Não é possível abrir o arquivo solicitado."  
  
-   "Não é possível conectar à Internet."  
  
#### <a name="provide-information-about-how-to-fix-the-problem"></a>Fornece informações sobre como corrigir o problema.  
 Oferece as sugestões de como corrigir o problema do usuário. Ser honesto com o usuário se não houver nenhuma sugestão. Fornece links diretos para fontes online alternativas, como suporte técnico ou suporte da comunidade. Tente direcionar os usuários para informações específicas online pertinentes ao problema. Para uma identificação de erro, considere a possibilidade de vincular usuários a um thread de discussão sobre esse erro específico. Exemplos de bons mensagens:  
  
-   "Certifique-se de que você está conectado à Internet e tente novamente."  
  
-   "Verifique se o arquivo existe e se você tem permissão para abri-lo."  
  
#### <a name="write-a-message-that-is-short-and-to-the-point"></a>Gravar uma mensagem curta e o ponto.  
 Uma mensagem de erro pode notificar, explicar e oferecem uma solução mas ainda ser ignorado se for muito prolixo. Uma solução é usar divulgação progressiva com um botão de detalhes. Por exemplo, forneça uma breve descrição/solução e, em seguida, colocar mais detalhes em um botão de detalhes. Se os usuários optarem ler mais informações sobre o erro, eles podem fazer isso.  
  
 O idioma da mensagem deve ser:  
  
-   **Domínio apropriado.** Use o usuário compreenderá de linguagem. Apesar de nossos clientes são desenvolvedores, geralmente não é necessário o contexto e a terminologia que nós temos.  
  
-   **Específico.** Evite texto vago e dar nomes específicos e os locais dos objetos envolvidos. Por exemplo, uma mensagem de erro como "o caractere é inválido" não é útil. O caractere? "Arquivo não encontrado". O arquivo?  
  
-   **É recomendável.** Não culpa o usuário ou torná-los a sentir tolos. Evitar linguagem ofensiva ou hostil (eliminar, execução, encerrar, fatal, inválido). Evite texto em maiusculas, que é normalmente visto como shouting e não está mais legíveis. Não use o humor.  
  
-   **Corrigi.** Use a gramática e ortografia correta (mesmo em Alfas). Erros de digitação são profissional e embaraçoso.  
  
-   **Contextualmente apropriadas.** Use o texto do botão apropriado. Evite o botão "Okey" e usar "Continue" ou "Sim/não".  
  
### <a name="error-message-examples"></a>Exemplos de mensagem de erro  
  
|Bom|Incorreta|  
|----------|---------|  
|"O número discado não está mais no serviço. Verifique o número e disque novamente ou discar 0 para o operador."|-"(449) erro: número inválido"<br />-"Esse erro de exceção sem tratamento indica que a operação foi concluída com êxito."<br /><br /> ![Mensagem de erro inválido no Visual Studio](~/docs/extensibility/ux-guidelines/media/0602-a_errordialog.png "0602-a_ErrorDialog")|  
  
## <a name="accessing-help"></a>Acessando a Ajuda  
  
### <a name="overview"></a>Visão Geral  
 Além de documentação no MSDN, um usuário do Visual Studio tem vários pontos de acesso para ajudar o usuário enquanto na interface do usuário. Para garantir que esses pontos de acesso estão constantemente disponíveis, as equipes de recursos necessário tirar proveito do sistema de ajuda oferecido pelo ambiente. Esses pontos de acesso são:  
  
-   **Texto de ensino e complementar em caixas de diálogo.** Texto estático que dá a direção ou explicação, na interface do usuário disponível na passe o mouse sobre um ícone InfoDica ou superfície.  
  
-   **Ajuda F1** (editor). No editor do Visual Studio, o usuário pode confiar que a qualquer momento, pressionando F1 abrirá um tópico da Ajuda específica para a seleção atual. Certifique-se de que tópicos associados F1 são apropriadas e informativos.  
  
-   **Hiperlinks para tópicos da Ajuda.** Um hiperlink em uma caixa de diálogo, janela de ferramenta ou superfície de design que inicia um tópico para ajudar o usuário em saber mais sobre uma tecnologia, recurso ou obter informações sobre como realizar uma tarefa.  
  
-   **Mecanismos de interface do usuário de auxiliar, como marcas inteligentes e caixas de diálogo de criação.** Esses mecanismos ajude o usuário Noções básicas sobre um elemento de interface do usuário ou facilitam uma tarefa, como marcas inteligentes ou caixas de diálogo do construtor.  
  
-   **Botões de Ajuda da interface do usuário** (preterido). Um indicador visível na barra de título que fornece acesso para o tópico da Ajuda F1 relacionado.  
  
### <a name="text"></a>Texto  
  
#### <a name="instructional-and-supplemental-text-in-dialogs"></a>Texto de instrução e complementar em caixas de diálogo  
 Nas caixas de diálogo que oferecem suporte a tarefas complexas, pode haver a necessidade de dar instruções texto na interface do usuário, geralmente na parte superior da caixa de diálogo ou próximo controles complexos. Consulte [UI texto e terminologia](../../extensibility/ux-guidelines/ui-text-and-help-for-visual-studio.md#BKMK_UITextAndTerminology) para obter detalhes sobre o estilo de texto.  
  
#### <a name="infotips"></a>InfoTips  
 Com frequência, texto de instrução pode ser muito demorado para posicionar no local na interface do usuário ou pode ser útil somente para os novos usuários, pareçam resíduos para usuários experientes. Nesse caso, o texto das instruções informativas deve ser colocado como uma dica de ferramenta em uma InfoDica.  
  
 InfoTips devem ser colocados perto de controles que eles estão relacionados e devem usar o ícone InfoDica específico, que ainda não é invasivo perceptível.  
  
 ![InfoDica no Visual Studio](../../extensibility/ux-guidelines/media/0601-d_infotip.png "d_InfoTip&0601;")  
  
 **Exemplo de uma InfoDica no Visual Studio**  
  
### <a name="interactive-help-mechanisms"></a>Mecanismos de ajuda interativos  
  
#### <a name="f1-help"></a>F1 Ajuda  
 Ajuda F1 é necessária em um editor ou a superfície de design, mas não em outro lugar no ambiente do Visual Studio.  
  
#### <a name="hyperlinks-to-help-topics"></a>Hiperlinks para tópicos da Ajuda  
 Hiperlinks podem ser usados para executar uma ação, navegue no IDE ou iniciar a Ajuda em um navegador. Consulte [UI texto e terminologia](../../extensibility/ux-guidelines/ui-text-and-help-for-visual-studio.md#BKMK_UITextAndTerminology) para obter detalhes sobre a linguagem e 07.10.01 botões e hiperlinks para diretrizes visual e layout.  
  
#### <a name="help--buttons-in-dialog-title-bars-deprecated"></a>Ajuda [?] botões em barras de título da caixa de diálogo (preteridas)  
 Geralmente, os botões de Ajuda [?] na barra de título de caixas de diálogo são preteridos. Tópicos de interface do usuário não fazem parte de nosso modelo de documento e, portanto, talvez não haja um tópico relevante para vincular a. Essencialmente, o botão da barra de título era a mesma coisa que ajuda F1, e que não é mais necessário nas caixas de diálogo. Em alguns casos, isso pode ainda ser usado como um indicador de que há mais informações conceituais ou procedimentos, embora os hiperlinks são mais comumente usados na interface do usuário mais recente.  
  
##### <a name="dialogs-created-through-the-environment"></a>Caixas de diálogo criadas através do ambiente  
 Muitas caixas de diálogo do shell são criadas por meio de **VBDialogBoxParam** função. Essa função compartilhada foi atualizada para auxiliar na movimentação de **ajuda** botão da caixa de diálogo para o **?** botão mantendo uma arquitetura com versões anteriores compatíveis e extensível.  
  
 Especificamente, o **VBDialogBoxParam** função examina o modelo de caixa de diálogo para um botão cuja ID é **IDHELP** (9) ou rótulo é **ajuda** ou **< / ajuda**. Se um botão de ajuda for encontrado, ele está oculto e o **WS_EX_CONTEXTHELP** estilo é adicionado à caixa de diálogo, que coloca o **?** botão da barra de título da caixa de diálogo.  
  
 Quando a caixa de diálogo é criada, ele envia proc a caixa de diálogo para uma pilha e invoca a caixa de diálogo com um processo caixa de diálogo pré-processando chamado **DialogPreProc**. Quando o **?** botão é clicado, ele envia um **WM_SYSCOMMAND** de **SC_CONTEXTHELP** à caixa de diálogo. O **DialogPreProc** captura esse comando e o altera para um **WM_HELP** mensagem, que é passada para o procedimento de diálogo original  
  
 A maioria das caixas de diálogo ambiente criado tem um botão Ajuda na caixa de diálogo. Quando a caixa de diálogo for exibida, o botão Ajuda estiver oculta automaticamente e somente o **?** botão funciona. Se o **?** botão nunca é removido ou alterado no Windows, essa solução permite que você rapidamente mover de volta para os botões de ajuda originais.  
  
 Essa solução faz quatro suposições que podem causar erros:  
  
-   Botão de Ajuda da caixa de diálogo é **IDHELP** (9).  
  
-   A caixa de diálogo parece correta quando o botão Ajuda é oculto.  
  
-   A caixa de diálogo não substituir seu winproc.  
  
-   A caixa de diálogo não é inserida dentro de outra caixa de diálogo.  
  
 Se a caixa de diálogo reside no msenv e não usa **VBDialogBoxParam**, investigue aproveitando **VBDialogBoxParam** antes de implementar seu próprio manipulador.  
  
##### <a name="dialogs-created-through-other-packages"></a>Caixas de diálogo criadas por meio de outros pacotes  
 Você pode implementar sua própria solução para caixas de diálogo que residem fora msenv. Para uma classe de diálogo compartilhadas no VSPackage, considere mover o botão à barra de título ou implementar um manipulador em cada caixa de diálogo. O código a seguir é um esqueleto de uma implementação para ajudá-lo a começar a usar:  
  
```  
struct DLGPROCITEM  
{  
    FARPROC proc; // The info used to create the dialog.  
    DLGPROCITEM* procPrev;  
};  
  
DLGPROCITEM* g_dlgProcStack = NULL;  
  
// A dialog starter/wrapper function is used to push the new  
// dialog proc to the top of our dialog proc stack.  
  
int SomeDialogStarterFunction(hinst, id, proc, etc)  
{  
    if (g_dlgProcStack == NULL)  
    {  
        g_dlgProcStack = new DLGPROCITEM;  
        g_dlgProcStack->procPrev = NULL;  
    }  
    else  
    {  
        DLGPROCITEM* procItem = new DLGPROCITEM;  
        g_dlgProcStack->procPrev = g_dlgProcStack;  
        g_dlgProcStack = procItem;  
    }  
}  
  
// Pop this dialog proc off the dialog proc stack.  
  
DialogBoxIndirectParam...(...)  
{  
    DLGPROCITEM* procItem = g_dlgProcStack->procPrev;  
    delete g_dlgProcStack;  
    g_dlgProcStack = procItem;  
}  
  
// A wrapper dialog procedure will allow us to capture the  
// SC_CONTEXTHELP button on the title bar from Windows and  
// forward it as a simple WM_HELP message back to the dialog.  
  
INT_PTR CALLBACK DialogPreProc(HWND hwndDlg, UINT uMsg,  
    WPARAM wParam, LPARAM lParam)  
{  
    if (uMsg == WM_SYSCOMMAND && wParam == SC_CONTEXTHELP)  
    {  
        uMsg = WM_HELP;  
        wParam = 0;  
        lParam = 0;  
    }  
    return CallWindowProc((WNDPROC)g_dlgProcStack->proc,  
        hwndDlg, uMsg, wParam, lParam);  
}  
```  
  
##### <a name="help-buttons-in-managed-code"></a>Botões de Ajuda no código gerenciado  
 Substituindo o comportamento padrão de janela título barra Ajuda do botão é fácil em código gerenciado. Abaixo é um aplicativo de demonstração completo que demonstra esse comportamento. Em essência, você precisa substituir o formulário **WndProc** método e dispara desativar a Ajuda de F1 solicitações quando uma **SC_CONTEXTHELP** mensagem é interceptada.  
  
```  
using System;  
using System.Windows.Forms;  
  
public class HelpForm : Form  
{  
    private const int SC_CONTEXTHELP = 0xF180;  
    private const int WM_SYSCOMMAND = 0x0112;  
  
    public HelpForm()  
    {  
        this.ClientSize = new System.Drawing.Size(300, 250);  
        this.HelpButton = true;  
        this.MaximizeBox = false;  
        this.MinimizeBox = false;  
        this.Name = "HelpForm";  
        this.Text = "Help Form";  
    }  
  
    protected override void WndProc(ref Message m)  
    {  
        if (m.Msg == WM_SYSCOMMAND && SC_CONTEXTHELP == (int)m.WParam)  
            ShowHelp();  
        else  
            base.WndProc(ref m);  
    }  
  
    private void ShowHelp()  
    {  
        MessageBox.Show("F1 Help goes here.");  
    }  
  
     [STAThread]  
    static void Main()  
    {  
        Application.EnableVisualStyles();  
        Application.EnableRTLMirroring();  
        Application.Run(new HelpForm());  
    }  
}  
```  
  
## <a name="see-also"></a>Consulte também  
 [Fontes e formatação para o Visual Studio](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md)   
 [Layout do Visual Studio](../../extensibility/ux-guidelines/layout-for-visual-studio.md)   
 [Notificações e o progresso do Visual Studio](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md)
