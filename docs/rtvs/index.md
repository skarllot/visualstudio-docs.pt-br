---
title: Ferramentas R para Visual Studio | Microsoft Docs
ms.custom: 
ms.date: 6/29/2017
ms.prod: visual-studio-dev15
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-r
ms.devlang: r
ms.tgt_pltfrm: 
ms.topic: hero-article
ms.assetid: 11324501-ceb6-47a2-ae13-e9e992d3603e
caps.latest.revision: 1
author: kraigb
ms.author: kraigb
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 712cc780388acc5e373f71d51fc8f1f42adb5bed
ms.openlocfilehash: 80a10c710aac8413bd59b53bb61de7a982c09952
ms.contentlocale: pt-br
ms.lasthandoff: 07/12/2017

---

# <a name="working-with-r-in-visual-studio"></a>Trabalho com o R no Visual Studio

O R é uma linguagem altamente extensível e um ambiente para gráficos e computação estatística. Ele é distribuído gratuitamente sob a Licença Pública Geral GNU, dispõe de suporte à comunidade forte e é conhecido por sua capacidade de gerar plotagens de qualidade de publicação incluindo fórmulas e símbolos matemáticos. Você pode saber mais sobre o R em [r-project.org](https://www.r-project.org/about.html) e [Uma introdução ao R](https://cran.r-project.org/doc/manuals/r-release/R-intro.html).

As Ferramentas R para Visual Studio (RTVS) são uma extensão de [código-fonte aberto](https://github.com/microsoft/RTVS) gratuita para Visual Studio 2017 e Visual Studio 2015 Atualização 3 (ou superior), lançado sob a licença MIT. (Um segundo componente de código-fonte aberto chamado [RHost](https://github.com/microsoft/R-Host), que é vinculado aos binários do interpretador do R, é lançado sob a Licença Pública GNU V2.)

Para experimentar o R no Visual Studio:

- [Instalar as Ferramentas R](installation.md).
- Siga o guia de [Introdução](getting-started-with-r.md), bem como os tópicos [Exemplos](getting-started-samples.md) e [Obtendo ajuda](getting-started-help.md).

Depois, siga os links para saber mais sobre recursos relacionados ao R, bem como os próprios recursos gerais do Visual Studio.

| Recurso | Descrição | Documentação geral do Visual Studio | 
| --- | --- | --- |
| [Sistema de projeto do Visual Studio](projects.md) | Organize e gerencie arquivos relacionados em uma estrutura conveniente e aproveite modelos úteis para itens como código do R, documentação do R, Markdown do R, consultas SQL e procedimentos armazenados. Aproveite também o [gerenciador de pacotes](package-manager.md) e a [integração do SQL Server](sql-server.md).  | [Soluções e projetos no Visual Studio](../ide/solutions-and-projects-in-visual-studio.md) |
| [Espaço de trabalho](workspaces.md) | As RTVS podem ser associadas a espaços de trabalho locais e remotos, permitindo que você desenvolva o código R localmente com conjuntos de dados menores, em seguida, execute com facilidade o código em computadores baseados em nuvem mais poderosos com conjuntos de dados muito maiores. | N/D |
| [Opções de Ferramentas R](options.md) | Controle vários aspectos das RTVS. | [Caixa de diálogo de opções](../ide/reference/options-dialog-box-visual-studio.md) |
| [Edição avançada, IntelliSense, e trechos de código](code-editing.md) | Inclui coloração de sintaxe, [IntelliSense](code-intellisense.md) em todo o código e todas as bibliotecas, formatação de código, ajuda da assinatura, comandos Ir Para Definição e Localizar Todas as Referências, [trechos de código](code-snippets.md) e muito mais. | [Escrevendo código no editor de códigos e de texto](../ide/writing-code-in-the-code-and-text-editor.md) |
| [Markdown do R](rmarkdown.md) | Os documentos de Markdown do R ajudam você a compartilhar os resultados de dados, com código R integrado dentro dos blocos de código de markdown. | N/D |
| [Janela Interativa](interactive-repl.md) | Fornece uma experiência completa de REPL para o R com a capacidade de executar facilmente o código em um arquivo de origem na janela interativa. | N/D |
| [Visualização de dados](visualizing-data.md) | A plotagem é parte integral da experiência do R, e as RTVS oferece suporte a várias janelas de plotagem independentes, cada qual com seu próprio histórico e a capacidade de mover as plotagens entre as janelas. As plotagens podem ser salvas em bitmap e arquivos PDF ou copiadas para a área de transferência como um bitmap ou metarquivo.  | N/D |
| [Gerenciador de Variáveis](variable-explorer.md) | Examine as variáveis em escopos globais ou específicos do pacote, com a possibilidade de exibir tabelas classificáveis e exportar para CSV. | N/D |
| [Depuração completa](debugging.md) | Inclui a integração com a janela interativa. | [Depurando no Visual Studio](../debugger/debugging-in-visual-studio.md) |

O vídeo a seguir também oferece uma breve análise (5m 48s) dos recursos das Ferramentas R:

> [!VIDEO https://www.youtube.com/embed/RcSDEfMgUvU]

## <a name="frequently-asked-questions"></a>Perguntas frequentes

**P. As RTVS funcionam com edições do Visual Studio Express?**

R. Nº

**P. Com quais intérpretes do R as RTVS funcionam?**

R. [CRAN R](https://cran.r-project.org/), [Microsoft R Client e Microsoft R Server](https://msdn.microsoft.com/microsoft-r/)

**P. Onde posso baixar esses intérpretes?**

R. Veja [Instalação](installation.md).

**P. Posso usar extensões do Visual Studio com as RTVS?**

R. Com certeza. Na verdade, aqui estão algumas opções que são comuns para pessoas que trabalham com o R.

- [VsVim para associações de chave vim](https://marketplace.visualstudio.com/items?itemName=JaredParMSFT.VsVim)
- [Github](https://marketplace.visualstudio.com/items?itemName=GitHub.GitHubExtensionforVisualStudio)
- [Editor de markdown com visualização em tempo real](https://marketplace.visualstudio.com/items?itemName=MadsKristensen.MarkdownEditor)

Veja o [Visual Studio Marketplace](https://marketplace.visualstudio.com/) para saber mais.

**P. Como as RTVS estão no Visual Studio, isso significa que o R pode ser facilmente usado com o C#, C++ e outras linguagens da Microsoft?**

R. Nº As RTVS são uma ferramenta para desenvolver código R e usa os intérpretes nativos de R padrão. Atualmente, não há suporte para interoperabilidade entre o R e outras linguagens.

**P. O recurso X está ausente, mas o RStudio o tem!**

R. O RStudio é um IDE fantástico e maduro para R que vem sendo desenvolvido há vários anos. As RTVS procuram ter todos os recursos mais importantes que você precisa para ser bem-sucedido. Ajude a priorizar futuros trabalhos por meio da [Pesquisa de RTVS](https://www.surveymonkey.com/r/RTVS1).

**P. As RTVS funciona no OS X ou no Linux?**

R. Não, as RTVS se baseiam no Visual Studio, que é uma implementação somente do Windows. Dito isso, a Microsoft está investigando a criação de um novo conjunto de ferramentas com base no [Visual Studio Code](https://code.visualstudio.com/), o editor entre plataformas popular da Microsoft.

**P. Posso contribuir para RTVS?**

R. Claro! O código-fonte reside no [Github](https://github.com/microsoft/RTVS). Use o rastreador de problemas para enviar bugs e comentar sobre aqueles já arquivados.

Você também pode contribuir com esta documentação &mdash; basta selecionar o comando **Editar** no canto superior direito de qualquer página. Os comentários sobre os documentos também são bem-vindos, os quais você pode adicionar à parte inferior de qualquer página.

**P. As RTVS funcionam com meu sistema de controle do código-fonte?**

R. Sim, você pode usar qualquer sistema de controle do código-fonte que esteja integrado ao Visual Studio.

**P. O RTVS funciona com uma localidade diferente do inglês?**

R. A versão 1.0 do RTVS será somente em inglês. A versão 1.1 será localizado para o mesmo conjunto de idiomas do Visual Studio. Enquanto isso, use o [Pacote do idioma inglês para o Visual Studio 2015](https://www.microsoft.com/download/details.aspx?id=48157) ou, no Visual Studio 2017, execute o instalador e selecione inglês na guia **Pacotes de idiomas**.

![Configurações internacionais do Visual Studio 2017](~/rtvs/media/FAQ-international-settings.png)

**P. As RTVS funcionarão com as edições de 32 bits do R?**

R. Não, as RTVS só dão suporte às edições de 64 bits do R em execução em edições de 64 bits do Windows.

**P. Eu gosto muito das minhas configurações atuais do Visual Studio, mas desejo testar as novas configurações de Ciência de Dados. O que devo fazer?**

R. Salve suas configurações atuais do Visual Studio usando **Ferramentas > Importar e Exportar Configurações...** e, em seguida, mude para as configurações de Ciência de Dados. Para restaurar as configurações salvas, use o comando **Importar e Exportar Configurações...** novamente.

**P. Quais são as configurações `.gitignore` recomendadas para um projeto das RTVS?**

R. O Github mantém um repositório de arquivos `.gitignore` recomendados. Você pode vê-lo aqui: [.gitignore do R](https://github.com/github/gitignore/blob/master/R.gitignore)

**P. Posso armazenar meu projeto do Visual Studio em um compartilhamento de rede?**

R. Não, o Visual Studio não dá suporte ao carregamento de projetos de um compartilhamento de rede.

## <a name="send-us-your-feedback"></a>Envie-nos seus comentários!

1. **Problemas do Github**: a melhor maneira de alcançar a equipe de RTVS é [registrar um problema no GitHub](https://github.com/Microsoft/RTVS/issues) ou usar o menu **Ferramentas R > Comentários**.

1. **Envie um Smiley/Rosto Triste**: o menu **Ferramentas R > Comentários** é uma maneira rápida de enviar comentários e anexar arquivos de log das RTVS para auxiliar no diagnóstico do seu problema. (Os logs serão registrados nos `%temp%/RTVSlogs.zip` caso você queira enviá-los separadamente.) O log será desabilitado se você tiver cancelado a telemetria do Visual Studio por meio do comando de menu **Ajuda > Comentários > Configurações** ou durante a instalação.

1. **Email**: você pode enviar comentários diretos para a equipe em *rtvsuserfeedback (arroba) microsoft.com*.

