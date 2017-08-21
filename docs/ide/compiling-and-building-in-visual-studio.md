---
title: Compilando e criando no Visual Studio | Microsoft Docs
ms.custom: 
ms.date: 7/14/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- builds [Visual Studio], about building in Visual Studio
- custom build steps, types of builds
ms.assetid: c7958821-285f-4e28-9e7a-b5d8b40336a1
caps.latest.revision: 28
author: kempb
ms.author: kempb
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: e2b7ff9126e1cc38ac2e58d6be339b656a024e7f
ms.openlocfilehash: 1a2db8a10664e1d4b38b1d6867c5a3bad1532b39
ms.contentlocale: pt-br
ms.lasthandoff: 08/10/2017

---

# <a name="compiling-and-building-in-visual-studio"></a>Compilando e criando no Visual Studio

Executar um build cria assemblies e aplicativos executáveis do seu código-fonte a qualquer momento durante um ciclo de desenvolvimento. De modo geral, o processo de compilação é muito semelhante entre vários tipos de projeto diferentes, como Windows, ASP.NET, aplicativos móveis e outros. O processo de compilação também é muito semelhante entre linguagens de programação, como C#, Visual Basic, C++ e F#. 

Compilando seu código com frequência, é possível identificar erros rapidamente em tempo de compilação, como sintaxe incorreta, palavras-chave com erros de ortografia e erros de digitação. Também é possível detectar e corrigir com rapidez erros em tempo de execução, como erros lógicos e semânticos, compilando e executando frequentemente versões de depuração do código.  

Uma compilação bem-sucedida é, essencialmente, uma validação de que o código-fonte do aplicativo contém sintaxe correta e de que todas as referências estáticas a bibliotecas, assemblies e outros componentes foram resolvidas. Isso produz um executável de aplicativo que pode, por sua vez, ser testado quanto ao funcionamento adequado em um [ambiente de depuração](../debugger/index.md) e por meio de uma variedade de testes manuais e automatizados para [validar a qualidade do código](../test/improve-code-quality.md). Após o aplicativo ter sido totalmente testado, você pode compilar uma versão de lançamento para ser implantada por seus clientes. Para obter uma introdução a esse processo, consulte [Passo a passo: criando um aplicativo](../ide/walkthrough-building-an-application.md).  

Dentro da família de produtos do Visual Studio, há três métodos que você pode usar para compilar um aplicativo: o IDE do Visual Studio, ferramentas de linha de comando do MSBuild e o Team Foundation Build no Visual Studio Team Services:
 
| Método de build | Benefícios | 
| --- |--- | --- |  
| IDE |– Criar compilações imediatamente e testá-las em um depurador.<br />– Executar builds em multiprocessador para projetos C++ e C#.<br />– Personalizar diferentes aspectos do sistema de build. |
| Linha de comando do MSBuild| – Criar projetos sem instalar o Visual Studio.<br />– Executar builds em multiprocessador para todos os tipos de projeto.<br />– Personalizar a maioria das áreas do sistema de build.|
| Compilação do Team Foundation | – Automatizar o processo de build como parte de um pipeline de integração contínua/entrega contínua.<br />– Aplicar testes automatizados com cada compilação.<br />– Empregar recursos baseados em nuvem praticamente ilimitados para processos de compilação.<br />– Modificar o fluxo de trabalho de compilação e, conforme necessário, criar atividades de compilação para realizar tarefas profundamente personalizadas.|  

A documentação nesta seção detalha mais o processo de compilação baseado no IDE. Para obter mais informações sobre os outros métodos, consulte [MSBuild](../msbuild/msbuild.md) e [Integração contínua e implantação](https://www.visualstudio.com/docs/build/overview), respectivamente.

## <a name="overview-of-building-from-the-ide"></a>Visão geral da compilação no IDE  

Quando você cria um projeto, o Visual Studio cria configurações de compilação padrão para o projeto e para a solução que contém o projeto.  Essas configurações definem a maneira como as soluções e os projetos são criados e implantados. Configurações de projeto, em particular, são exclusivas a uma plataforma de destino (por exemplo, o Windows ou Linux) e tipo de build (por exemplo, depuração ou lançamento). Você pode editar essas configurações como quiser e também pode criar suas próprias configurações, conforme necessário.

Para obter uma introdução à compilação com o IDE, consulte [Passo a passo: criando um aplicativo](walkthrough-building-an-application.md).  

Em seguida, consulte [Compilando e limpando projetos e soluções no Visual Studio](building-and-cleaning-projects-and-solutions-in-visual-studio.md) para saber mais sobre as personalizações de diferentes aspectos que você pode fazer no processo. As personalizações incluem [alterar diretórios de saída](how-to-change-the-build-output-directory.md), [especificar eventos de build personalizados](specifying-custom-build-events-in-visual-studio.md), [gerenciar dependências do projeto](how-to-create-and-remove-project-dependencies.md), [gerenciar arquivos de log de build](how-to-view-save-and-configure-build-log-files.md) e [suprimir avisos do compilador](how-to-suppress-compiler-warnings.md).

A partir daí, você pode explorar uma variedade de outras tarefas:
- [Compreender configurações de build](understanding-build-configurations.md)
- [Compreender plataformas de build](understanding-build-platforms.md)
- [Gerenciar propriedades de solução e de projeto](managing-project-and-solution-properties.md).  
- Especificar eventos de build em [C#](how-to-specify-build-events-csharp.md) e [Visual Basic](how-to-specify-build-events-visual-basic.md). 
- [Definir opções de build](reference/options-dialog-box-projects-and-solutions-build-and-run.md)
- [Compilar vários projetos paralelamente](../msbuild/building-multiple-projects-in-parallel-with-msbuild.md).  
  
## <a name="see-also"></a>Consulte também  

- [Criando (compilando) projetos de site da Web](http://msdn.microsoft.com/Library/a9cbb88c-8fff-4c67-848b-98fbfd823193)   

