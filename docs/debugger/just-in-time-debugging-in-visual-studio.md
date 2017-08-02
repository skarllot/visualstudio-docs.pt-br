---
title: "Depura&#231;&#227;o Just-In-Time no Visual Studio | Microsoft Docs"
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
  - "C++"
  - "CSharp"
  - "VB"
helpviewer_keywords: 
  - "depurando [Visual Studio], Just-In-Time"
  - "Depuração Just-In-Time"
ms.assetid: 14972d5f-69bc-479b-9529-03b8787b118f
caps.latest.revision: 48
caps.handback.revision: 42
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Depura&#231;&#227;o Just-In-Time no Visual Studio
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Depuração Just\-In\-Time inicia o Visual Studio automaticamente quando ocorre uma exceção ou uma falha em um aplicativo que está em execução fora do Visual Studio. Isso permite que você teste seu aplicativo quando o Visual Studio não está em execução e iniciar a depuração com o Visual Studio quando ocorre um problema.  
  
 Depuração Just\-In\-Time funciona para aplicativos de desktop do Windows. Ele não funciona para aplicativos Windows Universal e não funciona para código gerenciado hospedado em um aplicativo nativo, como Visualizers.  
  
## Usando a depuração Just\-In\-Time  
 Esta seção mostra o que acontece quando um executável lança uma exceção.  
  
 Você deve ter o Visual Studio instalado para executar essas etapas. Se você não tiver o Visual Studio, você pode baixar gratuitamente o [Visual Studio 2015 Community Edition](https://www.microsoft.com/en-us/download/details.aspx?id=48146).  
  
 Quando você instala o Visual Studio Just\-In\-Time de depuração está habilitado por padrão.  
  
 Para os fins desta seção, criaremos um aplicativo de console c\# no Visual Studio que gera um [NullReferenceException](../Topic/NullReferenceException%20Class.md).  
  
 No Visual Studio, crie um aplicativo de console c\# \(**arquivo \/ novo \/ projeto \/ Visual c\# \/ aplicativo de Console**\) denominada **ThrowsNullException**. Para obter mais informações sobre a criação de projetos no Visual Studio, consulte [Instruções passo a passo: criar um aplicativo simples](../ide/walkthrough-create-a-simple-application-with-visual-csharp-or-visual-basic.md).  
  
 Quando o projeto é aberto no Visual Studio, abra o arquivo Program.cs. Substitua o método Main \(\) com o código a seguir, que imprime uma linha para o console e, em seguida, lança uma NullReferenceException:  
  
```c#  
static void Main(string[] args)  
{  
    Console.WriteLine("we will now throw a NullReferenceException");  
    throw new NullReferenceException("this is the exception thrown by the console app");  
}  
```  
  
> [!IMPORTANT]
>  Para que este procedimento funcione um [configuração versão](../debugger/how-to-set-debug-and-release-configurations.md), você precisará desativar [Apenas Meu Código](../debugger/just-my-code.md). No Visual Studio, clique em **Ferramentas \/ opções**. No **opções** caixa de diálogo, selecione **depuração**. Remover a seleção de **Habilitar Just My Code**.  
  
 Compile a solução \(no Visual Studio, escolha **Construir \/ recompilar solução**\). Você pode escolher a depuração ou a configuração da versão. Para obter mais informações sobre configurações de compilação, consulte [Noções sobre configurações de compilação](../ide/understanding-build-configurations.md).  
  
 O processo de compilação cria um executável ThrowsNullException.exe. Você pode encontrar na pasta onde você criou o projeto c\#: **...\\ThrowsNullException\\ThrowsNullException\\bin\\Debug** ou **...\\ThrowsNullException\\ThrowsNullException\\bin\\Release**.  
  
 Clique duas vezes o ThrowsNullException.exe. Você deverá ver uma janela de comando como este:  
  
 ![ThrowsNullExceptionConsole](../debugger/media/throwsnullexceptionconsole.png "ThrowsNullExceptionConsole")  
  
 Depois de alguns segundos, uma janela de erro será exibida:  
  
 ![ThrowsNullExceptionError](../debugger/media/throwsnullexceptionerror.png "ThrowsNullExceptionError")  
  
 Não clique **Cancelar**\! Depois de alguns segundos, você verá dois botões, **Depurar** e **Close program**. Clique em **Depurar**.  
  
> [!CAUTION]
>  Se seu aplicativo contiver código não confiável, aparecerá uma caixa de diálogo com um aviso de segurança. Essa caixa de diálogo permite que você decida se deseja ou não prosseguir com a depuração. Antes de continuar com a depuração, decida se você confia no código. Você escreve o código? Você confia no Programador? Se o aplicativo é executado em uma máquina remota, você reconhece o nome do processo? Mesmo que o aplicativo seja executado localmente, isso não significa necessariamente é confiável. Considere a possibilidade de código mal\-intencionado em execução no seu computador. Se você decidir que o código que você está prestes a depurar é confiável, clique em **Depurar**. Caso contrário, clique em **não depurar**.  
  
 O **depurador do Visual Studio Just\-In\-Time** janela é exibida:  
  
 ![JustInTimeDialog](~/docs/debugger/media/justintimedialog.png "JustInTimeDialog")  
  
 Em **possíveis depuradores**, você verá que o **nova instância do Microsoft Visual Studio 2015** linha está selecionada. Se ainda não estiver selecionado, selecione\-o agora.  
  
 Na parte inferior da janela, em **você deseja depurar usando o depurador selecionado?**, clique em **Sim**.  
  
 O projeto ThrowsNullException abre em uma nova instância do Visual Studio, com a execução interrompida na linha que lança a exceção:  
  
 ![NullReferenceSecondInstance](../debugger/media/nullreferencesecondinstance.png "NullReferenceSecondInstance")  
  
 Você pode iniciar a depuração nesse ponto. Se este fosse um aplicativo real, você precisaria descobrir por que o código está lançando a exceção.  
  
##  <a name="BKMK_Enabling"></a> Ativando ou desativando o Just\-In\-Time de depuração  
 Você pode habilitar ou desabilitar a depuração do Visual Studio Just\-In\-Time **Ferramentas \/ opções** caixa de diálogo.  
  
#### Para habilitar ou desabilitar Just\-In\-Time a depuração  
  
1.  Abra o Visual Studio. No menu **Ferramentas**, clique em **Opções**.  
  
2.  No **opções** caixa de diálogo, selecione o **depuração** pasta.  
  
3.  No **depuração** pasta, selecione o **Just\-In\-Time** página.  
  
4.  No **Just\-In\-Time Habilitar depuração desses tipos de código** caixa, marque ou desmarque os tipos de programa relevantes: **Managed**, **nativo**, ou **Script**.  
  
     Para desabilitar a depuração, quando ela tiver sido habilitada Just\-In\-Time, você deve estar executando com privilégios de administrador. Habilitar Just\-In\-Time depuração define uma chave do registro e são necessários privilégios de administrador para alterar essa chave.  
  
5.  Clique em **OK**.  
  
#### Para habilitar Just\-In\-Time a depuração de um formulário do Windows  
  
1.  Por padrão, os aplicativos do Windows Forms têm um manipulador de exceção de nível superior que permite que o programa continuar a executar se puder recuperar. Por exemplo, se seu aplicativo Windows Forms lança uma exceção sem tratamento, você verá uma caixa de diálogo semelhante à seguinte:  
  
     ![WindowsFormsUnhandledException](../debugger/media/windowsformsunhandledexception.png "WindowsFormsUnhandledException")  
  
     Para habilitar Just\-In\-Time a depuração de um aplicativo Windows Forms, você deve executar as seguintes etapas adicionais:  
  
2.  Definir o `jitDebugging` valor `true` no `system.windows.form` seção de Machine. config ou *\< nome do aplicativo \>*. exe:  
  
    ```  
    <configuration>  
        <system.windows.forms jitDebugging="true" />  
    </configuration>  
    ```  
  
3.  Em um aplicativo C\+\+ do Windows Form, você também deve definir `DebuggableAttribute` em um arquivo. config ou em seu código. Se você compilar com [\/Zi](/visual-cpp/build/reference/z7-zi-zi-debug-information-format) sem [\/Og](/visual-cpp/build/reference/og-global-optimizations), o compilador define esse atributo para você. Se você quiser depurar uma compilação de versão não otimizada, no entanto, você deve definir isso sozinho. Você pode fazer isso adicionando a seguinte linha ao está o arquivo AssemblyInfo cpp do seu aplicativo:  
  
    ```  
    [assembly:System::Diagnostics::DebuggableAttribute(true, true)];   
    ```  
  
     Para obter mais informações, consulte <xref:System.Diagnostics.DebuggableAttribute>.  
  
 Depuração Just\-In\-Time ainda pode ser ativado mesmo que o Visual Studio não está instalado no seu computador. Quando o Visual Studio não estiver instalado, não é possível desabilitar depuração do Visual Studio Just\-In\-Time **opções** caixa de diálogo. Nesse caso, você pode desabilitar depuração editando o registro do Windows Just\-In\-Time.  
  
#### Para desabilitar editando o registro de depuração Just\-In\-Time  
  
1.  Sobre o **Iniciar** menu, procure e execute `regedit.exe`  
  
2.  No **Editor do registro** janela, localize e exclua as entradas de registro de acompanhamento:  
  
    -   HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\Windows NT\\CurrentVersion\\AeDebug\\Debugger  
  
    -   HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\. NETFramework\\DbgManagedDebugger  
  
3.  Se o computador estiver executando um sistema operacional de 64 bits, exclua as seguintes entradas de registro também:  
  
    -   HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Wow6432Node\\Microsoft\\Windows NT\\CurrentVersion\\AeDebug\\Debugger  
  
    -   HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Wow6432Node\\Microsoft\\. NETFramework\\DbgManagedDebugger  
  
4.  Tome cuidado para não excluir acidentalmente ou alterar quaisquer outras chaves do registro.  
  
5.  Feche o **Editor do registro** janela.  
  
## Erros de depuração Just\-In\-Time  
 Se você não vir a caixa de diálogo quando o programa falha, isso pode ser devido a configurações de relatório de erros do Windows em seu computador. Para obter mais informações, consulte [. Configurações WER](https://msdn.microsoft.com/en-us/library/windows/desktop/bb513638\(v=vs.85\).aspx).  
  
 Você pode ver as seguintes mensagens de erro que estão associadas com Just\-In\-Time de depuração.  
  
-   **Não é possível anexar ao processo de travamento. O programa especificado não é um programa do Windows ou MS\-DOS.**  
  
     Esse erro ocorre quando você tenta anexar a um processo em execução como outro usuário.  
  
     Para contornar esse problema, inicie o Visual Studio, abra o **anexar ao processo** caixa de diálogo de **Depurar** menu e localize o processo que você deseja depurar no **processos disponíveis** lista. Se você não souber o nome do processo, examine o **depurador do Visual Studio Just\-In\-Time** caixa de diálogo e observe o ID de processo. Selecione o processo no **processos disponíveis** lista e clique em **Attach**. No **depurador do Visual Studio Just\-In\-Time** caixa de diálogo, clique em **não** para descartar a caixa de diálogo.  
  
-   **Não foi possível iniciar o depurador porque nenhum usuário está conectado.**  
  
     Esse erro ocorre quando Just\-In\-Time depuração tenta iniciar o Visual Studio em um computador onde não há nenhum usuário conectado ao console. Como nenhum usuário está conectado, não há nenhuma sessão de usuário para exibir o Just\-In\-Time depurando a caixa de diálogo.  
  
     Para corrigir esse problema, faça logon na máquina.  
  
-   **Classe não registrada.**  
  
     Esse erro indica que o depurador tentou criar uma classe COM que não está registrada, provavelmente devido a um problema de instalação.  
  
     Para corrigir esse problema, use o disco de instalação para reinstalar ou reparar a instalação do Visual Studio.  
  
## Consulte também  
 [Segurança do depurador](../debugger/debugger-security.md)   
 [Noções básicas do depurador](../debugger/debugger-basics.md)   
 [Caixa de diálogo Just\-In\-Time, Depuração, Opções](../debugger/just-in-time-debugging-options-dialog-box.md)   
 [Aviso de segurança: anexar a um processo de propriedade de um usuário não confiável pode ser perigoso. Caso as informações a seguir pareçam suspeitas ou você não tenha certeza, não anexe a esse processo](../debugger/security-warning-attaching-to-a-process-owned-by-an-untrusted-user-can-be-dangerous-if-the-following-information-looks-suspicious-or-you-are-unsure-do-not-attach-to-this-process.md)