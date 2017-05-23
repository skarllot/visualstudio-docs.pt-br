---
title: Desabilitar ou mover o cache do pacote | Microsoft Docs
description: "Desabilitar, habilitar ou mover o cache do pacote para implantações do Visual Studio."
ms.date: 04/14/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-install
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- cache
- nocache
helpviewer_keywords:
- '{{PLACEHOLDER}}'
- '{{PLACEHOLDER}}'
ms.assetid: 2429993A-3F0E-41C5-9562-FEA6AE994440
author: heaths
ms.author: heaths
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
ms.openlocfilehash: e07f1c04d9695e092db7aa29e641ce9bd36250f9
ms.contentlocale: pt-br
ms.lasthandoff: 05/09/2017

---
# <a name="disable-or-move-the-package-cache"></a>Desabilitar ou mover o cache do pacote

O cache do pacote fornece uma origem de pacotes instalados, caso você precise reparar o Visual Studio ou outros produtos relacionados, em casos em não há conexão com a Internet. Com algumas unidades ou configurações de sistema, no entanto, não convém manter todos os pacotes.
O instalador os baixará quando necessário. Portanto, se você deseja salvar ou recuperar espaço em disco, pode desabilitar ou mover o cache do pacote.

## <a name="disable-the-package-cache"></a>Desabilitar o cache do pacote

Antes de instalar, modificar ou reparar o Visual Studio ou outros produtos com o novo instalador, você pode iniciar o instalador com a opção `--nocache` para o instalador.

```
"%ProgramFiles(x86)%\Microsoft Visual Studio\Installer\vs_installer.exe" --nocache
```

Qualquer operação que você fizer em qualquer produto removerá quaisquer pacotes existentes para o produto e evitará salvar pacotes após a instalação. Se você modificar ou reparar o Visual Studio e pacotes forem necessários, serão baixados automaticamente e removidos após a instalação.

Se você quiser reabilitar o cache, passe `--cache` em vez disso. Somente os pacotes que são necessários serão armazenados. Portanto, se você precisar restaurar todos os pacotes, deverá reparar o Visual Studio antes de se desconectar da rede.

```
"%ProgramFiles(x86)%\Microsoft Visual Studio\Installer\vs_installer.exe" repair --passive --norestart --cache
```

Você também pode definir a `KeepDownloadedPayloads` [política do Registro](set-defaults-for-enterprise-deployments.md) para desabilitar o cache antes de instalar, modificar ou reparar o Visual Studio.

## <a name="move-the-package-cache"></a>Mover o cache do pacote

Uma configuração comum do sistema é ter o Windows instalado em um SSD com um disco rígido maior (ou mais) para necessidades de desenvolvimento, como código-fonte, binários de programa e muito mais. Se quiser trabalhar offline em vez disso, você poderá mover o cache do pacote.

No momento, você só poderá fazer isso se definir a `CachePath`[política do Registro](set-defaults-for-enterprise-deployments.md) antes de instalar, modificar ou reparar o Visual Studio.

## <a name="see-also"></a>Consulte também

 * [Instalar o Visual Studio](install-visual-studio.md)
 * [Definir padrões para implantações corporativas](set-defaults-for-enterprise-deployments.md)
 * [Usar parâmetros de linha de comando para instalar o Visual Studio](use-command-line-parameters-to-install-visual-studio.md)
 * [Relatar um problema com o Visual Studio](../ide/how-to-report-a-problem-with-visual-studio-2017.md)

