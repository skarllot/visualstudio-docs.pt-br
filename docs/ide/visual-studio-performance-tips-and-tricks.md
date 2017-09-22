---
title: Dicas e truques de desempenho do Visual Studio | Microsoft Docs
ms.date: 08/31/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- debugger
ms.assetid: 2fbcb59e-e981-4b40-8b7a-c1140d31ec4b
caps.latest.revision: 1
author: gewarren
ms.author: gewarren
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: HT
ms.sourcegitcommit: 4306111cd49a5299bfa5d4e5e22b212bc7799fe2
ms.openlocfilehash: fbaa543564506a99d3ed6833ec4d1f692fae43f7
ms.contentlocale: pt-br
ms.lasthandoff: 09/06/2017

---
# <a name="visual-studio-performance-tips-and-tricks"></a>Dicas e truques de desempenho do Visual Studio

As recomendações de desempenho do Visual Studio destinam-se a situações de baixa memória, o que podem ocorrer em casos raros. Nessas situações, é possível otimizar determinados recursos do Visual Studio que você talvez não esteja usando. As dicas a seguir não devem ser consideradas como as recomendações gerais.

> [!NOTE]
> Se você estiver tendo dificuldades para usar o produto devido a problemas de memória, conte para nós pela ferramenta de comentários.

## <a name="optimize-your-environment"></a>Otimizar seu ambiente

- **Usar um sistema operacional de 64 bits**

    Se você atualizar seu sistema de uma versão de 32 bits do Windows para uma versão de 64 bits, expanda a quantidade de memória virtual disponível para o Visual Studio de 2 GB para 4 GB. Isso permite que o Visual Studio lide com cargas de trabalho significativamente maiores, mesmo sendo um processo de 32 bits.

    Para obter mais informações, consulte [Limites de memória](https://msdn.microsoft.com/en-us/library/windows/desktop/aa366778(v=vs.85).aspx#memory_limits) e [Usando /LARGEADDRESSAWARE no Windows de 64 bits](https://blogs.msdn.microsoft.com/oldnewthing/20050601-24/?p=35483/).

## <a name="configure-solution-and-projects"></a>Configurar solução e projetos

Se você tiver uma solução muito grande com vários projetos, poderá ser útil fazer as seguintes otimizações:

- **Habilitar a carga de solução leve**

    Usar a **Carga de solução leve** pode melhorar o desempenho de CPU e de memória, adiando a carga de alguns projetos na solução. Também é possível habilitar esse recurso por solução. Essa opção fica desativada por padrão.

    Para habilitar a **Carga de solução leve**, escolha **Ferramentas > Opções > Projetos e Soluções > Carga de solução leve**.

    Alguns recursos IDE não estão habilitados nesse modo. Para determinar se essa opção pode ajudar, confira [Tempo mais curto da carga de solução](https://blogs.msdn.microsoft.com/visualstudio/2016/10/11/shorter-solution-load-time-in-visual-studio-15/) e [Otimizar carregamento da solução](../ide/optimize-solution-loading-in-visual-studio).

- **Descarregar projetos**

    Você pode descarregar manualmente projetos individuais raramente usados no Gerenciador de Soluções usando o menu de contexto do clique com o botão direito do mouse.

- **Refatorar a solução**

    Você pode dividir a solução em vários arquivos menores de solução com projetos usados com frequência. Esta refatoração deve reduzir significativamente o uso de memória para o fluxo de trabalho. Soluções menores também são carregadas mais rapidamente.

## <a name="configure-debugging-options"></a>Configurar as opções de depuração
Se você tem ficado com pouca memória durante as sessões de depuração normalmente, você pode otimizar o desempenho fazendo uma ou mais alterações de configuração.

- **Habilitar Apenas Meu Código**

    A otimização mais simples é habilitar o recurso **Apenas Meu Código**, que só carrega símbolos para o seu projeto. Habilitar esse recurso pode resultar em uma economia significativa de memória para depurar aplicativos gerenciados (.NET). Esta opção já fica habilitada por padrão em alguns tipos de projeto.

    Para habilitar o **Apenas Meu Código**, escolha **Ferramentas > Opções > Depuração > Geral** e selecione **Habilitar Apenas Meu Código**.

- **Especificar os símbolos a serem carregados**

    Para depuração nativa, o carregamento de arquivos de símbolo (.pdb) é caro em termos de recursos de memória. Você pode definir as configurações de símbolo de depuração para economizar memória. Normalmente, você pode configurar a solução para carregar somente os módulos do seu projeto.

    Para especificar o carregamento de símbolos, escolha **Ferramentas > Opções > Depuração > Símbolos**.

    Defina as opções para **Somente os módulos especificados** em vez de **Todos os módulos** e, em seguida, especifique quais módulos você deseja carregar. Durante a depuração, você também pode clicar com o botão direito do mouse em módulos específicos na janela **Módulos** para incluir explicitamente um módulo no carregamento de símbolo. (Para abrir a janela durante a depuração, escolha **Depurar > Windows > Módulos**.)

    Para saber mais, consulte [Noções básicas sobre arquivos de símbolos](https://blogs.msdn.microsoft.com/visualstudioalm/2015/01/05/understanding-symbol-files-and-visual-studios-symbol-settings/).

- **Desabilitar Ferramentas de Diagnóstico**

    É recomendável desabilitar a criação de perfil de CPU após o uso. Esse recurso pode consumir grandes quantidades de recursos. Quando a criação de perfil de CPU está habilitada, esse estado é mantido nas sessões de depuração subsequentes, por isso vale a pena desativá-lo explicitamente após terminar. Você pode economizar alguns recursos desabilitando as ferramentas de diagnóstico durante a depuração se você não precisar dos recursos fornecidos.

    Para desabilitar as Ferramentas de Diagnóstico, inicie uma sessão de depuração, escolha **Ferramentas > Opções > Habilitar Ferramentas de Diagnóstico** e desmarque a opção.

    Para obter mais informações, consulte [Ferramentas de Criação de Perfil](https://docs.microsoft.com/en-us/visualstudio/profiling/profiling-tools).

## <a name="disable-tools-and-extensions"></a>Desabilitar ferramentas e extensões
Algumas ferramentas ou extensões podem desativadas para melhorar o desempenho.

> [!TIP]
> Geralmente, é possível isolar problemas de desempenho desativando as extensões, uma por vez e verificando novamente o desempenho.

### <a name="managed-language-services-roslyn"></a>Serviços de linguagem gerenciados (Roslyn)

Para obter mais informações sobre as considerações de desempenho do Roslyn, consulte [Considerações de desempenho para grandes soluções] (https://github.com/dotnet/roslyn/wiki/Performance-considerations-for-large-solutions).

- **Desabilitar análise de solução completa**

    O Visual Studio executa a análise em toda a sua solução para proporcionar uma experiência avançada sobre os erros antes de invocar um build. Esse recurso é útil para identificar erros assim que possível. No entanto, para soluções muito grandes, esse recurso pode consumir recursos significativos de memória. Se você estiver tendo problemas semelhantes ou pressão de memória, desabilite essa experiência para liberar esses recursos. Por padrão, essa opção é habilitada para o Visual Basic e desabilitada para C#.

    Para desabilitar a **Análise completa da solução**, escolha **Ferramentas > Opções > Editor de texto ><Visual Basic ou C#>**. Em seguida, escolha **Avançado** e desmarque **Habilitar análise de solução completa**.

- **Desabilitar CodeLens**

    O Visual Studio executa uma tarefa **Localizar todas as referências** em cada método como exibido. O CodeLens fornece recursos como a exibição embutida do número de referências. O trabalho é executado em um processo separado (por exemplo, ServiceHub.RoslynCodeAnalysisService32). Em soluções muito grandes ou em sistemas com recursos restritos, esse recurso pode impactar significativamente o desempenho, mesmo que seja executado em uma prioridade baixa. Se estiver enfrentando alta utilização da CPU neste processo ou problemas de memória (por exemplo, ao carregar uma solução grande em um computador de 4 GB), você poderá tentar desabilitar esse recurso para liberar recursos.

    Para desabilitar o CodeLens, escolha **Ferramentas > Opções > Editor de texto > Todas as linguagens > CodeLens** e desmarque o recurso.

    O recurso está disponível apenas no Visual Studio Professional e no Visual Studio Enterprise.

### <a name="other-tools-and-extensions"></a>Outras ferramentas e extensões

- **Desabilitar extensões**

    Extensões são componentes de software adicionais acrescentados ao Visual Studio que fornecem uma funcionalidade nova ou estendem a funcionalidade existente. Extensões geralmente podem ser uma fonte de problemas de recursos de memória. Se você estiver tendo problemas de recursos de memória, tente desabilitar as extensões, uma por vez, para ver como ele afeta o cenário ou o fluxo de trabalho.

    Para desabilitar as extensões, acesse **Ferramentas | Extensões e Atualizações** e desabilite uma extensão específica.

- **Desabilitar o XAML Designer**

    O XAML Designer é habilitado por padrão, mas só consumirá recursos se você abrir um arquivo .XAML. Se você trabalha com arquivos XAML, mas não quer usar a funcionalidade do designer, desabilite esse recurso para liberar memória.

    Para desabilitar o XAML Designer, acesse **Ferramentas > Opções > XAML Designer > Habilitar XAML Designer** e desmarque a opção.

- **Remover as cargas de trabalho**

    Você pode usar o Instalador do Visual Studio para remover as cargas de trabalho que não são mais usadas. Esta ação pode simplificar o custo de inicialização e do tempo de execução ignorando pacotes e assemblies que não são mais necessários.

## <a name="force-a-garbage-collection"></a>Forçar uma coleta de lixo

O CLR usa um sistema de gerenciamento de memória de coleta de lixo. Nesse sistema, às vezes a memória é usada pelos objetos que não são mais necessários. Esse estado é temporário. O coletor de lixo liberará esta memória com base em seu desempenho e a heurística de uso de recursos. Você pode forçar o CLR a coletar a memória não utilizada usando uma tecla de atalho no Visual Studio. Se houver uma quantidade significativa de lixo aguardando a coleta e você forçar uma coleta de lixo, você verá o uso de memória do processo devenv.exe ser deixado no Gerenciador de Tarefas. Raramente é necessário usar esse método. No entanto, após uma operação cara (como um build completo, sessão de depuração ou um evento de abertura de solução), ele pode ajudar a determinar a quantidade de memória que realmente está sendo usado pelo processo. Como o Visual Studio é misto (gerenciado e nativo), geralmente é possível que o alocador nativo e o coletor de lixo disputem pelos recursos de memória limitada. Em condições de alto uso de memória, pode ser útil forçar o coletor de lixo a ser executado.

Para forçar uma coleta de lixo, use a tecla de atalho: **Ctrl+Alt + Shift + F12**, **Ctrl + Alt + Shift + F12** (pressione duas vezes).

Se forçar a coleta de lixo de forma confiável faz seu cenário funcionar, relate isso na ferramenta de comentários do Visual Studio, pois esse comportamento provavelmente trata-se de um bug.

Para ver uma descrição detalhada do coletor de lixo CLR, consulte [Noções básicas da coleta de lixo](https://msdn.microsoft.com/en-us/library/ee787088(v=vs.110).aspx).

## <a name="see-also"></a>Consulte também  
 [Visual Studio IDE](../ide/index.md)

