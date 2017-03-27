---
title: Guia do administrador do Visual Studio | Microsoft Docs
ms.custom: 
ms.date: 03/07/2017
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
ms.sourcegitcommit: a42f5a30375192c89c9984e40ba0104da98d7253
ms.openlocfilehash: 69ac1327fa9233bf0ecc18be5e7d2f2a4f82b3b0
ms.lasthandoff: 03/07/2017

---
# <a name="visual-studio-administrator-guide-for-visual-studio-2017"></a>Guia do administrador do Visual Studio para Visual Studio 2017

Você pode implantar o Visual Studio em uma rede, com a condição de que cada computador de destino atenda aos [requisitos mínimos de instalação](https://www.visualstudio.com/en-us/productinfo/vs2017-system-requirements-vs). É possível criar um compartilhamento de rede executando o arquivo de instalação com a opção --layout (conforme descrito na página [Criar uma instalação offline do Visual Studio](create-an-offline-installation-of-visual-studio.md)) e, em seguida, copiá-lo do computador local para o compartilhamento de rede.   

 Observe que as instalações de um compartilhamento de rede “lembrarão” do local de origem de onde vieram. Isso significa que um reparo de um computador cliente pode ter que retornar para o compartilhamento de rede do qual o cliente foi instalado originalmente. Escolha cuidadosamente seu local de rede para que ele se alinhe com o tempo de vida esperado de execução de clientes do Visual Studio 2017 na sua organização.

## <a name="tools"></a>Ferramentas

 Temos várias ferramentas em oferta para ajudá-lo a gerenciar as instalações do Visual Studio:

* [VS-Setup-Samples](https://github.com/microsoft/vs-setup-samples): amostras do C# e C++ para ajudar os usuários a investigar as instâncias do VS em seus computadores.
* [VSWhere](https://github.com/microsoft/vswhere): um .exe do C++ que ajuda você a encontrar as principais ferramentas do Visual Studio.
* [VSSetup.PowerShell](https://github.com/microsoft/vssetup.powershell): scripts avançados do PowerShell para tarefas comuns de administração relacionadas à instalação.


## <a name="see-also"></a>Consulte também
* [Instalar o Visual Studio 2017](install-visual-studio.md)
* [Usar parâmetros de linha de comando para instalar o Visual Studio 2017](use-command-line-parameters-to-install-visual-studio.md)
* [Criar uma instalação offline do Visual Studio 2017](create-an-offline-installation-of-visual-studio.md)
* [Usar IDs de carga de trabalho e de componente do Visual Studio para personalizar a instalação offline](workload-and-component-ids.md)
* [Relatar um problema com o Visual Studio 2017](../ide/how-to-report-a-problem-with-visual-studio-2017.md)

