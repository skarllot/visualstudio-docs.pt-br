---
title: "Implantar uma extensão de modelo de camada | Documentos do Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- dependency diagrams, deploying extensions
- layer models, deploying extensions
ms.assetid: 00a4675b-d20e-487e-8fd5-be2b1e0ba238
caps.latest.revision: 27
author: alexhomer1
ms.author: ahomer
manager: douge
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
translationtype: Machine Translation
ms.sourcegitcommit: 8f84f22444a5df5b9f4f4af44cd8ee9136403467
ms.openlocfilehash: 03164fe80a0b8f4dbc321a7e57b7db9e38e405d5
ms.lasthandoff: 02/22/2017

---
# <a name="deploy-a-layer-model-extension"></a>Implantar uma extensão de modelo de camada
Outros usuários do Visual Studio podem instalar extensões que você criar usando o Visual Studio de modelagem da camada.  
  
## <a name="installing-your-extension"></a>Instalando a extensão  
 A extensão é compilada em um arquivo VSIX, que pode ser instalado em outros computadores. Você também pode instalá-lo no seu computador de desenvolvimento, para disponibilizar a extensão na instância principal do Visual Studio.  
  
#### <a name="to-install-the-extension"></a>Para instalar a extensão  
  
1.  No projeto que contém **source.vsix.manifest**, abra **bin\\ \* ** no Explorador de arquivos.  
  
2.  Copie o ** \*. VSIX** arquivo para o computador no qual você deseja instalar a extensão.  
  
3.  No computador de destino, clique duas vezes no arquivo de *.vsix no Windows Explorer.  
  
     Abre o instalador VSIX.  
  
#### <a name="to-uninstall-the-extension"></a>Para desinstalar a extensão  
  
1.  No Visual Studio, no **ferramentas** menu, clique em **extensões e atualizações**.  
  
2.  Clique no nome da extensão e, em seguida, clique em **desinstalar**.  
  
## <a name="installing-an-extension-on-a-team-foundation-build-server"></a>Instalando uma extensão em um servidor de compilação do Team Foundation  
 [!INCLUDE[esprbuild](../misc/includes/esprbuild_md.md)]servidores normalmente não tenha instalado o Visual Studio, e portanto não é possível instalar o VSIX clicando duas vezes nele. A instalação do [!INCLUDE[esprbuild](../misc/includes/esprbuild_md.md)] inclui alguns componentes que permitem que uma extensão do VSIX executar, mas você deve instalar a extensão manualmente.  
  
#### <a name="to-install-your-layer-extension-on-a-includeesprbuildmiscincludesesprbuildmdmd-server"></a>Para instalar a extensão de camada em um [!INCLUDE[esprbuild](../misc/includes/esprbuild_md.md)] Server  
  
1.  Copie o **. VSIX** arquivos do seu computador de desenvolvimento para o [!INCLUDE[esprbuild](../misc/includes/esprbuild_md.md)] computador.  
  
     Coloque o arquivo VSIX em um dos seguintes locais:  
  
    -   Para instalar todos os usuários e serviços:  
  
         %ProgramFiles%\Microsoft visual Studio [version] \Common7\IDE\Extensions\Microsoft  
  
    -   Para instalar somente para o serviço de rede que executa [!INCLUDE[esprbuild](../misc/includes/esprbuild_md.md)]:  
  
         %WinDir%\ServiceProfiles\NetworkService\AppData\Local\Microsoft\VisualStudio\\\Extensions\Microsoft [version]  
  
    -   Se você tiver configurado [!INCLUDE[esprbuild](../misc/includes/esprbuild_md.md)] para executar no modo interativo como um usuário específico, você pode instalar apenas para o usuário:  
  
         %LocalAppData%\Microsoft\VisualStudio\\\Extensions\Microsoft [version]  
  
        > [!NOTE]
        >  % LocalAppData % é normalmente *DriveName*: usuários*nome de usuário*AppDataLocal.  
  
2.  Expanda cada arquivo VSIX em uma pasta no mesmo local:  
  
    1.  Alterar a extensão de nome de arquivo de **. VSIX** para **. zip**.  
  
    2.  Extraia o conteúdo do arquivo. zip para uma pasta.  
  
    3.  Excluir o arquivo. zip  
  
3.  Reinicie o [!INCLUDE[esprbuild](../misc/includes/esprbuild_md.md)].

