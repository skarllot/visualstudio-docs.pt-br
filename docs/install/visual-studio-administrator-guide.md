---
title: Guia do administrador do Visual Studio | Microsoft Docs
ms.custom: 
ms.date: 04/03/2017
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
ms.sourcegitcommit: af9699b63fdfb81a274affb78856817520c38b05
ms.openlocfilehash: fb7a87b720ad29252c602d9be5b958d8417ab93e
ms.lasthandoff: 04/03/2017

---
# <a name="visual-studio-administrator-guide-for-visual-studio-2017"></a>Guia do administrador do Visual Studio para Visual Studio 2017

 Você pode implantar o Visual Studio em uma rede, com a condição de que cada computador de destino atenda aos [requisitos mínimos de instalação](https://www.visualstudio.com/en-us/productinfo/vs2017-system-requirements-vs).

 Se você estiver implantando por meio de softwares como o System Center ou por meio de um arquivo em lotes, normalmente é preciso percorrer as etapas a seguir:

1. [Armazenar em cache o layout do produto do Visual Studio](create-an-offline-installation-of-visual-studio.md) para um local de rede.

2. [Selecione as cargas de trabalho e os componentes](workload-and-component-ids.md) que deseja instalar.

3. [Crie um script de instalação](use-command-line-parameters-to-install-visual-studio.md) usando os itens selecionados e outros parâmetros de linha de comando para controlar a instalação.

4. Opcionalmente, [aplique uma chave de produto de licença de volume](automatically-apply-product-keys-when-deploying-visual-studio.md) como parte do script de instalação para que os usuários não precisem ativar o software separadamente.

5. Usa a tecnologia de implantação de sua escolha para executar o script gerado nas etapas anteriores em suas estações de trabalho do desenvolvedor de destino.

6. Atualize seu local de rede com as atualizações mais recentes do Visual Studio ao executar o comando usado na etapa 1 regularmente para adicionar componentes atualizados.

> [!IMPORTANT]
>  Observe que as instalações de um compartilhamento de rede “lembrarão” do local de origem de onde vieram. Isso significa que um reparo de um computador cliente pode ter que retornar para o compartilhamento de rede do qual o cliente foi instalado originalmente. Escolha cuidadosamente seu local de rede para que ele se alinhe com o tempo de vida esperado de execução de clientes do Visual Studio 2017 na sua organização.

## <a name="tools"></a>Ferramentas

 Tornamos várias ferramentas disponíveis que ajudarão você a detectar e gerenciar instâncias do Visual Studio instaladas em computadores cliente:

* [VSWhere](https://github.com/microsoft/vswhere): um C++ executável que ajuda você a encontrar o local de ferramentas de núcleo do Visual Studio por meio de uma instância instalada do Visual Studio.
* [VSSetup.PowerShell](https://github.com/microsoft/vssetup.powershell): scripts do PowerShell que usam a API de Configuração de Instalação para identificar instâncias instaladas do Visual Studio.
* [VS-Setup-Samples](https://github.com/microsoft/vs-setup-samples): amostras do C# e C++ que demonstram como usar a API de Configuração de Instalação para consultar uma instalação existente.

Além disso, a [API de Configuração de Instalação](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.setup.configuration.aspx) fornece interfaces para desenvolvedores que desejam criar seus próprios utilitários para interrogar instâncias do Visual Studio.

>[!TIP]
>Para obter mais informações sobre a instalação do Visual Studio 2017, consulte [artigos de blog de Heath Stewart](https://blogs.msdn.microsoft.com/heaths/tag/vs2017/).


## <a name="see-also"></a>Consulte também
* [Instalar o Visual Studio 2017](install-visual-studio.md)
* [Criar um instalador offline para o Visual Studio 2017](create-an-offline-installation-of-visual-studio.md)
* [Usar parâmetros de linha de comando para instalar o Visual Studio 2017](use-command-line-parameters-to-install-visual-studio.md)
* [Relatar um problema com o Visual Studio 2017](../ide/how-to-report-a-problem-with-visual-studio-2017.md)

