---
title: "Anatomia de um teste de IU codificado | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "testes de IU codificados"
ms.assetid: 9c5d82fc-3fb7-4bb1-a9ac-ac1fa3a4b500
caps.latest.revision: 23
caps.handback.revision: 23
ms.author: "mlearned"
manager: "douge"
---
# Anatomia de um teste de IU codificado
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Quando você cria um teste de IU codificado em um projeto de teste de IU codificado, vários arquivos são adicionados à sua solução.  Neste tópico, usaremos um exemplo de teste de IU codificado para explorar esses arquivos.  
  
 **Requisitos**  
  
-   O Visual Studio Enterprise  
  
## Conteúdo de um teste de IU codificado  
 Quando você cria um teste de IU codificado, o **Construtor de teste de IU codificado** cria um mapa da interface do usuário em teste e também os métodos de teste, parâmetros e asserções para todos os testes.  Ele também cria um arquivo de classe para cada teste.  
  
|Arquivo|Conteúdo|Editável?|  
|-------------|--------------|---------------|  
|[UIMap.Designer.cs](#UIMapDesignerFile)|[Seção de declarações](#UIMapDesignerFile)<br /><br /> [UIMap classe](#UIMapClass) \(parcial, gerado automaticamente\)<br /><br /> [Métodos](#UIMapMethods)<br /><br /> [Propriedades](#UIMapProperties)|Não|  
|[UIMap.cs](#UIMapCS)|[UIMap classe](#UIMapCS) \(parcial\)|Sim|  
|[Codeduitest1](#CodedUITestCS)|[Classe CodedUITest1](#CodedUITestCS)<br /><br /> [Métodos](#CodedUITestMethods)<br /><br /> [Propriedades](#CodedUITestProperties)|Sim|  
|[Uitest](#UIMapuitest)|O mapa XML da interface do usuário para o teste.|Não|  
  
###  <a name="UIMapDesignerFile"></a> UIMap.Designer.cs  
 Esse arquivo contém o código que é criado automaticamente com o **Construtor de teste de IU codificado** quando um teste é criado.  Esse arquivo é recriado cada vez que um teste for alterado, para que não seja um arquivo no qual você pode adicionar ou modificar o código.  
  
#### Seção de declarações  
 Esta seção inclui as seguintes declarações para uma interface de usuário do Windows.  
  
```c#  
using System;  
using System.CodeDom.Compiler;  
using System.Collections.Generic;  
using System.Drawing;  
using System.Text.RegularExpressions;  
using System.Windows.Input;  
using Microsoft.VisualStudio.TestTools.UITest.Extension;  
using Microsoft.VisualStudio.TestTools.UITesting;  
using Microsoft.VisualStudio.TestTools.UITesting.WinControls;  
using Microsoft.VisualStudio.TestTools.UnitTesting;  
using Keyboard = Microsoft.VisualStudio.TestTools.UITesting.Keyboard;  
using Mouse = Microsoft.VisualStudio.TestTools.UITesting.Mouse;  
using MouseButtons = System.Windows.Forms.MouseButtons;  
```  
  
 O <xref:Microsoft.VisualStudio.TestTools.UITesting.WinControls> namespace é incluído para uma interface de usuário \(UI\) do Windows.  Para uma página da Web da interface do usuário, o namespace seria <xref:Microsoft.VisualStudio.TestTools.UITesting.HtmlControls>; para um Windows Presentation Foundation da interface do usuário, o namespace seria <xref:Microsoft.VisualStudio.TestTools.UITesting.WpfControls>.  
  
####  <a name="UIMapClass"></a> Classe UIMap  
 A próxima seção do arquivo é o <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UIMap.UIMap> classe.  
  
```  
[GeneratedCode("Coded UITest Builder", "10.0.21221.0")]  
public partial class UIMap  
```  
  
 O código da classe inicia com um <xref:System.CodeDom.Compiler.GeneratedCodeAttribute> que é aplicado à classe, que é declarada como uma classe parcial.  Você observará que o atributo também se aplica a todas as classes nesse arquivo.  O outro arquivo que pode conter mais de código para essa classe é `UIMap.cs`, que será discutido posteriormente.  
  
 Gerado `UIMap` classe inclui código para cada método que foi especificado quando o teste foi gravado.  
  
```  
public void LaunchCalculator()  
public void AddItems()  
public void VerifyTotal()  
public void CleanUp()  
```  
  
 Nesta parte do <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UIMap.UIMap> classe também inclui o código gerado para cada propriedade que é exigido pelos métodos.  
  
```  
public virtual LaunchCalculatorParams LaunchCalculatorParams  
public virtual AddItemsParams AddItemsParams  
public virtual VerifyTotalExpectedValues VerifyTotalExpectedValues  
public virtual CalculateItemsParams CalculateItemsParams  
public virtual VerifyMathAppTotalExpectedValues   
    VerifyMathAppTotalExpectedValues  
public UIStartMenuWindow UIStartMenuWindow  
public UIRunWindow UIRunWindow  
public UICalculatorWindow UICalculatorWindow  
public UIStartWindow UIStartWindow  
public UIMathApplicationWindow UIMathApplicationWindow  
```  
  
#####  <a name="UIMapMethods"></a> Métodos de UIMap  
 Cada método tem uma estrutura semelhante a `AddItems()` método.  Isso é explicado com mais detalhes em código, que é apresentado com quebras de linha para adicionar a clareza.  
  
```  
/// <summary>  
/// AddItems - Use 'AddItemsParams' to pass parameters into this method.  
/// </summary>  
public void AddItems()  
{  
    #region Variable Declarations  
    WinControl uICalculatorDialog =   
        this.UICalculatorWindow.UICalculatorDialog;  
    WinEdit uIItemEdit =   
        this.UICalculatorWindow.UIItemWindow.UIItemEdit;  
    #endregion  
  
    // Type '{NumPad7}' in 'Calculator' Dialog  
    Keyboard.SendKeys(uICalculatorDialog,   
        this.AddItemsParams.UICalculatorDialogSendKeys,   
        ModifierKeys.None);  
  
    // Type '{Add}{NumPad2}{Enter}' in 'Unknown Name' text box  
    Keyboard.SendKeys(uIItemEdit,   
        this.AddItemsParams.UIItemEditSendKeys,   
        ModifierKeys.None);  
}  
```  
  
 O comentário de resumo para cada definição do método informa qual classe usar para valores de parâmetro para o método.  Nesse caso, é o `AddItemsParams` classe, que é definido posteriormente o `UIMap.cs` arquivo e que também é o tipo de valor que é retornado pelo `AddItemsParams` propriedade.  
  
 Na parte superior do método de código é um `Variable Declarations` objetos de região que define as variáveis locais para a interface do usuário que será usado pelo método.  
  
 Nesse método, ambos `UIItemWindow` e `UIItemEdit` são propriedades que são acessadas por meio de `UICalculatorWindow` classe, que é definido posteriormente o `UIMap.cs` arquivo.  
  
 Em seguida, são linhas que enviar texto do teclado para o aplicativo Calculadora usando propriedades do `AddItemsParams` objeto.  
  
 O `VerifyTotal()` método tem uma estrutura muito semelhante e inclui o seguinte código de declaração.  
  
```  
// Verify that 'Unknown Name' text box's property 'Text' equals '9. '  
Assert.AreEqual(  
    this.VerifyTotalExpectedValues.UIItemEditText,   
    uIItemEdit.Text);  
```  
  
 O nome da caixa de texto é listado como desconhecido porque o desenvolvedor do aplicativo Calculadora do Windows não forneceu um nome publicamente disponível para o controle.  O <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.AreEqual%2A?displayProperty=fullName> método falhar quando o valor real não é igual ao valor esperado, o que causa a falha de teste.  Observe também que o valor esperado inclui um ponto decimal seguido por um espaço.  Se você alguma vez precisar modificar a funcionalidade desse teste específico, você deve permitir esse ponto decimal e o espaço.  
  
#####  <a name="UIMapProperties"></a> Propriedades de UIMap  
 O código para cada propriedade é também muito padrão por meio da classe.  O código a seguir para o `AddItemsParams` propriedade é usada no `AddItems()` método.  
  
```  
public virtual AddItemsParams AddItemsParams  
{  
    get  
    {  
        if ((this.mAddItemsParams == null))  
        {  
            this.mAddItemsParams = new AddItemsParams();  
        }  
        return this.mAddItemsParams;  
    }  
}  
```  
  
 Observe que a propriedade usa uma variável particular local chamado `mAddItemsParams` para manter o valor antes de retornar a ele.  O nome da propriedade e o nome da classe do objeto que ela retorna são os mesmos.  A classe é definida posteriormente o `UIMap.cs` arquivo.  
  
 Cada classe é retornado por uma propriedade é estruturado de maneira semelhante.  A seguir está o `AddItemsParams` classe.  
  
```  
/// <summary>  
/// Parameters to be passed into 'AddItems'  
/// </summary>  
[GeneratedCode("Coded UITest Builder", "10.0.21221.0")]  
public class AddItemsParams  
{  
    #region Fields  
    /// <summary>  
    /// Type '{NumPad7}' in 'Calculator' Dialog  
    /// </summary>  
    public string UICalculatorDialogSendKeys = "{NumPad7}";  
  
    /// <summary>  
    /// Type '{Add}{NumPad2}{Enter}' in 'Unknown Name' text box  
    /// </summary>  
    public string UIItemEditSendKeys = "{Add}{NumPad2}{Enter}";  
    #endregion  
}  
```  
  
 Assim como acontece com todas as classes no `UIMap.cs` arquivo, essa classe inicia com o <xref:System.CodeDom.Compiler.GeneratedCodeAttribute>.  Nessa classe pequeno é um `Fields` região que define as cadeias de caracteres para usar como parâmetros para o <xref:Microsoft.VisualStudio.TestTools.UITesting.Keyboard.SendKeys%2A?displayProperty=fullName> método que é usado no `UIMap.AddItems()` método que foi discutido anteriormente.  Você pode escrever código para substituir os valores nesses campos de cadeia de caracteres antes de é chamado o método no qual esses parâmetros são usados.  
  
###  <a name="UIMapCS"></a> UIMap.cs  
 Por padrão, esse arquivo contém um parcial `UIMap` classe que não tem métodos ou propriedades.  
  
#### Classe UIMap  
 Isso é onde você pode criar códigos personalizados para estender a funcionalidade da <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UIMap.UIMap> classe.  O código que você cria neste arquivo não será regenerado pelo **Construtor de teste de IU codificado** toda vez que um teste é modificado.  
  
 Todas as partes do <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UIMap.UIMap> pode usar os métodos e propriedades de qualquer outra parte do <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UIMap.UIMap> classe.  
  
###  <a name="CodedUITestCS"></a> Codeduitest1  
 Esse arquivo é gerado pelo **Construtor de teste de IU codificado**, mas não será recriado sempre que o teste for modificado, para que você pode modificar o código neste arquivo.  O nome do arquivo é gerado do nome que você especificou para o teste quando você o criou.  
  
#### Classe CodedUITest1  
 Por padrão, esse arquivo contém a definição para apenas uma classe.  
  
```  
[CodedUITest]  
public class CodedUITest1  
```  
  
 O T:Microsoft.VisualStudio.TestTools.UITesting.CodedUITestAttribute é aplicada automaticamente a classe, que permite que o framework de teste para reconhecê\-lo como uma extensão de teste.  Além disso, observe que isso não é uma classe parcial.  Todo código de classe está contido nesse arquivo.  
  
#####  <a name="CodedUITestProperties"></a> Propriedades de CodedUITest1  
 A classe contém duas propriedades padrão que estão localizadas na parte inferior do arquivo.  Eles não devem ser modificados.  
  
```  
/// <summary>  
/// Gets or sets the test context which provides  
/// information about and functionality for the current test run.  
///</summary>  
public TestContext TestContext  
public UIMap UIMap  
```  
  
#####  <a name="CodedUITestMethods"></a> Métodos de CodedUITest1  
 Por padrão, a classe contém apenas um método.  
  
```  
public void CodedUITestMethod1()  
```  
  
 Este método chama cada `UIMap` método especificado quando você registrou seu teste, que é descrito na seção sobre o [UIMap classe](#UIMapClass).  
  
 Uma região é intitulada `Additional test attributes`, se removidos, contém dois métodos opcionais.  
  
```  
// Use TestInitialize to run code before running each test   
[TestInitialize()]  
public void MyTestInitialize()  
{  
    // To generate code for this test, select "Generate Code for Coded   
    // UI Test" from the shortcut menu and select one of the menu items.  
    // For more information on generated code, see   
    // http://go.microsoft.com/fwlink/?LinkId=179463  
  
    // You could move this line from the CodedUITestMethod1() method  
    this.UIMap.LaunchCalculator();  
}  
  
// Use TestCleanup to run code after each test has run  
[TestCleanup()]  
public void MyTestCleanup()  
{  
    // To generate code for this test, select "Generate Code for Coded   
    // UI Test" from the shortcut menu and select one of the menu items.  
    // For more information on generated code, see   
    // http://go.microsoft.com/fwlink/?LinkId=179463  
  
    // You could move this line from the CodedUITestMethod1() method  
    this.UIMap.CloseCalculator();  
}  
```  
  
 O `MyTestInitialize()` método tem o <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestInitializeAttribute> aplicada, que faz com que a estrutura de testes para chamar esse método antes de quaisquer outros métodos de teste.  Da mesma forma, o `MyTestCleanup()` método tem o <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestCleanupAttribute> aplicado a ele, que informa a estrutura de testes para chamar esse método após todos os outros métodos de teste ter sido chamado.  O uso desses métodos é opcional.  Para este teste, o `UIMap.LaunchCalculator()` método poderia ser chamado de `MyTestInitialize()` e o `UIMap.CloseCalculator()` método poderia ser chamado de `MyTestCleanup()` em vez do `CodedUITest1Method1()`.  
  
 Se você adicionar mais métodos para essa classe usando o <xref:Microsoft.VisualStudio.TestTools.UITesting.CodedUITestAttribute>, a estrutura de testes irá chamar cada método como parte do teste.  
  
###  <a name="UIMapuitest"></a> Uitest  
 Este é um arquivo XML que representa a estrutura da interface do usuário codificado teste gravação e todas as suas partes.  Isso inclui as ações e as classes além dos métodos e propriedades dessas classes.  O [UIMap.Designer.cs](#UIMapDesignerFile) arquivo contém o código que é gerado pelo construtor de IU codificado para reproduzir a estrutura do teste e fornece a conexão com a estrutura de testes.  
  
 O `UIMap.uitest` arquivo não é editável diretamente.  No entanto, você pode usar o construtor de IU codificado para modificar o teste, que modifica automaticamente o `UIMap.uitest` arquivo e o [UIMap.Designer.cs](#UIMapDesignerFile) arquivo.  
  
## Consulte também  
 <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UIMap.UIMap>   
 <xref:Microsoft.VisualStudio.TestTools.UITesting.WinControls>   
 <xref:Microsoft.VisualStudio.TestTools.UITesting.HtmlControls>   
 <xref:Microsoft.VisualStudio.TestTools.UITesting.WpfControls>   
 <xref:System.CodeDom.Compiler.GeneratedCodeAttribute>   
 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.AreEqual%2A?displayProperty=fullName>   
 <xref:Microsoft.VisualStudio.TestTools.UITesting.Keyboard.SendKeys%2A?displayProperty=fullName>   
 <xref:Microsoft.VisualStudio.TestTools.UITesting.CodedUITestAttribute>   
 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestInitializeAttribute>   
 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestCleanupAttribute>   
 [Usar automação de interface do usuário para testar código](../test/use-ui-automation-to-test-your-code.md)   
 [Criando testes de UI codificados](../test/use-ui-automation-to-test-your-code.md#VerifyingCodeUsingCUITCreate)   
 [Práticas recomendadas para testes de IU codificados](../test/best-practices-for-coded-ui-tests.md)   
 [Testando um aplicativo grande com vários mapas de interface do usuário](../test/testing-a-large-application-with-multiple-ui-maps.md)   
 [Configurações e plataformas compatíveis para testes de IU codificados e gravações de ações](../test/supported-configurations-and-platforms-for-coded-ui-tests-and-action-recordings.md)