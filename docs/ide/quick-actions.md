---
title: "Ações Rápidas | Microsoft Docs"
ms.custom: 
ms.date: 05/08/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.devlang: csharp
ms.assetid: e173fb7d-c5bd-4568-ba0f-aa61913b3244
author: gewarren
ms.author: gewarren
manager: ghogen
dev_langs:
- CSharp
- VB
ms.translationtype: Human Translation
ms.sourcegitcommit: 8bf0b097be929b30627e0f1139c6e0b145933ab4
ms.openlocfilehash: ec2ae70312c7cb5f26630246046cadc7c210e1c2
ms.contentlocale: pt-br
ms.lasthandoff: 05/26/2017

---
# <a name="quick-actions"></a>Ações Rápidas

As [Ações Rápidas](refactoring-code-generation-quick-actions.md#quick-actions) permitem refatorar, gerar ou, de outro modo, modificar o código de maneira fácil com uma única ação.  Embora existam várias Ações Rápidas que se aplicam especificamente ao C# ou ao Visual Basic, também existem algumas que se aplicam a projetos do C# e do Visual Basic.  Elas podem ser aplicadas usando o ícone de Lâmpada ![Ícone de lâmpada pequeno](media/vs2015_lightbulbsmall.png "VS2017_LightBulbSmall") ou pressionando **Ctrl + .** quando o cursor estiver sobre a linha de código apropriada.

Você verá uma lâmpada se houver um rabisco vermelho e o Visual Studio tiver uma sugestão para corrigir o problema. Por exemplo se você tiver um erro indicado por um rabisco vermelho, uma lâmpada aparecerá quando correções estiverem disponíveis para esse erro. Para qualquer idioma, terceiros podem oferecer diagnóstico e sugestões personalizados, por exemplo, como parte de um SDK, e as lâmpadas do Visual Studio serão acesas de acordo com essas regras.  

### <a name="to-see-a-light-bulb"></a>Para ver uma lâmpada  

1. Em muitos casos, as lâmpadas aparecem espontaneamente ao focalizar o mouse no ponto de um erro ou na margem esquerda do editor ao mover o cursor em uma linha que contém um erro. Quando você vir um rabisco vermelho, poderá focalizar o mouse sobre ele para exibir a lâmpada. Você também poderá fazer com que uma lâmpada seja exibida ao usar o mouse ou o teclado para ir para qualquer lugar da linha em que ocorre o problema.  

2. Pressione **Ctrl + .** em qualquer lugar de uma linha para invocar a lâmpada e ir diretamente para a lista de possíveis correções.  

   ![Lâmpada com o mouse focalizando](../ide/media/vs2015_lightbulb_hover.png "VS2017_LightBulb_Hover")  

### <a name="to-see-potential-fixes"></a>Para ver as possíveis correções  
Clique na seta para baixo ou no link Mostrar possíveis correções para exibir uma lista de ações rápidas que a lâmpada pode executar para você.  

![Lâmpada expandida](../ide/media/vs2015_lightbulb_hover_expanded.png "VS2017_LightBulb_hover_expanded")

## <a name="common-quick-actions"></a>Ações Rápidas comuns
Estas são algumas das Ações Rápidas comuns que são aplicáveis ao código C# e Visual Basic.

### <a name="add-missing-casesdefault-caseboth"></a>Adicionar maiúsculas e minúsculas ausentes/maiúsculas e minúsculas padrão/ambas
Ao criar uma instrução `switch` no C# ou uma instrução `Select Case` no Visual Basic, é possível usar uma Ação de Código para adicionar automaticamente itens com maiúsculas e minúsculas ausentes, uma instrução com maiúsculas e minúsculas padrão ou ambos.  Para uma instrução vazia como a seguinte:

```csharp
enum MyEnum
{
    Item1,
    Item2,
    Item3
}

...

MyEnum myEnum = MyEnum.Item1;

switch(myEnum)
{
}
```
```vb
Enum MyEnum
    Item1
    Item2
    Item3
End Enum

...

Dim myEnum as MyEnum = MyEnum.Item1

Select Case myEnum
End Select
```

O uso da Ação Rápida **Adicionar Ambos** para preencher maiúsculas e minúsculas ausentes e maiúsculas e minúsculas padrão criará o seguinte:

```csharp
switch(myEnum)
{
    case MyEnum.Item1:
        break;
    case MyEnum.Item2:
        break;
    case MyEnum.Item3:
        break;
    default:
        break;
}
```
```vb
Select Case myEnum
    Case MyEnum.Item1
        Exit Select
    Case MyEnum.Item2
        Exit Select
    Case Else
        Exit Select
End Select
```

### <a name="correct-misspelled-type"></a>Corrigir tipo com ortografia incorreta
Se você digitar incorretamente um tipo no Visual Studio acidentalmente, essa Ação Rápida corrigirá isso de forma automática para você.  Você verá esses itens no menu de lâmpada como **“Alterar '*tipo digitado incorretamente*' para '*tipo correto*'”**.  Por exemplo:

```csharp
// Before
private viod MyMethod()
{
}

// Change 'viod' to 'void'

// After
private void MyMethod()
{
}
```
```vb
' Before
Function MyFunction as Intger
End Function

' Change 'Intger' to 'Integer'

' After
Function MyFunction as Integer
End Function
```

### <a name="remove-unnecessary-cast"></a>Remover conversão desnecessária
Se você converter um tipo em outro que não exige uma conversão, o item de Ação Rápida **Remover Conversão Desnecessária** removerá a conversão do código.

```csharp
// before
int number = (int)3;

// Remove Unnecessary Cast

// after
int number = 3;
```
```vb
' Before
Dim number as Integer = CType(3, Integer)

' Remove Unnecessary Cast

' After
Dim number as Integer = 3
```

### <a name="replace-method-with-property--replace-property-with-method"></a>Substituir método por propriedade/Substituir propriedade por método
Essas Ações Rápidas converterão um método em uma propriedade ou vice-versa.  O exemplo abaixo mostra a alteração de um método em uma propriedade.  Para o caso contrário, basta inverter as seções *Antes* e *Depois*.

```csharp
private int MyValue;

// Before
public int GetMyValue()
{
    return MyValue;
}

// Replace 'GetMyValue' with property

// After
public int MyValue
{
    get { return MyValue; }
}
```
```vb
Dim MyValue As Integer

' Before
Function GetMyValue() As Integer
    Return MyValue
End Function

' Replace 'GetMyValue' with property

' After
ReadOnly Property MyValue As Integer
    Get
        Return MyValue
    End Get
End Property
```

### <a name="make-method-synchronous"></a>Tornar o Método Síncrono
Ao usar a palavra-chave `async`/`Async` em um método, espera-se que, em algum lugar desse método, a palavra-chave `await`/`Await` também seja usada.  No entanto, se esse não for o caso, uma Ação Rápida será exibida, que permitirá tornar o método síncrono removendo a palavra-chave `async`/`Async` e alterando o tipo de retorno.  Use a opção **Tornar o método síncrono** do menu Ações Rápidas.

```csharp
// Before
async Task<int> MyAsyncMethod()
{
    return 3;
}

// Make method synchronous

// After
int MyAsyncMethod()
{
    return 3;
}
```
```vb
' Before
Async Function MyAsyncMethod() As Task(Of Integer)
    Return 3
End Function

' Make method synchronous

' After
Function MyAsyncMethod() As Integer
    Return 3
End Function
```

### <a name="make-method-asynchronous"></a>Tornar o Método Assíncrono
Ao usar a palavra-chave `await`/`Await` em um método, espera-se que o próprio método seja marcado com a palavra-chave `async`/`Async`.  No entanto, se esse não for o caso, uma Ação Rápida será exibida, que permitirá tornar o método assíncrono.  Use a opção **Tornar o método ou a função síncrona** do menu Ações Rápidas.

```csharp
// Before
int MyAsyncMethod()
{
    return await Task.Run(...);
}

// Make method synchronous

// After
async Task<int> MyAsyncMethod()
{
    return await Task.Run(...);
}
```
```vb
' Before
Function MyAsyncMethod() as Integer
    Return  Await Task.Run(...)
End Function

' Make method synchronous

' After
Async Function MyAsyncMethod() As Task(Of Integer)
    Return Await Task.Run(...)
End Function
```

### <a name="remove-unnecesary-usingsimports"></a>Remover Usos/Importações Desnecessários
A Ação Rápida **Remover Usos/Importações Desnecessários** removerá todas as instruções `using` e `Import` não utilizadas do arquivo atual.  Ao selecionar esse item, as importações de namespace não utilizadas serão removidas imediatamente.

### <a name="add-usingsimports-for-types-in-reference-assemblies-nuget-packages-or-other-types-in-your-solution"></a>Adicionar usos/importações para tipos em assemblies de referência, pacotes NuGet ou outros tipos na solução
O uso dos tipos localizados em outros projetos da solução exibirá a Ação Rápida automaticamente. No entanto, as outras precisam ser habilitadas na guia **Ferramentas > Opções > C#** ou **Basic > Avançado**:  

* Sugerir usos/importações para tipos em assemblies de referência
* Sugerir usos/importações para tipos em pacotes NuGet

Quando essa opção estiver habilitada, se você usar um tipo em um namespace que não foi importado, mas que existe em um assembly de referência ou pacote NuGet, a instrução de uso/importação será criada.

```csharp
// Before
Debug.WriteLine("Hello");

// using System.Diagnostics;

// After
using System.Diagnostics;

Debug.WriteLine("Hello");
```
```vb
' Before
Debug.WriteLine("Hello")

' Imports System.Diagnostics

// After
Imports System.Diagnostics

Debug.WriteLine("Hello")
```

### <a name="convert-to-interpolated-string"></a>Converter em Cadeia de Caracteres Interpolada
[Cadeias de caracteres interpoladas](/dotnet/csharp/language-reference/keywords/interpolated-strings) são uma maneira fácil de expressar cadeias de caracteres com variáveis inseridas, semelhante ao método **[String.Format](https://msdn.microsoft.com/library/system.string.format.aspx)**.  Essa Ação Rápida reconhece maiúsculas e minúsculas nas quais as cadeias de caracteres são concatenadas ou que usam **String.Format** e altera o uso de uma cadeia de caracteres interpolada.

```csharp
// Before
int num = 3;
string s = string.Format("My string with {0} in the middle", num);

// Convert to interpolated string

// After
int num = 3;
string s = $"My string with {num} in the middle";
```
```vb
' Before
Dim num as Integer = 3
Dim s as String = String.Format("My string with {0} in the middle", num)

' Convert to interpolated string

' After
Dim num as Integer = 3
Dim s As String = $"My string with {num} in the middle"
```

### <a name="remove-merge-conflict-markers"></a>Remover marcadores de conflito de mesclagem
Essas ações rápidas permitem que você resolva conflitos de mesclagem "fazendo uma alteração", que remove o código conflitante e os marcadores. (Disponível apenas no Visual Studio 2017 (versão 15.3 - versão prévia)).

![Refatoração - resolver conflitos de mesclagem](../ide/media/vside-refactoring-merge-conflicts.png)

### <a name="add-null-checks-for-parameters"></a>Adicionar verificações de null para parâmetros
Essa Ação Rápida permite que você adicione uma verificação ao código para determinar se um parâmetro é nulo. (Disponível apenas no Visual Studio 2017 (versão 15.3 - versão prévia)).

![Refatoração - adicionar verificação de nulos](../ide/media/vside-refactoring-nullcheck.png)

### <a name="constructor-generator-improvements"></a>Aperfeiçoamentos do gerador de construtor
Quando você está criando um construtor, essa ação rápida permite selecionar as propriedades ou os campos a serem gerados ou você pode gerar o construtor com base em um corpo vazio. Você também pode usá-lo para adicionar parâmetros a um construtor existente do site de chamada. (Disponível apenas no Visual Studio 2017 (versão 15.3 - versão prévia)).

![Refatoração - gerar construtores](../ide/media/vside-refactoring-constructors.png)

### <a name="remove-unused-variables"></a>Remover variáveis não utilizadas
Essa Ação Rápida permite remover variáveis que foram declaradas, mas nunca foram usadas no código. (Disponível apenas no Visual Studio 2017 (versão 15.3 - versão prévia)).

![Refatoração - variáveis não utilizadas](../ide/media/vside-refactoring-unusedvars.png)

### <a name="generate-overrides"></a>Gerar substituições
Essa Ação Rápida permite que você crie uma substituição de uma linha em branco em uma classe ou estrutura. A caixa de diálogo **Escolher Membros** permite que você escolha os membros a serem substituídos. (Disponível apenas no Visual Studio 2017 (versão 15.3 - versão prévia)).

![Refatoração - substituições](../ide/media/vside-refactoring-overrides.png)

![Refatoração - caixa de diálogo de substituições](../ide/media/vside-refactoring-overrides-dialog.png)

### <a name="change-base-for-numeric-literals"></a>Alterar base para literais numéricas
Essa Ação Rápida permite que você converta um literal numérico de um sistema numérico base para outro. Por exemplo, você pode alterar um número para hexadecimal ou formato binário. (Disponível apenas no Visual Studio 2017 (versão 15.3 - versão prévia)).

![Refatoração - alterar base](../ide/media/vside-refactoring-changebase1.png)

![Refatoração - alterar base](../ide/media/vside-refactoring-changebase2.png)

### <a name="insert-digit-separators-into-literals"></a>Inserir separadores de dígitos em literais
Essa Ação Rápida permite que você adicione caracteres separadores em valores literais. (Disponível apenas no Visual Studio 2017 (versão 15.3 - versão prévia)).

![Refatoração - alterar separadores de dígitos](../ide/media/vside-refactoring-separators.png)

### <a name="convert-if-construct-to-switch"></a>Converter construtor **se** para **alternar**
Essa Ação Rápida permite que você converta um construtor **if-then-else** em um construtor **switch**. (Disponível apenas no Visual Studio 2017 (versão 15.3 - versão prévia)).

```csharp
// Before
if (obj is string s)
{
  Console.WriteLine("obj is a string: " + s);  
}

else if (obj is int i && i > 10)
{
  Console.WriteLine("obj is an int greater than 10");
}

// Convert to switch

// After
switch (obj)
{
  case string s:
    Console.WriteLine("Obj is a string: " + s);
    break;
  case int i when i > 10:
    Console.WriteLine("obj is an int greater than 10");
    break;
}
```
```vb
' Before
If TypeOf obj Is String s Then
    Console.WriteLine("obj is a string: " + s)
Else If TypeOf obj Is Integer i And i > 10 Then
    Console.WriteLine("obj is an int greater than 10")
End If

' Convert to switch

' After
Select Case obj
  Case String s
    Console.WriteLine("Obj is a string: " + s)
    Exit Sub
  Case Integer i when i > 10
    Console.WriteLine("obj is an int greater than 10")
    Exit Sub
End Select
```

# <a name="see-also"></a>Consulte também
* [Estilos de código e ações rápidas](code-styles-and-quick-actions.md)

