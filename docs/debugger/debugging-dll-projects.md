---
title: "Depurando projetos de DLL | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
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
helpviewer_keywords: 
  - "depurando DLLs"
  - "modelos, depuração de DLLs"
  - "DLLs, depuração"
  - "depuração [Visual Studio], DLLs"
ms.assetid: 433cab30-d191-460b-96f7-90d2530ca243
caps.latest.revision: 38
caps.handback.revision: 38
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Depurando projetos de DLL
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Os seguintes modelos criam DLLs:  
  
-   \(C\+\+, c\# e Visual Basic\) Biblioteca de classes  
  
-   \(C\+\+, c\# e Visual Basic\): biblioteca de controle do Windows Forms  
  
     Depuração de uma biblioteca de controle do Windows é semelhante a depuração de um projeto de biblioteca de classes. Na maioria dos casos, você chamará o controle do Windows de outro projeto. Quando você depurar o projeto de chamada, pode entrar no código do controle do Windows, definir pontos de interrupção e executar outras operações de depuração. Para obter mais informações, consulte [controles dos Windows Forms](../Topic/Windows%20Forms%20Controls.md).  
  
-   \(C\# e Visual Basic\): biblioteca de controle Web  
  
     Para obter mais informações, consulte [Biblioteca de Controles da Web \(código gerenciado\)](../debugger/web-control-library-managed-code.md).  
  
-   \(C\+\+\): controle ActiveX de dispositivo inteligente do controle ActiveX do MFC e MFC  
  
     Controles ActiveX são controles que podem ser baixados pela Internet em um computador cliente e exibidos e ativados em páginas da Web.  
  
     Depurando controles ActiveX é semelhante à depuração de outros tipos de controles porque não é possível executar como autônomos, mas devem ser inseridos em uma página da HTML Web. Para obter mais informações, consulte [Como depurar um controle ActiveX](../debugger/how-to-debug-an-activex-control.md).  
  
-   \(C\+\+\): DLL de dispositivo inteligente do MFC  
  
     Para obter mais informações, consulte [Técnicas de depuração MFC](../debugger/mfc-debugging-techniques.md).  
  
 Esta seção também contém informações sobre os seguintes tópicos:  
  
-   [Como depurar a partir de um projeto de DLL](../debugger/how-to-debug-from-a-dll-project.md)  
  
-   [Como depurar no modo misto](../debugger/how-to-debug-in-mixed-mode.md)  
  
 Este tópico contém as seções a seguir, que fornecem considerações sobre a preparação depurar bibliotecas de classes:  
  
-   [Criação de uma versão de depuração](#vxtskdebuggingdllprojectsbuildingadebugversion)  
  
-   [Depuração de modo misto](#vxtskdebuggingdllprojectsmixedmodedebugging)  
  
-   [Alterando configurações padrão](#vxtskdebuggingdllprojectschangingdefaultconfigurations)  
  
-   [Maneiras de depurar a DLL](#vxtskdebuggingdllprojectswaystodebugthedll)  
  
-   [O aplicativo de chamada](#vxtskdebuggingdllprojectsthecallingapplication)  
  
-   [Controles em uma página da Web](#vxtskdebuggingdllprojectscontrolsonawebpage)  
  
-   [A janela imediata](#vxtskdebuggingdllprojectstheimmediatewindow)  
  
##  <a name="vxtskdebuggingdllprojectsbuildingadebugversion"></a> Criação de uma versão de depuração  
 Não importa como você iniciar a depuração, certifique\-se de que você compilar a versão de depuração da DLL primeiro e certifique\-se de que a versão de depuração está no local onde o aplicativo espera encontrá\-lo. Isso pode parecer óbvio, mas se você esquecer desta etapa, o aplicativo pode encontrar uma versão diferente da DLL e carregá\-lo. O programa continuará a executar, embora você esteja se perguntando por que o ponto de interrupção nunca foi atingido. Quando você estiver depurando, você pode verificar quais DLLs seu programa carregou abrindo o depurador **módulos** janela. O **módulos** janela lista cada DLL ou EXE carregados no processo que você está depurando. Para obter mais informações, consulte [Como usar a janela Módulos](../debugger/how-to-use-the-modules-window.md).  
  
 Para o depurador anexar a códigos escritos em C\+\+, o código deve emitir `DebuggableAttribute`. Você pode adicionar isso ao seu código automaticamente por meio da vinculação com o [\/ASSEMBLYDEBUG](/visual-cpp/build/reference/assemblydebug-add-debuggableattribute) opção de vinculador.  
  
##  <a name="vxtskdebuggingdllprojectsmixedmodedebugging"></a> Depuração de modo misto  
 O aplicativo que chama sua DLL pode ser escrito em código gerenciado ou código nativo. Se a DLL gerenciada é chamada pelo código nativo e você deseja depurar ambos, gerenciado e nativos depuradores devem estar habilitadas. Você pode selecionar no **\< projeto \>páginas de propriedade** caixa de diálogo ou janela. Como fazer isso depende se você iniciar a depuração do projeto de DLL ou o projeto de aplicativo de chamada. Para obter mais informações, consulte [Como depurar no modo misto](../debugger/how-to-debug-in-mixed-mode.md).  
  
##  <a name="vxtskdebuggingdllprojectschangingdefaultconfigurations"></a> Alterando configurações padrão  
 Quando você cria um projeto de aplicativo de console com o modelo de projeto, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] cria automaticamente as configurações necessárias para as configurações Debug e Release. Se necessário, você pode alterar essas configurações. Para obter mais informações, consulte [Definições do projeto para uma configuração de depuração do C\+\+](../debugger/project-settings-for-a-cpp-debug-configuration.md), [Definições do projeto para configurações de depuração do C\#](../debugger/project-settings-for-csharp-debug-configurations.md), [Definições do projeto para uma configuração de depuração do Visual Basic](../debugger/project-settings-for-a-visual-basic-debug-configuration.md), e [Como definir configurações de depuração e versão](../debugger/how-to-set-debug-and-release-configurations.md).  
  
##  <a name="vxtskdebuggingdllprojectswaystodebugthedll"></a> Maneiras de depurar a DLL  
 Cada um dos projetos nesta seção cria uma DLL. Não é possível executar uma DLL diretamente. ele deve ser chamado por um aplicativo, geralmente um EXE. Para obter mais informações, consulte [Criando e gerenciando projetos do Visual C\+\+](/visual-cpp/ide/creating-and-managing-visual-cpp-projects). O aplicativo de chamada pode conter qualquer um dos seguintes critérios:  
  
-   Um aplicativo criado em outro projeto na mesma [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] solução que contém a biblioteca de classes.  
  
-   Um aplicativo existente já implantado em um computador de teste ou de produção.  
  
-   Localizado na Web e acessado por meio de uma URL.  
  
-   Um aplicativo Web que contém uma página da Web que incorpore a DLL.  
  
###  <a name="vxtskdebuggingdllprojectsthecallingapplication"></a> Depurando o aplicativo de chamada  
 Para depurar uma DLL, inicie depurando o aplicativo de chamada, geralmente um executável ou um aplicativo Web. Há várias maneiras de depurá\-lo.  
  
-   Se você tiver um projeto para o aplicativo de chamada, você pode abrir o projeto e iniciar a execução do **Depurar** menu. Para obter mais informações, consulte [How to: Start Execution](http://msdn.microsoft.com/pt-br/b0fe0ce5-900e-421f-a4c6-aa44ddae453c).  
  
-   Se o aplicativo de chamada é um programa existente já implantado em um computador de teste ou produção e já está em execução, você pode anexar a ele. Use esse método se a DLL for um controle hospedado pelo Internet Explorer, ou um controle em uma página da Web. Para obter mais informações, consulte [How to: Attach to a Running Process](http://msdn.microsoft.com/pt-br/636d0a52-4bfd-48d2-89ad-d7b9ca4dc4f4).  
  
-   Você pode depurá\-la do projeto da DLL. Para obter mais informações, consulte [Como depurar a partir de um projeto de DLL](../debugger/how-to-debug-from-a-dll-project.md).  
  
-   Você pode depurá\-lo do [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] **imediato** janela.  Nesse caso, o **imediato** janela desempenha a função do aplicativo.  
  
 Antes de iniciar a depuração do aplicativo de chamada, você geralmente deseja definir um ponto de interrupção na biblioteca de classes. Para obter mais informações, consulte [Breakpoints and Tracepoints](http://msdn.microsoft.com/pt-br/fe4eedc1-71aa-4928-962f-0912c334d583). Quando o ponto de interrupção é atingido, você pode percorrer o código, observando a ação em cada linha até isolar o problema. Para obter mais informações, consulte [Code Stepping Overview](http://msdn.microsoft.com/pt-br/8791dac9-64d1-4bb9-b59e-8d59af1833f9).  
  
###  <a name="vxtskdebuggingdllprojectscontrolsonawebpage"></a> Controles em uma página da Web  
 Para depurar um controle de página da Web, crie um [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] página que incorpore, se essa página já não existir. Você colocar pontos de interrupção no código da página da Web, bem como o código de controle. Você então chama a página da Web [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
 Antes de iniciar a depuração do aplicativo de chamada, você geralmente deseja definir um ponto de interrupção na DLL. Quando o ponto de interrupção é atingido, você pode percorrer o código, observando a ação em cada linha até isolar o problema. Para obter mais informações, consulte [Breakpoints and Tracepoints](http://msdn.microsoft.com/pt-br/fe4eedc1-71aa-4928-962f-0912c334d583).  
  
###  <a name="vxtskdebuggingdllprojectstheimmediatewindow"></a> A janela imediata  
 Você pode avaliar funções ou métodos na DLL sem ter um aplicativo de chamada. Faça a depuração em tempo de design e você usar o **imediato** janela. Para depurar dessa maneira, execute as seguintes etapas enquanto o projeto DLL está aberto:  
  
1.  Abra o depurador **imediato** janela.  
  
2.  Para testar um método denominado `Test` na classe `Class1`, instancie um objeto do tipo `Class1` digitando o código c\# a seguir na janela imediata. Esse código gerenciado funciona para Visual Basic e C\+\+, com alterações de sintaxe apropriadas:  
  
    ```  
    Class1 obj = new Class1();  
    ```  
  
     No c\#, todos os nomes devem ser totalmente qualificados. Além disso, quaisquer métodos ou variáveis devem estar no escopo atual e no contexto da sessão de depuração.  
  
3.  Supondo que `Test` leva um `int` parâmetro, avaliar `Test` usando o **imediato** janela:  
  
    ```  
    ?obj.Test(10)  
    ```  
  
     O resultado será impresso no **imediato** janela.  
  
4.  Você pode continuar a depuração `Test` colocando um ponto de interrupção dentro dele e avaliando a função novamente:  
  
    ```  
    ?obj.Test(10);  
    ```  
  
     O ponto de interrupção será atingido e você poderá percorrer `Test`. Após a execução `Test`, o depurador estará novamente no modo de Design.  
  
## Consulte também  
 [Depurando código gerenciado](../debugger/debugging-managed-code.md)   
 [Tipos de projeto do Visual C\+\+](../debugger/debugging-preparation-visual-cpp-project-types.md)   
 [Tipos de projeto C\#, F\# e Visual Basic](../debugger/debugging-preparation-csharp-f-hash-and-visual-basic-project-types.md)   
 [Definições do projeto para uma configuração de depuração do C\+\+](../debugger/project-settings-for-a-cpp-debug-configuration.md)   
 [Definições do projeto para configurações de depuração do C\#](../debugger/project-settings-for-csharp-debug-configurations.md)   
 [Definições do projeto para uma configuração de depuração do Visual Basic](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)   
 [Segurança do depurador](../debugger/debugger-security.md)