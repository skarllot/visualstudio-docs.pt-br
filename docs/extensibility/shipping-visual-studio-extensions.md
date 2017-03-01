---
title: "Envio de extensões do Visual Studio | Documentos do Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- VSIX deployment
- deployment, VSIX
- satellite DLLs, in VSIX packages
ms.assetid: 13cd263d-25f7-488e-9c1a-cff908caedb6
caps.latest.revision: 26
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
ms.openlocfilehash: f0cb683cfa2fcafd2f3313aea52ec08fbba578a6
ms.lasthandoff: 02/22/2017

---
# <a name="shipping-visual-studio-extensions"></a>Envio de extensões do Visual Studio
Depois de desenvolver sua extensão, instalá-lo em outros computadores, compartilhá-lo com seus amigos e colegas de trabalho ou publicá-lo na Galeria do Visual Studio. Nesta seção, explicaremos todas as coisas que você precisa fazer para publicar e manter sua extensão: trabalhar com arquivos. VSIX, publicação, localizando e atualizando.  
  
## <a name="working-with-vsix-extensions"></a>Trabalhando com extensões VSIX  
 Você pode criar um extensões VSIX criando um projeto do VSIX em branco e, em seguida, adicionar modelos de item diferente a ele. Para obter mais informações, consulte [modelo de projeto do VSIX](../extensibility/vsix-project-template.md).  
  
 Você pode usar o formato do VSIX para modelos de projeto do pacote, componentes Managed Extensibility Framework (MEF) VSPackages, modelos de item **Toolbox** controles, assemblies e tipos personalizados (Isso inclui páginas de inicialização personalizada). O formato do VSIX usa implantação baseada em arquivo. Para obter mais informações sobre pacotes VSIX, consulte [Anatomia de um pacote VSIX](../extensibility/anatomy-of-a-vsix-package.md).  
  
 O formato do VSIX não dá suporte à instalação de trechos de código. Ele também não suporta outros cenários, como escrita para o Cache de Assembly Global (GAC) ou no registro do sistema. Se você precisar escrever no GAC ou no registro na instalação, você deve usar o Windows Installer. Para obter mais informações, consulte [Preparando extensões para implantação do Windows Installer](../extensibility/preparing-extensions-for-windows-installer-deployment.md).  
  
## <a name="publishing-your-extension-to-the-visual-studio-gallery"></a>Publicar sua extensão na Galeria do Visual Studio  
 Você pode distribuir sua extensão a outras pessoas simplesmente, enviando-o no arquivo. VSIX ou colocar um servidor. Mas a melhor maneira de obter o código nas mãos de muitas pessoas é colocá-lo no [Galeria do Visual Studio](http://go.microsoft.com/fwlink/?LinkID=123847). Extensões da Galeria do Visual Studio estão disponíveis para usuários do Visual Studio por meio de **extensões e atualizações**. Para obter mais informações, consulte [Localizando e usando extensões do Visual Studio](../ide/finding-and-using-visual-studio-extensions.md).  
  
 Para obter um exemplo completo que mostra como carregar uma extensão para a Galeria do Visual Studio, consulte [passo a passo: publicando uma extensão do Visual Studio](../extensibility/walkthrough-publishing-a-visual-studio-extension.md).  
  
## <a name="private-galleries"></a>Galerias privadas  
 À medida que desenvolve controles, modelos e ferramentas, você pode compartilhá-los com sua organização postando-os em uma galeria privada em sua intranet. Para obter mais informações, consulte [galerias particular](../extensibility/private-galleries.md).  
  
## <a name="localizing-your-extension"></a>Localizando a extensão  
 Se você estiver planejando lançar sua extensão em locais diferentes, considere a possibilidade de localização. Para obter uma explicação do que está envolvido, consulte [Localizando pacotes VSIX](../extensibility/localizing-vsix-packages.md).  
  
## <a name="updating-and-versioning-your-extension"></a>A extensão de controle de versão e atualização  
 Após ter publicado sua extensão, será colocado um tempo quando você precisa atualizá-lo. Para saber como atualizar uma extensão que foi publicada na Galeria do Visual Studio, consulte [como: atualizar uma extensão](../extensibility/how-to-update-a-visual-studio-extension.md).  
  
 Você pode definir sua extensão para oferecer suporte a várias versões do Visual Studio. Para obter mais informações, consulte [suporte a várias versões do Visual Studio](../extensibility/supporting-multiple-versions-of-visual-studio.md).  
  
## <a name="related-topics"></a>Tópicos relacionados  
  
|Título|Descrição|  
|-----------|-----------------|  
|[Introdução ao modelo de projeto do VSIX](../extensibility/getting-started-with-the-vsix-project-template.md)|Explica como usar o modelo de projeto do VSIX para instalar um modelo de projeto personalizado.|  
|[Anatomia de um pacote VSIX](../extensibility/anatomy-of-a-vsix-package.md)|Descreve os componentes de um pacote VSIX.|  
|[Modelo de projeto do VSIX](../extensibility/vsix-project-template.md)|Fornece instruções passo a passo sobre como empacotar e publicar uma extensão.|  
|[Localizando pacotes VSIX](../extensibility/localizing-vsix-packages.md)|Explica como fornecer texto localizado para o processo de instalação por meio de extension.vsixlangpack arquivos.|  
|[Como: atualizar uma extensão](../extensibility/how-to-update-a-visual-studio-extension.md)|Descreve como atualizar uma extensão no seu sistema e como implantar uma atualização em uma extensão existente do Visual Studio.|  
|[Como: adicionar uma dependência a um pacote VSIX](../extensibility/how-to-add-a-dependency-to-a-vsix-package.md)|Descreve como adicionar referências aos pacotes de implantação do VSIX.|  
|[Preparando extensões para a implantação do Windows Installer](../extensibility/preparing-extensions-for-windows-installer-deployment.md)|Explica como implantar sua extensão com o Windows Installer.|  
|[Assinando pacotes VSIX](../extensibility/signing-vsix-packages.md)|Explica como assinar pacotes VSIX.|  
|[Galerias privadas](../extensibility/private-galleries.md)|Explica como criar galerias privadas para extensões.|  
|[Suporte a várias versões do Visual Studio](../extensibility/supporting-multiple-versions-of-visual-studio.md)|Mostra como fazer com que o suporte à extensão de várias versões do Visual Studio.|
