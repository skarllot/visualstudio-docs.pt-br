---
title: "Instru&#231;&#245;es passo a passo: escrevendo um visualizador em C# | Microsoft Docs"
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
ms.assetid: 53467461-8e0f-45ee-9bc4-374bbaeaf00f
caps.latest.revision: 33
caps.handback.revision: 33
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Instru&#231;&#245;es passo a passo: escrevendo um visualizador em C# #
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Este passo a passo mostra como escrever um visualizador simples usando C\#.  O visualizador que você criará neste passo a passo exibe o conteúdo de uma cadeia de caracteres usando uma caixa de mensagem do Windows Forms.  Esse visualizador simples de cadeia de caracteres não é especialmente útil em si mesmo, mas mostra as etapas básicas a seguir para criar visualizadores mais úteis para outros tipos de dados.  
  
> [!NOTE]
>  As caixas de diálogo e os comandos do menu que você vê podem ser diferentes dos descritos na Ajuda, dependendo da edição ou das configurações ativas.  Para alterar as configurações, vá para o menu **Ferramentas** e escolha **Importar e Exportar Configurações**.  Para obter mais informações, consulte [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/pt-br/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
 O código do visualizador deve ser colocado em uma DLL, que será lido pelo depurador.  Consequentemente, a primeira etapa é criar um projeto da Biblioteca de Classes para a DLL.  
  
#### Para criar um projeto da biblioteca de classes  
  
1.  No menu **Arquivo**, escolha **Novo** e clique em **Novo Projeto**.  
  
2.  Na caixa de diálogo **Novo Projeto**, em **Tipo de Projeto**, selecione **Visual C\#**.  
  
3.  Na caixa **Modelos**, escolha **Biblioteca de Classes**.  
  
4.  Na caixa **Nome**, digite um nome apropriado para a biblioteca de classes, por exemplo, MyFirstVisualizer.  
  
5.  Clique em **OK**.  
  
 Depois de ter criado a biblioteca de classes, você deverá adicionar uma referência a Microsoft.VisualStudio.DebuggerVisualizers.DLL de forma que possa usar as classes definidas nela.  Antes de adicionar a referência, no entanto, você deverá renomear algumas classes de modo que tenham nomes significativos.  
  
#### Para renomear Class1.cs e adicionar Microsoft.VisualStudio.DebuggerVisualizers  
  
1.  No **Gerenciador de Soluções**, clique com o botão direito em Class1.cs e escolha **Renomear** no menu de atalho.  
  
2.  Altere o nome de Class1.cs para algo significativo, por exemplo, DebuggerSide.cs.  
  
    > [!NOTE]
    >  O [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] automaticamente altera a declaração de classes em DebuggerSide.cs para corresponder ao novo nome do arquivo.  
  
3.  No **Gerenciador de Soluções**, clique com o botão direito em **Referências** e escolha **Adicionar Referência** no menu de atalho.  
  
4.  Na caixa de diálogo **Adicionar Referência**, na guia **.NET**, escolha Microsoft.VisualStudio.DebuggerVisualizers.DLL.  
  
5.  Clique em **OK**.  
  
6.  Em DebuggerSide.cs, adicione a seguinte instrução às instruções `using`:  
  
    ```  
    using Microsoft.VisualStudio.DebuggerVisualizers;  
    ```  
  
 Agora você está pronto para criar o código do lado do depurador.  Este é o código executado no depurador para exibir as informações que você deseja visualizar.  Primeiro, você tem que alterar a declaração do objeto `DebuggerSide` de forma que ele herde da classe base `DialogDebuggerVisualizer`.  
  
#### Para herdar de DialogDebuggerVisualizer  
  
1.  Em DebuggerSide.cs, vá para a seguinte linha de código:  
  
    ```  
    public class DebuggerSide  
    ```  
  
2.  Altere o código para:  
  
    ```  
    public class DebuggerSide : DialogDebuggerVisualizer  
    ```  
  
 `DialogDebuggerVisualizer` tem um método abstrato \(`Show`\) que você deve substituir.  
  
#### Para substituir o método DialogDebuggerVisualizer.Show  
  
-   Em `public class DebuggerSide`, adicione o seguinte **método:**  
  
    ```  
    override protected void Show(IDialogVisualizerService windowService, IVisualizerObjectProvider objectProvider)  
    {  
    }  
    ```  
  
 O método `Show` contém o código que realmente cria a caixa de diálogo DO visualizador ou outra interface de usuário e exibe as informações que foram passadas para o visualizador do depurador.  Adicione o código que cria a caixa de diálogo e exibe as informações.  Neste passo a passo, você fará isso usando uma caixa de mensagem do Windows Forms.  Primeiro, você deve adicionar uma referência e uma instrução `using` para System.Windows.Forms.  
  
#### Para adicionar System.Windows.Forms  
  
1.  No **Gerenciador de Soluções**, clique com o botão direito em **Referências** e escolha **Adicionar Referência** no menu de atalho.  
  
2.  Na caixa de diálogo **Adicionar Referência**, na guia **.NET**, escolha System.Windows.Forms.DLL.  
  
3.  Clique em **OK**.  
  
4.  Em DebuggerSide.cs, adicione a seguinte instrução às instruções `using`:  
  
    ```  
    using System.Windows.Forms;  
    ```  
  
 Agora, você adicionará um código para criar e exibir a interface de usuário para o visualizador.  Como esse é o primeiro visualizador, manteremos a interface do usuário simples e usaremos uma caixa de mensagem.  
  
#### Para mostrar a saída do visualizador em uma caixa de diálogo  
  
1.  No método `Show`, adicione a seguinte linha de código:  
  
    ```  
    MessageBox.Show(objectProvider.GetObject().ToString());  
    ```  
  
     Esse código de exemplo não inclui tratamento de erros.  Você deve incluir o tratamento de erros em um visualizador real ou qualquer outro tipo de aplicativo.  
  
2.  No menu **Compilação**, escolha **Compilar MyFirstVisualizer**.  O projeto deve ser compilado com êxito.  Corrija os erros de compilação antes de continuar.  
  
 Esse é o final do código do lado do depurador.  Há mais uma etapa, porém; o atributo que diz ao lado a ser depurado qual coleção de classes integra o visualizador.  
  
#### Para adicionar o código do lado a ser depurado  
  
1.  Adicione o seguinte código do atributo a DebuggerSide.cs, depois das instruções `using`, mas antes de `namespace MyFirstVisualizer`:  
  
    ```  
    [assembly:System.Diagnostics.DebuggerVisualizer(  
    typeof(MyFirstVisualizer.DebuggerSide),  
    typeof(VisualizerObjectSource),  
    Target  = typeof(System.String),  
    Description  = "My First Visualizer")]  
    ```  
  
2.  No menu **Compilação**, escolha **Compilar MyFirstVisualizer**.  O projeto deve ser compilado com êxito.  Corrija os erros de compilação antes de continuar.  
  
 Neste momento, o primeiro visualizador é concluído.  Se você seguiu as etapas corretamente, poderá compilar o visualizador e instalá\-lo no [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  Antes de instalar um visualizador no [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], no entanto, você deverá testá\-lo para garantir que seja executado corretamente.  Agora você criará um teste automatizado para executar o visualizador sem instalá\-lo no [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
#### Para adicionar um método de teste para mostrar o visualizador  
  
1.  Adicione o método a seguir à classe `public DebuggerSide`.  
  
    ```  
    public static void TestShowVisualizer(object objectToVisualize)  
    {  
       VisualizerDevelopmentHost visualizerHost = new VisualizerDevelopmentHost(objectToVisualize, typeof(DebuggerSide));  
       visualizerHost.ShowVisualizer();  
    }  
    ```  
  
2.  No menu **Compilação**, escolha **Compilar MyFirstVisualizer**.  O projeto deve ser compilado com êxito.  Corrija os erros de compilação antes de continuar.  
  
 Em seguida, você deverá criar um projeto executável para chamar sua DLL do visualizador.  Para simplificar, usaremos um projeto de aplicativo de console.  
  
#### Para adicionar um projeto de aplicativo de console à solução  
  
1.  No menu **Arquivo**, escolha **Adicionar** e clique em **Novo Projeto**.  
  
2.  Na caixa de diálogo **Adicionar Novo Projeto**, na caixa **Modelos**, escolha **Aplicativo de Console**.  
  
3.  Na caixa **Nome**, digite um nome significativo para o aplicativo de console, por exemplo, `MyTestConsole`.  
  
4.  Clique em **OK**.  
  
 Agora, você deve adicionar as referências necessárias para que MyTestConsole possa chamar MyFirstVisualizer.  
  
#### Para adicionar as referências necessárias a MyTestConsole  
  
1.  No **Gerenciador de Soluções**, clique com o botão direito em **MyTestConsole** e escolha **Adicionar Referência** no menu de atalho.  
  
2.  Na caixa de diálogo **Adicionar Referência**, na guia **.NET**, escolha Microsoft.VisualStudio.DebuggerVisualizers.DLL.  
  
3.  Clique em **OK**.  
  
4.  Clique com o botão direito em **MyTestConsole** e escolha **Adicionar Referência** novamente.  
  
5.  Na caixa de diálogo **Adicionar Referência**, clique na guia **Projetos** e clique em MyFirstVisualizer.  
  
6.  Clique em **OK**.  
  
 Agora, você adicionará o código para concluir um teste automatizado.  
  
#### Para adicionar código a MyTestConsole  
  
1.  No **Gerenciador de Soluções**, clique com o botão direito em Program.cs e escolha **Renomear** no menu de atalho.  
  
2.  Edite o nome de Program.cs para algo mais significativo, por exemplo, TestConsole.cs.  
  
     **Observação** O [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] automaticamente altera a declaração de classes em TestConsole.cs para corresponder ao novo nome do arquivo.  
  
3.  Em TestConsole.cs, adicione o seguinte código às instruções `using`:  
  
    ```  
    using MyFirstVisualizer;  
    ```  
  
4.  No método `Main`, adicione o seguinte código:  
  
    ```  
    String myString = "Hello, World";  
    DebuggerSide.TestShowVisualizer(myString);  
    ```  
  
 Agora, você está pronto para testar seu primeiro visualizador.  
  
#### Para testar o visualizador  
  
1.  No **Gerenciador de Soluções**, clique com o botão direito em **MyTestConsole** e escolha **Definir como Projeto de Inicialização** no menu de atalho.  
  
2.  No menu **Depurar**, escolha **Iniciar**.  
  
     O aplicativo de console inicia e o visualizador aparece e exibe a cadeia de caracteres “Hello World”.  
  
 Parabéns.  Você acabou de criar e testar seu primeiro visualizador.  
  
 Se você quiser usar o visualizador no [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] em vez de apenas chamá\-lo do teste automatizado, será preciso instalá\-lo.  Para obter mais informações, consulte [Como instalar um visualizador](../debugger/how-to-install-a-visualizer.md).  
  
## Usando o modelo de item do visualizador  
 Até agora, este passo a passo mostrou como criar um visualizador manualmente.  Isto foi feito como um exercício de aprendizado.  Agora que você sabe como um visualizador simples funciona, há uma forma mais fácil de criar um: usando o modelo de item do visualizador.  
  
 Primeiro, você precisará criar um novo projeto de biblioteca de classes.  
  
#### Para criar uma nova biblioteca de classes  
  
1.  No menu **Arquivo**, escolha **Adicionar** e clique em **Novo Projeto**.  
  
2.  Na caixa de diálogo **Adicionar Novo Projeto**, em **Tipo de Projeto**, selecione **Visual C\#**.  
  
3.  Na caixa **Modelos**, escolha **Biblioteca de Classes**.  
  
4.  Na caixa **Nome**, digite um nome apropriado para a biblioteca de classes, por exemplo, MySecondVisualizer.  
  
5.  Clique em **OK**.  
  
 Agora, você pode adicionar um item de visualizador a ele:  
  
#### Para adicionar um item de visualizador  
  
1.  No **Gerenciador de Soluções**, clique com o botão direito em MySecondVisualizer.  
  
2.  No menu de atalho, escolha **Adicionar**, e clique em **Novo Item**.  
  
3.  Na caixa de diálogo **Adicionar Novo Item**, em **Modelos**, **Modelos Instalados do Visual Studio**, selecione **Visualizador do Depurador**.  
  
4.  Na caixa **Nome**, digite um nome apropriado, por exemplo, SecondVisualizer.cs.  
  
5.  Clique em **Adicionar**.  
  
 É tudo que se precisa.  Examine o arquivo SecondVisualizer.cs e exiba o código que o modelo adicionou para você.  Agora tente com o código.  Agora que você conhece as noções básicas, está em condições de criar visualizadores mais complexos e úteis.  
  
## Consulte também  
 [Arquitetura do visualizador](../debugger/visualizer-architecture.md)   
 [Como instalar um visualizador](../debugger/how-to-install-a-visualizer.md)   
 [Visualizadores](../debugger/create-custom-visualizers-of-data.md)