---
title: "Configurando um repositório do Subversion no Visual Studio para Mac"
description: Usando o Git e o Subversion no Visual Studio para Mac.
author: asb3993
ms.author: amburns
ms.date: 04/14/2017
ms.topic: article
ms.assetid: 0D58FB37-530E-495B-BED6-FD499477A9B6
ms.translationtype: HT
ms.sourcegitcommit: e2b7ff9126e1cc38ac2e58d6be339b656a024e7f
ms.openlocfilehash: ea2dffed0b9091dae61792783eb83c103ca9375c
ms.contentlocale: pt-br
ms.lasthandoff: 08/11/2017

---

# <a name="setting-up-a-subversion-repository"></a>Configurando um repositório do Subversion

O Subversion é um sistema de controle de versão centralizado. Isso significa que há um único servidor que contém todos os arquivos e as revisões do qual os usuários podem fazer check-out de qualquer versão de qualquer arquivo. Ao fazer check-out de arquivos de um repositório Subversion remoto, o usuário receberá um instantâneo do repositório no momento em questão.

Antes de começar a usar o Subversion, as ferramentas de linha de comando do Xcode devem ser instaladas, pois elas incluem os pacotes de svn corretos. Verifique se o SVN está instalado no Terminal com o seguinte comando:

`svn h`

1. Crie um repositório SVN online gratuito. Neste exemplo, [Assembla](https://app.assembla.com/) foi usado. Depois de criado, uma URL será fornecida, que será usada para se conectar ao repositório: 

    ![Obtenha a URL do SVN e copie-a](media/version-control-subversion1-sml.png)

2. Abra ou crie um Projeto do Visual Studio para Mac.

3. Clique com o botão direito do mouse no Projeto e selecione **Controle de versão > Publicar no Controle de versão...**: 

    ![Iniciar a publicação do projeto](media/version-control-subversion2.png)

4. Na guia **Conectar-se ao repositório**, selecione **Subversion** na lista suspensa superior.

5. Insira a URL da etapa 1. Isso deve popular os outros campos por padrão: 

    ![Selecione o Repositório e a caixa de diálogo Insira os detalhes](media/version-control-subversion3.png)

7. Clique em **OK** e confirme pressionando **Publicar**.

7. Pode ser solicitado que você insira suas credenciais para o site no qual você está criando o repositório. Insira-os conforme ilustrado abaixo:

    ![](media/version-control-subversion5.png)

8.  Todos os comandos de controle de versão disponíveis agora devem estar visíveis no menu de controle de versão.


