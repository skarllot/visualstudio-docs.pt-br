---
title: Shell (isolado ou integrado) | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Visual Studio shell
- Visual Studio, Shell
- Shell [Visual Studio]
- Visual Studio shell, shell-based applications
- Shell [Visual Studio], shell-based applications
ms.assetid: c64a9bf0-9bf8-45c3-8fa2-306fa6cab66a
caps.latest.revision: 25
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
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: ed0e82dbc2c093a94080fe3fcf07a3e3b20e1a50
ms.lasthandoff: 02/22/2017

---
# <a name="shell-isolated-or-integrated"></a>Shell (isolado ou integrado)
Você pode criar seu próprio aplicativo com base no Visual Studio no modo integrado ou isolado. No modo integrado, muitos recursos do Visual Studio estão disponíveis, além de seu aplicativo. No modo isolado, você deve escolher um subconjunto de recursos do Visual Studio que você deseja distribuir junto com sua própria extensão.  
  
## <a name="integrated-mode"></a>Modo integrado  
 Modo integrado permite que os usuários usem os recursos padrão do Visual Studio juntamente com suas ferramentas personalizadas. O shell integrado é destinado principalmente para hospedagem de linguagens de programação e ferramentas de desenvolvimento de software.  
  
 Ferramentas personalizadas que são criadas automaticamente no shell integrado se mesclar com qualquer outra edição do Visual Studio está instalado no mesmo computador. Se o Visual Studio não estiver instalado, você pode fornecer uma versão redistribuível do shell do Visual Studio integrado.  
  
 A versão redistribuível do shell do Visual Studio integrado não inclui os recursos que oferecem suporte a seus respectivos sistemas de projeto e linguagens de programação.  
  
> [!NOTE]
>  O modo integrado do Visual Studio shell pode ser instalado junto com todas as edições do Visual Studio, exceto as edições Express.  
  
 Para obter mais informações, consulte [Visual Studio Shell (integrado)](../extensibility/visual-studio-shell-integrated.md).  
  
## <a name="isolated-mode"></a>Modo isolado  
 Modo isolado permite que você crie ferramentas personalizadas que executam lado a lado com outras versões do Visual Studio. Ele destina-se principalmente de ferramentas que podem acessar os serviços do Visual Studio sem dependendo de todos os recursos padrão do Visual Studio. Você pode personalizar a aparência de aplicativos baseados no shell do Visual Studio isolada. Você pode facilmente desativar os recursos e grupos de comando de menu que você não deseja aparecem junto com seu aplicativo.  
  
 Para obter mais informações, consulte [Shell isolado do Visual Studio](../extensibility/visual-studio-isolated-shell.md).  
  
## <a name="distributing-your-integrated-or-isolated-shell-application"></a>Distribuir seu aplicativo de Shell isolado ou integrado  
 Para distribuir seu aplicativo de shell integrado ou isolados, você precisa incluir o seu aplicativo, um especial shell integrado ou isolado redistribuível e um programa de instalação. Para obter mais informações sobre instalação e distribuição, consulte [distribuindo aplicativos isolados do Shell](../extensibility/distributing-isolated-shell-applications.md).  
  
> [!IMPORTANT]
>  O [contrato de licença de usuário final (EULA)](https://www.visualstudio.com/en-us/support/legal/mt171552) para o Visual Studio integrado e isolada shells inclui uma seção sobre a coleta de dados (**seção 3. Data**).  Ele descreve os dados de uso do cliente podem ser coletados pela Microsoft de usuários de qualquer shell integrado ou isolado software que você criou no seu aplicativo. Para obter mais informações, consulte [Microsoft Visual Studio família de declaração de privacidade do](https://www.visualstudio.com/en-us/dn948229).  
>   
>  Se você coletar dados de uso separados de seus clientes através de seu aplicativo, você deve fornecer o aviso apropriado aos usuários do seu aplicativo do qual você coletar.  Quando você distribui o software de shell isolado ou integrado como parte do seu aplicativo, de acordo com a licença do Visual Studio SDK, você deve incluir um dos seguintes:  
>   
>  -   o contrato de licença de usuário final como parte da sua licença do aplicativo  
> -   seu próprio EULA que exige que os clientes concordar com os termos que protegem o Visual Studio integrado ou isolada shell pelo menos a quantidade como os termos de licença de usuário final da Microsoft para o software de shell  
  
## <a name="additional-resources"></a>Recursos adicionais  
 Para obter mais informações sobre os pacotes redistribuíveis, consulte o [Downloads do Visual Studio Extensibility](http://go.microsoft.com/fwlink/?LinkID=119298) site da Web.  
  
## <a name="see-also"></a>Consulte também  
 [Envio de extensões do Visual Studio](../extensibility/shipping-visual-studio-extensions.md)
