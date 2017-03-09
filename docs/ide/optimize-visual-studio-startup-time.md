---
title: "Otimizar o tempo de inicialização do Visual Studio | Microsoft Docs"
ms.custom: 
ms.date: 01/09/2016
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
translationtype: Human Translation
ms.sourcegitcommit: ba88bad0753653dcde8a4d28b4dd1c71522d6506
ms.openlocfilehash: 435197f1536dc9006691c0f2e58fafd0fcf27718
ms.lasthandoff: 02/22/2017

---
# <a name="optimize-visual-studio-startup-time"></a>Otimizar o tempo de inicialização do Visual Studio
Idealmente, o Visual Studio sempre deve iniciar o mais rápido possível. No entanto, extensões do Visual Studio e janelas de ferramentas abertas podem afetar o tempo de inicialização porque eles são carregados automaticamente na inicialização. A janela **Gerenciar o Desempenho do Visual Studio** permite que você não apenas veja quais extensões e recursos afetam o tempo de inicialização do Visual Studio, mas também permite que você determine o comportamento de carregamento para ter mais controle sobre quão rapidamente o Visual Studio é iniciado.

## <a name="control-startup-behavior"></a>Controlar o comportamento de inicialização

Para evitar a estender o tempo de inicialização, o Visual Studio 2017 RC evita carregar extensões durante a inicialização, usando uma abordagem de carregamento sob demanda. Isso significa que as extensões não abrem imediatamente após o Visual Studio ser iniciado, mas abrem de forma assíncrona conforme o necessário após a inicialização. Além disso, como as janelas de ferramentas deixadas abertas em uma sessão anterior do Visual Studio podem deixar o tempo de inicialização lento, o Visual Studio abre as janelas de ferramentas de uma maneira mais inteligente para evitar afetar o tempo de inicialização.

Se o Visual Studio detectar lentidão na inicialização, uma mensagem pop-up será exibida, alertando-o para a janela de ferramentas ou extensão que está causando a lentidão. A mensagem também fornece um link para a caixa de diálogo **Gerenciar o Desempenho do Visual Studio**, que lista as extensões e janelas de ferramentas que estão afetando o desempenho de inicialização. Essa caixa de diálogo permite que você altere as configurações de janela de ferramentas e extensão para melhorar o desempenho de inicialização.

![Gerenciar o Desempenho do Visual Studio – pop-up](../ide/media/vside_perfdialog_popup.PNG "Gerenciar o Desempenho do Visual Studio – pop-up")

A caixa de diálogo **Gerenciar o Desempenho do Visual Studio** tem duas categorias: **Extensões** e **Janelas de Ferramentas**.

### <a name="control-extensions"></a>Controlar extensões
Se uma extensão estiver tornando a inicialização do Visual Studio lenta, a extensão aparecerá na caixa de diálogo **Gerenciar o Desempenho do Visual Studio** quando você escolher um dos tipos de extensão. Se o impacto no tempo de inicialização (que está listado na seção **Impacto**) estiver inaceitavelmente alto, você poderá optar por sempre desabilitar a extensão na inicialização escolhendo o botão **Desabilitar**. Você pode habilitar novamente a extensão para sessões futuras usando o Gerenciador de Extensões ou a caixa de diálogo Gerenciar o Desempenho do Visual Studio.

![Gerenciar o Desempenho do Visual Studio – extensões](../ide/media/vside_perfdialog_extensions.PNG "Gerenciar o Desempenho do Visual Studio – extensões")

Além das extensões de inicialização, você também pode desabilitar extensões que são carregadas quando as soluções são carregadas ou quando um usuário digita. Basta escolha o cenário para ver uma lista das extensões associadas.

### <a name="control-tool-windows"></a>Controlar as janelas de ferramentas
Se uma janela de ferramentas estiver tornando a inicialização do Visual Studio lenta, você poderá optar por deixá-la com seu comportamento padrão (não fornecendo nenhum benefício na velocidade de inicialização) ou pode substituir seu comportamento escolhendo um dos dois comportamentos:

- **Não mostrar janela na inicialização:** se você escolher essa opção, a janela de ferramentas especificada sempre estará fechada ao abrir o Visual Studio, mesmo se ala for deixada aberta em uma sessão anterior. Você pode abrir a janela de ferramentas no menu.
- **Ocultar automaticamente janela na inicialização:** se uma janela de ferramentas tiver sido deixada aberta em uma sessão anterior, escolher essa opção recolherá o grupo da janela de ferramentas na inicialização para evitar inicializar a janela de ferramentas. Essa é uma boa opção se você usar uma janela de ferramentas com frequência, pois a janela de ferramentas ainda estará disponível, mas não afetará negativamente o tempo de inicialização do Visual Studio.

![Gerenciar o Desempenho do Visual Studio – janelas de ferramentas](../ide/media/vside_perfdialog_toolwindows.PNG "Gerenciar o Desempenho do Visual Studio – janelas de ferramentas")

Se posteriormente você mudar de ideia, poderá reverter qualquer uma dessas opções na caixa de diálogo **Gerenciar o Desempenho do Visual Studio**. Para abrir a caixa de diálogo **Gerenciar o Desempenho do Visual Studio**, na barra de menus, escolha **Ajuda**, **Gerenciar o Desempenho do Visual Studio**.

## <a name="speed-up-solution-load"></a>Acelerar o carregamento da solução

O Visual Studio 2017 RC introduz um novo recurso chamado **carga de solução leve** que reduz a quantidade de tempo e memória necessárias para carregar soluções grandes no IDE. Se você tiver uma solução grande que contém muitos projetos C#, VB ou C++, provavelmente observará um benefício significativo do desempenho se habilitar a carga de solução leve.

Como alguns recursos do IDE não estão totalmente disponíveis quando a carga de solução leve está habilitada, o recurso é desativado por padrão. As seções a seguir o ajudarão a decidir se deve ou não habilitar esse recurso.

### <a name="enable-lightweight-solution-load"></a>Habilitar a carga de solução leve

Você pode habilitar a carga de solução leve para o IDE como um todo ou para soluções individuais. Para habilitar a carga de solução leve para todo o IDE, vá para **Ferramentas**, **Opções** e vá para a seção **Projetos e Soluções**.

![Caixa de diálogo Opções de Ferramentas](../ide/media/VSIDE_LightweightSolutionLoad.png)

Para habilitar a carga de solução leve para uma solução individual, escolha o nó da solução de nó superior no Gerenciador de Soluções.  Na janela Propriedades, escolha um dos seguintes valores para a propriedade **Carregamento leve**.

- **Habilitado:** a carga de solução leve será habilitada para esta solução, independentemente da configuração de todo o IDE.
- **Desabilitado:** a carga de solução leve será desabilitada para esta solução, independentemente da configuração de todo o IDE.
- **Padrão:** o comportamento da carga de solução leve passará para a configuração de todo o IDE.

![Gerenciador de Soluções](../ide/media/VSIDE_LSL Solution Setting.png)

Quando você altera a configuração da carga de solução leve, a alteração entra em vigor na próxima vez em que a solução for carregada. Não é necessário reiniciar o IDE.

### <a name="automatically-enable-lightweight-solution-load"></a>Habilitar a carga de solução leve automaticamente

Quando você abre uma solução grande no Visual Studio 2017 RC, pode ver uma mensagem pop-up oferecendo para habilitar a carga de solução leve. A mensagem é exibida somente para soluções que contêm vários projetos C#, VB ou C++. Escolher o comando **habilitar** habilitará a carga de solução leve apenas para aquela solução. A configuração de todo o IDE não será alterada.

![Janela pop-up](../ide/media/VSIDE_LSL Popup.png)

Você pode desabilitar a carga de solução leve posteriormente na janela Propriedades da solução.

### <a name="lightweight-solution-load-limitations"></a>Limitações da carga de solução leve
A maioria dos recursos do IDE estão totalmente disponíveis quando a carga de solução leve está habilitada. No entanto, alguns recursos do IDE e extensões de terceiros podem não ser totalmente compatíveis.  Os recursos a seguir são conhecidos por não funcionar quando a carga de solução leve está habilitada:

#### <a name="third-party-extensions"></a>Extensões de terceiros
Algumas extensões podem não se comportar da forma esperada quando a carga de solução leve está habilitada.

#### <a name="edit-and-continue"></a>Editar e continuar
Editar e continuar não funcionam em projetos que não são carregados ao iniciar a depuração. Os arquivos contidos no projeto serão somente leitura e será relatado um erro de que o projeto não foi carregado se houver a tentativa de realizar uma edição.

#### <a name="f-support"></a>Suporte do F#
Quando a carga da solução leve está habilitada, os projetos do F# podem não ser compilados corretamente e os símbolos podem não estar totalmente disponíveis em GoTo.

