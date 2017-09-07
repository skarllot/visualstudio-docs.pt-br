---
title: "Considerações especiais para a instalação do Visual Studio em um ambiente offline | Microsoft Docs"
description: "{{ESPAÇO RESERVADO}}"
ms.date: 08/14/2017
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
ms.translationtype: HT
ms.sourcegitcommit: f23906933add1f4706d8786b2950fb3b5d2e6781
ms.openlocfilehash: 62fc2d38a628cfc28913a0a45e1e3cb5d3852330
ms.contentlocale: pt-br
ms.lasthandoff: 08/14/2017

---
# <a name="special-considerations-for-installing-visual-studio-in-an-offline-environment"></a>Considerações especiais para a instalação do Visual Studio em um ambiente offline

O Visual Studio é projetado principalmente para instalação em um computador conectado à Internet, pois muitos componentes são atualizados regularmente. No entanto, com algumas etapas adicionais, é possível implantar o Visual Studio em um ambiente em que uma conexão com a Internet operacional não está disponível.

## <a name="install-certificates-needed-for-visual-studio-offline-installation"></a>Instalar os certificados necessários para instalação offline do Visual Studio
O mecanismo de instalação do Visual Studio instalará apenas conteúdo confiável. Ele faz isso ao conferir as assinaturas Authenticode do conteúdo que está sendo baixado e verificar se todo o conteúdo é confiável antes de instalá-lo. Isso mantém seu ambiente seguro contra ataques nos quais o local de download está comprometido. A instalação do Visual Studio, portanto, requer que vários certificados intermediários e raiz padrão da Microsoft estejam instalados e atualizados no computador do usuário. Se o computador tiver sido mantido atualizado com o Windows Update, os certificados de autenticação serão atualizados automaticamente e, durante a instalação, o Visual Studio atualizará os certificados conforme necessário para verificar as assinaturas de arquivo.

Para empresas com computadores offline sem os certificados raiz mais recentes, um administrador poderá usar as instruções na página [Configurar raízes confiáveis e certificados não permitidos](https://technet.microsoft.com/en-us/library/dn265983.aspx) para atualizá-los. Como alternativa, ao criar um layout de rede, os certificados necessários são baixados para a pasta `certificates`. Você pode instalar manualmente os certificados clicando duas vezes no arquivo de certificado e clicando no assistente Gerenciador de Certificados. Se for solicitado a fornecer uma senha, deixe-a em branco.

Se estiver usando o script de implantação do Visual Studio em um ambiente offline para estações de trabalho cliente, você deverá seguir estas etapas:

1. Copie a [ferramenta Gerenciador de Certificados](https://msdn.microsoft.com/en-us/library/e78byta0.aspx) (`certmgr.exe`) para o compartilhamento de instalação (por exemplo, `\\server\share\vs2017`). `certmgr.exe` não está incluído como parte do Windows em si, mas está disponível como parte do [SDK do Windows](https://developer.microsoft.com/en-US/windows/downloads/windows-10-sdk).

2. Crie um arquivo em lotes com os seguintes comandos:

   ```cmd
   certmgr.exe -add -c certificates\manifestSignCertificates.p12 -n "Microsoft Code Signing PCA 2011" -s -r LocalMachine CA

   certmgr.exe -add -c certificates\manifestSignCertificates.p12 -n "Microsoft Root Certificate Authority" -s -r LocalMachine root

   certmgr.exe -add -c certificates\manifestCounterSignCertificates.p12 -n "Microsoft Time-Stamp PCA 2010" -s -r LocalMachine CA

   certmgr.exe -add -c certificates\manifestCounterSignCertificates.p12 -n "Microsoft Root Certificate Authority" -s -r LocalMachine root

   certmgr.exe -add -c certificates\vs_installer_opc.SignCertificates.p12 -n "Microsoft Code Signing PCA" -s -r LocalMachine CA

   certmgr.exe -add -c certificates\vs_installer_opc.SignCertificates.p12 -n "Microsoft Root Certificate Authority" -s -r LocalMachine root
   ```

3. Implante o arquivo em lotes para o cliente. Este comando deve ser executado de um processo elevado.

### <a name="what-are-the-certificates-files-in-the-certificates-folder"></a>Quais são os certificados de arquivos na pasta `certificates`?
Os três arquivos `.p12` nesta pasta contêm um certificado intermediário e um certificado raiz. A maioria dos sistemas atuais com o Windows Update têm esses certificados já instalados.

* `ManifestSignCertificates.p12` contém:
    * Certificado intermediário: **ACP de Assinatura de Código da Microsoft 2011**
        * Não obrigatório. Melhora o desempenho em alguns cenários, se estiver presente.
    * Certificado raiz: **Autoridade de Certificação Raiz da Microsoft 2011**
        * Necessário nos sistemas Windows 7 Service Pack 1 que não têm as atualizações mais recentes do Windows instaladas.
* `ManifestCounterSignCertificates.p12`
    * Certificado intermediário: **ACP do carimbo de data/hora da Microsoft 2010**
        * Não obrigatório. Melhora o desempenho em alguns cenários, se estiver presente.
    * Certificado raiz: **Autoridade de Certificação Raiz da Microsoft 2010**
        * Necessário para os sistemas Windows 7 Service Pack 1 que não têm as atualizações mais recentes do Windows instaladas.
* `vs_installer_opc.SignCertificates.p12`
    * Certificado intermediário: **ACP de Assinatura de Código da Microsoft**
        * Necessário para todos os sistemas. Observe que os sistemas com todas as atualizações aplicadas pelo Windows Update podem não ter esse certificado.
    * Certificado raiz: **Autoridade de Certificação Raiz da Microsoft**
        * Necessário. Esse certificado é fornecido com os sistemas que executam o Windows 7 ou posterior.

### <a name="why-are-the-certificates-from-the-certificates-folder-not-installed-automatically"></a>Por que certificados da pasta `certificates` não são instalados automaticamente?
Quando uma assinatura é verificada em um ambiente online, as APIs do Windows são usadas para baixar e adicionar os certificados no sistema. A verificação de que o certificado é confiável e permitido por meio de configurações administrativas ocorre durante esse processo. Esse processo de verificação não pode ocorrer na maioria dos ambientes offline. Instalar certificados manualmente permite aos administradores de empresa garantir que eles sejam confiáveis e atendam à política de segurança de suas organizações.

### <a name="checking-if-certificates-are-already-installed"></a>Verificando se os certificados já estão instalados
Uma maneira de verificar no sistema de instalação é seguir estas etapas:
1. Execute `mmc.exe`.<br/>
  a. Clique em Arquivo e selecione **Adicionar/Remover Snap-in**.<br/>
  b. Clique duas vezes em **Certificados**, selecione **Conta do computador** e clique em **Avançar**.<br/>
  c. Selecione **Computador local**, clique em **Concluir** e depois em **OK**.<br/>
  d. Expanda os **Certificados (computador local)**.<br/>
  e. Expanda **Autoridades de Certificação Confiáveis** e selecione **Certificados**.<br/>
    * Verifique os certificados raiz necessários para esta lista.<br/>
  
   f. Expanda **Autoridades de Certificação Intermediárias** e selecione **Certificados**.<br/>
    * Verifique os certificados intermediários necessários desta lista.<br/>

2. Clique em Arquivo e selecione **Adicionar/Remover Snap-in**.<br/>
  a. Clique duas vezes em **Certificados**, selecione **Minha conta de usuário**, clique em **Concluir** e em **OK**.<br/>
  b. Expanda **Certificados – Usuário atual**.<br/>
  c. Expanda **Autoridades de Certificação Intermediárias** e selecione **Certificados**.<br/>
    * Verifique os certificados intermediários necessários desta lista.<br/>

Se os nomes dos certificados não estiverem na coluna **Emitido Para**, eles terão que ser instalados.  Se um certificado intermediário estiver apenas no repositório de certificados intermediários do **Usuário Atual**, ele só estará disponível para o usuário que estiver conectado e talvez precise ser instalado para outros usuários.

## <a name="install-visual-studio"></a>Instalar o Visual Studio
Depois de instalar os certificados, implantação do Visual Studio pode continuar offline sem etapas especiais adicionais usando as instruções da seção [Implantação de uma instalação de rede]((create-a-network-installation-of-visual-studio.md#deploying-from-a-network-installation) da página "Criar uma instalação de rede do Visual Studio".


## <a name="see-also"></a>Consulte também
* [Instalar o Visual Studio](install-visual-studio.md)
* [Guia do administrador do Visual Studio](visual-studio-administrator-guide.md)
* [Usar parâmetros de linha de comando para instalar o Visual Studio](use-command-line-parameters-to-install-visual-studio.md)
* [Carga de trabalho do Visual Studio e IDs do componente](workload-and-component-ids.md)

