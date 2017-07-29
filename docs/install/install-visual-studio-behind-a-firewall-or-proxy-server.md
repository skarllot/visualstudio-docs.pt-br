---
title: "Instalar o Visual Studio por trás de um firewall ou servidor proxy | Microsoft Docs"
description: 
ms.custom: 
ms.date: 07/18/2017
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
- list of domains, locations, URLs
ms.assetid: 
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: ddbbda1069749e2ce685507d55a070f1dec27c17
ms.openlocfilehash: 48fd143f917d6e13c18f6913bea625b2e8cf5ce8
ms.contentlocale: pt-br
ms.lasthandoff: 07/19/2017

---
# <a name="install-visual-studio-behind-a-firewall-or-proxy-server"></a>Instalar o Visual Studio por trás de um firewall ou servidor proxy

O Instalador do Visual Studio baixa arquivos de vários domínios e seus servidores de download. Esta página lista as URLs de domínio que talvez você queira colocar na "lista de permissões" como confiáveis em seus scripts de implantação.

Se for possível para seu ambiente, considere adicionar os domínios a seguir com os protocolos HTTP e HTTPS.

## <a name="microsoft-domains"></a>Domínios da Microsoft
| Domain | Finalidade |
| ------ | ------- |
| go.microsoft.com | Resolução da URL de instalação |
| aka.ms | Resolução da URL de instalação |
| download.visualstudio.microsoft.com | Local de download de pacotes de instalação |
| download.microsoft.com | Local de download de pacotes de instalação |
| download.visualstudio.com | Local de download de pacotes de instalação |
| dl.xamarin.com | Local de download de pacotes de instalação |
| visualstudiogallery.msdn.microsoft.com | Local de download de extensões do Visual Studio |
| www.visualstudio.com | Local da documentação |
| msdn.microsoft.com | Local da documentação |
| www.microsoft.com | Local da documentação |

## <a name="non-microsoft-domains"></a>Domínios que não são da Microsoft
| Domain | Instala essas cargas de trabalho |
| ------ | ------- |
| archive.apache.org |  Desenvolvimento móvel com JavaScript <br />(Cordova) |
| cocos2d-x.org | Desenvolvimento de jogos com C++ <br />(Cocos) |
| download.epicgames.com | Desenvolvimento de jogos com C++ <br />(Unreal Engine) |
| download.oracle.com | Desenvolvimento móvel com JavaScript <br />(SDK do Java) <br /><br />Desenvolvimento móvel com .NET <br />(SDK do Java) |
| download.unity3d.com | Desenvolvimento de jogos com Unity <br />(Unity) |
| netstorage.unity3d.com | Desenvolvimento de jogos com Unity <br /> (Unity) |
| dl.google.com | Desenvolvimento móvel com JavaScript <br />(NDK e SDK do Android, emulador) <br /><br />Desenvolvimento móvel com .NET <br />(NDK e SDK do Android, emulador) |
| www.incredibuild.com | Desenvolvimento de jogos com C++ <br />(IncrediBuild) |
| incredibuildvs2017i.azureedge.net | Desenvolvimento de jogos com C++ <br />(IncrediBuild) |
| www.python.org | Desenvolvimento do Python <br />(Python) <br /><br />Ciência de dados e aplicativos analíticos <br />(Python) |

## <a name="see-also"></a>Consulte também
* [Instalar o Visual Studio 2017](install-visual-studio.md)
* [Guia do administrador do Visual Studio](visual-studio-administrator-guide.md)
  * [Usar parâmetros de linha de comando para instalar o Visual Studio 2017](use-command-line-parameters-to-install-visual-studio.md)
    * [Exemplos de parâmetro de linha de comando](command-line-parameter-examples.md)
    * [Referência de ID de componente e carga de trabalho](workload-and-component-ids.md)
  * [Criar uma instalação em rede do Visual Studio](create-a-network-installation-of-visual-studio.md)
    * [Considerações especiais para a instalação do Visual Studio em um ambiente offline](install-visual-studio-in-offline-environment.md)
  * [Automatizar o Visual Studio com um arquivo de resposta](automated-installation-with-response-file.md)
  * [Chaves de produto automaticamente durante a implantação do Visual Studio](automatically-apply-product-keys-when-deploying-visual-studio.md)
  * [Definir padrões para implantações empresariais do Visual Studio](set-defaults-for-enterprise-deployments.md)
  * [Desabilitar ou mover o cache do pacote](disable-or-move-the-package-cache.md)
  * [Atualizar uma instalação em rede do Visual Studio](update-a-network-installation-of-visual-studio.md)
  * [Atualizações de controle para implantações do Visual Studio](controlling-updates-to-visual-studio-deployments.md)
  * [Ferramentas para detectar e gerenciar instâncias do Visual Studio](tools-for-managing-visual-studio-instances.md)
  * [Relatar um problema com o Visual Studio 2017](../ide/how-to-report-a-problem-with-visual-studio-2017.md)

