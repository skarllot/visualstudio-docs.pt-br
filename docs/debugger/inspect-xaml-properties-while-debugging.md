---
title: "Inspecione as propriedades XAML durante a depura&#231;&#227;o | Microsoft Docs"
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
ms.assetid: 390edde4-7b8d-4c89-8d69-55106b7e6b11
caps.latest.revision: 3
caps.handback.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Inspecione as propriedades XAML durante a depura&#231;&#227;o
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Você pode obter uma visão em tempo real do seu código XAML em execução com o**árvore Visual do Live**e**Live propriedade Explorer**.  Essas ferramentas oferecem um modo de exibição de árvore dos elementos da interface do usuário do seu aplicativo em execução do XAML e mostram as propriedades de tempo de execução de qualquer elemento de interface do usuário selecionado.  
  
 Você pode usar essas ferramentas nas seguintes configurações:  
  
|Tipo de aplicativo|Sistema operacional e ferramentas|  
|------------------------|---------------------------------------|  
|Aplicativos de Windows Presentation Foundation \(4.0 e superior\)|O Windows 7 e versões posteriores|  
|Windows Store e Windows Phone 8.1 aplicativos|Windows 10 e acima, com a[Windows 10 SDK](https://dev.windows.com/en-us/downloads/windows-10-sdk)|  
|Aplicativos universais do Windows|Windows 10 e acima, com a[Windows 10 SDK](https://dev.windows.com/en-us/downloads/windows-10-sdk)|  
  
## Examinando os elementos na árvore Visual ao vivo  
 Vamos começar com um aplicativo do WPF muito simples que tem um modo de exibição de lista e um botão.  Sempre que você clicar no botão, o outro item é adicionado à lista.  Itens pares são coloridos cinza e itens ímpares são coloridos de amarelos.  
  
 Criar um novo aplicativo WPF c\# \(arquivo \/ novo \/ projeto, selecione c\# e localizar um aplicativo WPF\).  O nome TestXAML.  
  
 Altere MainWindow. XAML com o seguinte:  
  
```xaml  
<Window x:Class="WpfApplication1.MainWindow"  
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"  
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"  
    xmlns:d="http://schemas.microsoft.com/expression/blend/2008"  
    xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"  
    xmlns:local="clr-namespace:WpfApplication1"  
    mc:Ignorable="d"  
     Title="MainWindow" Height="350" Width="525">  
    <Grid>  
        <Button x:Name="button" Background="LightBlue" Content="Add Item" HorizontalAlignment="Left" Margin="216,206,0,0" VerticalAlignment="Top" Width="75" Click="button_Click"/>  
        <ListBox x:Name="listBox" HorizontalAlignment="Left" Height="100" VerticalAlignment="Top" Width="100" Margin="205,80,0,0"/>  
    </Grid>  
</Window>  
```  
  
 Adicione o seguinte manipulador de comando para o arquivo de MainWindow.xaml.cs:  
  
```c#  
private void button_Click(object sender, RoutedEventArgs e)  
{  
    ListBoxItem item = new ListBoxItem();  
    item.Content = "Item" + ++count;  
    if (count % 2 == 0)  
    {  
        item.Background = Brushes.LightGray;  
    }  
    else  
    {  
        item.Background = Brushes.LightYellow;  
    }  
    listBox.Items.Add(item);  
}  
```  
  
 Compile o projeto e iniciar a depuração.  \(A configuração de compilação deve ser depuração, e não de versão.  Para obter mais informações sobre configurações de compilação, consulte[Noções sobre configurações de compilação](../ide/understanding-build-configurations.md).\)  
  
 Quando a janela é exibida, clique o**Adicionar Item**botão duas vezes.  Você deve ver algo assim:  
  
 ![Main window of the app](~/debugger/media/livevisualtree-app.png "LiveVIsualTree\-App")  
  
 Agora, abra o**árvore Visual do Live**janela \(**Debug \/ Windows \/ árvore Visual do Live**ou a encontrá\-lo no lado esquerdo do IDE\).  Arraste\-a para fora de sua posição de encaixe para que possamos observar essa janela e o**Propriedades Live**janela lado a lado.  No**árvore Visual do Live**janela, expanda o**ContentPresenter**nó.  Ele deve conter nós para o botão e a caixa de listagem.  Expanda a caixa de listagem \(e, em seguida, o**ScrollContentPresenter**e**ItemsPresenter**\) para ver a lista de itens de caixa.  A janela deve ter esta aparência:  
  
 ![ListBoxItems in the Live Visual Tree](../debugger/media/livevisualtree-listboxitems.png "LiveVisualTree\-ListBoxItems")  
  
 Volte à janela do aplicativo e adicionar alguns itens.  Você deverá ver mais itens de caixa de lista no**árvore Visual do Live**.  
  
 Agora vamos examinar as propriedades de um dos itens da caixa de lista.  Selecione o primeiro item de caixa de listagem no**árvore Visual do Live**e clique no**Mostrar propriedades**ícone na barra de ferramentas.  O**Live propriedade Explorer**deve aparecer.  Observe que o**conteúdo**campo é "Item1" e o**fundo**campo é**\#FFFFFFE0**\(amarelo\-claro\).  Volte para o**árvore Visual do Live**e selecione o segundo item de caixa de listagem.  O**Live propriedade Explorer**deve mostrar que o**conteúdo**campo é "Item2" e o**em segundo plano**campo é**\#FFD3D3D3**\(cinza claro\).  
  
 A estrutura real do XAML tem vários elementos que você provavelmente não está interessado diretamente e se você não souber o código também pode ter dificuldade para navegar pela árvore para encontrar o que você está procurando.  Portanto, o**árvore Visual do Live**tem algumas maneiras que permitem usar a interface do usuário do aplicativo para ajudá\-lo a localizar o elemento que você deseja examinar.  
  
 **Ativar a seleção do aplicativo em execução**.  Você pode habilitar esse modo quando você seleciona o botão mais à esquerda no**árvore Visual do Live**barra de ferramentas.  Com esse modo em, você pode selecionar um elemento de interface do usuário no aplicativo e o**árvore Visual do Live**\(e o**Live Visualizador de propriedade**\) é atualizado automaticamente para mostrar o nó da árvore que corresponde ao elemento e suas propriedades.  
  
 **Exibir adorners de layout do aplicativo em execução**.  Você pode habilitar esse modo quando você seleciona o botão que está imediatamente à direita do botão de seleção Enable.  Quando**exibir adorners layout**estiver ativado, ele faz com que a janela do aplicativo Mostrar linhas horizontais e verticais ao longo dos limites do objeto selecionado, você pode ver o que ele alinha, bem como retângulos que mostram as margens.  Por exemplo, ativar ambos**Ativar seleção**e**layout de exibição**ativado e selecione o**Adicionar Item**bloco de texto no aplicativo.  Você deve ver o nó de bloco de texto no**árvore Visual do Live**e o bloco de texto propriedades**Live Visualizador de propriedade**bem como as linhas horizontais e verticais dos limites do bloco de texto.  
  
 ![LivePropertyViewer in DisplayLayout](~/debugger/media/livevisualtreelivepropertyviewer-displaylayout.png "LiveVisualTreeLivePropertyViewer\-DisplayLayout")  
  
 **Visualizar seleção**.  Você pode habilitar esse modo selecionando o terceiro botão da esquerda na barra de ferramentas Live árvore Visual.  Este modo mostra o XAML onde o elemento foi declarado, se você tiver acesso ao código\-fonte do aplicativo.  Selecione**Ativar seleção**e**Visualizar seleção**e, em seguida, selecione o botão no nosso aplicativo de teste.  O arquivo MainWindow. XAML é aberto no Visual Studio e o cursor é colocado na linha em que o botão é definido.  
  
## Usando ferramentas XAML com aplicativos em execução  
 Você pode usar essas ferramentas XAML, mesmo quando você não tiver o código\-fonte.  Quando você anexa a um aplicativo XAML em execução, você pode usar o**árvore Visual do Live**nos elementos da interface do usuário de aplicativo muito.  Aqui está um exemplo, com o mesmo aplicativo de teste WPF que usamos antes.  
  
1.  Inicie o aplicativo TestXaml na configuração de versão.  Você não pode anexar a um processo que está sendo executado em um**Depurar**configuração.  
  
2.  Abra uma segunda instância do Visual Studio e clique em**Depurar \/ anexar a processo**.  Localizar**TestXaml.exe**na lista de processos disponíveis e clique em**Attach**.  
  
3.  O aplicativo começa a ser executado.  
  
4.  Na segunda instância do Visual Studio, abra o**árvore Visual do Live**\(**Debug \/ Windows \/ Live árvore Visual**\).  Você deve ver os elementos de UI TestXaml e você deve ser capaz de manipulá\-los como você durante a depuração do aplicativo diretamente.