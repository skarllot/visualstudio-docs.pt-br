---
title: "Definir uma propriedade de automa&#231;&#227;o exclusiva para controles da Windows Store para teste | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 9bdd74ff-2534-4fc7-a5c3-a77bf7843037
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "mlearned"
manager: "douge"
---
# Definir uma propriedade de automa&#231;&#227;o exclusiva para controles da Windows Store para teste
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Se você desejar executar testes codificados da interface do usuário para seu aplicativo baseado XAML\- do Windows Store, você deve ter uma propriedade exclusiva de automação que identifica cada controle.  
  
 Você pode atribuir uma propriedade exclusiva de automação com base no tipo de controle XAML em seu aplicativo.  Veja como atribuir essa propriedade exclusiva de automação nas seguintes situações:  
  
-   [Definição estático XAML de controles](#UniquePropertyWindowsStoreControlsStaticXAML)  
  
-   [Atribuir propriedades exclusivas de automação usando o Visual Studio ou misture\-as para Visual Studio](#UniquePropertyWindowsStoreControlsExpressionBlend)  
  
-   [Use um DataTemplate](#UniquePropertyWindowsStoreControlsDataTemplate)  
  
-   [Use um modelo de controle](#UniquePropertyWindowsStoreControlsControlTemplate)  
  
-   [Controles dinâmicos](#UniquePropertyWindowsStoreControlsDynamicControls)  
  
## Use métodos para atribuir uma propriedade exclusiva de automação  
  
###  <a name="UniquePropertyWindowsStoreControlsStaticXAML"></a> Definição estático XAML  
 Para especificar uma propriedade exclusiva de automação para um controle que é definido no arquivo XAML, você pode definir o AutomationProperties.AutomationId ou o AutomationProperties.Name implícita ou explicitamente, como mostrado nos exemplos.  Definir qualquer um desses valores da ao controle uma propriedade exclusiva de automação que pode ser usado para identificar o controle quando você cria uma gravação codificado de teste ou da ação de interface do usuário.  
  
 **Defina a propriedade implicitamente**  
  
 Definir o AutomationProperties.AutomationId a ButtonX usando a propriedade de nome em XAML para o controle.  
  
```xaml  
<Button Name="ButtonX" Height="31" HorizontalAlignment="Left" Margin="23,26,0,0"  VerticalAlignment="Top" Width="140" Click="ButtonX_Click" />  
  
```  
  
 Definir o AutomationProperties.Name a ButtonY usando a propriedade de conteúdo em XAML para o controle.  
  
```xaml  
<Button Content="ButtonY" Height="31" HorizontalAlignment="Left" Margin="23,76,0,0" VerticalAlignment="Top" Width="140" Click="ButtonY_Click" />  
  
```  
  
 **Defina a propriedade explicitamente**  
  
 Definir o AutomationProperties.AutomationId a ButtonX explicitamente em XAML para o controle.  
  
```xaml  
<Button AutomationProperties.AutomationId=“ButtonX” Height="31" HorizontalAlignment="Left" Margin="23,26,0,0"  VerticalAlignment="Top" Width="140" Click="ButtonX_Click" />  
  
```  
  
 Definir o AutomationProperties.Name a ButtonY explicitamente em XAML para o controle.  
  
```  
<Button AutomationProperties.Name="ButtonY" Height="31" HorizontalAlignment="Left" Margin="23,76,0,0" VerticalAlignment="Top" Width="140" Click="ButtonY_Click" />  
```  
  
###  <a name="UniquePropertyWindowsStoreControlsExpressionBlend"></a> Atribuir propriedades exclusivas de automação usando o Visual Studio ou misture\-as para Visual Studio  
 Você pode usar o Visual Studio ou misturar\-se para que o Visual Studio atribua nomes exclusivos para elementos interativos como os botões, as caixas de listagem, as caixas de combinação e as caixas de texto.  Isso fornece ao controle um valor exclusivo para AutomationProperties.Name.  
  
 **Visual Studio:** No menu de **Ferramentas** , aponte para **Opções** e escolha **Editor de Texto**, em **XAML**e, finalmente **Diversos**.  
  
 **Nomear automaticamente os elementos interativos na criação** Selecione e escolha **OK**.  
  
 ![XAML Miscellaneous options](../test/media/cuit_windowsstoreapp_b.png "CUIT\_WindowsStoreApp\_B")  
  
 Use um de**Blend para o Visual Studio:** dos seguintes métodos para fazer isso Blend do Visual Studio.  
  
> [!NOTE]
>  Você só pode usar esse método para os controles que são criados estaticamente usando XAML.  
  
 **Para fornecer um nome exclusivo para controles existentes**  
  
 No menu de **Ferramentas** , escolha **Nomear elementos interativos**, como mostrado a seguir:  
  
 ![Choose Name Interactive Elements from Tools menu](../test/media/cuit_windowsstoreproperty_blend_1.png "CUIT\_WindowsStoreProperty\_Blend\_1")  
  
 **Para conceder automaticamente um nome exclusivo para controles que você cria**  
  
 No menu de **Ferramentas** , aponte para **Opções**, e escolha **Projeto**.  **Nomear automaticamente os elementos interativos na criação** Selecione e escolha **OK**, como mostrado a seguir:  
  
 ![Set project to name interactive elements](../test/media/cuit_windowsstoreproeprty_blend_2.png "CUIT\_WindowsStoreProeprty\_Blend\_2")  
  
###  <a name="UniquePropertyWindowsStoreControlsDataTemplate"></a> Use um modelo de dados  
 Você pode definir um modelo simples usando ItemTemplate para associar os valores em uma caixa de listagem para variáveis usando o seguinte XAML.  
  
```xaml  
  
<ListBox Name="listBox1" ItemsSource="{Binding Source={StaticResource employees}}">  
   <ListBox.ItemTemplate>  
      <DataTemplate>  
         <StackPanel Orientation="Horizontal">  
            <TextBlock Text="{Binding EmployeeName}" />  
            <TextBlock Text="{Binding EmployeeID}" />  
         </StackPanel>  
      </DataTemplate>  
   </ListBox.ItemTemplate>  
</ListBox>  
```  
  
 Você também pode usar um modelo com ItemContainerStyle para associar os valores a variáveis usando o seguinte XAML.  
  
```xaml  
  
      <ListBox Name="listBox1" ItemsSource="{Binding Source={StaticResource employees}}">  
            <ListBox.ItemContainerStyle>  
                <Style TargetType="ListBoxItem">  
                    <Setter Property="Template">  
                        <Setter.Value>  
                            <ControlTemplate TargetType="ListBoxItem">  
                                <Grid>  
                                    <Button Content="{Binding EmployeeName}" AutomationProperties.AutomationId="{Binding EmployeeID}"/>  
                                </Grid>  
                            </ControlTemplate>  
                        </Setter.Value>  
                    </Setter>  
                </Style>  
            </ListBox.ItemContainerStyle>           
        </ListBox>  
  
```  
  
 Para ambos os exemplos, você deve então substituir o método de ToString\(\) de ItemSource, como mostrado usando\-se o código a seguir.  Esse código assegura que o valor de AutomationProperties.Name será definido e é exclusivo, pois você não pode definir uma propriedade exclusiva de automação para cada item da lista associado de dados usando a associação.  Definir um valor exclusivo para a automação Properties.Name é suficiente nesse caso.  
  
> [!NOTE]
>  Usando essa abordagem, o conteúdo internos do item da lista também podem ser definidos como uma cadeia de caracteres na classe do funcionário na associação.  Conforme mostrado no exemplo, o controle de botão em cada item de lista é atribuído um ID exclusivo de automação que é a ID de funcionário  
  
```  
  
Employee[] employees = new Employee[]   
{  
   new Employee("john", "4384"),  
   new Employee("margaret", "7556"),  
   new Employee("richard", "8688"),  
   new Employee("george", "1293")  
};  
  
listBox1.ItemsSource = employees;  
  
public override string ToString()  
{  
    return EmployeeName + EmployeeID; // Unique Identification to be set as the AutomationProperties.Name  
}  
  
```  
  
###  <a name="UniquePropertyWindowsStoreControlsControlTemplate"></a> Use um modelo de controle  
 Você pode usar um modelo de controle de modo que cada instância de um tipo específico obtenha uma propriedade exclusiva de automação quando é definido no código.  Você deve criar o modelo para que o AutomationProperty se associe a uma ID exclusiva na instância do controle.  XAML o seguinte demonstra uma abordagem para criar essa associação com um modelo do controle.  
  
```xaml  
  
<Style x:Key="MyButton" TargetType="Button">  
<Setter Property="Template">  
   <Setter.Value>  
<ControlTemplate TargetType="Button">  
   <Grid>  
      <CheckBox HorizontalAlignment="Left" AutomationProperties.AutomationId="{TemplateBinding Content}"></CheckBox>  
      <Button Width="90" HorizontalAlignment="Right" Content="{TemplateBinding Content}" AutomationProperties.AutomationId="{TemplateBinding Content}"></Button>  
   </Grid>  
</ControlTemplate>  
   </Setter.Value>  
</Setter>  
</Style>  
  
```  
  
 Quando você define duas instâncias de um botão usando esse modelo de controle, a ID de automação está definida como a cadeia de caracteres de conteúdo exclusivo para os controles no modelo, como mostrado no seguinte XAML.  
  
```xaml  
  
<Button Content=”Button1” Style="{StaticResource MyButton}" Width="140"/>  
<Button Content=”Button2” Style="{StaticResource MyButton}" Width="140"/>  
```  
  
###  <a name="UniquePropertyWindowsStoreControlsDynamicControls"></a> Controles dinâmicos  
 Se você tiver os controles que são criados dinamicamente no seu código e não são criados estática ou pelos modelos em arquivos XAML, você deve definir as propriedades de conteúdo ou do nome do controle.  Isso garante que cada controle dinâmico tem uma propriedade exclusiva de automação.  Por exemplo, se você tiver uma caixa de seleção que deve ser exibida quando você seleciona um item de lista, você pode definir essas propriedades, como mostrado a seguir:  
  
```c#  
  
private void CreateCheckBox(string txt, StackPanel panel)  
   {  
      CheckBox cb = new CheckBox();  
      cb.Content = txt; // Sets the AutomationProperties.Name  
      cb.Height = 50;  
      cb.Width = 100;  
      cb.Name = "DynamicCheckBoxAid"+ txt; // Sets the AutomationProperties.AutomationId  
      panel.Children.Add(cb);  
    }  
  
```  
  
## Consulte também  
 [Aplicativos da Windows Store teste 8.1 com testes de UI codificados](../test/test-windows-store-8-1-apps-with-coded-ui-tests.md)