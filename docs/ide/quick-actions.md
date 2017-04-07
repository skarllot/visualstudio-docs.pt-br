---
title: "Ações Rápidas | Microsoft Docs"
ms.custom: 
ms.date: 03/10/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.devlang: csharp
ms.assetid: e173fb7d-c5bd-4568-ba0f-aa61913b3244
author: BrianPeek
ms.author: brpeek
manager: ghogen
dev_langs:
- CSharp
- VB
translation.priority.ht:
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
translationtype: Human Translation
ms.sourcegitcommit: 46846db26bee30841e6cb35913d533b512d01ba0
ms.openlocfilehash: 226e51ace56d51945cc380aaaf3450ae7dacf8e4
ms.lasthandoff: 03/27/2017

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

```CSharp
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

```VB
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

```CSharp
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

```VB
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

```CSharp
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

```VB
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

```CSharp
// before
int number = (int)3;

// Remove Unnecessary Cast

// after
int number = 3;
```

```VB
' Before
Dim number as Integer = CType(3, Integer)

' Remove Unnecessary Cast

' After
Dim number as Integer = 3
```

### <a name="replace-method-with-property--replace-property-with-method"></a>Substituir método por propriedade/Substituir propriedade por método
Essas Ações Rápidas converterão um método em uma propriedade ou vice-versa.  O exemplo abaixo mostra a alteração de um método em uma propriedade.  Para o caso contrário, basta inverter as seções *Antes* e *Depois*.

```CSharp
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

```VB
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

```CSharp
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

```VB
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

```CSharp
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

```VB
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

```CSharp
// Before
Debug.WriteLine("Hello");

// using System.Diagnostics;

// After
using System.Diagnostics;

Debug.WriteLine("Hello");
```

```VB
' Before
Debug.WriteLine("Hello")

' Imports System.Diagnostics

// After
Imports System.Diagnostics

Debug.WriteLine("Hello")
```

### <a name="convert-to-interpolated-string"></a>Converter em Cadeia de Caracteres Interpolada
[Cadeias de caracteres interpoladas](/dotnet/articles/csharp/language-reference/keywords/interpolated-strings) são uma maneira fácil de expressar cadeias de caracteres com variáveis inseridas, semelhante ao método **[String.Format](https://msdn.microsoft.com/library/system.string.format(v=vs.110).aspx)**.  Essa Ação Rápida reconhecerá maiúsculas e minúsculas nas quais as cadeias de caracteres são concatenadas ou que usam **String.Format**, e alterará o uso de uma cadeia de caracteres interpolada.

```CSharp
// Before
int num = 3;
string s = string.Format("My string with {0} in the middle", num);

// Convert to interpolated string

// After
int num = 3;
string s = $"My string with {num} in the middle";
```

```VB
' Before
Dim num as Integer = 3
Dim s as String = String.Format("My string with {0} in the middle", num)

' Convert to interpolated string

' After
Dim num as Integer = 3
Dim s As String = $"My string with {num} in the middle"
```

# <a name="see-also"></a>Consulte também
* [Estilos de código e ações rápidas](code-styles-and-quick-actions.md)
