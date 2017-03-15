---
title: "Compilando e limpando projetos e soluções no Visual Studio | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VS.BuildProjectPicker
- vs.batchbuild
helpviewer_keywords:
- Clean Solution command
- builds [Visual Studio], managing
- solution build configurations, starting
- Build Solution command
- project build configurations, starting
- build configurations, starting
- project build configurations, dependencies
- Rebuild Solution command
- solution build configurations, build order
- builds [Visual Studio], preparing
ms.assetid: 710891fd-379e-42c2-a84b-44a7af694ca0
caps.latest.revision: 35
author: kempb
ms.author: kempb
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
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 96fad179fb30f3b5e8fe6ddfd041c8e289dde48a

---
# <a name="building-and-cleaning-projects-and-solutions-in-visual-studio"></a>Compilando e limpando projetos e soluções no Visual Studio
Usando os procedimentos neste tópico, é possível criar, recriar ou limpar todos ou alguns projetos ou itens de projeto em uma solução. Para ver um tutorial passo a passo, consulte [Instruções passo a passo: criando um aplicativo](../ide/walkthrough-building-an-application.md).  
  
> [!NOTE]
>  A interface do usuário na sua edição do Visual Studio pode ser diferente do que este tópico descreve, dependendo das suas configurações ativas. Para alterar as configurações, abra o menu **Ferramentas** e escolha **Importar e Exportar Configurações**. Para obter mais informações, consulte [Personalizando configurações de desenvolvimento no Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-build-rebuild-or-clean-an-entire-solution"></a>Para criar, recriar ou limpar uma solução inteira  
  
1.  No **Gerenciador de Soluções**, escolha ou abra a solução.  
  
2.  Na barra de menus, escolha **Compilar** e, em seguida, escolha um dos comandos a seguir:  
  
    -   Escolha **Compilar** ou **Compilar Solução** para compilar somente esses componentes e arquivos de projeto e componentes que foram alterados desde o build mais recente.  
  
        > [!NOTE]
        >  O comando **Compilar** torna-se **Compilar Solução** quando uma solução inclui mais de um projeto.  
  
    -   Escolha **Recompilar Solução** para "limpar" a solução e, em seguida, crie todos os arquivos de projeto e componentes.  
  
    -   Escolha **Limpar Solução** para excluir arquivos de saída e intermediários. Com apenas os arquivos de projeto e de componente restantes, novas instâncias dos arquivos de saída e intermediários podem ser criadas.  
  
### <a name="to-build-or-rebuild-a-single-project"></a>Para compilar ou recompilar um único projeto  
  
1.  No **Gerenciador de Soluções**, escolha ou abra o projeto.  
  
2.  Na barra de menus, escolha **Compilar** e, em seguida, escolha **Compilar***ProjectName* ou **Recompilar***ProjectName*.  
  
    -   Escolha **Compilar***ProjectName* para compilar somente esses componentes de projeto que foram alterados desde o build mais recente.  
  
    -   Escolha **Recompilar***ProjectName* para "limpar" o projeto e, em seguida, compile os arquivos de projeto e todos os componentes do projeto.  
  
### <a name="to-build-only-the-startup-project-and-its-dependencies"></a>Para compilar apenas o projeto de inicialização e suas dependências  
  
1.  Na barra de menus, escolha **Ferramentas**, **Opções**.  
  
2.  Na caixa de diálogo **Opções**, expanda o nó **Projetos e Soluções** e, em seguida, escolha a página **Compilar e Executar**.  
  
     A caixa de diálogo **Compilar e Executar, Projetos e Soluções, Opções** é aberta.  
  
3.  Marque a caixa de seleção **Compilar apenas projetos de inicialização e dependências ao Executar**.  
  
     Quando essa caixa de seleção estiver marcada, somente o projeto de inicialização atual e suas dependências serão compilados quando você executar qualquer uma das seguintes etapas:  
  
    -   Na barra de menus, escolha **Depurar**, **Iniciar** (F5).  
  
    -   Na barra de menus, escolha **Compilar**, **Compilar Solução** (CTRL+SHIFT+B).  
  
     Quando essa caixa de seleção estiver desmarcada, todos os projetos, suas dependências e os arquivos de solução serão compilados quando você executar um dos comandos anteriores. Por padrão, essa caixa de seleção está desmarcada.  
  
### <a name="to-build-only-the-selected-visual-c-project"></a>Para compilar somente o projeto Visual C++ selecionado  
  
1.  Escolha um projeto [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)] e, em seguida, na barra de menus, escolha **Compilar**, **Somente Projeto** e um dos seguintes comandos:  
  
    -   **Somente build** *ProjectName*  
  
    -   **Somente Recompilação** *ProjectName*  
  
    -   **Somente Limpeza** *ProjectName*  
  
    -   **Somente Vinculação** *ProjectName*  
  
     Esses comandos são aplicáveis somente ao projeto [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)] escolhido, sem compilar, recompilar, limpar ou vincular as dependências do projeto ou os arquivos de solução. Dependendo da sua versão do [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], o submenu **Somente Projeto** pode conter mais comandos.  
  
### <a name="to-compile-multiple-c-project-items"></a>Para compilar vários itens de projeto C++  
  
1.  Em **Gerenciador de Soluções**, escolha vários arquivos que possam ter ações compiladas, abra o menu de atalho para um desses arquivos e, em seguida, escolha **Compilar**.  
  
     Se os arquivos tiverem dependências, os arquivos serão compilados em ordem de dependência. A operação de compilação falhará se os arquivos exigirem um cabeçalho pré-compilado que não está disponível quando você compila. A operação de compilação usa a configuração de solução ativa atual.  
  
### <a name="to-stop-a-build"></a>Para interromper um build  
  
1.  Execute uma das seguintes etapas:  
  
    -   Na barra de menus, escolha **Compilar**, **Cancelar**.  
  
    -   Escolha as teclas Ctrl + Break.  
  
## <a name="see-also"></a>Consulte também  
 [How to: View, Save, and Configure Build Log Files](../ide/how-to-view-save-and-configure-build-log-files.md)  (Como exibir, salvar e configurar arquivos de log de build)  
 [Obtaining Build Logs (Obtendo logs de build)](../msbuild/obtaining-build-logs-with-msbuild.md)   
 [Compilando e criando](../ide/compiling-and-building-in-visual-studio.md)   
 [Noções sobre configurações de build](../ide/understanding-build-configurations.md)   
 [Debug and Release Project Configurations (Configurações de projeto de depuração e lançamento)](http://msdn.microsoft.com/en-us/0440b300-0614-4511-901a-105b771b236e)   
 [Referência de build do C/C++](/visual-cpp/build/reference/c-cpp-building-reference)   
 [Opções de linha de comando devenv](../ide/reference/devenv-command-line-switches.md)   
 [Soluções e projetos](../ide/solutions-and-projects-in-visual-studio.md)


<!--HONumber=Feb17_HO4-->


