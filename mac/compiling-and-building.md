---
title: "Compilação e Criação no Visual Studio para Mac"
description: 
author: asb3993
ms.author: amburns
ms.date: 04/14/2017
ms.topic: article
ms.assetid: FB253757-DB00-4889-A6BF-E44722E25BD1
ms.translationtype: HT
ms.sourcegitcommit: e2b7ff9126e1cc38ac2e58d6be339b656a024e7f
ms.openlocfilehash: ea98f80d037a03912cf3d8212588ebb7520b4bbb
ms.contentlocale: pt-br
ms.lasthandoff: 08/11/2017

---

# <a name="compiling-and-building-in-visual-studio-for-mac"></a>Compilação e criação no Visual Studio para Mac

O Visual Studio para Mac pode ser usado para compilar aplicativos e criar assemblies durante o desenvolvimento do seu projeto. É importante compilar e criar seu código antecipadamente e com frequência para poder identificar tipos incompatíveis e outros erros do tempo de compilação.

## <a name="choosing-a-build-method"></a>Escolhendo um método de build:

### <a name="using-the-ide"></a>Como usar o IDE

Usar o Visual Studio para Mac permite criar e executar builds imediatamente, fornecendo ainda controle sobre a funcionalidade de build. O Visual Studio para Mac usa o MSBuild como o sistema de build subjacente.

Todos os Projetos e Soluções criados no IDE terão uma configuração de build padrão, que define o contexto para builds. Essas configurações podem ser editadas ou você pode criar suas próprias. Criar ou modificar essas configurações atualizará automaticamente o arquivo de projeto, que é usado pelo MSBuild para compilar o projeto.  

Para obter mais informações sobre como compilar projetos e soluções no IDE, consulte o guia [Compilação e limpeza de Projetos e Soluções](~/building-and-cleaning-projects-and-solutions.md).

O Visual Studio para Mac também pode ser usado para fazer o seguinte:

* Alterar o caminho de saída. Isso é editado nas opções do Projeto:

    ![Alterar o caminho de saída](media/compiling-and-building-image4.png)

* Alterar o nível de detalhes da saída de build:

    ![Alterar o nível de detalhes de build](media/compiling-and-building-image5.png)

* Adicione comandos personalizados antes, durante ou depois da Compilação ou Limpeza:

    ![adicionar comandos personalizados](media/compiling-and-building-image6.png)

### <a name="building-from-command-line"></a>Compilação na linha de comando

É possível usar o Microsoft Build Engine para compilar aplicativos por meio da linha de comando.

Consulte o conteúdo do [MSBuild](https://docs.microsoft.com/en-us/visualstudio/msbuild/msbuild) para ver mais informações sobre como usar o MSBuild.

### <a name="using-visual-studio-team-services"></a>Usando o Visual Studio Team Services

* [Compilar seu aplicativo Xamarin](https://www.visualstudio.com/en-us/docs/build/apps/mobile/xamarin)
* [Integração contínua com o Xamarin](https://developer.xamarin.com/guides/cross-platform/ci/)
