---
title: "Como depurar a partir de um projeto de DLL | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "C++"
helpviewer_keywords: 
  - "depurando [Visual Studio], DLLs"
  - "depurando DLLs"
  - "projetos DLL, depuração"
  - "DLLs, depurando projetos"
ms.assetid: 40a94339-d3f7-4ab9-b8a1-b8cf82942f44
caps.latest.revision: 30
caps.handback.revision: 30
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Como depurar a partir de um projeto de DLL
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Para iniciar a depuração de um projeto DLL, você deve especificar o aplicativo de chamada nas propriedades do projeto.  As páginas de propriedade do C\+\+ diferem no layout e o conteúdo do c\# e Visual Basic páginas de propriedades.  
  
 Se uma DLL gerenciada é chamada pelo código nativo e você deseja depurar ambos, você pode especificar isso nas propriedades do projeto.  Para obter mais informações, consulte [Como depurar no modo misto](../debugger/how-to-debug-in-mixed-mode.md).  
  
> [!NOTE]
>  Você não pode especificar um aplicativo de chamada externa nas edições Express do Visual Studio.  Em vez disso, você precisa adicionar um projeto executável à solução, defini\-lo como o projeto de inicialização e chamar métodos na DLL do projeto executável.  
  
### Para especificar o aplicativo de chamada em um projeto C\+\+  
  
1.  Com o botão direito no nó do projeto no **Solution Explorer** e selecione **propriedades**.  Vá para o **Depurar** guia.  
  
2.  Verifique se o **configuração** campo na parte superior da janela é definido como **Depurar**.  
  
3.  Vá para **Propriedades de configuração \/ depuração**.  
  
4.  Na lista **Depurador a iniciar**, escolha **Depurador Local do Windows** ou **Depurador Remoto do Windows**.  
  
5.  No **comando** ou **comando remoto** caixa, adicione o nome do caminho totalmente qualificado do aplicativo.  
  
6.  Adicionar quaisquer argumentos necessários do programa para o **argumentos de comando** caixa.  
  
### Para especificar o aplicativo de chamada em um projeto C\# ou Visual Basic  
  
1.  Com o botão direito no nó do projeto no **Solution Explorer** e selecione **propriedades**.  Vá para o **Depurar** guia.  
  
     Selecione **Iniciar programa externo**, e adicione o nome de caminho totalmente qualificado do programa a ser executado.  
  
     Se você precisar adicionar argumentos de linha de comando do programa externo, adicioná\-las a **argumentos de linha de comando** campo.  
  
2.  Você também pode chamar um aplicativo como uma URL.  \(Você poderá fazer isso se estiver depurando uma DLL gerenciada usada por um aplicativo local do ASP.NET.\)  
  
     Em **Iniciar ação**, selecione o **Iniciar navegador na URL:** botão de opção e preencha a URL.  
  
### Para iniciar a depuração do projeto da DLL  
  
1.  Defina pontos de interrupção conforme necessário.  
  
2.  Iniciar a depuração \(pressione F5, clique na seta verde ou clique **Depurar \/ iniciar depuração**\).  
  
## Consulte também  
 [Depurando projetos de DLL](../debugger/debugging-dll-projects.md)   
 [Definições do projeto para configurações de depuração do C\#](../debugger/project-settings-for-csharp-debug-configurations.md)   
 [Definições do projeto para uma configuração de depuração do Visual Basic](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)   
 [Definições do projeto para uma configuração de depuração do C\+\+](../debugger/project-settings-for-a-cpp-debug-configuration.md)