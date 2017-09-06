---
title: Criando um controle de caixa de ferramentas do WPF | Documentos do Microsoft
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 059b3e5fc64f3251ca46f4c141772db44c46f081
ms.contentlocale: pt-br
ms.lasthandoff: 02/22/2017

---
# <a name="creating-a-wpf-toolbox-control"></a>Criando um controle de caixa de ferramentas do WPF
O modelo de controle de caixa de ferramentas do WPF (Windows Presentation Framework) permite que você crie controles do WPF que são adicionados automaticamente para o **caixa de ferramentas** quando a extensão é instalada. Este tópico mostra como usar o modelo para criar um **Toolbox** controle que você pode distribuir para outros usuários.  
  
 A partir do Visual Studio 2015, você não instale o SDK do Visual Studio no Centro de download. Ele é fornecido como um recurso opcional na instalação do Visual Studio. Você também pode instalar o SDK do VS mais tarde. Para obter mais informações, consulte [instalar o SDK do Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-wpf-toolbox-control"></a>Criando um controle de caixa de ferramentas do WPF  
  
#### <a name="create-an-extension-with-a-wpf-toolbox-control"></a>Criar uma extensão com um controle de caixa de ferramentas do WPF  
  
1.  Crie um projeto do VSIX chamado `MyToolboxControl`. Você pode encontrar o modelo de projeto do VSIX no **novo projeto** caixa de diálogo em **Visual c# / extensibilidade**.  
  
2.  Quando o projeto for aberto, adicione uma **controle de caixa de ferramentas do WPF** item modelo nomeado `MyToolboxControl`. No **Solution Explorer**, com o botão direito no nó do projeto e selecione **Adicionar / Novo Item**. No **Adicionar Novo Item** caixa de diálogo, vá para **Visual c# / extensibilidade** e selecione **controle de caixa de ferramentas do WPF**. No **nome** campo na parte inferior da janela, altere o nome do arquivo de comando para `MyToolboxControl.cs`.  
  
     A solução agora contém um controle de usuário, uma `ProvideToolboxControlAttribute` <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute>que adiciona o controle para o **Toolbox**e um **Microsoft.VisualStudio.ToolboxControl** entrada ativo no manifesto VSIX para implantação.</xref:Microsoft.VisualStudio.Shell.RegistrationAttribute>  
  
#### <a name="to-create-the-control-ui"></a>Para criar o controle da interface do usuário  
  
1.  Abra MyToolboxControl.xaml no designer.  
  
     O designer mostra um <xref:System.Windows.Controls.Grid>controle que contém um <xref:System.Windows.Controls.Button>controle.</xref:System.Windows.Controls.Button> </xref:System.Windows.Controls.Grid>  
  
2.  Organize o layout de grade. Quando você seleciona o <xref:System.Windows.Controls.Grid>controlar, barras de controle azuis são exibidas nas bordas superior e esquerdas da grade.</xref:System.Windows.Controls.Grid> Você pode adicionar linhas e colunas à grade clicando nas barras.  
  
3.  Adicione controles filho à grade. Você pode posicionar um controle filho, arrastando-o da **Toolbox** para uma seção da grade, ou definindo seu `Grid.Row` e `Grid.Column` atributos no XAML. O exemplo a seguir adiciona dois rótulos na linha superior da grade e um botão na segunda linha.  
  
    ```xaml  
    <Grid>  
        <Label Grid.Row="0" Grid.Column="0" Name="label1" />  
        <Label Grid.Row="0" Grid.Column="1" Name="label2" />  
        <Button Name="button1" Click="button1_Click" Grid.Row="1" Grid.ColumnSpan="2" />  
    </Grid>  
    ```  
  
## <a name="renaming-the-control"></a>Renomeando o controle  
 Por padrão, o controle será exibido no **Toolbox** como **MyToolboxControl** em um grupo denominado **MyToolboxControl.MyToolboxControl**. Você pode alterar esses nomes no arquivo MyToolboxControl.xaml.cs.  
  
1.  Abra MyToolboxControl.xaml.cs na exibição de código.  
  
2.  Localize a classe MyToolboxControl e renomeá-lo para TestControl. (A maneira mais rápida de fazer isso é renomear a classe, selecione **Renomear** no menu de contexto e conclua as etapas. (Para obter mais informações sobre o **Renomear** de comando, consulte [renomear refatoração (c#)](../csharp-ide/rename-refactoring-csharp.md).)  
  
3.  Vá para o `ProvideToolboxControl` de atributo e altere o valor do primeiro parâmetro para **teste**. Esse é o nome do grupo que contém o controle de **ferramentas**.  
  
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
 Quando você depura o projeto, você deve encontrar o controle instalado no **Toolbox** da instância experimental do Visual Studio.  
  
#### <a name="to-build-and-test-the-control"></a>Para compilar e testar o controle  
  
1.  Recompilar o projeto e iniciar a depuração.  
  
2.  Na nova instância do Visual Studio, crie um projeto de aplicativo WPF. Verifique se que o Designer XAML é aberto.  
  
3.  Localize o controle no **ferramentas** e arraste-o para a superfície de design.  
  
4.  Inicie a depuração do aplicativo do WPF.  
  
5.  Verifique se o controle aparece.  
  
#### <a name="to-deploy-the-control"></a>Para implantar o controle  
  
1.  Depois de criar o projeto testado, você pode encontrar o arquivo. VSIX na pasta \bin\debug\ do projeto.  
  
2.  Você pode instalá-lo em um computador local clicando duas vezes no arquivo. VSIX e seguir o procedimento de instalação. Para desinstalar o controle, vá para **ferramentas / extensões e atualizações** e procure a extensão de controle e clique em **desinstalar**.  
  
3.  Carregue o arquivo. VSIX em uma rede ou para um site da Web.  
  
     Se você carregar o arquivo para o [Galeria do Visual Studio](http://go.microsoft.com/fwlink/?LinkID=123847) site da Web, outros usuários podem usar **ferramentas / extensões e atualizações** no Visual Studio para localizar o controle online e instalá-lo.
