---
title: "Passo a passo: Publicando uma extensão do Visual Studio | Documentos do Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- publishing web controls
- web controls, publishing
ms.assetid: a7816161-0490-4043-86f5-0f7331ed83b3
caps.latest.revision: 17
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
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
translationtype: Machine Translation
ms.sourcegitcommit: 574af4ff2b3858201c13121475de02a763572f6b
ms.openlocfilehash: fcfb0724b89d60553d6686a0705ab1e9459014ce
ms.lasthandoff: 02/22/2017

---
# <a name="walkthrough-publishing-a-visual-studio-extension"></a>Passo a passo: Publicando uma extensão do Visual Studio
Este passo a passo mostra como publicar uma extensão do Visual Studio para a Galeria do Visual Studio. Quando você adiciona sua extensão na galeria, os desenvolvedores podem usar **extensões e atualizações** para procurar extensões novas e atualizadas não existe.  
  
## <a name="prerequisites"></a>Pré-requisitos  
 Para seguir este passo a passo, você deve instalar o SDK do Visual Studio. Para obter mais informações, consulte [Visual Studio SDK](../extensibility/visual-studio-sdk.md).  
  
## <a name="create-a-visual-studio-extension"></a>Criar uma extensão do Visual Studio  
 Nesse caso, usaremos uma extensão de VSPackage padrão, mas as mesmas etapas são válidas para cada tipo de extensão.  
  
1.  Criar um VSPackage no c# chamado `TestPublishing` que possui um comando de menu. Para obter mais informações, consulte [criando uma extensão com um comando de Menu](../extensibility/creating-an-extension-with-a-menu-command.md).  
  
## <a name="test-the-extension"></a>A extensão de teste  
 Antes de distribuir a extensão, compilar e testar para verificar se que ele está instalado corretamente na instância experimental do Visual Studio.  
  
1.  No Visual Studio, inicie a depuração. Para abrir uma instância experimental do Visual Studio.  
  
2.  Na instância experimental, vá para o **ferramentas** menu e clique em **Extension Manager**. A extensão TestPublishing deve aparecer no painel central e ser habilitada.  
  
3.  Sobre o **ferramentas** menu, verifique se o comando de teste.  
  
## <a name="publish-the-extension-to-the-visual-studio-gallery"></a>Publicar a extensão para a Galeria do Visual Studio  
 Agora você pode publicar a extensão para a Galeria do Visual Studio.  
  
1.  Certifique-se de que você criou a versão de lançamento da sua extensão e que é atualizado.  
  
2.  Em um navegador da web, abra o [Galeria do Visual Studio](http://go.microsoft.com/fwlink/?LinkId=194329) site.  
  
3.  No canto superior direito, clique em **SIGN IN**.  
  
4.  Use sua conta da Microsoft para entrar. Se você não tiver uma conta da Microsoft, você pode criar um neste momento.  
  
5.  Clique em **carregar**.  
  
6.  Em **etapa 1: tipo de extensão**, selecione **ferramenta** e, em seguida, clique em **próxima**.  
  
7.  Em **etapa 2: carregar**, você pode optar por carregar diretamente à Galeria do Visual Studio ou simplesmente adicionar um link para seu próprio site. Nesse caso selecione **gostaria de carregar minha ferramenta**. O **selecionar seu controle** caixa é exibida. Clique em **procurar** e, em seguida, selecione TestPublish.vsix na pasta \bin\Release do projeto. Clique em **Avançar**.  
  
8.  Em **etapa 3: informações básicas**, campos de arquivo source.extension.vsixmanifest são exibidos. Selecione um **categoria** e adicione **marcas** para ajudar os usuários a localizar a sua extensão. Você talvez queira adicionar um resumo e uma descrição (a descrição deve ter pelo menos de 280 caracteres) mais detalhadas. Deixe **tipo de extensão** como **não uma extensão da Microsoft** e **categoria de custo** como **avaliação**.  
  
9. Leia o contrato de contribuição na parte inferior da página e verifique **concordo**.  
  
10. Clique em **criar contribuição**. Isso exibe a página que terá sua extensão na Galeria do Visual Studio, com uma mensagem de que a página ainda não foi publicada.  
  
11. Clique em **publicar**.  
  
12. Pesquise a Galeria do Visual Studio para a sua extensão. A listagem para a extensão TestPublish deve aparecer.  
  
## <a name="install-the-extension-from-the-visual-studio-gallery"></a>Instalar a extensão da Galeria do Visual Studio  
 Agora que a extensão é publicada, instalá-lo no Visual Studio e testá-lo lá.  
  
1.  No Visual Studio, no **ferramentas** menu, clique em **extensões e atualizações**.  
  
2.  Clique em **Online** e procure por TestPublish. A listagem para a extensão TestPublish deve aparecer.  
  
3.  Clique em **Baixar**. Depois que a extensão é baixada, clique em **instalar**.  
  
4.  Para concluir a instalação, reinicie o Visual Studio.  
  
## <a name="removing-the-extension"></a>Removendo a extensão  
 Você pode remover a extensão da Galeria do Visual Studio e do seu computador.  
  
#### <a name="to-remove-the-extension-from-the-visual-studio-gallery"></a>Para remover a extensão da Galeria do Visual Studio  
  
1.  Abra o [Galeria do Visual Studio](http://go.microsoft.com/fwlink/?LinkId=194329) site.  
  
2.  No centro, clique em **extensões My**. A listagem para TestPublish é exibida.  
  
3.  Clique em **excluir**.  
  
#### <a name="to-remove-the-extension-from-your-computer"></a>Para remover a extensão do seu computador  
  
1.  No Visual Studio, no **ferramentas** menu, clique em **Extension Manager**.  
  
2.  Selecione TestPublish e, em seguida, clique em **desinstalar**.  
  
3.  Para concluir a desinstalação, reinicie o Visual Studio.

