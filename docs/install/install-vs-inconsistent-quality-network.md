---
title: "Instalar em ambientes de rede não confiável ou de baixa largura de banda | Microsoft Docs"
description: "Descreve como o instalador do Visual Studio funciona em condições de rede não confiável e explica como baixar os arquivos de instalação antes de iniciar a instalação."
ms.date: 04/14/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-install
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- '{{PLACEHOLDER}}'
- '{{PLACEHOLDER}}'
ms.assetid: 44DB1998-68CD-4560-870A-EE5B993DCF6E
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
ms.openlocfilehash: 9dbe70bce6c246416df64de304b06cd211320f2a
ms.contentlocale: pt-br
ms.lasthandoff: 05/09/2017

---

# <a name="install-visual-studio-2017-on-low-bandwidth-or-unreliable-network-environments"></a>Instalar o Visual Studio 2017 em ambientes de rede não confiável ou de baixa largura de banda
Projetamos o novo instalador do Visual Studio 2017 para funcionar bem em uma ampla variedade de condições de rede e computador.

- Os arquivos de que você precisará para instalar o Visual Studio é distribuído em uma rede de fornecimento global. Portanto, é possível obtê-lo para você de um servidor local;
- Durante o processo de instalação, tentamos três tecnologias de download diferentes (WebClient, BITS e WinInet) para minimizar a interferência com o software antivírus e proxy;
- O novo modelo com base em cargas de trabalho significa que você precisará instalar menos do que em versões anteriores do Visual Studio.

Portanto, recomendamos que você experimente o novo instalador da Web. Acreditamos que ele lhe proporcionará uma boa experiência. Porém, se você quer ter certeza de que baixou os arquivos de instalação com êxito antes de iniciar a instalação do Visual Studio, nós o ajudamos. Você pode usar a linha de comando para criar um cache local dos arquivos necessários antes de iniciar a instalação.

Veja como.

## <a name="download-the-visual-studio-bootstrapper"></a>Baixar o bootstrapper do Visual Studio
Comece baixando o bootstrapper do Visual Studio para sua edição do Visual Studio escolhida.

O arquivo de instalação &mdash; ou para ser mais específico, um arquivo bootstrapper &mdash; corresponderá ou será semelhante a um dos listados a seguir.

| Edição                    | Arquivo                                                                    |
|----------------------------|-------------------------------------------------------------------------|
| Comunidade Visual Studio    | [vs_community.exe](https://aka.ms/vs/15/release/vs_community.exe)       |
| Visual Studio Professional | [vs_professional.exe](https://aka.ms/vs/15/release/vs_professional.exe) |
| Visual Studio Enterprise   | [vs_enterprise.exe](https://aka.ms/vs/15/release/vs_enterprise.exe)     |

## <a name="create-a-local-install-cache"></a>Criar um cache local de instalação
Para criar um layout local, abra um prompt de comando e use um dos comandos dos exemplos a seguir. Estes exemplos supõem que você baixou o bootstrapper do Visual Studio Community: ajuste o comando conforme apropriado para sua edição.

- Para .NET Web e desenvolvimento de área de trabalho do .NET, execute:
  ```
  vs_community.exe --layout c:\vs2017layout --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Microsoft.VisualStudio.Workload.NetWeb --add Component.GitHub.VisualStudio --includeOptional --lang en-US
  ```
- Para a área de trabalho do .NET e o desenvolvimento do Office, execute:
  ```
  vs_community.exe --layout c:\vs2017layout --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Microsoft.VisualStudio.Workload.Office --includeOptional --lang en-US
  ```
- Para desenvolvimento do C++ da área de trabalho, execute:
  ```
  vs_community.exe --layout c:\vs2017layout --add Microsoft.VisualStudio.Workload.NativeDesktop --includeRecommended --lang en-US
  ```

- Para criar um layout de local completo com todos os recursos (isso levará algum tempo, pois temos _muitos_ recursos!), execute:
  ```
  vs_community.exe --layout c:\vs2017layout --lang en-US
  ```

Se você quiser instalar um idioma diferente do inglês, altere `en-US` para uma localidade da lista na parte inferior desta página. Use esta [lista de componentes e cargas de trabalho disponíveis](workload-and-component-ids.md) para personalizar ainda mais o cache de instalação conforme necessário.

## <a name="install-from-the-local-cache"></a>Instalar do cache local
Quando você executar de um cache local de instalação, usaremos as versões locais de cada um desses arquivos. Porém, se você selecionar componentes que não estão no cache durante a instalação, tentaremos baixá-los da Internet.

Para garantir que você instale somente os arquivos que baixou, use as mesmas opções de linha de comando que usou para criar o cache de layout. Por exemplo, se você tiver criado um cache de layout com o seguinte comando:

```
vs_community.exe --layout c:\vs2017layout --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Microsoft.VisualStudio.Workload.NetWeb --add Component.GitHub.VisualStudio --includeOptional --lang en-US
```

Use este comando para executar a instalação:

```
c:\vs2017layout\vs_community.exe --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Microsoft.VisualStudio.Workload.NetWeb --add Component.GitHub.VisualStudio --includeOptional
```

## <a name="list-of-language-locales"></a>Lista de localidades de idioma
| **Localidade de idioma** | **Linguagem** |
| ----------------------- | --------------- |  
| cs-CZ | Tcheco |
| de-DE | Alemão |
| pt-BR | Inglês |
| es-ES | Espanhol |
| fr-FR | Francês |
| it-IT | Italiano |
| ja-JP | Japonês |
| ko-KR | Coreano |
| pl-PL | Polonês |
| pt-BR | Português - Brasil |
| ru-RU | Russo |
| tr-TR | Turco |
| zh-CN | Chinês – Simplificado |
| zh-TW | Chinês – Tradicional |

## <a name="see-also"></a>Consulte também
* [Instalar o Visual Studio](install-visual-studio.md)
* [Guia do administrador do Visual Studio](visual-studio-administrator-guide.md)
* [Usar parâmetros de linha de comando para instalar o Visual Studio](use-command-line-parameters-to-install-visual-studio.md)

