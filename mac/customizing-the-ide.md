---
title: Personalizando o IDE
description: "O Visual Studio para Mac pode ser personalizado de várias maneiras, permitindo que os usuários desenvolvam aplicativos em um ambiente que atenda tanto suas necessidades estéticas quanto de eficiência. Este tópico explora as várias formas em que o Visual Studio para Mac pode ser adaptado para atender às suas necessidades."
author: asb3993
ms.author: amburns
ms.date: 04/14/2017
ms.topic: article
ms.assetid: F7C2A28C-0759-4E0D-A28E-B72D5AB73DB6
ms.translationtype: HT
ms.sourcegitcommit: e2b7ff9126e1cc38ac2e58d6be339b656a024e7f
ms.openlocfilehash: 514f758718105db366363cd1c9e69163a9872dc7
ms.contentlocale: pt-br
ms.lasthandoff: 08/11/2017

---

#<a name="customizing-the-ide"></a>Personalizando o IDE

O Visual Studio para Mac pode ser personalizado de várias maneiras, permitindo que os usuários desenvolvam aplicativos em um ambiente que atenda suas necessidades estéticas e de eficiência. Este tópico explora as várias formas em que o Visual Studio para Mac pode ser adaptado para atender às suas necessidades.

## <a name="dark-theme"></a>Tema escuro

![Exibição de tema escuro](media/customizing-the-ide-image7a.png)

Você pode trocar os temas no Visual Studio para Mac navegando para **Visual Studio > Preferências... > Ambiente > Estilo Visual** e selecionando o tema desejado na lista suspensa **Tema da Interface do Usuário**, conforme ilustrado na captura de tela a seguir:

 ![Seleção de tema escuro](media/customizing-the-ide-image7b.png)

## <a name="localization"></a>Localização

O Visual Studio para Mac está traduzido em 13 idiomas, permitindo que ele fique acessível para mais desenvolvedores. Os idiomas disponíveis no momento estão listados abaixo:

* Chinês – China
* Chinês – Taiwan
* Tcheco
* Francês
* Alemão
* Inglês
* Italiano
* Japonês
* Coreano
* Português - Brasil
* Russo
* Espanhol
* Turco

Para trocar os idiomas exibidos temas no Visual Studio para Mac, navegue para **Visual Studio > Preferências... > Ambiente > Estilo Visual** e selecione o idioma desejado na lista suspensa **Idioma da Interface do Usuário**, conforme ilustrado na captura de tela a seguir:


![Seleção de Idioma](media/customizing-the-ide-image11a.png)

## <a name="author-information"></a>Informações do autor

O painel de informações do autor permite que você adicione informações relevantes sobre si mesmo como nome, endereço de email, o proprietário dos direitos autorais do seu trabalho, sua empresa e marca registrada, conforme ilustrado abaixo:

 ![Seção Editar Informações do Autor](media/customizing-the-ide-image9a.png)

Essas informações são usadas para popular os cabeçalhos de arquivo padrão, como uma licença, que podem ser adicionadas a novos arquivos criados no Visual Studio para Mac:

 ![Opções de cabeçalho padrão](media/customizing-the-ide-image8a.png)


Os campos **Nome** e **Email** populados serão usados para adicionar informações a qualquer confirmação feita por meio do Controle de Versão no Visual Studio para Mac. Se você não popular esses campos, o Visual Studio para Mac solicitará que você faça isso quando você tentar usar o Controle de Versão.

## <a name="key-bindings"></a>Associações de teclas

Associações de teclas permitem adaptar seu ambiente de desenvolvimento para que você possa mover-se com mais eficiência por todo o Visual Studio para Mac. Ele fornece associações de teclas familiares para muitos IDEs populares, como o Visual Studio (Windows), ReSharper, Visual Studio Code e Xcode.

As associações de teclas podem ser definidas navegando para **Visual Studio > Preferências... > Ambiente > Associações de teclas**, conforme ilustrado abaixo:

 ![Definir associações de teclas](media/customizing-the-ide-image10a.png)

Aqui você pode pesquisar combinações de associações de teclas, exibir associações conflitantes, adicionar novas associações e editar as associações existentes.

## <a name="workspace-layout"></a>Layout do espaço de trabalho

O espaço de trabalho do Visual Studio para Mac consiste em uma área de documento principal (normalmente o editor, superfície do designer ou o arquivo de opções), cercada por *painéis* complementares que contêm informações úteis para acessar e gerenciar arquivos de aplicativo, teste e depuração.

 ![Layout do espaço de trabalho](media/customizing-the-ide-image1a.png)

### <a name="viewing-and-arranging-pads"></a>Exibindo e organizando os painéis

Quando você abrir qualquer nova solução ou arquivo no Visual Studio para Mac, observe alguns *painéis* no espaço de trabalho, incluindo o Painel de Soluções, Estrutura de tópicos do documento e Erros, conforme ilustrado abaixo:

![Painéis de Solução](media/customizing-the-ide-image2a.png)

O Visual Studio para Mac fornece painéis que contém informações adicionais, ferramentas e auxílios de navegação que podem ser acessados navegando para o item de menu **Exibir > Painéis** e selecionando um painel para adicioná-lo:

 ![Selecionar novo painel](media/customizing-the-ide-image3a.png)

Os painéis também podem ser abertos automaticamente por vários comandos, como o comando **Localizar nos arquivos** (Shift + Cmd + F), que abre um painel desanexado dos resultados da pesquisa.

Painéis podem ser movidos e organizados por todo o fluxo de trabalho da forma que for mais útil para você. Por exemplo, eles podem ser encaixados em qualquer lado do editor de documentos, adjacente a outro painel, acima ou abaixo de outro painel ou como um conjunto de painéis com guias que permite alternar rapidamente entre elas.

Para os painéis usados com frequência, você também pode desanexar completamente um painel da janela do Visual Studio para Mac e criar uma janela separada para esse painel.

Os painéis podem ser ocultos e fechados usando os botões no canto superior direito de cada painel:

![Ocultando e fechando painéis](media/customizing-the-ide-image5a.png)

Painéis ocultos automaticamente são encaixados nas laterais do espaço de trabalho, tornando-os facilmente acessíveis quando são necessários. Focalizar o painel o exibirá novamente e ele será ocultado quando o foco do teclado e do mouse deixá-lo.


### <a name="organizing-layouts"></a>Organizando layouts

Os painéis que são exibidos a qualquer momento dependem do contexto atual. Por exemplo, ao usar o designer visual, os painéis da caixa de ferramentas e da grade de propriedade são mais importantes; durante a depuração, é útil ter painéis do depurador para exibir a pilha e os locais.

O estado dos painéis abertos é representado por um *layout*. Os layouts podem ser alternados manualmente por meio do menu Exibir, conforme ilustrado abaixo ou alternamos automaticamente quando você executar uma ação, como depuração ou ao abrir um Storyboard:

![Selecionar novos Layouts](media/customizing-the-ide-image6b.png)

Sempre há um layout de ativo e qualquer alteração feita em um layout, como adicionar ou reposicionar um painel, alterará apenas o layout ativo. Quando você fechar o Visual Studio para Mac, as alterações feitas não serão salvas.


No entanto, é possível criar um novo layout usando o item de menu **Exibir > Salvar layout atual...**. Isso adicionará o layout atual ao menu para que você pode selecioná-lo a qualquer momento:

![Salva o layout atual](media/customizing-the-ide-image6a.png)

### <a name="side-by-side-editing-support"></a>Suporte à edição lado a lado

O Visual Studio para Mac permite abrir os editores de texto lado a lado ou ter um editor como uma janela flutuante desanexada.

O modo de duas colunas pode ser habilitado por meio do item de menu Exibir selecionando **Exibir > Colunas do Editor > Duas colunas** ou arrastando uma guia do editor para uma das bordas da área do editor, conforme mostrado abaixo:

 ![Modo de duas colunas lado a lado](media/customizing-the-ide-sbs.png)

As guias do Editor podem ser arrastadas para fora da área de documento para criar uma janela flutuante do editor. Essa janela flutuante também dá suporte a editores lado a lado e pode conter várias guias do editor:

 ![Criar nova janela](media/customizing-the-ide-sbs1.png)

 ![Duas colunas lado a lado com guias adicionais](media/customizing-the-ide-sbs2.png)

Para reverter para um único editor aberto, selecione **Exibir > Colunas do Editor > Uma coluna**.

