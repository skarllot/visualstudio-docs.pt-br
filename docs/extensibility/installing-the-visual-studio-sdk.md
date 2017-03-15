---
title: Instalar o SDK do Visual Studio | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- visual-studio-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c730edb6-5099-4c16-85a8-08def09f1455
caps.latest.revision: 3
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
ms.sourcegitcommit: 9c25532605613b34ded15a4bd6a533e589b7fce2
ms.openlocfilehash: d039c50cea2ee038baec26fad02a98ae45f0d521
ms.lasthandoff: 02/22/2017

---
# <a name="installing-the-visual-studio-sdk"></a>Instalar o SDK do Visual Studio
A partir do Visual Studio 2015, você não instale o SDK do Visual Studio no Centro de download. Ele é fornecido como um recurso opcional na instalação do Visual Studio. Você também pode instalar o SDK do VS mais tarde.  
  
## <a name="installing-the-visual-studio-sdk-as-part-of-a-visual-studio-installation"></a>Instalar o SDK do Visual Studio como parte de uma instalação do Visual Studio  
 Se você gostaria de incluir o VSSDK em sua instalação do Visual Studio, você deve fazer uma instalação personalizada.  
  
> [!NOTE]
>  Executável da instalação, o SDK do Visual Studio é chamado **ferramentas de extensibilidade do Visual Studio**.  
  
1.  Inicie a instalação do Visual Studio 2015. Você pode instalar qualquer edição do Visual Studio, exceto Express.  
  
2.  Na primeira tela, selecione **personalizado**, não **padrão**. Clique em **Avançar**.  
  
3.  Você deve ver uma exibição de árvore de recursos personalizados. Abra **ferramentas comuns**. Você deve ver **ferramentas de extensibilidade do Visual Studio** .  
  
     ![VSSDKInstall](../extensibility/media/vssdkinstall.png "VSSDKInstall")  
  
4.  Verificar **ferramentas de extensibilidade do Visual Studio** , em seguida, clique em **próxima** e continuar a instalação.  
  
## <a name="installing-the-visual-studio-sdk-after-installing-visual-studio"></a>Instalando o SDK do Visual Studio depois de instalar o Visual Studio  
 Se você optar por instalar o SDK do Visual Studio depois de concluir a instalação do Visual Studio, você deve seguir o procedimento a seguir:  
  
1.  Vá para **painel de controle / programas / programas e recursos**e procure **Visual Studio 2015**. Você pode instalar o SDK do Visual Studio para qualquer edição do Visual Studio 2015 exceto Express.  
  
2.  Clique com botão direito **Visual Studio 2015**e, em seguida, clique em **alteração**. Você deve ver a página de instalação.  
  
3.  Siga o mesmo procedimento que em **instalar o SDK do Visual Studio como parte de uma instalação do Visual Studio** acima.  
  
4.  Clique o **ferramentas de extensibilidade do Visual Studio** link para instalar o SDK do Visual Studio.  
  
## <a name="installing-the-visual-studio-sdk-from-a-solution"></a>Instalar o SDK do Visual Studio de uma solução  
 Se você abrir uma solução com um projeto de extensibilidade sem precisar instalar primeiro o VSSDK, você será solicitado por uma barra de informações realçadas acima do Gerenciador de soluções. Ele deve ser semelhante ao seguinte:  
  
 ![SolutionExplorerInstall](../extensibility/media/solutionexplorerinstall.png "SolutionExplorerInstall")  
  
## <a name="installing-the-visual-studio-sdk-from-the-command-line"></a>Instalar o SDK do Visual Studio na linha de comando  
 Você pode instalar o VSSDK da linha de comando usando o **/InstallSelectableItems** alternar com o instalador do Visual Studio. Para obter detalhes sobre como usar parâmetros de linha de comando com o instalador, consulte [usar parâmetros de linha de comando para instalar o Visual Studio](../install/use-command-line-parameters-to-install-visual-studio.md).  
  
 Aqui está como instalar o VSSDK silenciosamente usando o instalador do Visual Studio 2015 Community:  
  
```  
vs_community.exe /s /installSelectableItems VS_SDK_GROUPV1  
```  
  
 Observe que você deve usar o instalador do Visual Studio que corresponda à versão instalada do Visual Studio. Por exemplo, se você tiver o Visual Studio Enterprise instalado no seu computador, você deve executar o instalador do Visual Studio Enterprise (vs_enterprise.exe).
