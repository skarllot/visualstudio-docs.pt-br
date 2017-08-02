---
title: Visualizando dados com as Ferramentas do R para Visual Studio | Microsoft Docs
ms.custom: 
ms.date: 5/1/2017
ms.prod: visual-studio-dev15
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-r
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 
caps.latest.revision: 1
author: kraigb
ms.author: kraigb
manager: ghogen
translation.priority.ht:
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
ms.translationtype: Human Translation
ms.sourcegitcommit: 7a873df77756e5a957d327049566c8e0db1f3a8a
ms.openlocfilehash: cd9e0afac5c9a0975197cb65001f8f2698242b85
ms.contentlocale: pt-br
ms.lasthandoff: 05/12/2017

---


# <a name="creating-visual-data-plots-with-r"></a>Criando gráficos de dados visuais com R

Criar gráficos é uma parte fundamental do fluxo de trabalho de um cientista de dados. Nas RTVS (Ferramentas do R para Visual Studio), todas as atividades de criação de gráficos giram em torno de uma ou mais janelas de gráficos, que são projetadas para melhorar a produtividade nesta importante atividade.

![Imagem hero de criação de gráficos](~/docs/rtvs/media/plotting-hero-image.png)

Neste tópico:

- [A janela de gráficos](#the-plot-window)
- [Várias janelas de gráficos](#multiple-plot-windows)
- [Histórico de gráficos](#plot-history)
- [Manipulando a janela de gráficos de forma programática](#programmatically-manipulating-plot-windows)

O vídeo a seguir (2min02s) fornece uma breve visão geral de criação de gráficos nas RTVS:

<iframe width="560" height="315" src="https://www.youtube.com/embed/ZTbKmz5RSgY" frameborder="0" allowfullscreen></iframe>

## <a name="the-plot-window"></a>A janela de gráficos

Uma janela de gráficos contém uma série de gráficos, em que cada gráfico é gerado por um comando `plot`. Por exemplo, usar `plot(1:100)` cria uma nova janela de gráficos se já não houver alguma disponível:

![Gráfico linear de 1 a 100](~/docs/rtvs/media/plotting-1-to-100.png)

Tecnicamente falando, os comandos R `plot` renderizam a saída para um dispositivo de gráficos do R. Uma janela de gráficos renderiza o conteúdo de um dispositivo de gráficos do R, por isso, cada janela de gráficos recebe um número de dispositivo.

As janelas de gráficos são independentes dos projetos do Visual Studio e permanecem abertas ao carregar e fechar projetos.

A geração de um gráfico usará a janela de gráficos “ativa”, salvando todos os gráficos anteriores no histórico de gráficos (consulte [Histórico de gráficos](#plot-history)). Por exemplo, insira `plot(100:1)` e você verá que o gráfico acima é substituído por uma linha para baixo.

Como todas as outras janelas do Visual Studio. a janela de gráficos dá suporte a layouts personalizados (consulte [Personalização de layouts de janela no Visual Studio](../ide/customizing-window-layouts-in-visual-studio.md). As janelas de gráficos podem ser encaixadas em diferentes locais dentro do quadro do Visual Studio, redimensionadas dentro desse quadro ou retiradas inteiramente do quadro para um redimensionamento independente. 

Redimensionar uma janela de gráficos sempre renderiza o gráfico novamente para fornecer a melhor qualidade de imagem. Geralmente, é importante fazer isso antes de exportar o gráfico para um arquivo ou para a área de transferência usando os comandos descritos na próxima seção.

## <a name="plot-window-commands"></a>Comandos da janela de gráficos

A barra de ferramentas da janela de gráficos contém comandos aplicáveis e a maioria deles também está disponível por meio do menu **Ferramentas do R > Gráficos**.

| Botão | Comando | Descrição | 
| --- | --- | --- |
| ![Botão Nova janela de gráficos](~/docs/rtvs/media/plotting-toolbar-01-new-plot-window.png) | Nova janela de gráficos | Cria uma janela de gráficos separada com seu próprio histórico. Consulte [Várias janelas de gráficos](#multiple-plot-windows). |
| ![Botão Ativar janela de gráficos](~/docs/rtvs/media/plotting-toolbar-02-activate-plot-window.png) | Ativar a janela de gráficos | Define a janela de gráficos atual como a janela ativa, de modo que os próximos comandos `plot` sejam renderizados para essa janela. Consulte [Várias janelas de gráficos](#multiple-plot-windows). Consulte [Várias janelas de gráficos](#multiple-plot-windows). |
| ![Botão Janela de histórico de gráficos](~/docs/rtvs/media/plotting-toolbar-03-plot-history.png) | Janela de histórico de gráficos | Abre uma janela com todos os gráficos no histórico mostrados como miniaturas. Consulte [Histórico de gráficos](#plot-history). |
| ![Botões Histórico de gráficos](~/docs/rtvs/media/plotting-toolbar-04-plot-history-arrows.png) | Gráfico anterior/seguinte |  Navega para gráfico anterior ou seguinte no histórico. Você também pode navegar no histórico com Ctrl + Alt + F11 (anterior) e Ctrl + Alt + F12 (seguinte). Consulte [Histórico de gráficos](#plot-history). |
| ![Botão Salvar como imagem](~/docs/rtvs/media/plotting-toolbar-05-save-as-image.png)| Salvar como imagem | Solicita um nome de arquivo e salva o gráfico atual (o conteúdo da janela, no tamanho da janela) em um arquivo de imagem. Os formatos disponíveis são `.png`, `.jpg`, `.bmp` e `.tif`. |
| ![Botão Salvar como PDF](~/docs/rtvs/media/plotting-toolbar-06-save-as-pdf.png)| Salvar como PDF | Salva o gráfico atual em um arquivo PDF, usando o tamanho da janela atual. O gráfico será renderizado novamente se o PDF for dimensionado. |
| ![Botão Copiar como bitmap](~/docs/rtvs/media/plotting-toolbar-07-copy-as-bitmap.png)| Copiar como bitmap | Copia o gráfico na área de transferência como um bitmap de varredura, usando o tamanho da janela atual. | 
| ![Botão Copiar como metarquivo](~/docs/rtvs/media/plotting-toolbar-08-copy-as-metafile.png)| Copiar como metarquivo | Copia o gráfico na área de transferência como um [metarquivo do Windows](https://en.wikipedia.org/wiki/Windows_Metafile) (Wikipédia). | 
| ![Botão Remover gráfico](~/docs/rtvs/media/plotting-toolbar-09-remove-plot.png)| Remover gráfico | Remove o gráfico atual do histórico. |
| ![Botão Limpar todos os gráficos](~/docs/rtvs/media/plotting-toolbar-10-clear-all-plots.png) | Limpar todos os gráficos | Remove todos os gráficos do histórico (solicita confirmação). |

## <a name="multiple-plot-windows"></a>Várias janelas de gráficos

Como os cientistas de dados costumam trabalham com muitos gráficos de vários conjuntos de dados diferentes, as RTVS permitem criar quantas janelas de gráficos independentes forem necessárias, que podem ser organizadas conforme o desejado no quadro do Visual Studio ou fora dessa quadro. (Consulte [Personalização de layouts de janela no Visual Studio](../ide/customizing-window-layouts-in-visual-studio.md) para obter informações gerais sobre encaixe e redimensionando de janelas.)

Você pode criar uma nova janela de gráficos usando o botão de barra de ferramentas ou **Ferramentas do R > Gráficos > Nova Janela de Gráficos**. A nova janela de gráficos se torna a janela *ativa*, que é onde os novos gráficos serão renderizados. Para alterar a janela ativa, mude para ela e selecione o botão de barra de ferramentas Ativar janela de gráficos ou **Ferramentas do R > Gráficos > Ativar janela de gráficos**.

Os gráficos também são objetos independentes, o que significa que você pode copiá-los ou movê-los entre as janelas de gráficos usando o recurso do tipo “arrastar e soltar” com o mouse ou os comandos **Copiar**, **Recortar** e **Colar** no menu de contexto acionado com um clique do botão direito do mouse ou no menu **Editar**.

 O comportamento padrão do tipo "arrastar e soltar" é copiar. Para mover, arraste e solte mantendo pressionada a tecla Shift.

## <a name="plot-history"></a>Histórico de gráficos

Os comandos de gráficos são mantidos em um histórico de gráficos de cada janela, garantindo que todos os gráficos dentro de uma sessão sejam preservados. Para navegar no histórico, use os botões de seta na barra de ferramentas da janela de gráficos ou Ctrl + Alt + F11 e Ctrl + Alt + F12. Você também pode remover gráficos individuais ou limpar todos os gráficos na janela, novamente usando os botões da barra de ferramentas ou os comandos de menu **Ferramentas do R > Gráficos**.

Para ver a coleção inteira de gráficos, abra a janela de histórico de gráficos usando o botão de barra de ferramentas ou **Ferramentas do R > Gráficos > Janela de histórico de gráficos**.
Isso fornece uma lista de miniaturas dos gráficos que foram exibidos nessa janela, agrupadas por diferentes janelas de gráficos (ou dispositivos). Usar os botões de zoom na barra de ferramentas altera o tamanho das miniaturas.

![Janela de histórico de gráficos](~/docs/rtvs/media/plotting-plot-history-window.png)

Para abrir um gráfico em sua janela associada, selecione-o clicando duas vezes e, em seguida, selecione o botão de barra de ferramentas **Mostrar gráfico** ou clique como botão direito do mouse e selecione **Mostrar Gráfico**. Você também pode selecionar um gráfico individual e copiar, recortar ou excluir usando o menu de contexto acionado com um clique do botão direito do mouse ou o menu **Editar**.

O tempo de vida de seu histórico de gráficos em todas as janelas está vinculado ao tempo de vida da sessão interativa do R. Se você redefinir a sessão do R ou sair e reiniciar o Visual Studio, o histórico de gráficos será redefinido.

## <a name="programmatically-manipulating-plot-windows"></a>Manipulando a janela de gráficos de forma programática

Você pode manipular as janelas de gráficos do código R de forma programática, usando números de dispositivo para identificar janelas de gráficos específicas. 

- `dev.list()`: listar todos os dispositivos de gráficos na sessão atual do R.
- `dev.new()`: criar um novo dispositivo de gráficos (uma nova janela de gráficos).
- `dev.set(<device number>)`: definir o dispositivo de gráficos ativo.
- `dev.off()`: excluir o dispositivo ativo.

