---
title: "Otimizar o tempo de inicialização do Visual Studio | Microsoft Docs"
ms.custom: 
ms.date: 7/20/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- startup time [Visual Studio]
- optimizing startup time [Visual Studio]
- speed up start time [Visual Studio]
ms.assetid: d1508121-8499-4084-8eb5-fa89fa7b17d3
caps.latest.revision: 4
author: kempb
ms.author: kempb
manager: ghogen
f1_keywords:
- vs.performancecenter
ms.translationtype: HT
ms.sourcegitcommit: c3521e1de25854db012cb91bbe09d9463ecb42c7
ms.openlocfilehash: af1ff0dbeeb30e6b3169c6a94dab8da50085bf20
ms.contentlocale: pt-br
ms.lasthandoff: 07/21/2017

---

# <a name="optimize-visual-studio-startup-time"></a>Otimizar o tempo de inicialização do Visual Studio
Idealmente, o Visual Studio sempre deve iniciar o mais rápido possível. No entanto, extensões do Visual Studio e janelas de ferramentas abertas podem afetar o tempo de inicialização porque eles são carregados automaticamente na inicialização. A janela **Gerenciar Desempenho do Visual Studio** permite ver quais extensões e recursos afetam o tempo de inicialização do Visual Studio e controlar o comportamento de carregamento dessas extensões e recursos.

## <a name="control-startup-behavior"></a>Controlar o comportamento de inicialização

Para evitar a extensão do tempo de inicialização, o Visual Studio 2017 evita carregar extensões durante a inicialização, usando uma abordagem de carregamento sob demanda. Esse comportamento significa que as extensões não abrem imediatamente após o Visual Studio ser iniciado, mas conforme necessário após a inicialização. Além disso, como as janelas de ferramentas deixadas abertas em uma sessão anterior do Visual Studio podem deixar o tempo de inicialização lento, o Visual Studio abre as janelas de ferramentas de uma maneira mais inteligente para evitar afetar o tempo de inicialização.

Se o Visual Studio detectar lentidão na inicialização, uma mensagem pop-up será exibida, alertando-o para a janela de ferramentas ou extensão que está causando a lentidão. A mensagem também fornece um link para a caixa de diálogo **Gerenciar o Desempenho no Visual Studio**, que também pode ser aberta usando o comando de menu **Ajuda > Gerenciar o Desempenho do Visual Studio**.

![Gerenciar o Desempenho do Visual Studio – pop-up indicando "Observamos que a extensão ... está deixando o Visual Studio mais lento"](../ide/media/vside_perfdialog_popup.png)

A caixa de diálogo lista as janelas de ferramentas e extensões que estão afetando o desempenho de inicialização. Essa caixa de diálogo permite que você altere as configurações de janela de ferramentas e extensão para melhorar o desempenho de inicialização.

### <a name="change-extension-settings"></a>Alterar as configurações de extensão

Se uma extensão estiver tornando a inicialização do Visual Studio lenta, a extensão aparecerá na caixa de diálogo **Gerenciar o Desempenho do Visual Studio** quando você escolher um dos tipos de extensão. A caixa de diálogo mostra quais extensões afetam o desempenho na inicialização, ao carregar uma solução e ao digitar no editor.

![Gerenciar o Desempenho do Visual Studio – exibição de extensões](../ide/media/vside_perfdialog_extensions.png)

Se o impacto na inicialização, carregamento da solução ou tempo de digitação for inaceitavelmente alto, desabilite a extensão para esse cenário selecionando o botão **Desabilitar**. Você pode sempre habilitar novamente a extensão para sessões futuras usando o Gerenciador de Extensões ou a caixa de diálogo Gerenciar o Desempenho do Visual Studio.

### <a name="change-tool-window-settings"></a>Alterar as configurações da janela de ferramentas

Se uma janela de ferramentas estiver retardando a inicialização do Visual Studio e você quiser alterar o impacto, é possível substituir o comportamento dela escolhendo uma das opções em vez de **Usar o comportamento padrão**:

- **Não mostrar janela na inicialização:** a janela de ferramentas especificada sempre estará fechada ao abrir o Visual Studio, mesmo se ela for deixada aberta em uma sessão anterior. Você pode abrir a janela de ferramentas no menu apropriado.
- **Ocultar automaticamente janela na inicialização:** se uma janela de ferramentas tiver sido deixada aberta em uma sessão anterior, essa opção recolherá o grupo da janela de ferramentas na inicialização para evitar inicializar a janela de ferramentas. Essa é uma boa opção se você usar uma janela de ferramentas com frequência, pois a janela de ferramentas ainda estará disponível, mas não afetará negativamente o tempo de inicialização do Visual Studio.

![Gerenciar o Desempenho do Visual Studio – exibição da janela de ferramentas](../ide/media/vside_perfdialog_toolwindows.png)

Você poderá retornar a este diálogo a qualquer momento para alterar as configurações de qualquer janela de ferramentas.

## <a name="speed-up-solution-load"></a>Acelerar o carregamento da solução

O Visual Studio 2017 suporta **carga de solução leve**, que reduz o tempo e a memória necessários para carregar soluções grandes no IDE. Se você tiver uma solução grande que contém muitos projetos C#, VB e/ou C++, provavelmente observará um benefício significativo do desempenho se habilitar a carga de solução leve.

Como alguns recursos do IDE não estão totalmente disponíveis quando a carga de solução leve está habilitada, o recurso é desativado por padrão. As seções a seguir o ajudarão a decidir se deve ou não habilitar esse recurso.

### <a name="enable-lightweight-solution-load"></a>Habilitar a carga de solução leve

Você pode habilitar a carga de solução leve para o IDE como um todo ou para soluções individuais.

Para alterar a carga de solução leve para configurações de todos os projetos e soluções, acesse **Ferramentas > Opções > Projetos e Soluções > Geral** e selecione uma das três opções de carregamento:

![Caixa de diálogo Opções de Ferramentas](../ide/media/VSIDE_LightweightSolutionLoad.png)

- **Deixar o Visual Studio escolher o que é melhor para minha solução:** o Visual Studio determina automaticamente se deve aplicar o carregamento de solução leve analisando cada solução quando você abri-las. 
- **Habilitar:** a carga de solução leve será habilitada para esta solução, independentemente da configuração de todo o IDE.
- **Desabilitar:** a carga de solução leve será desabilitada para esta solução, independentemente da configuração de todo o IDE.

Para habilitar a carga de solução leve para uma solução individual, selecione o nó da solução de nó superior no Gerenciador de Soluções. Na janela **Propriedades**, escolha **Padrão**, **Habilitar** ou **Desabilitar** para a propriedade **Carga leve**.

![Gerenciador de Soluções](../ide/media/VSIDE_LSL Solution Setting.png)

Você também pode clicar com o botão direito no nó da solução no Gerenciador de Soluções e selecionar **Habilitar a Carga de Solução Leve** (se o recurso estiver desabilitado no momento) ou **Desabilitar a Carga de Solução Leve** (se o recurso estiver habilitado no momento):

Quando você altera a configuração da carga de solução leve, a alteração entra em vigor na próxima vez em que a solução for carregada. Não é necessário reiniciar o IDE.

### <a name="automatically-enable-lightweight-solution-load"></a>Habilitar a carga de solução leve automaticamente

Ao abrir uma solução grande no Visual Studio 2017, você poderá ver uma mensagem pop-up oferecendo para habilitar a carga de solução leve. A mensagem só será exibida para soluções que contêm vários projetos C#, VB ou C++. Escolher **habilitar** ativará a carga de solução leve apenas para aquela solução. A configuração de todo o IDE não será alterada.

![Janela pop-up](../ide/media/VSIDE_LSL Popup.png)

Você pode desabilitar a carga de solução leve posteriormente na janela **Propriedades** da solução.

### <a name="limitations"></a>Limitações

A maioria dos recursos do IDE estão totalmente disponíveis quando a carga de solução leve está habilitada. No entanto, alguns recursos do IDE e extensões de terceiros podem não ser totalmente compatíveis.  Os recursos a seguir são conhecidos por não funcionar quando a carga de solução leve está habilitada:

- Algumas extensões de terceiros podem não se comportar da forma esperada quando a carga de solução leve está habilitada.
- Editar e continuar não funcionam em projetos que não são carregados ao iniciar a depuração. Os arquivos contidos no projeto serão somente leitura e será relatado um erro de que o projeto não foi carregado se houver a tentativa de realizar uma edição.
- Quando a carga da solução leve está habilitada, os projetos do F# podem não ser compilados corretamente e os símbolos podem não estar totalmente disponíveis em GoTo.

