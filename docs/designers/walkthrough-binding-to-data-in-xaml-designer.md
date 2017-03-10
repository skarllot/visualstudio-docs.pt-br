---
title: "Passo a passo: Associando dados no XAML Designer | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VS.XamlDesigner.DataBinding"
ms.assetid: 1a99aeae-c3ef-407d-ba79-b8055489a43d
caps.latest.revision: 20
caps.handback.revision: 20
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Passo a passo: Associando dados no XAML Designer
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

No Designer XAML, você pode definir propriedades de associação de dados por meio da prancheta e na janela Propriedades.  O exemplo neste passo a passo mostra como associar dados a um controle.  Especificamente, o passo a passo mostra como criar uma classe de carrinho de compras simples que tem um [DependencyProperty](http://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.dependencyproperty.aspx) chamado `ItemCount`, e associar o `ItemCount` propriedade para o **texto** propriedade de um [TextBlock](http://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.textblock.aspx) controle.  
  
### Para criar uma classe a ser usada como uma fonte de dados  
  
1.  No menu **Arquivo**, escolha **Novo Projeto**.  
  
2.  No **novo projeto** caixa de diálogo caixa, escolha o o **Visual C\#** ou **Visual Basic** nó, expanda o **Windows Desktop** nó e, em seguida, escolha o **aplicativo WPF** modelo.  
  
3.  Nomeie o projeto BindingTest e, em seguida, escolha o **OK** botão.  
  
4.  Abra o arquivo MainWindow.xaml.cs \(ou MainWindow.xaml.vb\) e adicione o código a seguir.  No c\#, adicione o código a `BindingTest` espaço para nome \(antes do parêntese de fechamento no arquivo\).  No Visual Basic, basta adicione a nova classe.  
  
    ```c#  
    public class ShoppingCart : DependencyObject  
    {  
        public int ItemCount  
        {  
            get { return (int)GetValue(ItemCountProperty); }  
            set { SetValue(ItemCountProperty, value); }  
        }  
  
        public static readonly DependencyProperty ItemCountProperty =  
             DependencyProperty.Register("ItemCount", typeof(int),  
             typeof(ShoppingCart), new PropertyMetadata(0));  
    }  
  
    ```  
  
    ```vb  
    Public Class ShoppingCart  
        Inherits DependencyObject  
  
        Public Shared ReadOnly ItemCountProperty As DependencyProperty = DependencyProperty.Register(  
            "ItemCount", GetType(Integer), GetType(ShoppingCart), New PropertyMetadata(0))  
        Public Property ItemCount As Integer  
            Get  
                ItemCount = CType(GetValue(ItemCountProperty), Integer)  
            End Get  
            Set(value As Integer)  
                SetValue(ItemCountProperty, value)  
            End Set  
        End Property  
    End Class  
    ```  
  
     Esse código define um valor de 0 como a contagem de itens padrão usando o [PropertyMetadata](http://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.propertymetadata.aspx) objeto.  
  
5.  Sobre o **arquivo** menu, escolha **criar**, **Build Solution**.  
  
### Para associar a propriedade ItemCount a um controle TextBlock  
  
1.  No Solution Explorer, abra o menu de atalho de MainWindow. XAML e escolha **View Designer**.  
  
2.  Na caixa de ferramentas, escolha uma [grade](http://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.grid.aspx) de controle e adicioná\-lo ao formulário.  
  
3.  Com o `Grid` selecionado, na janela Propriedades, escolha o **novo** botão ao lado de **DataContext** propriedade.  
  
4.  No **Selecionar objeto** caixa de diálogo caixa, certifique\-se de que **Mostrar todos os assemblies** caixa de seleção estiver desmarcada, escolha **ShoppingCart** sob o **BindingTest** namespace e, em seguida, escolha o **OK** botão.  
  
     A ilustração a seguir mostra o **Selecionar objeto** caixa de diálogo com **ShoppingCart** selecionado.  
  
     ![The Select Object dialog box](../designers/media/blendselectobject.PNG "BlendSelectObject")  
  
5.  No **Toolbox**, escolha um `TextBlock` controle para adicioná\-lo ao formulário.  
  
6.  Com o `TextBlock` controle selecionado, na janela Propriedades, escolha o marcador de propriedade à direita do **texto** propriedade e escolha **criar associação de dados**.  \(Marcador de propriedade se parece com uma pequena caixa.\)  
  
7.  Nos dados criar associação de caixa de diálogo, no **caminho** caixa, escolha o **ItemCount: \(int32\)** propriedade e, em seguida, escolha o **OK** botão.  
  
     A ilustração a seguir mostra o **criar associação de dados** caixa de diálogo com o **ItemCount** propriedade selecionada.  
  
     ![Criar caixa de diálogo vinculação de dados](../designers/media/xaml_create_data_binding.png "xaml\_create\_data\_binding")  
  
8.  Pressione F5 para executar o aplicativo.  
  
     O `TextBlock` controle deve mostrar o valor padrão de 0 como texto.  
  
## Consulte também  
 [Criando uma interface de usuário usando o Designer XAML](../designers/creating-a-ui-by-using-xaml-designer-in-visual-studio.md)   
 [NIB: Add Value Converter dialog box](http://msdn.microsoft.com/pt-br/c5f3d110-a541-4b55-8bca-928f77778af8)