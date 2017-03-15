---
title: "Ferramentas de avaliação do Visual Studio | Documentos do Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 94e0e9a3-440c-4943-ad7b-772ed742e034
caps.latest.revision: 3
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
ms.openlocfilehash: d1cf05406ecb3801758ff1d2166f247f7804bd41
ms.lasthandoff: 02/22/2017

---
# <a name="evaluation-tools-for-visual-studio"></a>Ferramentas de avaliação do Visual Studio
## <a name="craftsmanship-checklist-for-visual-studio"></a>Lista de verificação de habilidade para Visual Studio  
 Use esta lista de verificação para avaliar a qualidade de experiência do usuário para obter detalhes visuais e interação.  
  
### <a name="overview"></a>Visão Geral  
  
-   Verifique se todos os comandos resultam em comentários que informa aos usuários que os comandos foram realizados.  
  
-   Verifique se todos os controles e elementos de interface do usuário são visíveis em todos os temas e no modo de alto contraste.  
  
-   Verifique se que inativa e ativa a seleção sempre são diferenciados, no padrão e o modo de alto contraste.  
  
-   Verifique se que o foco esteja sempre visível e aparente.  
  
### <a name="performance"></a>Desempenho  
  
-   Verifique se algum tipo de "ocupado" indicador é mostrado se um comando tem mais de um segundo.  
  
-   Verifique se um comando demorar mais de 10 segundos para ser concluído, uma barra de progresso explícito ou determinada (preferencial) ou indeterminado, é exibida.  
  
### <a name="ui-text"></a>Texto de interface do usuário  
  
-   Verifique se todos os rótulos são capitalização de título ou frase e que nenhum texto é totalmente em minúsculas.  
  
    ||Corrigir|Incorreto|  
    |-|-------------|---------------|  
    |**Texto de comando (tudo)**|Sentença inteira:<br /><br /> **Nome do diretório:**|Nome do diretório:|  
    |**Texto do botão (cliente)**|Capitalização de título:<br /><br /> **[Definir como padrão]**|DEFINIR COMO PADRÃO|  
    |**Texto do botão (online)**|Sentença inteira:<br /><br /> **[Definir como padrão]**||  
  
-   Verifique se todos os rótulos, exceto os cabeçalhos de grupo e botões, terminam com dois-pontos e precedem o controle com o qual eles estão emparelhados.  
  
-   Verifique se botões, comandos e links de comando que inicie a interface do usuário para capturar a entrada do usuário final em um sinal de reticências **[...] **.  
  
     Exemplos:  
  
    -   Um **[Avançado...] ** botão em uma caixa de diálogo.  
  
    -   As opções de comando do menu Ferramentas (**Ferramentas > opções**) não deve obter uma elipse, como iniciar a própria caixa de diálogo é a intenção do comando.  
  
-   Verifique se a interface do usuário não contém nenhuma abreviações, exceto para termos de padrão da indústria. Por exemplo, HTML nem TCP/IP precisa ser esclarecido, apesar de OOM (memória insuficiente) e PII (informações de identificação pessoal) devem.  
  
### <a name="keyboard-access"></a>Acesso de teclado  
  
-   Verifique se há uma maneira de executar cada tarefa com o teclado. Geralmente isso é feito por meio do acesso de teclado para cada controle, mas algumas áreas altamente visuais, uma alternativa como vai para o modo de exibição de código é aceitável.  
  
-   Verifique se que você pode percorrer os controles em uma ordem lógica (esquerda para a direita e cima para baixo). Embora essa seja uma prática recomendada para a maioria dos controles, nem todos os controles exigem essa abordagem. Por exemplo, verifique se esse botão de opção são controles em um grupo com uma única parada de tabulação.  
  
-   Verifique se todos os controles têm rótulos e cada rótulo possui um mnemônico (exceções incluem alguns controles de rotulado não podem seguir um controle identificado na guia).  
  
-   Verifique se que não há nenhum conflito mnemônico.  
  
### <a name="fonts"></a>Fontes  
  
-   Verifique se todas as fontes (face, tamanho, cor) são usadas de forma consistente e mantêm a hierarquia.  
  
-   Verifique se todos os elementos de interface do usuário usam o serviço de fonte de ambiente. (Consulte [fontes e formatação para o Visual Studio](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md))  
  
     Para verificar se o serviço está sendo usado, vá para **Ferramentas > opções > fontes e cores**. Na lista suspensa de configurações, escolha a fonte de ambiente e alterar a face de fonte para algo stylistically diferente (como Souza ou em quadrinhos Sans) e defina o tamanho para 12 pt. Em seguida, clique em Okey. Talvez seja necessário reiniciar o IDE, mas a maioria dos IU vai alterar imediatamente. Áreas que não fizerem a alteração de fonte até mesmo na reinicialização não estiver usando a fonte de ambiente.  
  
-   Verifique se que as fontes que são derivados do serviço (por exemplo, texto em negrito ou ampliado) mantenham o tamanho e a formatação em relação ao texto "normal" quando o tamanho da fonte de ambiente é alterado.  
  
-   Verifique não se há nenhum erro de recorte devido a fontes ampliados. As fontes que fique recortadas provavelmente são o resultado de controles de altura fixa ou contêineres de altura fixa.  
  
### <a name="dialogs"></a>Diálogos  
  
-   Verifique se o título da caixa de diálogo é o mesmo que o comando que o iniciou.  
  
-   Verifique se todos os controles padrão são consistentes com o sistema operacional: cor de plano de fundo é o padrão e controles não deve ter um estilo de re-modelo especial que torna um aspecto diferente dos controles padrão.  
  
-   Verifique se margens dentro do formulário devem ser 12 pixels e devem aparecer uniforme e consistente.  
  
-   Verifique se as caixas de diálogo aparecem centralizadas no shell do IDE ou na janela que gerado-los.  
  
-   Quando úteis, caixas de diálogo devem ser redimensionáveis. Para caixas de diálogo que são redimensionáveis, verifique se que ao redimensionamento, os controles apropriados devem redimensionar enquanto outras partes da caixa de diálogo permanecem constantes.  
  
-   Verifique se as caixas de diálogo redimensionáveis manter qualquer tamanho ajustadas pelo usuário (tamanho, localização, expansão de controles de caixa de diálogo e assim por diante).  
  
-   Verifique não se há nenhum ícone na barra de título.  
  
-   Verifique não se há nenhum minimizar e maximizar botões na barra de título.  
  
#### <a name="dialog-operation-buttons-vs-client-only"></a>Botões de operação da caixa de diálogo (somente cliente VS)  
  
-   Verifique se os botões de operação são nesta ordem: **Okey**, **Cancelar**, **aplicar**.  
  
-   Verifique **Okey** e **Cancelar** botões são o tamanho padrão: 23 x 75 pixels.  
  
-   Verifique **Okey** e **Cancelar** botões são de tamanhos iguais, independentemente do comprimento da cadeia de caracteres.  
  
-   Se o rótulo em um botão de operação exige que o botão seja maior do que o padrão, verifique se que o correspondente **Cancelar** botão é de tamanho igual.  
  
-   Verifique se há um preenchimento de pixel 6 entre botões e controles associados.  
  
-   Verifique o **Okey** e **Cancelar** botões não possuem mnemônica (teclas de acesso definidas por uma letra sublinhada).  
  
-   Verifique se um botão (normalmente **Okey**) tem o foco por padrão.  
  
-   Verifique **Esc** cancela a caixa de diálogo  
  
-   Verifique **Enter** executa o botão padrão se o foco não está em um controle que processa Enter.  
  
-   Verifique o **Okey** e **Cancelar** botões estão posicionados no canto inferior direito da caixa de diálogo. Em raras exceções, é aceitável para que eles possam ser empilhados verticalmente no canto superior direito.  
  
-   Verifique se a configuração vertical é usada somente se outros botões estão em um alinhamento horizontal na caixa de diálogo.  
  
### <a name="control-standards"></a>Padrões de controle  
  
#### <a name="general"></a>Geral  
  
-   Verifique se que, quando possível, há valores padrão para acelerar a interação do usuário e direcionar os usuários para um resultado comum ou seguro.  
  
-   Verifique se os controles padrão se comportam da mesma maneira para que os usuários saibam o que acontecerá com base na experiência anterior.  
  
#### <a name="label-controls"></a>Controles de rótulo  
  
-   Verifique se cada controle tem um rótulo e que cada rótulo visualmente é associado a seu controle (geralmente em um intervalo de pixel de 4 a 6) e é mais perto de seu controle correspondente que para outros controles.  
  
-   Verifique se que os rótulos são posicionados recuo à esquerda com o controle extremidade esquerda se posicionado acima e centralizada horizontalmente, para que a linha de base do rótulo é alinhada com a linha de base de texto de entrada se posicionado à esquerda.  
  
-   Verifique se vários empilhado rótulo e controles de entrada são posicionados à esquerda de um controle, os rótulos de recuo estão à esquerda e uma distância da borda da caixa de diálogo, nunca liberar direita e uma distância igual dos controles. Pares devem ser distribuídos uniformemente, a menos que eles precisam espaçamento adicional para indicar o agrupamento.  
  
#### <a name="input-controls-text-boxes-and-combo-boxes"></a>Controles de entrada (caixas de texto e caixas de combinação)  
  
-   Verifique se que, ao usar a fonte padrão do ambiente, a altura da exibição de caixas de texto, caixas de combinação e botões são todos os 23 pixels.  
  
-   Se o texto de dica é usado, verifique se que a cor é definida como `Environment.ControlEditHintText` usando o serviço de cor.  
  
-   Se o campo é um campo obrigatório que deve ser identificado como tal, verifique se:  
  
    -   o plano de fundo definido como `Environment.ControlEditRequiredBackground` e o primeiro plano é definido como`Environment.ControlEditRequiredHintText`  
  
    -   há texto de dica dentro do controle aparece como **"\<necessária >"**  
  
#### <a name="button-controls"></a>Controles de botão  
  
-   Verifique se botões um tamanho mínimo de 75 x 23 pixels, a menos que acomodar mais texto.  
  
-   Verifique se que botões têm esquerda e direita as margens de 3 a 5 pixels, bem como preenchimento para o conteúdo.  
  
-   É aceitável usar um pequeno botão quadrado com apenas uma elipse **[...] ** nela em vez de um **[procurar...] ** botão (ou uma funcionalidade semelhante). Se usado, verifique se o botão 23 x 23 de tamanho.  
  
-   Se houver mais de um **[procurar...] ** botão em uma caixa de diálogo e, em seguida, verifique a versão abreviada (somente reticências **[...] **) é usado para todos.  
  
-   Verifique se esse botão de reticências **[...] ** botões não possuem um mnemônico. Quando o foco estiver no controle de entrada ao lado dela, uma guia deve mover o foco para o botão de reticências.  
  
-   Verifique se que os botões, comandos e links de comando que iniciam a interface de usuário secundário que captura a entrada do usuário mais deve terminar em uma elipse **[...] **.  
  
#### <a name="hyperlinks"></a>Hiperlinks  
  
-   Verifique se que um controle de hiperlink nunca pisca em vermelho quando ativo. Isso é um indicador de que o serviço de cor não está sendo usada  
  
-   Verifique se as cores do VS usadas são:  
  
    -   `Environment.ControlLinkText`  
  
    -   `Environment.ControlLinkTextHover`  
  
    -   `Environment.ControlLinkTextPressed`  
  
-   Verifique se que hiperlinks aparecem em azuis com nenhum sublinhado, a menos que incorporado em um parágrafo.  
  
#### <a name="check-boxes"></a>Caixas de seleção  
  
-   Se uma caixa de seleção tem várias linha texto, verifique se que a caixa se alinha com a primeira linha de texto, não centralizado verticalmente em todas as linhas.  
  
-   Verifique se as caixas de seleção sempre indicam uma escolha binária e não navegação do usuário ou abrir novas janelas ou páginas.  
  
-   Se uma caixa de seleção apresenta uma opção relacionada a um controle de entrada, verifique se que é posicionada recuo à esquerda e quase sob controle para indicar sua relação.  
  
-   Verifique se a caixa de seleção é **nunca** usado como um meio para habilitar todo o conteúdo de uma caixa de diálogo ou página.  
  
#### <a name="group-boxes"></a>Caixas de grupo  
  
-   Verifique se uma caixa de diálogo não contém uma caixa de grupo único dentro dele que contém todo o conteúdo da caixa de diálogo.  
  
-   Verifique se há pelo menos dois controles em cada caixa de grupo.  
  
-   Raramente deve haver mais de duas caixas de grupo em uma caixa de diálogo.  
  
-   Verifique se que não há nenhuma caixa de grupo aninhado.  
  
### <a name="icons"></a>Ícones  
  
-   Verifique se os ícones aparecem corretamente invertidos no tema no escuro.  
  
-   Verifique se que todos os ícones são baseados nos conceitos básicos.  
  
-   Verifique se cada ícone é distintos e fáceis de reconhecer e não contém mais de dois conceitos (sem modificador status/idioma).  
  
-   Verifique se o ícone de base aparece centralizado dentro do espaço.  
  
-   Verifique se todos os ícones aparecem legíveis em modo de alto contraste.  
  
-   Verifique se que qualquer cor usada se alinha com padrões de uso de cor.  
  
-   Verifique não se há nenhum halos (bordas) em torno de ícones. (Se estiver presente, o halo deve corresponder a cor de plano de fundo da interface do usuário adjacente).  
  
### <a name="touch-enabled-ui"></a>Interface do usuário sensível ao toque  
  
-   Verifique se controles interativos são grandes o suficiente para ser facilmente touchable – mínimo **23 x&23; pixels** no tamanho  
  
-   Verifique se os controles usados com mais frequência estão pelo menos **40 x&40; pixels** de tamanho.  
  
-   Verifique se controles interativos tem pelo menos **5 pixels de espaçamento** entre eles
