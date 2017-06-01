---
title: Guia do administrador do Visual Studio | Microsoft Docs
ms.custom: 
ms.date: 05/06/2017
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
ms.translationtype: Human Translation
ms.sourcegitcommit: b5b496e0de0a12c9f52c944ef9e768c82d9be783
ms.openlocfilehash: c88a932beac964117ac2fd6ffe171bf4256ac706
ms.contentlocale: pt-br
ms.lasthandoff: 05/08/2017

---
# <a name="visual-studio-2017-administrator-guide"></a>Guia do administrador do Visual Studio 2017

Em ambientes empresariais, é comum que administradores de sistema implantem instalações para os usuários finais de um compartilhamento de rede ou usando software de gerenciamento de sistemas. Projetamos o mecanismo de instalação do Visual Studio para dar suporte à implantação empresarial, permitindo que os administradores de sistema tenham a capacidade de criar um local de instalação de rede, pré-configurar padrões de instalação para implantar chaves de produto durante o processo de instalação e gerenciar atualizações de produto depois de uma implementação bem-sucedida. Este guia do administrador fornece orientação baseada em cenários de implantação corporativa em ambientes de rede comuns.

## <a name="steps-for-deploying-visual-studio-2017-in-an-enterprise-environment"></a>Etapas para implantar o Visual Studio 2017 em um ambiente corporativo

Você pode implantar o Visual Studio 2017 para estações de trabalho cliente, contanto que cada computador de destino atenda a [requisitos mínimos de instalação](https://www.visualstudio.com/en-us/productinfo/vs2017-system-requirements-vs). Se você estiver implantando por meio de softwares como o System Center ou por meio de um arquivo em lotes, normalmente é preciso percorrer as etapas a seguir:

1. [Criar um compartilhamento de rede que contém os arquivos de produto do Visual Studio](create-a-network-installation-of-visual-studio.md) para um local de rede;

2. [Selecione as cargas de trabalho e os componentes](workload-and-component-ids.md) que deseja instalar;

3. [Criar um arquivo de resposta](automated-installation-with-response-file.md) que contém opções de instalação padrão. Ou, como alternativa, [criar um script de instalação](use-command-line-parameters-to-install-visual-studio.md) usando parâmetros de linha de comando para controlar a instalação;

4. Opcionalmente, [aplique uma chave de produto de licença de volume](automatically-apply-product-keys-when-deploying-visual-studio.md) como parte do script de instalação para que os usuários não precisem ativar o software separadamente;

5. Atualizar o layout de rede para [controlar quando as atualizações de produto são entregues aos usuários finais](controlling-updates-to-visual-studio-deployments.md);

6. Opcionalmente, defina as chaves do Registro para [controlar o que é armazenado em cache em estações de trabalho cliente](set-defaults-for-enterprise-deployments.md);

7. Usa a tecnologia de implantação de sua escolha para executar o script gerado nas etapas anteriores em suas estações de trabalho do desenvolvedor de destino;

8. [Atualize seu local de rede com as atualizações mais recentes](update-a-network-installation-of-visual-studio.md) do Visual Studio ao executar o comando usado na etapa 1 regularmente para adicionar componentes atualizados.

> [!IMPORTANT]
> Observe que as instalações de um compartilhamento de rede “lembrarão” do local de origem de onde vieram. Isso significa que um reparo de um computador cliente pode ter que retornar para o compartilhamento de rede do qual o cliente foi instalado originalmente. Escolha cuidadosamente seu local de rede para que ele se alinhe com o tempo de vida esperado de execução de clientes do Visual Studio 2017 na sua organização.

## <a name="tools"></a>Ferramentas
Tornamos várias ferramentas disponíveis que ajudarão você a [detectar e gerenciar instâncias do Visual Studio instaladas](tools-for-managing-visual-studio-instances.md) em computadores cliente.

> [!TIP]
> Além de documentação no guia do administrador, uma boa fonte de informações sobre a instalação do Visual Studio 2017 é o [blog de Heath Stewart](https://blogs.msdn.microsoft.com/heaths/tag/vs2017/).

## <a name="see-also"></a>Consulte também
* [Instalar o Visual Studio 2017](install-visual-studio.md)
* [Instalar o Visual Studio em ambientes offline](install-visual-studio-in-offline-environment.md)
* [Usar parâmetros de linha de comando para instalar o Visual Studio 2017](use-command-line-parameters-to-install-visual-studio.md)
  * [Exemplos de parâmetro de linha de comando](command-line-parameter-examples.md)
* [Relatar um problema com o Visual Studio 2017](../ide/how-to-report-a-problem-with-visual-studio-2017.md)

