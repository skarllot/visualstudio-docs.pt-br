---
title: Criando um controle de caixa de ferramentas do WPF | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- toolbox control
- toolbox
- wpf
ms.assetid: 9cc34db9-b0d1-4951-a02f-7537fbbb51ad
caps.latest.revision: 16
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
ms.translationtype: MT
ms.sourcegitcommit: 4a36302d80f4bc397128e3838c9abf858a0b5fe8
ms.openlocfilehash: 40196a61c1fdc1dd7f2cf7d75e5fa65fb0580160
ms.contentlocale: pt-br
ms.lasthandoff: 09/26/2017

---
# <a name="creating-a-wpf-toolbox-control"></a>Criando um controle de caixa de ferramentas do WPF
O modelo de controle de caixa de ferramentas do WPF (Windows Presentation Framework) permite que você crie controles do WPF que são adicionados automaticamente para o **caixa de ferramentas** quando a extensão está instalada. Este tópico mostra como usar o modelo para criar um **caixa de ferramentas** controle que você pode distribuir para outros usuários.  
  
 A partir do Visual Studio 2015, você não instalar o SDK do Visual Studio no Centro de download. Ele está incluído como um recurso opcional na instalação do Visual Studio. Você também pode instalar o SDK do VS posteriormente. Para obter mais informações, consulte [instalar o SDK do Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-wpf-toolbox-control"></a>Criando um controle de caixa de ferramentas do WPF  
  
#### <a name="create-an-extension-with-a-wpf-toolbox-control"></a>Criar uma extensão com um controle de caixa de ferramentas do WPF  
  
1.  Crie um projeto do VSIX denominado `MyToolboxControl`. Você pode encontrar o modelo de projeto do VSIX no **novo projeto** caixa de diálogo em **Visual C# / extensibilidade**.  
  
2.  Quando o projeto é aberto, adicione um **controle de caixa de ferramentas do WPF** item modelo chamado `MyToolboxControl`. No **Solution Explorer**, com o botão direito no nó do projeto e selecione **Adicionar / Novo Item**. No **Adicionar Novo Item** caixa de diálogo, vá para **Visual C# / extensibilidade** e selecione **controle de caixa de ferramentas do WPF**. No **nome** campo na parte inferior da janela, altere o nome do arquivo de comando para `MyToolboxControl.cs`.  
  
     A solução agora contém um controle de usuário, uma `ProvideToolboxControlAttribute` <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute> que adiciona o controle para o **caixa de ferramentas**e um **Microsoft.VisualStudio.ToolboxControl** entrada ativo no manifesto do VSIX para  implantação.  
  
#### <a name="to-create-the-control-ui"></a>Para criar o controle de interface do usuário  
  
1.  Abra MyToolboxControl.xaml no designer.  
  
     O designer mostra um <xref:System.Windows.Controls.Grid> controle que contém um <xref:System.Windows.Controls.Button> controle.  
  
2.  Organize o layout de grade. Quando você seleciona o <xref:System.Windows.Controls.Grid> controlar, barras de controle azul aparecem nas bordas superior e esquerdas da grade. Você pode adicionar linhas e colunas à grade clicando nas barras.  
  
3.  Adicione controles filho à grade. Você pode posicionar um controle filho arrastando-o do **caixa de ferramentas** para uma seção da grade ou definindo seu `Grid.Row` e `Grid.Column` atributos no XAML. O exemplo a seguir adiciona dois rótulos na linha superior da grade e um botão na segunda linha.  
  
    ```xaml  
    <Grid>  
        <Label Grid.Row="0" Grid.Column="0" Name="label1" />  
        <Label Grid.Row="0" Grid.Column="1" Name="label2" />  
        <Button Name="button1" Click="button1_Click" Grid.Row="1" Grid.ColumnSpan="2" />  
    </Grid>  
    ```  
  
## <a name="renaming-the-control"></a>Renomear o controle  
 Por padrão, o controle será exibido no **caixa de ferramentas** como **MyToolboxControl** em um grupo denominado **MyToolboxControl.MyToolboxControl**. Você pode alterar esses nomes no arquivo MyToolboxControl.xaml.cs.  
  
1.  Abra MyToolboxControl.xaml.cs na exibição de código.  
  
2.  Localizar a classe MyToolboxControl e renomeie-o para TestControl. (É a maneira mais rápida para fazer isso renomear a classe, selecione **Renomear** no menu de contexto e conclua as etapas. (Para obter mais informações sobre o **Renomear** command, consulte [renomear refatoração (c#)](../csharp-ide/rename-refactoring-csharp.md).)  
  
3.  Vá para o `ProvideToolboxControl` de atributo e altere o valor do primeiro parâmetro para **teste**. Este é o nome do grupo que contém o controle no **caixa de ferramentas**.  
  
     O código resultante deve ter esta aparência:  
  
    ```csharp  
    [ProvideToolboxControl("Test", true)]  
    public partial class TestControl : UserControl  
    {  
        public TestControl()  
        {  
            InitializeComponent();  
        }  
    }  
    ```  
  
## <a name="building-testing-and-deployment"></a>Criação, teste e implantação  
 Quando você depura o projeto, você deve encontrar o controle instalado no **caixa de ferramentas** da instância experimental do Visual Studio.  
  
#### <a name="to-build-and-test-the-control"></a>Para compilar e testar o controle  
  
1.  Recompile o projeto e iniciar a depuração.  
  
2.  Na nova instância do Visual Studio, crie um projeto de aplicativo do WPF. Verifique se que o XAML Designer é aberto.  
  
3.  Localizar seu controle no **caixa de ferramentas** e arraste-o para a superfície de design.  
  
4.  Inicie a depuração de aplicativo do WPF.  
  
5.  Verifique se o controle é exibido.  
  
#### <a name="to-deploy-the-control"></a>Para implantar o controle  
  
1.  Depois de compilar o projeto testado, você pode encontrar o arquivo .vsix na pasta \bin\debug\ do projeto.  
  
2.  Você pode instalá-lo em um computador local duas vezes no arquivo .vsix e seguindo o procedimento de instalação. Para desinstalar o controle, vá para **ferramentas / extensões e atualizações** e procure a extensão de controle, clique em **desinstalação**.  
  
3.  Carregar o arquivo de .vsix em uma rede ou para um site da Web.  
  
     Se você carregar o arquivo para o [Galeria do Visual Studio](http://go.microsoft.com/fwlink/?LinkID=123847) site da Web, outros usuários podem usar **ferramentas / extensões e atualizações** no Visual Studio para localizar o controle online e instalá-lo.
