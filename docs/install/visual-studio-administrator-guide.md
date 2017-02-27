---
title: Guia do administrador do Visual Studio | Microsoft Docs
ms.custom: 
ms.date: 01/12/2017
ms.prod: visual-studio-dev15
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-install
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- network installation, Visual Studio
- administrator guide, Visual Studio
- installing Visual Studio, administrator guide
ms.assetid: 4af353f5-6cfd-4ebe-bcfb-f42306e451a0
author: TerryGLee
ms.author: tglee
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Human Translation
ms.sourcegitcommit: 5e1ab0284a11fb9ecf30694d22b8bb5dc7a52a6d
ms.openlocfilehash: 91fb897e0bf124234484c3aada08ac57c4be1923

---
# <a name="visual-studio-administrator-guide-for-visual-studio-2017-rc"></a>Guia de administrador do Visual Studio para Visual Studio 2017 RC

Você pode implantar o Visual Studio em uma rede, com a condição de que cada computador de destino atenda aos [requisitos mínimos de instalação](https://www.visualstudio.com/en-us/productinfo/vs2017-system-requirements-vs). Você pode criar um compartilhamento de rede, executando o arquivo de instalação com a opção --layout (conforme descrito na página [Criar uma instalação offline do Visual Studio](create-an-offline-installation-of-visual-studio.md)) e, em seguida, copiá-lo do computador local para o compartilhamento de rede.   

 Observe que as instalações de um compartilhamento de rede “lembrarão” do local de origem de onde vieram. Isso significa que um reparo de um computador cliente pode ter que retornar para o compartilhamento de rede do qual o cliente foi instalado originalmente. Escolha cuidadosamente seu local de rede para que ele se alinhe com o tempo de vida esperado de execução de clientes do Visual Studio 2017 na sua organização.  

 > [!IMPORTANT]
 > Embora o Visual Studio 2017 RC, de modo geral, tenha suporte para uso em um ambiente de produção, as cargas de trabalho e componentes que estão marcados como "Visualização" na interface do usuário da instalação não têm suporte para uso em ambiente de produção.

## <a name="see-also"></a>Consulte também
* [Instalar o Visual Studio 2017 RC](install-visual-studio.md)
* [Usar parâmetros de linha de comando para instalar o Visual Studio 2017 RC](use-command-line-parameters-to-install-visual-studio.md)
* [Criar uma instalação offline do Visual Studio 2017 RC](create-an-offline-installation-of-visual-studio.md)
* [How to Report a Problem with Visual Studio 2017 RC](../ide/how-to-report-a-problem-with-visual-studio-2017.md) (Como relatar um problema com o Visual Studio 2017 RC)



<!--HONumber=Feb17_HO4-->


