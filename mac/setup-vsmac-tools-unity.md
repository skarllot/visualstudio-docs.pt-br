---
title: Configurar as Ferramentas do Visual Studio para Mac para Unity
author: dantogno
ms.author: v-davian
ms.date: 07/17/2017
ms.topic: article
ms.assetid: 83FDD7A3-5D16-4B4B-9080-078E3FB5C623
ms.translationtype: HT
ms.sourcegitcommit: e2b7ff9126e1cc38ac2e58d6be339b656a024e7f
ms.openlocfilehash: c2290b1165b8d2688b280684e1251b929d002594
ms.contentlocale: pt-br
ms.lasthandoff: 08/11/2017

---
# <a name="setup-visual-studio-for-mac-tools-for-unity"></a>Configurar as Ferramentas do Visual Studio para Mac para Unity

Esta seção explica como começar a usar as Ferramentas do Visual Studio para Mac para Unity.

## <a name="install-visual-studio-for-mac"></a>Instalar o Visual Studio para Mac

Baixe e instale o Visual Studio para Mac. Todas as edições do Visual Studio para Mac dão suporte às Ferramentas do Visual Studio para Mac para Unity, incluindo a edição Community gratuita:

* Baixe o Visual Studio para Mac de [visualstudio.com](https://www.visualstudio.com/).
* As Ferramentas do Visual Studio para Mac para Unity são instaladas automaticamente durante o processo de instalação.
* Siga as etapas no [guia de instalação](/visualstudio/mac/installation) para obter ajuda de instalação adicional.

## <a name="confirm-that-the-visual-studio-for-mac-tools-for-unity-extension-is-enabled"></a>Confirme se a extensão das Ferramentas do Visual Studio para Mac para Unity está habilitada

Embora a extensão das Ferramentas do Visual Studio para Mac para Unity devem ser habilitadas por padrão, você pode confirmar isso e verificar o número de versão instalada:

1.  No menu do Visual Studio, escolha **Extensões...**.

  ![Selecionar Extensões](media/setup-vsmac-tools-unity-image1.png)

2.  Expanda a seção de Desenvolvimento de Jogos e confirme a entrada das Ferramentas do Visual Studio para Mac para Unity.

  ![Exibir a Entrada do Unity](media/setup-vsmac-tools-unity-image2.png)

## <a name="install-unity"></a>Instalar o Unity

As Ferramentas do Visual Studio para Mac para Unity requerem o Unity versão 5.6.1 ou superior. Todos os planos do Unity funcionam com as Ferramentas do Visual Studio para Unity, incluindo o plano Pessoal gratuito. Baixe o Unity de [store.unity.com](https://store.unity.com/).

> [!NOTE]
> Para verificar se as Ferramentas do Visual Studio para Unity estão habilitadas na sua versão do Unity, selecione **Sobre o Unity** no menu do Unity e procure o texto “Ferramentas do Microsoft Visual Studio para Unity habilitadas” na parte inferior esquerda da caixa de diálogo.
>
>   ![Sobre o Unity](media/setup-vsmac-tools-unity-image3.png)

## <a name="configure-unity-for-use-with-visual-studio-for-mac"></a>Configurar o Unity para ser usado com o Visual Studio para Mac

O Visual Studio deve ser definido como o editor de script externo no Unity:

1.  Selecione **Preferências...**  no menu do Unity.

  ![Selecionar preferências](media/setup-vsmac-tools-unity-image4.png)

2.  Na caixa de diálogo Preferências, selecione a guia **Ferramentas Externas**.

3.  Na lista suspensa do Editor de script externo, escolha **Visual Studio** se ele estiver listado, caso contrário, selecione **Procurar...**.

  ![Selecionar o Visual Studio](media/setup-vsmac-tools-unity-image5.png)

4.  Se **Procurar...** foi selecionado, navegue para o Diretório de aplicativos, selecione o Visual Studio e clique em **Abrir**.

  ![Selecione Abrir](media/setup-vsmac-tools-unity-image6.png)

5.  Depois de selecionar o Visual Studio na lista **Editor de script externo**, feche a caixa de diálogo Preferências para concluir o processo de configuração.

