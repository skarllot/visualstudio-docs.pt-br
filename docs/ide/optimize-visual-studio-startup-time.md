---
title: "Otimizar o tempo de inicialização do Visual Studio | Microsoft Docs"
ms.custom: 
ms.date: 8/31/2017
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
author: mikejo
ms.author: mikejo
manager: ghogen
f1_keywords:
- vs.performancecenter
ms.translationtype: HT
ms.sourcegitcommit: 4306111cd49a5299bfa5d4e5e22b212bc7799fe2
ms.openlocfilehash: 8e419de02104d30344b32e28174bd7de41f91677
ms.contentlocale: pt-br
ms.lasthandoff: 09/06/2017

---

# <a name="optimize-visual-studio-startup-time"></a>Otimizar o tempo de inicialização do Visual Studio
Idealmente, o Visual Studio sempre deve iniciar o mais rápido possível. No entanto, extensões do Visual Studio e janelas de ferramentas abertas podem afetar o tempo de inicialização porque eles são carregados automaticamente na inicialização. A janela **Gerenciar Desempenho do Visual Studio** permite ver quais extensões e recursos afetam o tempo de inicialização do Visual Studio e controlar o comportamento de carregamento dessas extensões e recursos.

Para ver mais dicas gerais sobre como melhorar o desempenho, consulte [Dicas e truques de desempenho do Visual Studio](../ide/visual-studio-performance-tips-and-tricks.md).

## <a name="control-startup-behavior"></a>Controlar o comportamento de inicialização

Para evitar a extensão do tempo de inicialização, o Visual Studio 2017 evita carregar extensões durante a inicialização, usando uma abordagem de carregamento sob demanda. Esse comportamento significa que as extensões não abrem imediatamente após o Visual Studio ser iniciado, mas conforme necessário após a inicialização. Além disso, como as janelas de ferramentas deixadas abertas em uma sessão anterior do Visual Studio podem deixar o tempo de inicialização lento, o Visual Studio abre as janelas de ferramentas de uma maneira mais inteligente para evitar afetar o tempo de inicialização.

Se o Visual Studio detectar lentidão na inicialização, uma mensagem pop-up será exibida, alertando-o para a janela de ferramentas ou extensão que está causando a lentidão. A mensagem também fornece um link para a caixa de diálogo **Gerenciar o Desempenho do Visual Studio**. Você também pode abrir essa janela usando o comando de menu **Ajuda > Gerenciar o Desempenho do Visual Studio**.

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

## <a name="speed_up_solution_load"></a>Carregar grandes soluções mais rapidamente no Visual Studio 2017

O Visual Studio 2017 introduz um novo recurso chamado carga de solução leve, que reduz o tempo e a memória necessários para carregar soluções grandes no IDE. Se você tiver uma solução grande que contém muitos projetos C#, VB ou C++, provavelmente observará um benefício significativo do desempenho se habilitar a carga de solução leve. Para saber mais detalhadas sobre como você pode se beneficiar usando esse recurso, confira [Otimizar o carregamento de solução](../ide/optimize-solution-loading-in-visual-studio).

> [!NOTE]
> Esse conteúdo se aplica ao Visual Studio 2017 Atualização 3.

### <a name="enable-or-disable-lightweight-solution-load"></a>Habilitar ou desabilitar a carga de solução leve

Você pode clicar com o botão direito do mouse no nome da solução no Gerenciador de Soluções e selecionar **Habilitar a Carga de Solução Leve**. Depois de selecionar a opção, você precisa fechar e reabrir a solução para ativar a carga de solução leve.

![Gerenciador de Soluções](../ide/media/VSIDE_LSL_Solution_Setting.png)

Para definir as configurações globais para carga de solução leve, confira [Otimizar o carregamento de solução](../ide/optimize-solution-loading-in-visual-studio.md#global_solution_load_settings).

## <a name="see-also"></a>Consulte também
[Dicas e truques de desempenho do Visual Studio](../ide/visual-studio-performance-tips-and-tricks.md)

