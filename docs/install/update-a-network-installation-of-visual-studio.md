---
title: "Atualizar uma instalação baseada em rede do Visual Studio | Microsoft Docs"
description: "{{ESPAÇO RESERVADO}}"
ms.date: 05/05/2017
ms.reviewer: tims
ms.suite: 
ms.technology:
- vs-ide-install
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- '{{PLACEHOLDER}}'
- '{{PLACEHOLDER}}'
ms.assetid: 1AF69C0E-0AC9-451B-845D-AE4EDBCEA65C
author: timsneath
ms.author: tims
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
ms.translationtype: Human Translation
ms.sourcegitcommit: 85576806818a6ed289c2f660f87b5c419016c600
ms.openlocfilehash: 75c65d75ab751058ac435d62f253ead149ccfe42
ms.contentlocale: pt-br
ms.lasthandoff: 05/09/2017

---
# <a name="update-a-network-based-installation-of-visual-studio"></a>Atualizar uma instalação em rede do Visual Studio

É possível atualizar um layout de instalação de rede do Visual Studio com as últimas atualizações de produto, para que ele possa ser usado como um ponto de instalação para a atualização mais recente do Visual Studio e também manter instalações que já estão implantadas em estações de trabalho do cliente.

## <a name="how-to-update-a-network-layout"></a>Como atualizar um layout de rede
Para atualizar o compartilhamento de instalação de rede para que ele inclua as atualizações mais recentes, execute o mesmo comando `--layout` executado ao criar inicialmente o layout para baixar pacotes atualizados de forma incremental.

Se você selecionou um layout parcial ao criar o layout de rede, use os mesmos parâmetros de linha de comando que usou ao criar o layout de instalação de rede (ou seja, as cargas de trabalho e as linguagens). Se você escolher opções diferentes, o segundo comando `--layout` não atualizará os pacotes que não foram especificados pela segunda vez.

Se você hospedar um layout em um compartilhamento de arquivo, será recomendável atualizar uma cópia privada do layout (por exemplo, `c:\vs2017offline`) e, depois que todo o conteúdo atualizado for baixado, copiá-lo para o compartilhamento de arquivo (por exemplo, `\\server\products\VS2017`).  Se você não fizer isso, haverá uma chance maior de que qualquer usuário que execute a instalação enquanto o layout está sendo atualizado não possa obter todo o conteúdo do layout, pois ele não está completamente atualizado.

## <a name="how-to-deploy-an-update-to-client-machines"></a>Como implantar uma atualização em computadores cliente
Dependendo de como o ambiente de rede é configurado, uma atualização pode ser implantada por um administrador de empresa ou iniciada de um computador cliente. 

- Os usuários podem atualizar uma instância do Visual Studio instalada de uma pasta de instalação offline:
  - Execute o instalador do Visual Studio.
  - Em seguida, clique em **Atualizar**.

- Os administradores podem atualizar implantações de cliente do Visual Studio sem qualquer interação do usuário com dois comandos separados:
  - Primeiro, atualize o instalador do Visual Studio: <br>```vs_enterprise.exe --quiet --update```
  - Depois, atualize o próprio aplicativo do Visual Studio: <br>```vs_enterprise.exe update --installPath "C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise" --quiet --wait --norestart```

> [!NOTE]
> Use o [comando vswhere.exe](tools-for-managing-visual-studio-instances.md) para identificar o caminho de instalação de uma instância existente do Visual Studio em um computador cliente.

> [!TIP]
> Para obter detalhes sobre como controlar quando as notificações de atualização são apresentadas aos usuários, confira [Controlar as atualizações nas implantações do Visual Studio com base em rede](controlling-updates-to-visual-studio-deployments.md).


## <a name="see-also"></a>Consulte também
* [Instalar o Visual Studio](install-visual-studio.md)
* [Guia do administrador do Visual Studio](visual-studio-administrator-guide.md)
* [Usar parâmetros de linha de comando para instalar o Visual Studio](use-command-line-parameters-to-install-visual-studio.md)
* [Ferramentas para detectar e gerenciar instâncias do Visual Studio](tools-for-managing-visual-studio-instances.md)
* [Atualizações de controle para implantações do Visual Studio com base em rede](controlling-updates-to-visual-studio-deployments.md)

