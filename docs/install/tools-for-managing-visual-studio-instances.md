---
title: "Ferramentas para detectar e gerenciar instâncias do Visual Studio | Microsoft Docs"
description: "{{ESPAÇO RESERVADO}}"
ms.date: 08/14/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-install
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- '{{PLACEHOLDER}}'
- '{{PLACEHOLDER}}'
ms.assetid: 85686707-14C0-4860-9B7A-66485D43D241
author: timsneath
ms.author: tims
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: f23906933add1f4706d8786b2950fb3b5d2e6781
ms.openlocfilehash: 1e81071d8a67fd5b8c38bcf87629604efe6fa4a5
ms.contentlocale: pt-br
ms.lasthandoff: 08/14/2017

---

# <a name="tools-for-detecting-and-managing-visual-studio-instances"></a>Ferramentas para detectar e gerenciar instâncias do Visual Studio

## <a name="detecting-existing-visual-studio-instances"></a>Detectando instâncias existentes do Visual Studio
Tornamos várias ferramentas disponíveis que ajudarão você a detectar e gerenciar instâncias do Visual Studio instaladas em computadores cliente:

* [VSWhere](https://github.com/microsoft/vswhere): um executável integrado ao Visual Studio ou disponível para distribuição separada que ajuda a encontrar o local de todas as instâncias do Visual Studio em um computador específico.
* [VSSetup.PowerShell](https://github.com/microsoft/vssetup.powershell): scripts do PowerShell que usam a API de Configuração de Instalação para identificar instâncias instaladas do Visual Studio.
* [VS-Setup-Samples](https://github.com/microsoft/vs-setup-samples): amostras do C# e C++ que demonstram como usar a API de Configuração de Instalação para consultar uma instalação existente.

Além disso, a [API de Configuração de Instalação](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.setup.configuration.aspx) fornece interfaces para desenvolvedores que desejam criar seus próprios utilitários para interrogar instâncias do Visual Studio.

## <a name="using-vswhereexe"></a>Usar o vswhere.exe
`vswhere.exe` é incluído automaticamente no Visual Studio 2017 versão 15.2 ou superior, ou pode ser baixado da [página de versões](https://github.com/Microsoft/vswhere/releases). Use o `vswhere -?` para obter informações de ajuda sobre a ferramenta. Como exemplo, este comando mostra todas as versões do Visual Studio, incluindo versões mais antigas do produto e pré-lançamentos e gera os resultados no formato JSON:

```cmd
C:\Program Files (x86)\Microsoft Visual Studio\Installer> vswhere.exe -legacy -prerelease -format json
```

>[!TIP]
>Para obter mais informações sobre a instalação do Visual Studio 2017, consulte [artigos de blog de Heath Stewart](https://blogs.msdn.microsoft.com/heaths/tag/vs2017/).


## <a name="editing-the-registry-for-a-visual-studio-instance"></a>A edição do Registro para uma instância do Visual Studio
No Visual Studio de 2017, configurações do Registro são armazenadas em um local privado, o que permite várias instâncias lado a lado no mesmo computador com a mesma versão do Visual Studio.

Como essas entradas não são armazenadas no Registro global, há instruções especiais para usar o Editor do Registro para fazer alterações nas configurações do Registro:

1. Se você tiver uma instância do Visual Studio 2017 aberta, feche-a.
2. Inicie o `regedit.exe`.
3. Selecione o nó `HKEY_LOCAL_MACHINE`.
4. No menu principal do Regedit, selecione **Arquivo -> Carregar Hive...** e selecione o arquivo de Registro privado, que é armazenado na pasta **AppData\Local**. Por exemplo:
   ```
   %localappdata%\Microsoft\VisualStudio\<config>\privateregistry.bin
   ```

> [!NOTE]
> `<config>` corresponde à instância do Visual Studio que você deseja procurar.

Você precisará fornecer um nome de hive, que se tornará o nome do hive isolado. Depois de fazer isso, você poderá pesquisar o Registro no hive isolado que criou.

> [!IMPORTANT]
> Antes de iniciar o Visual Studio novamente, você deve descarregar a seção isolada que criou. Para fazer isso, selecione Arquivo -> Descarregar Hive no menu principal do Regedit. (Se você não fizer isso, o arquivo permanecerá bloqueado e o Visual Studio não poderá ser iniciado.)

