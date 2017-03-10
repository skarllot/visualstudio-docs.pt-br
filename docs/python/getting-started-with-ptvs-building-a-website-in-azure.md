---
title: "Introdução ao PTVS: compilando um site no Azure | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-python
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3bdbda36-14d2-4fde-ba42-d91042777ff6
caps.latest.revision: 4
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
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 2d84d0c8949772feab8f5bd046651449e58271d8
ms.lasthandoff: 02/22/2017

---
# <a name="getting-started-with-ptvs-building-a-website-in-azure"></a>Introdução ao PTVS: compilando um site no Azure
Você pode começar a criar rapidamente um site Python no Azure.  
  
 É possível assistir a essas instruções em um breve [vídeo no YouTube](https://www.youtube.com/watch?v=FJx5mutt1uk&list=PLReL099Y5nRdLgGAdrb_YeTdEnd23s6Ff&index=6).  
  
 Comece pela caixa de diálogo Novo Projeto... e, nos projetos Python, escolha o projeto Web Garrafa.  Esse modelo [Garrafa](http://bottlepy.org/docs/dev/index.html) é um site inicial com base no [Framework de inicialização](http://getbootstrap.com/).  Quando você cria o projeto, o Visual Studio solicitará a instalação das dependências (Garrafa neste caso) em um ambiente virtual.  Como você está implantando para um site do Azure, será necessário adicionar as dependências a um ambiente virtual para implantar os bits necessários para a operação do seu site.  Você também precisa basear seu ambiente em Python 2.7 ou 3.4 de 32 bits.  Depois de criar o projeto, pressione F5 para iniciar a execução de seu site localmente.  
  
 É fácil testar o site no Azure.  Se você não tiver uma assinatura do Azure, poderá usar [try.azurewebsites.net](https://trywebsites.azurewebsites.net/).  Este site oferece uma maneira simples de testar Sites do Azure por uma hora por vez com apenas um logon social.  Não é necessário informar um cartão de crédito.  Escolha o modelo Site vazio no menu suspenso Alterar idioma e escolha Criar.  Em “Trabalhar com seu aplicativo Web”, escolha Baixar Perfil de Publicação e salve o arquivo para ser usado com o Visual Studio.  Você também pode implantá-lo usando git de qualquer sistema operacional.  
  
 Retorne para o Visual Studio e para o projeto que você criou.  Selecione o nó do projeto no Gerenciador de Soluções, escolha o botão do ponteiro do mouse à direita e selecione Publicar.  Se você tiver uma assinatura do Azure, poderá clicar nos Sites do Microsoft Azure e na caixa de diálogo para gerenciar seus sites daqui.  Para este passo a passo, selecione Importar para importar o perfil de publicação que você acabou de baixar.  Como o perfil de publicação tem todas as informações necessárias, você pode escolher Publicar.  Em poucos segundos, uma nova janela do navegador será aberta, e o site estará ativo e hospedado na nuvem do Azure.  
  
 Sites simples são fáceis, porém para obter informações sobre aplicativos Web mais significativos no Azure, consulte o vídeo de [aprofundamento](https://www.youtube.com/watch?v=WG3pGmoo8nE&list=PLReL099Y5nRdLgGAdrb_YeTdEnd23s6Ff&index=10), bem como outros vídeos neste canal (link na parte superior direita das páginas Introdução ou Vídeo de aprofundamento ou abaixo.  
  
 É possível assistir a essas instruções em um breve [vídeo no YouTube](https://www.youtube.com/watch?v=FJx5mutt1uk&list=PLReL099Y5nRdLgGAdrb_YeTdEnd23s6Ff&index=6).  
  
## <a name="see-also"></a>Consulte também  
 [Documentação do wiki](https://github.com/Microsoft/PTVS/wiki/Web-Project)   
 [Introdução ao PTVS e vídeos de aprofundamento](https://www.youtube.com/playlist?list=PLReL099Y5nRdLgGAdrb_YeTdEnd23s6Ff)
