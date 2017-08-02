---
title: "Publicando um aplicativo do Python no Serviço de Aplicativo do Azure por meio do Visual Studio | Microsoft Docs"
ms.custom: 
ms.date: 3/7/2017
ms.prod: visual-studio-dev15
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-python
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 85031f91-3a65-463b-a678-1e69f1b843e6
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
translationtype: Human Translation
ms.sourcegitcommit: a42f5a30375192c89c9984e40ba0104da98d7253
ms.openlocfilehash: 0163d1279b41ef8fecf9ca774cd3e67f0f47f1b1
ms.lasthandoff: 03/07/2017

---

# <a name="publishing-to-azure-app-service"></a>Publicando no Serviço de Aplicativo do Azure

É possível começar a compilar um site do Python rapidamente no Visual Studio e publicá-lo no Serviço de Aplicativo do Azure por meio das seguintes etapas:

- [Criar uma assinatura do Azure](#create-an-azure-subscription)
- [Criar e testar o projeto inicial](#create-and-test-the-initial-project)
- [Publicar no Serviço de Aplicativo do Azure](#publish-to-azure-app-service)

Um breve passo a passo desse processo pode ser encontrado em [Visual Studio Python Tutorial: Building a Website](https://www.youtube.com/watch?v=FJx5mutt1uk&list=PLReL099Y5nRdLgGAdrb_YeTdEnd23s6Ff&index=6) (Tutorial do Python do Visual Studio: Compilando um site) (youtube.com, 3min10s). 

> [!VIDEO https://www.youtube.com/embed/FJx5mutt1uk] 

## <a name="create-an-azure-subscription"></a>Criar uma assinatura do Azure

A publicação no Azure exige uma assinatura do Azure ou é possível usar um site temporário.

Para assinaturas, comece com uma [conta gratuita completa do Azure](https://azure.microsoft.com/en-us/free/), que inclui generosos créditos para os serviços do Azure. Além disso, considere inscrever-se no [Visual Studio Dev Essentials](https://azure.microsoft.com/en-us/pricing/member-offers/vs-dev-essentials/), que fornece a você um crédito de US$ 25 todo mês durante um ano.

Para criar um site temporário no Serviço de Aplicativo do Azure, sem a necessidade de uma assinatura do Azure:

1. Abra o navegador em [try.azurewebsites.net](https://try.azurewebsites.net).
1. Selecione **Aplicativo Web** para o tipo de aplicativo e, em seguida, selecione **Avançar**.
1. Selecione **Site Vazio** para o modelo e, em seguida, **Criar >**.
1. Entre com um logon social de sua escolha e, após alguns instantes, seu site estará pronto na URL exibida.
1. Selecione **Baixar perfil de publicação** e salve o arquivo `.publishsettings`, que você usará mais tarde.

## <a name="create-and-test-the-initial-project"></a>Criar e testar o projeto inicial

1. No Visual Studio, selecione **Arquivo > Novo > Projeto**, pesquise “Bottle”, selecione o **Projeto Web do Bottle** e clique em **OK**.    

1. Quando solicitado a instalar pacotes externos, selecione **Instalar em um ambiente virtual**. Observe o controle **Mostrar os pacotes necessários** na parte inferior da caixa de diálogo que mostrará quais pacotes serão instalados:

  ![Instalando os pacotes necessários](~/python/media/tutorials-common-external-packages.png)

1. Selecione o interpretador base preferencial para o ambiente virtual (por exemplo, **Python 2.7** ou **Python 3.4**) e clique em **Criar**:

  ![Adicionando um ambiente virtual ao criar um projeto](~/python/media/tutorials-common-add-virtual-environment.png)

1. Quando o projeto for criado, teste-o localmente selecionando **Depurar > Iniciar Depuração** ou pressionando F5. Por padrão, o aplicativo usa um repositório na memória que não exige nenhuma configuração. Todos os dados são perdidos quando o servidor Web é interrompido.

1. Clique em torno do aplicativo para ver sua operação.

1. Pare o depurador quando terminar (**Depurar > Parar Depuração** ou Shift-F5).

## <a name="publish-to-azure-app-service"></a>Publicar no Serviço de Aplicativo do Azure

1. No **Gerenciador de Soluções**, clique com o botão direito do mouse no projeto e selecione **Publicar**. 

1. Na caixa de diálogo **Publicar**, selecione **Serviço de Aplicativo do Microsoft Azure**:

  ![Publicar no Azure etapa 1](~/python/media/tutorials-common-publish-1.png)

1. Selecione um destino:

    - Se você tiver uma assinatura do Azure, selecione **Serviço de Aplicativo do Microsoft Azure** como o destino de publicação e, em seguida, na próxima caixa de diálogo, selecione um Serviço de Aplicativo existente ou **Novo** para criar um novo.
    - Se estiver usando um local temporário de try.azurewebsites.net, selecione **Importação** como o destino de publicação, procure o arquivo `.publishsettings` baixado no site e selecione **OK**.

1. Os detalhes do Serviço de Aplicativo são exibidos na guia **Conexão** da caixa de diálogo **Publicar** abaixo.

  ![Publicar no Azure etapa 2](~/python/media/tutorials-common-publish-2.png)

1. Selecione **Avançar >**, conforme necessário, para examinar as configurações adicionais. Se você pretende [depurar o código do Python remotamente no Azure](debugging-azure-remote.md), defina **Configuração** como **Depuração**
1. Selecione **Publicar**. Depois que o aplicativo for implantado no Azure, o navegador padrão será aberto nesse site. 
