---
title: "O que há de novo no SDK do Visual Studio 2017 | Documentos do Microsoft"
ms.custom: 
ms.date: 11/09/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9efcf0a3-dbde-4cab-8ed3-425826a48b2e
caps.latest.revision: 1
author: gregvanl
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 221f4911981deec0330f76a82c0cc8a1b968e56e
ms.openlocfilehash: 60898d7cace1c10006436a8d98cbd7f7628cf972
ms.lasthandoff: 02/22/2017

---
# <a name="what39s-new-in-the-visual-studio-2017-sdk"></a>O que há de novo no SDK do Visual Studio 2017

>**Observação:** esta documentação é preliminar e com base na versão RC do Visual Studio 2017.

O SDK do Visual Studio tem os seguintes recursos novos e atualizados para 2017 do Visual Studio.

## <a name="vsix-v3-format"></a>Formato do VSIX v3

Para oferecer suporte a nova instalação leve do Visual Studio 2017, o formato do manifesto VSIX extensão foi atualizado para a versão 3 (v3 VSIX).

O novo formato tem suporte para:

* Declarar explicitamente os pré-requisitos para ser detectado e instalado pelo VSIXInstaller.
* Assemblies de Ngen'ing na instalação da extensão.
* Instalando ativos fora da raiz da extensão usual.

Para saber mais sobre essas alterações, consulte os seguintes tópicos:

* [Alterações de extensibilidade para 2017](breaking-changes-2017.md)
* [Suporte a NGen no VSIX v3](ngen-support.md)
* [Instalando fora da pasta de extensões](set-install-root.md)
* [Perguntas frequentes para extensibilidade do Visual Studio 2017](faq-2017.md)

## <a name="migrating-extensibility-project-to-visual-studio-2017"></a>Migrando projeto de extensibilidade do Visual Studio 2017

Para saber como atualizar seus projetos de extensibilidade e seus manifestos VSIX para Visual Studio 2017, consulte [como: migrar projetos de extensibilidade para Visual Studio 2017](how-to-migrate-extensibility-projects-to-visual-studio-2017.md).

## <a name="lightweight-solution-load-lsl"></a>Carga de solução leve (LSL)

Solução leve de carga é um novo recurso em 2017 VS que reduzirá significativamente o tempo de carregamento de solução, permitindo que você seja mais produtivo mais rapidamente. Quando LSL está habilitado, Visual Studio não será totalmente carregado projetos até começar a trabalhar com eles.

LSL pode afetar extensões do Visual Studio. Extensões cujos recursos dependem de um projeto que seja totalmente carregado podem não funcionar ou funcionem corretamente. Consulte [carga de solução leve](lightweight-solution-load-extension-impact.md) para saber se sua extensão pode ser afetada e obter orientação sobre como atualizar sua extensão.

## <a name="custom-project-and-item-templates"></a>Modelos personalizados de projeto e item

A partir do Visual Studio 2017, verificação de modelos de item e projeto personalizados serão não será executada. Em vez disso, a extensão deve fornecer arquivos de manifesto de modelo que descrevem o local de instalação desses modelos. Você pode usar o Visual Studio 2017 para atualizar as extensões VSIX. Se você implantar sua extensão usando um MSI, você deve gerar os arquivos de manifesto do modelo manualmente. Para obter mais informações, consulte [atualização personalizar modelos de projeto e Item para Visual Studio 2017](../extensibility/upgrading-custom-project-and-item-templates-for-visual-studio-2017.md). O esquema de modelo de manifesto é documentado em [Visual Studio manifesto referência esquema modelo](../extensibility/visual-studio-template-manifest-schema-reference.md).

## <a name="updated-extension-performance-guidelines"></a>Diretrizes de desempenho de extensão atualizada

Há uma nova [como: diagnosticar o desempenho de extensão](how-to-diagnose-extension-performance.md) tópico em [Gerenciando VSPackages](managing-vspackages.md) para mostrar como detectar e analisar o impacto de extensão no Visual Studio inicialização e solução de tempos de carregamento.

