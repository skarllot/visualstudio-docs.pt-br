---
title: "Atualizações de controle para as implantações do Visual Studio | Microsoft Docs"
description: "{{ESPAÇO RESERVADO}}"
ms.date: 05/06/2017
ms.reviewer: tims
ms.suite: 
ms.technology:
- vs-ide-install
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- '{{PLACEHOLDER}}'
- '{{PLACEHOLDER}}'
ms.assetid: 35C7AB05-07D5-4B38-BCAC-AB88444E7368
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
ms.openlocfilehash: 2e68d084c88c398d1576f53a79a156c111651895
ms.contentlocale: pt-br
ms.lasthandoff: 05/09/2017

---
# <a name="control-updates-to-network-based-visual-studio-deployments"></a>Atualizações de controle para implantações do Visual Studio com base em rede

Geralmente, os administradores de empresa criam um layout e o hospedam em um compartilhamento de arquivo de rede para implantação para seus usuários finais.

## <a name="controlling-where-visual-studio-looks-for-updates"></a>Controlar onde o Visual Studio procura atualizações
Por padrão, o Visual Studio continuará a procurar atualizações online, mesmo se a instalação for implantada de um compartilhamento de rede. Se uma atualização estiver disponível, o usuário poderá instalá-lo; qualquer conteúdo atualizado que não for encontrado no layout offline será baixado da Web.

Se desejar ter controle direto sobre onde o Visual Studio procura por atualizações, bem como para qual versão os usuários são atualizados, você poderá modificar o local em que o Visual Studio procura por atualizações seguindo estas etapas:

 1. Crie um layout offline:
    ```
    vs_enterprise.exe --layout C:\vs2017offline --lang en-US
    ```
 2. Copie-o para o compartilhamento de arquivo onde você deseja hospedá-lo:
    ```
    xcopy /e C:\vs2017offline \\server\share\VS2017
    ```
 3. Modifique o arquivo response.json no layout e altere o valor `channelUri` para apontar para uma cópia de channelManifest.json que o administrador controla. <b>Observação:</b> não se esqueça de incluir barras invertidas de escape no valor, desta forma:
    ```json
    "channelUri":"\\\\server\\share\\VS2017\\ChannelManifest.json"
    ```
 4. Agora os usuários finais podem executar a instalação deste compartilhamento para instalar o Visual Studio.
    ```
    \\server\share\VS2017\vs_enterprise.exe
    ```
 5. Quando um administrador de empresa determina que é hora de os usuários atualizarem para uma versão mais recente do Visual Studio, eles podem [atualizar a localização do layout](update-a-network-installation-of-visual-studio.md) para incorporar os arquivos atualizados, com um comando como este:
    ```
    vs_enterprise.exe --layout \\server\share\VS2017 --lang en-US
    ```
 6. Verifique se o arquivo response.json no layout atualizado ainda contém as personalizações, especificamente a modificação de channelUri:
    ```json
    "channelUri":"\\\\server\\share\\VS2017\\ChannelManifest.json"
    ```
 7. Instalações existentes do Visual Studio desse layout procurarão atualizações em `\\server\share\VS2017\ChannelManifest.json`. Se o channelManifest.json é mais recente do que o que usuário possui instalado, o Visual Studio notificará o usuário de que uma atualização está disponível.
 8. Novas instalações instalarão automaticamente a versão atualizada do Visual Studio diretamente do layout.

## <a name="controlling-notifications-in-the-visual-studio-ide"></a>Notificações de controle no IDE do Visual Studio
Conforme descrito acima, o Visual Studio verifica o local do qual foi instalado (por exemplo, o compartilhamento de rede ou a internet), para ver se há atualizações disponíveis. Quando uma atualização está disponível, por padrão, o Visual Studio notifica o usuário com um sinalizador de notificação no canto superior direito da janela: ![sinalizador de notificação de atualizações](~/docs/install/media/notification-flag.png)

Se você não quiser que os usuários finais sejam notificados de atualizações (por exemplo, você fornece atualizações por meio de um mecanismo de distribuição de software central), poderá desabilitar essas notificações.

Como o Visual Studio 2017 [Armazena as entradas do Registro em um Registro privado](tools-for-managing-visual-studio-instances.md#editing-the-registry-for-a-visual-studio-instance), você não pode editar diretamente o Registro da maneira normal. No entanto, o Visual Studio inclui um comando `vsregedit.exe` que você pode usar para alterar as configurações do Visual Studio. Você pode desativar as notificações com o seguinte comando:

```cmd
vsregedit.exe set "C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise" HKCU ExtensionManager AutomaticallyCheckForUpdates2 dword 0
```

Substitua o diretório no comando acima para coincidir com a instância instalada que deseja editar. 

> [!TIP]
> Use [vswhere.exe](tools-for-managing-visual-studio-instances.md#detecting-existing-visual-studio-instances) para localizar uma instância específica do Visual Studio em uma estação de trabalho cliente. 

## <a name="see-also"></a>Consulte também
* [Instalar o Visual Studio](install-visual-studio.md)
* [Guia do administrador do Visual Studio](visual-studio-administrator-guide.md)
* [Usar parâmetros de linha de comando para instalar o Visual Studio](use-command-line-parameters-to-install-visual-studio.md)
* [Ferramentas para gerenciar instâncias do Visual Studio](tools-for-managing-visual-studio-instances.md)

