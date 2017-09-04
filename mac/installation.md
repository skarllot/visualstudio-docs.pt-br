---
title: Instalar o Visual Studio para Mac
description: "Instruções sobre como instalar o Visual Studio para Mac e os componentes adicionais necessários para o desenvolvimento de plataforma cruzada."
author: asb3993
ms.author: amburns
ms.date: 04/14/2017
ms.topic: article
ms.technology: vs-ide-install
ms.assetid: 22B1F2CD-32AE-464D-80AC-C8AB4786B015
ms.translationtype: HT
ms.sourcegitcommit: e2b7ff9126e1cc38ac2e58d6be339b656a024e7f
ms.openlocfilehash: 24d2fa5f9054e621cd5167692a2571e9275c2bae
ms.contentlocale: pt-br
ms.lasthandoff: 08/11/2017

---

# <a name="setup-and-install-visual-studio-for-mac"></a>Configurar e instalar o Visual Studio para Mac

## <a name="setup"></a>Configuração

Para começar a desenvolver aplicativos de plataforma cruzada nativos após baixar o Visual Studio para Mac, é necessário preparar-se instalando e configurando alguns itens.

Para trabalhar com iOS no Visual Studio você precisará do seguinte:

* Um Mac com macOS Sierra 10.12 ou superior
* Xcode 8.3
* Uma ID da Apple. Se você ainda não tiver uma ID da Apple, crie uma nova em https://appleid.apple.com. Será necessário ter uma ID da Apple para instalar e entrar no Xcode.

## <a name="install"></a>Instalar o

1. Baixar o Visual Studio para Mac de [https://www.visualstudio.com/](https://www.visualstudio.com/)

2. Depois que o pacote do instalador for baixado, clique no arquivo **VisualStudioInstaller.dmg** para montar o instalador e executá-lo clicando duas vezes no logotipo, conforme ilustrado na imagem a seguir:

  ![Caixa de diálogo do instalador](media/installer-image1.png)

3. Você poderá ver uma caixa de diálogo de alerta semelhante à imagem a seguir. Nesse caso, clique em **Abrir**:

  ![caixa de diálogo de alerta](media/installer-image2.png)

4. O instalador inspeciona seu sistema para verificar quais componentes precisam ser instalados ou atualizados:

  ![Avaliando o seu sistema](media/installer-image3.png)

5. Em seguida, você verá uma caixa de diálogo de alerta solicitando que você confirme os termos de Privacidade e de Licença. Pressione o botão **Continuar** para confirmar os termos:

  ![Caixa de diálogo Licença](media/installer-image4.png)

6. O instalador apresenta uma lista de componentes necessários que estão faltando e que precisa ser baixados e instalados. Selecione os produtos que você deseja baixar aqui:

  ![Selecionar itens](media/installer-image5.png)

  Esta tela de instalação exibe a versão e o tamanho de cada componente individual. Você pode clicar em cada componente para exibir uma lista de dependências desse componente (para Android), consultar pacotes adicionais que ele baixa (para .NET Core) ou exibir os aplicativos adicionais necessários (iOS e macOS):

  ![Dependências adicionais de Android](media/installer-image6.png)

7. Quando você estiver satisfeito com sua seleção, pressione o botão **Instalar e Atualizar** para iniciar o processo de instalação.

8. O instalador iniciará o processo de download e instalação dos itens selecionados:

  ![Iniciando a instalação](media/installer-image7.png)

  ![Baixando o Xamarin.Mac](media/installer-image8.png)

  ![Concluindo a instalação](media/installer-image9.png)

9. Pode ser solicitado que você eleve as permissões necessárias para os componentes individuais que são necessários para concluir a instalação. Insira suas credenciais de administrador para continuar o processo de instalação:

  ![Insira as permissões para prosseguir com o instalador](media/installer-image10.png)

10. Depois que a instalação for bem-sucedida, você poderá começar a desenvolver aplicativos no Visual Studio pressionando **Iniciar**:

  ![Abrir o Visual Studio](media/installer-image11.png)

> [!NOTE]
Se você optou por não instalar uma plataforma ou ferramenta durante a instalação original (desmarcando-a na etapa 6), deverá executar o [instalador](https://www.visualstudio.com/vs/) novamente se desejar adicionar os componentes mais tarde.

