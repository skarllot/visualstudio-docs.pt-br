---
title: "Suporte a várias versões do Visual Studio | Documentos do Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Visual Studio, supporting multiple versions
- VSPackages, side-by-side compatibility
ms.assetid: 0047aa90-1ed4-40d3-8772-622b2719a4b1
caps.latest.revision: 20
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
ms.openlocfilehash: 969409366d789412d98b1e6208cc47bf3b1650d9
ms.lasthandoff: 02/22/2017

---
# <a name="supporting-multiple-versions-of-visual-studio"></a>Suporte a várias versões do Visual Studio
O termo *lado a lado* significa que você pode instalar e manter várias versões de um produto no mesmo computador. Para os VSPackages, isso significa que um usuário pode ter várias versões do Visual Studio instaladas no mesmo computador. No entanto, você não pode ter versões lado a lado do seu VSPackages carregados em uma única versão do Visual Studio.  
  
 Antes de fazer o VSPackage capaz de ser carregado no lado a lado versões do Visual Studio, considere o seguinte:  
  
-   Você deve determinar qual estratégia de implementação lado a lado que devem ser seguidas.  
  
     Para obter mais informações, consulte [escolhendo entre compartilhados e VSPackages versão](../extensibility/choosing-between-shared-and-versioned-vspackages.md).  
  
-   Seus formatos de arquivo de solução e projeto devem se ajustar à sua estratégia de implementação.  
  
     Para obter mais informações, consulte [atualização personalizada projetos](../misc/upgrading-custom-projects.md) e [registrar extensões de nome de arquivo para implantações lado a lado](../extensibility/registering-file-name-extensions-for-side-by-side-deployments.md).  
  
-   O instalador deve tratar a sua estratégia de implementação para que os componentes de controle de versão e os componentes compartilhados entre todas as versões, estão corretamente instalados e registrados.  
  
     Para obter mais informações, consulte [instalando os VSPackages com o Windows Installer](../extensibility/internals/installing-vspackages-with-windows-installer.md) e também [gerenciamento de componente](../extensibility/internals/component-management.md).  
  
    > [!NOTE]
    >  Instalar uma versão do Visual Studio também instala uma versão correspondente do [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]. Por exemplo, a instalação do Visual Studio 2010 e o Visual Studio 2012 no mesmo computador também instala versões 4.0 e 4.5 do [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)], respectivamente.  
  
## <a name="in-this-section"></a>Nesta seção  
 [Escolhendo entre os VSPackages compartilhados e controle de versão](../extensibility/choosing-between-shared-and-versioned-vspackages.md)  
 Explica como resolver problemas de lado a lado em seu VSPackage.  
  
 [Registrando extensões de nome de arquivo para implantações lado a lado](../extensibility/registering-file-name-extensions-for-side-by-side-deployments.md)  
 Descreve como o VSPackage pode registrar associações de arquivo em um cenário de lado a lado.  
  
## <a name="related-sections"></a>Seções relacionadas  
 [Instalando VSPackages](../misc/installing-vspackages.md)  
 Discute como criar e instalar os VSPackages e como oferecer suporte a usuários que estão executando várias versões do Visual Studio ao mesmo tempo.
