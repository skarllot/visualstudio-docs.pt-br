---
title: "Instru&#231;&#245;es passo a passo: escrevendo um visualizador no Visual Basic | Microsoft Docs"
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
  - "visualizadores, gravando"
  - "explicações passo a passo [Visual Studio], visualizadores"
ms.assetid: c93bf5a1-3e5e-422f-894e-bd72c9bc1b57
caps.latest.revision: 22
caps.handback.revision: 22
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Instru&#231;&#245;es passo a passo: escrevendo um visualizador no Visual Basic
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Este passo a passo mostra como escrever um visualizador simples usando [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)].  O visualizador que você criará neste passo a passo exibe o conteúdo de uma cadeia de caracteres usando uma caixa de mensagem do Windows Forms.  Esse visualizador simples de cadeia de caracteres é um exemplo básico para mostrar como você pode criar visualizadores para outros tipos de dados mais aplicáveis a seus projetos.  
  
> [!NOTE]
>  As caixas de diálogo e os comandos do menu que você vê podem ser diferentes dos descritos na Ajuda, dependendo da edição ou das configurações ativas.  Para alterar as configurações, vá para o menu **Ferramentas** e escolha **Importar e Exportar** .  Para obter mais informações, consulte [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/pt-br/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
 O código do visualizador deve ser colocado em uma DLL, que será lido pelo depurador.  A primeira etapa é criar um projeto da biblioteca de classes para a DLL.  
  
## Criar e preparar um projeto da biblioteca de classes  
  
#### Para criar um projeto da biblioteca de classes  
  
1.  No menu **Arquivo**, escolha **Novo** e clique em **Novo Projeto**.  
  
2.  Na caixa de diálogo **Novo Projeto**, em **Tipo de Projeto**, clique em **Visual Basic**.  
  
3.  Na caixa **Modelos**, clique em **Biblioteca de Classes**.  
  
4.  Na caixa **Nome**, digite um nome apropriado para a biblioteca de classes, por exemplo, MyFirstVisualizer.  
  
5.  Clique em **OK**.  
  
 Quando você criou a biblioteca de classes, você deverá adicionar uma referência a Microsoft.VisualStudio.DebuggerVisualizers.DLL de forma que possa usar as classes definidas nela.  Primeiro, no entanto, dê ao seu projeto um nome significativo.  
  
#### Para renomear Class1.vb e adicionar Microsoft.VisualStudio.DebuggerVisualizers  
  
1.  No **Gerenciador de Soluções**, clique com o botão direito em **Class1.vb** e, no menu de atalho, clique em **Renomear**.  
  
2.  Altere o nome de Class1.vb para algo significativo, por exemplo, DebuggerSide.vb.  
  
    > [!NOTE]
    >  O [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] automaticamente altera a declaração de classes em DebuggerSide.vb para corresponder ao novo nome do arquivo.  
  
3.  No **Gerenciador de Soluções**, clique com o botão direito em **Meu Primeiro Visualizador** e, no menu de atalho, clique em **Adicionar Referência**.  
  
4.  Na caixa de diálogo **Adicionar Referência**, na guia **.NET**, clique em Microsoft.VisualStudio.DebuggerVisualizers.DLL.  
  
5.  Clique em **OK**.  
  
6.  Em DebuggerSide.vb, adicione a seguinte instrução às instruções `Imports`:  
  
    ```  
    Imports Microsoft.VisualStudio.DebuggerVisualizers  
    ```  
  
## Adicionar o código do lado do depurador  
 Agora você está pronto para criar o código do lado do depurador.  Este é o código executado no depurador para exibir as informações que você deseja visualizar.  Primeiro, você tem que alterar a declaração do objeto `DebuggerSide` de forma que ele herde da classe base `DialogDebuggerVisualizer`.  
  
#### Para herdar de DialogDebuggerVisualizer  
  
1.  Em DebuggerSide.vb, vá para a seguinte linha de código:  
  
    ```  
    Public Class DebuggerSide  
    ```  
  
2.  Edite o código de forma que tenha esta aparência:  
  
    ```  
    Public Class DebuggerSide  
    Inherits DialogDebuggerVisualizer  
    ```  
  
 `DialogDebuggerVisualizer` tem um método abstrato `Show`, que você deve substituir.  
  
#### Para substituir o método DialogDebuggerVisualizer.Show  
  
-   Em `public class DebuggerSide`, adicione o seguinte método:  
  
    ```  
    Protected Overrides Sub Show(ByVal windowService As Microsoft.VisualStudio.DebuggerVisualizers.IDialogVisualizerService, ByVal objectProvider As Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider)  
  
        End Sub  
    ```  
  
 O método `Show` contém o código que realmente cria a caixa de diálogo DO visualizador ou outra interface de usuário e exibe as informações que foram passadas para o visualizador do depurador.  Adicione o código que cria a caixa de diálogo e exibe as informações.  Neste passo a passo, você fará isso usando uma caixa de mensagem do Windows Forms.  Primeiro, você deve adicionar uma referência e uma instrução `Imports` para <xref:System.Windows.Forms>.  
  
#### Para adicionar System.Windows.Forms  
  
1.  No **Gerenciador de Soluções**, clique com o botão direito em **Referências** e, no menu de atalho, clique em **Adicionar Referência**.  
  
2.  Na caixa de diálogo **Adicionar Referência**, na guia **.NET**, clique em **System.Windows.Forms**.  
  
3.  Clique em **OK**.  
  
4.  Em DebuggerSide .cs, adicione a seguinte instrução às instruções `Imports`:  
  
    ```  
    Imports System.Windows.Forms  
    ```  
  
## Criar a interface de usuário do visualizador  
 Agora, você adicionará um código para criar e exibir a interface de usuário para o visualizador.  Como esse é o primeiro visualizador, você manterá a interface do usuário simples e usará uma caixa de mensagem.  
  
#### Para mostrar a saída do visualizador em uma caixa de diálogo  
  
1.  No método `Show`, adicione a seguinte linha de código:  
  
    ```  
    MessageBox.Show(objectProvider.GetObject().ToString())  
    ```  
  
     Esse código de exemplo não inclui tratamento de erros.  Você deve incluir o tratamento de erros em um visualizador real ou qualquer outro tipo de aplicativo.  
  
2.  No menu **Compilação**, clique em **Compilar MyFirstVisualizer**.  O projeto deve ser compilado com êxito.  Corrija os erros de compilação antes de continuar.  
  
## Adicionar o atributo necessário  
 Esse é o final do código do lado do depurador.  Há mais uma etapa, porém: o atributo que diz ao lado a ser depurado qual coleção de classes integra o visualizador.  
  
#### Para adicionar o código do lado a ser depurado  
  
1.  Adicione o seguinte código do atributo a DebuggerSide.vb, depois das instruções `Imports`, mas antes de `namespace MyFirstVisualizer`:  
  
    ```  
    <Assembly: System.Diagnostics.DebuggerVisualizer(GetType(MyFirstVisualizer.DebuggerSide), GetType(VisualizerObjectSource), Target:=GetType(System.String), Description:="My First Visualizer")>  
    ```  
  
2.  No menu **Compilação**, clique em **Compilar MyFirstVisualizer**.  O projeto deve ser compilado com êxito.  Corrija os erros de compilação antes de continuar.  
  
## Criar um agente de teste  
 Neste momento, o primeiro visualizador é concluído.  Se você seguiu as etapas corretamente, poderá compilar o visualizador e instalá\-lo no [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  Antes de instalar um visualizador no [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], no entanto, você deverá testá\-lo para garantir que seja executado corretamente.  Agora você criará um teste automatizado para executar o visualizador sem instalá\-lo no [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
#### Para adicionar um método de teste para mostrar o visualizador  
  
1.  Adicione o método a seguir à classe `public DebuggerSide`.  
  
    ```  
    Shared Public Sub TestShowVisualizer(ByVal objectToVisualize As Object)  
        Dim visualizerHost As New VisualizerDevelopmentHost(objectToVisualize, GetType(DebuggerSide))  
    visualizerHost.ShowVisualizer()  
    End Sub  
    ```  
  
2.  No menu **Compilação**, clique em **Compilar MyFirstVisualizer**.  O projeto deve ser compilado com êxito.  Corrija os erros de compilação antes de continuar.  
  
 Em seguida, você deverá criar um projeto executável para chamar sua DLL do visualizador.  Para simplificar, use um projeto de aplicativo de console.  
  
#### Para adicionar um projeto de aplicativo de console à solução  
  
1.  No menu **Arquivo**, clique em **Adicionar** e em **Novo Projeto**.  
  
2.  Na caixa de diálogo **Adicionar Novo Projeto**, na caixa **Modelos**, clique em **Aplicativo de Console**.  
  
3.  Na caixa **Nome**, digite um nome significativo para o aplicativo de console, por exemplo, MyTestConsole.  
  
4.  Clique em **OK**.  
  
 Agora, você deve adicionar as referências necessárias para que MyTestConsole possa chamar MyFirstVisualizer.  
  
#### Para adicionar as referências necessárias a MyTestConsole  
  
1.  No **Gerenciador de Soluções**, clique com o botão direito em **MyTestConsole** e, no menu de atalho, clique em **Adicionar Referência**.  
  
2.  Na caixa de diálogo **Adicionar Referência**, na guia **.NET**, clique em Microsoft.VisualStudio.DebuggerVisualizers.  
  
3.  Clique em **OK**.  
  
4.  Clique com o botão direito em **MyTestConsole** e clique em **Adicionar Referência** novamente.  
  
5.  Na caixa de diálogo **Adicionar Referência**, clique na guia **Projetos** e selecione MyFirstVisualizer.  
  
6.  Clique em **OK**.  
  
## Conclua seu agente de teste e teste o visualizador  
 Agora, você adicionará o código para concluir um teste automatizado.  
  
#### Para adicionar código a MyTestConsole  
  
1.  No **Gerenciador de Soluções**, clique com o botão direito em **Program.vb** e, no menu de atalho, clique em **Renomear**.  
  
2.  Edite o nome de Module1.vb para algo apropriado, por exemplo, TestConsole.vb.  
  
     Observe que o [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] automaticamente altera a declaração de classes em TestConsole.vb para corresponder ao novo nome do arquivo.  
  
3.  No TestConsole.vb, adicione a seguinte instrução `Imports`:  
  
    ```  
    Imports MyFirstVisualizer  
    ```  
  
4.  No método `Main`, adicione o seguinte código:  
  
    ```  
    Dim myString As String = "Hello, World"  
    DebuggerSide.TestShowVisualizer(myString)  
    ```  
  
 Agora, você está pronto para testar seu primeiro visualizador.  
  
#### Para testar o visualizador  
  
1.  No **Gerenciador de Soluções**, clique com o botão direito em **MyTestConsole** e, no menu de atalho, clique em **Definir como Projeto de Inicialização**.  
  
2.  No menu **Depurar**, clique em **Iniciar**.  
  
     O aplicativo de console é iniciado.  O visualizador aparece e exibe a cadeia de caracteres “Hello, World”.  
  
 Parabéns.  Você acabou de criar e testar seu primeiro visualizador.  
  
 Se você quiser usar o visualizador no [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] em vez de apenas chamá\-lo do teste automatizado, será preciso instalá\-lo.  Para obter mais informações, consulte [Como instalar um visualizador](../debugger/how-to-install-a-visualizer.md).  
  
## Consulte também  
 [Arquitetura do visualizador](../debugger/visualizer-architecture.md)   
 [Como instalar um visualizador](../debugger/how-to-install-a-visualizer.md)   
 [Visualizadores](../debugger/create-custom-visualizers-of-data.md)