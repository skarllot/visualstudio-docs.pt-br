---
title: "Considerações especiais para a instalação do Visual Studio em um ambiente offline | Microsoft Docs"
description: "{{ESPAÇO RESERVADO}}"
ms.date: 05/09/2017
ms.reviewer: tims
ms.suite: 
ms.technology:
- vs-ide-install
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- '{{PLACEHOLDER}}'
- '{{PLACEHOLDER}}'
ms.assetid: 9750A3F3-89C7-4A8F-BA75-B0B06BD772C2
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
ms.openlocfilehash: b596b6b6f9cff58525d253157534b6b990c68fcd
ms.contentlocale: pt-br
ms.lasthandoff: 05/09/2017

---
# <a name="special-considerations-for-installing-visual-studio-in-an-offline-environment"></a>Considerações especiais para a instalação do Visual Studio em um ambiente offline

O Visual Studio é projetado principalmente para instalação de um computador conectado à Internet, pois muitos componentes são atualizados regularmente. No entanto, com algumas etapas adicionais, é possível implantar o Visual Studio em um ambiente em que uma conexão com a Internet operacional não está disponível.

## <a name="create-a-network-installation-layout"></a>Criar um layout de instalação de rede
* Para obter detalhes, confira [Criar uma instalação baseada em rede do Visual Studio](create-a-network-installation-of-visual-studio.md)

## <a name="install-certificates-needed-for-visual-studio-offline-installation"></a>Instalar os certificados necessários para instalação offline do Visual Studio
O mecanismo de instalação do Visual Studio instalará apenas o conteúdo que é confiável.  Verifica as assinaturas Authenticode do conteúdo que está sendo baixado e verifica se ele é confiável antes de instalá-lo.  Computadores com acesso à Internet baixarão e instalarão automaticamente os certificados necessários para verificar as assinaturas de arquivo.  No entanto, se você estiver operando em um ambiente offline ou em um sistema com conectividade de Internet ruim, isso talvez não seja possível.  Para usuários no ambiente, você precisa garantir que os certificados necessários sejam pré-instalados.  Esses certificados são baixados pela máquina de execução para a pasta "certificados" ao criar uma instalação offline.

Você pode instalar os certificados no cliente manualmente clicando duas vezes no arquivo de certificado e clicando no assistente de gerenciador de certificados. Se for solicitado a fornecer uma senha, deixe-a em branco.

Para criar o script de instalação de certificados, siga estas etapas:

1. Copie certmgr.exe para o compartilhamento de instalação (por exemplo, `\server\share\vs2017`). `certmgr.exe` está incluído no SDK do Windows, que pode ser instalado como um componente opcional da carga de trabalho _desenvolvimento da Plataforma Universal do Windows_. (ex.: `"C:\Program Files (x86)\Windows Kits\10\bin\x86\certmgr.exe"`)

2. Crie um arquivo em lotes com os seguintes comandos:

```cmd
\\server\share\vs2017\certmgr.exe -add -c \\server\share\vs2017\certificates\manifestSignCertificates.p12 -n "Microsoft Code Signing PCA" -s -r LocalMachine CA

\\server\share\vs2017\certmgr.exe -add -c \\server\share\vs2017\certificates\manifestSignCertificates.p12 -n "Microsoft Root Certificate Authority" -s -r LocalMachine root

\\server\share\vs2017\certmgr.exe -add -c \\server\share\vs2017\certificates\manifestCounterSignCertificates.p12 -n "Microsoft Time-Stamp PCA" -s -r LocalMachine CA

\\server\share\vs2017\certmgr.exe -add -c \\server\share\vs2017\certificates\manifestCounterSignCertificates.p12 -n "Microsoft Root Certificate Authority" -s -r LocalMachine root

\\server\share\vs2017\certmgr.exe -add -c \\server\share\vs2017\certificates\vs_installer_opc.SignCertificates.p12 -n "Microsoft Code Signing PCA" -s -r LocalMachine CA

\\server\share\vs2017\certmgr.exe -add -c \\server\share\vs2017\certificates\vs_installer_opc.SignCertificates.p12 -n "Microsoft Root Certificate Authority" -s -r LocalMachine root
```

3. Execute o arquivo em lotes no cliente de um shell de comando de administrador ou de um processo elevado.

### <a name="why-are-the-certificates-from-the-certificates-folder-not-installed-automatically"></a>Por que certificados da pasta `certificates` não são instalados automaticamente?
Quando uma assinatura é verificada em um ambiente online, as APIs do Windows são usadas para baixar e adicionar os certificados no sistema. A verificação de que o certificado é confiável e permitido por meio de configurações administrativas ocorre durante esse processo. Esse processo de verificação não pode ocorrer na maioria dos ambientes offline. Instalar certificados manualmente permite ao usuário garantir que os certificados sejam confiáveis e atendam aos requisitos do administrador.

## <a name="install-visual-studio"></a>Instalar o Visual Studio
Após a instalação dos certificados, a implantação do Visual Studio pode continuar offline sem etapas adicionais especiais, usando as [instruções aqui](create-a-network-installation-of-visual-studio.md#deploying-from-a-network-installation).


## <a name="see-also"></a>Consulte também
* [Instalar o Visual Studio](install-visual-studio.md)
* [Guia do administrador do Visual Studio](visual-studio-administrator-guide.md)
* [Usar parâmetros de linha de comando para instalar o Visual Studio](use-command-line-parameters-to-install-visual-studio.md)
* [Carga de trabalho do Visual Studio e IDs do componente](workload-and-component-ids.md)

