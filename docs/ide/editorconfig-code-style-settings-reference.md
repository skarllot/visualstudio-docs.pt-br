---
title: "Configurações de Conversão de Codificação .NET para o EditorConfig | Microsoft Docs"
ms.custom: 
ms.date: 12/14/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- CSharp
- VB
helpviewer_keywords:
- editor
ms.assetid: 
caps.latest.revision: 1
author: kaseyu
ms.author: kaseyu
manager: davidcsa
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
ms.translationtype: HT
ms.sourcegitcommit: 3037d92e9de377ab4b306a5a0e164e29fa6659e7
ms.openlocfilehash: 600cd62e7843274b52da5ac7200b5168311cab07
ms.contentlocale: pt-br
ms.lasthandoff: 08/08/2017

---

# <a name="net-coding-convention-settings-for-editorconfig"></a>Configurações de Conversão de Codificação .NET para o EditorConfig
As convenções de codificação .NET são configuradas usando um arquivo [EditorConfig](https://docs.microsoft.com/en-us/visualstudio/ide/create-portable-custom-editor-options). Os arquivos EditorConfig permitem **habilitar/desabilitar conversões de codificação .NET individuais** e **configurar o grau de imposição da conversão** (por meio de um nível de gravidade). Para saber mais sobre como usar o EditorConfig para impor a consistência em sua base de código, leia [este artigo](https://docs.microsoft.com/en-us/visualstudio/ide/create-portable-custom-editor-options).

Há três categorias de convenção de codificação .NET com suporte:
- As **[Convenções de Linguagem](#language)** são regras referentes à linguagem C# ou Visual Basic, por exemplo, `var`/tipo explícito, usam um membro de expressão incorporada.
- As **[Regras de Formatação](#formatting)** são regras referentes ao layout e estrutura do seu código para facilitar a leitura, por exemplo, chaves (Allman), espaços nos blocos de controle.
- As **[Convenções de Nomenclatura](#naming)** são regras que respeitam a forma como os objetos são nomeados, por exemplo, os métodos `async` devem terminar com "Async". 

# <a name="language">Convenções de Linguagem</a>
## <a name="overview"></a>Visão Geral
**Formatação de Regra:**
`options_name = false|true : none|suggestion|warning|error`

Para a opção de estilo de código, é necessário especificar **true** (prefira essa opção) ou **false** (não prefira essa opção), dois-pontos (`:`) e uma gravidade (`none`, `silent`, `suggestion`, `warning` ou `error`). Gravidade significa que o nível de imposição desse estilo que você deseja em sua base de código.

`none` e `silent` são sinônimos e significam que nenhuma indicação de nenhum tipo deve ser mostrada para o usuário. Isso tem o efeito de desabilitar essa regra.

Severidade | efeito
------------ | -------------
nenhum/silencioso | Não mostre nada ao usuário quando esse estilo não estiver sendo seguido. No entanto, os recursos de geração de código serão gerados nesse estilo. 
sugestão | Quando esse estilo não estiver sendo seguido, mostre-o para o usuário como uma sugestão (pontos subjacentes nos dois primeiros caracteres).
aviso | Quando esse estilo não estiver sendo seguido, mostre um aviso do compilador.
erro | Quando esse estilo não estiver sendo seguido, mostre um erro do compilador.

## <a name="net-language-convention-options"></a>Opções de Convenção de Linguagem .NET

- **[Configurações de Estilo de Código .NET](#this_and_me)**
    - ["This." e "Me." Qualificação](#this_and_me)
        - [Campos](#this_and_me_fields)
        - [Propriedades](#this_and_me_properties)
        - [Métodos](#this_and_me_methods)
        - [Eventos](#this_and_me_events)
    - [Palavras-chave de linguagens (int, string, etc.) vs nomes de tipos de estrutura para referências de tipo](#language_keywords)
        - [Locais, parâmetros e membros](#language_keywords_variables)
        - [Expressões de acesso de membro](#language_keywords_member_access)
    - [Preferências de nível de expressão](#expression_level)
        - [Inicializadores de objeto](#expression_level_object_initializers)
        - [Inicializadores de coleção](#expression_level_collection_initializers)
        - [Nomes de tupla explícita](#expression_level_tuple_names)
        - [Unindo expressões em verificação "null"](#expression_level_null_checking)
        - [Propagação nula na verificação "null"](#expression_level_null_propogation)
- **[Configurações de Estilo de Código CSharp](#csharp_codestyle)**
    - ["var"](#var)
        - ["var" para tipos internos](#var_built_in)
        - ["var" quando o tipo é aparente](#var_apparent)
        - ["var" em qualquer lugar](#var_elsewhere)
    - [Membros de expressão incorporada](#expression_body)
        - [Métodos](#expression_bodied_members_methods)
        - [Construtores](#expression_bodied_members_constructors)
        - [Operadores](#expression_bodied_members_operators)
        - [Propriedades](#expression_bodied_members_properties)
        - [Indexadores](#expression_bodied_members_indexers)
        - [Acessadores](#expression_bodied_members_accessors)
    - [Correspondência de padrões](#pattern_matching)
        - [verificação "is" com "cast"](#pattern_matching_is_cast)
        - [Verificação "as" com "null"](#pattern_matching_as_null)
    - [Declarações de variável embutida](#inlined_variable_declarations)
    - [Preferências de Nível de Expressão](#expression_level_csharp) -[Simplificar expressões `default`](#expression_level_default)
    - [Preferências da verificação "null"](#null_checking)
        - [Expressões throw](#null_checking_throw_expressions)
        - [Chamadas de delegados condicionais](#null_checking_conditional_delegate_calls)

## <a name="this_and_me">"This." e "Me." Qualificação</a>
### <a name="this_and_me_fields">Campos (IDE0003/IDE0009)</a>
|  Nome da opção | `dotnet_style_qualification_for_field` |
| ------------- |:-------------:|
| **Linguagens aplicáveis** | C# e Visual Basic

| Valor | Descrição | Aplicada 
| ------------- |:-------------|:-------------|
| verdadeiro | Preferir que todos os campos não estáticos usados em métodos não estáticos sejam antecedidos por `this.` em C# ou `Me.` no Visual Basic. | **C#:** <br>`this.capacity = 0;` <br><br> **Visual Basic:** <br> `Me.capacity = 0`
| False | Preferir que todos os campos não estáticos usados em métodos não estáticos não sejam antecedidos por `this.` em C# ou `Me.` no Visual Basic. | **C#:** <br>`capacity = 0;` <br><br> **Visual Basic:** <br>`capacity = 0`

#### <a name="example-editorconfig-file"></a>Exemplo de arquivo editorconfig:
```
# CSharp and VisualBasic code style settings:
[*.cs,*.vb]
dotnet_style_qualification_for_field = false:suggestion
```

### <a name="this_and_me_properties">Propriedades (IDE0003/IDE0009) </a>

|  Nome da opção | `dotnet_style_qualification_for_property` |
| ------------- |:-------------:|
| **Linguagens aplicáveis** | C# e Visual Basic

| Valor | Descrição | Aplicada 
| ------------- |:-------------|:-------------|
| verdadeiro | Preferir que todas as propriedades não estáticas usadas em métodos não estáticos sejam antecedidas por `this.` em C# ou `Me.` no Visual Basic.| **C#:** <br>`this.ID = 0;` <br><br> **Visual Basic:** <br>`Me.ID = 0`
| False | Preferir que todas as propriedades não estáticas usadas em métodos não estáticos *não* sejam antecedidas por `this.` em C# ou `Me.` no Visual Basic. | **C#:** <br>`ID = 0;` <br><br> **Visual Basic:** <br> `ID = 0`

#### <a name="example-editorconfig-file"></a>Exemplo de arquivo editorconfig:
```
# CSharp and VisualBasic code style settings:
[*.cs,*.vb]
dotnet_style_qualification_for_property = false:suggestion
```

### <a name="this_and_me_methods">Métodos (IDE0003/IDE0009) </a>
|  Nome da opção | `dotnet_style_qualification_for_method` |
| ------------- |:-------------:|
| **Linguagens aplicáveis** | C# e Visual Basic

| Valor | Descrição | Aplicada 
| ------------- |:-------------|:-------------|
| verdadeiro | Prefira que todos os métodos não estáticos chamados de dentro de métodos não estáticos sejam antecedidos por `this.` em C# e `Me.` no VB.| **C#:** <br>`this.Display();` <br><br> **Visual Basic:** <br> `Me.Display()`
| False | Prefira que todos os métodos não estáticos chamados de dentro de métodos não estáticos *não* sejam antecedidos por `this.` em C# e `Me.` no VB. | **C#:** <br>`Display();` <br><br> **Visual Basic:** <br> `Display()`


#### <a name="example-editorconfig-file"></a>Exemplo de arquivo editorconfig:
```
# CSharp and VisualBasic code style settings:
[*.cs, *.vb]
dotnet_style_qualification_for_method = false:suggestion
```

### <a name="this_and_me_events">Eventos (IDE0003/IDE0009) </a>
|  Nome da opção | `dotnet_style_qualification_for_event` |
| ------------- |:-------------:|
| **Linguagens aplicáveis** | C# e Visual Basic

| Valor | Descrição | Aplicada 
| ------------- |:-------------|:-------------|
| verdadeiro | Prefira que todos os eventos não estáticos referenciados de dentro de métodos não estáticos sejam antecedidos por `this.` em C# e `Me.` no VB.| **C#:** <br>`this.Elapsed += Handler;` <br><br> **Visual Basic:** <br> `AddHandler Me.Elapsed, AddressOf Handler`
| False | Prefira que todos os eventos não estáticos referenciados de dentro de métodos não estáticos *não* sejam antecedidos por `this.` em C# e `Me.` no VB. | **C#:** <br>`Elapsed += Handler;` <br><br> **Visual Basic:** <br>`AddHandler Elapsed, AddressOf Handler`

#### <a name="example-editorconfig-file"></a>Exemplo de arquivo editorconfig:
```
# CSharp and VisualBasic code style settings:
[*.cs, *.vb]
dotnet_style_qualification_for_event = false:suggestion
```

## <a name="language_keywords">Palavras-chave de linguagens (int, string, etc.) vs nomes de tipos de estrutura para referências de tipo </a>
### <a name="language_keywords_variables"> Locais, parâmetros e membros (IDE0012/IDE0014)</a>
|  Nome da opção | `dotnet_style_predefined_type_for_locals_parameters_members` |
| ------------- |:-------------:|
| **Linguagens aplicáveis** | C# e Visual Basic

| Valor | Descrição | Aplicada 
| ------------- |:-------------|:-------------|
| verdadeiro | Para membros locais, de parâmetros e de tipo, prefira tipos que têm uma palavra-chave de linguagem para representá-los (`int`, `double`, `float`, `short`, `long`, `decimal`, `string`) para usar a palavra-chave a usar o nome do tipo (`Int32`, `Int64`, etc.).| **C#:** <br>`private int _member;` <br><br> **Visual Basic:** `Private _member As Integer`
| False | Para membros locais, de parâmetros e de tipo, prefira tipos que têm uma palavra-chave de linguagem para representá-los (`int`, `double`, `float`, `short`, `long`, `decimal`, `string`) para usar o nome do tipo a usar a palavra-chave (`Int32`, `Int64`, etc.).  | **C#:** <br>`private Int32 _member;` <br><br> **Visual Basic:** <br> `Private _member As Int32`

#### <a name="example-editorconfig-file"></a>Exemplo de arquivo editorconfig:
```
# CSharp and VisualBasic code style settings:
[*.cs, *.vb]
dotnet_style_predefined_type_for_locals_parameters_members = true:suggestion
``` 

### <a name="language_keywords_member_access">Expressões de acesso de membro (IDE0013/IDE0015)</a>
|  Nome da opção | `dotnet_style_predefined_type_for_member_access` |
| ------------- |:-------------:|
| **Linguagens aplicáveis** | C# e Visual Basic

| Valor | Descrição | Aplicada 
| ------------- |:-------------|:-------------|
| verdadeiro | Prefira a palavra-chave sempre que uma expressão de acesso de membro for usada em um tipo com uma representação de palavra-chave (`int`, `double`, `float`, `short`, `long`, `decimal`, `string`).| **C#:** <br>`var local = int.MaxValue;` <br><br> **Visual Basic:** <br> `Dim local = Integer.MaxValue`
| False | Prefira o nome do tipo sempre que uma expressão de acesso de membro for usada em um tipo com uma representação de palavra-chave (`int`, `double`, `float`, `short`, `long`, `decimal`, `string`). | **C#:** <br>`var local = Int32.MaxValue;` <br><br> **Visual Basic:** <br> `Dim local = Int32.MaxValue`

#### <a name="example-editorconfig-file"></a>Exemplo de arquivo editorconfig:
```
# CSharp and VisualBasic code style settings:
[*.cs, *.vb]
dotnet_style_predefined_type_for_member_access = true:suggestion
``` 

## <a name="expression_level">Preferências de nível de expressão</a>
### <a name="expression_level_object_initializers">Inicializadores de objeto (IDE0017)</a>
|  Nome da opção | `dotnet_style_object_initializer` |
| ------------- |:-------------:|
| **Linguagens aplicáveis** | C# e Visual Basic

| Valor | Descrição | Aplicada 
| ------------- |:-------------|:-------------|
| verdadeiro | Prefira que objetos sejam inicializados usando inicializadores de objeto quando possível.| **C#:** <br>`var c = new Customer(){ Age = 21 };` <br><br> **Visual Basic:** <br> `Dim c = New Customer() With { .Age = 21 }`
| False | Prefira que objetos *não* sejam inicializados usando inicializadores de objeto. | **C#:** <br>`var c = new Customer();`<br>`c.Age = 21;` <br><br> **Visual Basic:** <br>`Dim c = new Customer() `<br>`c.Age = 21`

#### <a name="example-editorconfig-file"></a>Exemplo de arquivo editorconfig:
```
# CSharp and VisualBasic code style settings:
[*.cs, *.vb]
dotnet_style_object_initializer = true:suggestion
``` 

### <a name="expression_level_collection_initializers">Inicializadores de coleção (IDE0028)</a>
|  Nome da opção | `dotnet_style_collection_initializer` |
| ------------- |:-------------:|
| **Linguagens aplicáveis** | C# e Visual Basic

| Valor | Descrição | Aplicada 
| ------------- |:-------------|:-------------|
| verdadeiro | Prefira que coleções sejam inicializadas usando inicializadores de coleção quando possível.| **C#:** <br>`var list = new List<int>{ 1, 2, 3 };` <br><br> **Visual Basic:** <br> `Dim list = new List(Of Integer) From { 1, 2, 3}`
| False | Prefira que objetos *não* sejam inicializados usando inicializadores de coleção. | **C#:** <br>`var list = new List<int>();`<br>`list.Add(1);`<br>`list.Add(2);`<br>`list.Add(3);` <br><br> **Visual Basic:** <br>`Dim list = new List(Of Integer)`<br>`list.Add(1)`<br>`list.Add(2)`<br>`list.Add(3)`

#### <a name="example-editorconfig-file"></a>Exemplo de arquivo editorconfig:
```
# CSharp and VisualBasic code style settings:
[*.cs, *.vb]
dotnet_style_collection_initializer = true:suggestion
```

### <a name="expression_level_tuple_names">Nomes de tupla explícita (IDE0033)</a>
|  Nome da opção | `dotnet_style_explicit_tuple_names` |
| ------------- |:-------------:|
| **Linguagens aplicáveis** | C# 7.0+ e Visual Basic 15+

| Valor | Descrição | Aplicada 
| ------------- |:-------------|:-------------|
| verdadeiro | Prefira nomes de tupla a propriedades ItemX.| **C#:** <br>`(string name, int age) customer = GetCustomer();`<br>`var name = customer.name;` <br><br> **Visual Basic:** <br> `Dim customer As (name As String, age As Integer) = GetCustomer()`<br>`Dim name = customer.name`
| False | Prefira propriedades ItemX a nomes de tupla. | **C#:** <br>`(string name, int age) customer = GetCustomer();`<br>`var name = customer.Item1;` <br><br> **Visual Basic:** <br>`Dim customer As (name As String, age As Integer) = GetCustomer()`<br> `Dim name = customer.Item1`

#### <a name="example-editorconfig-file"></a>Exemplo de arquivo editorconfig:
```
# CSharp and VisualBasic code style settings:
[*.cs, *.vb]
dotnet_style_explicit_tuple_names = true:suggestion
``` 

### <a name="expression_level_null_checking">Unindo expressões em verificação "null" (IDE0029)</a>
|  Nome da opção | `dotnet_style_coalesce_expression` |
| ------------- |:-------------:|
| **Linguagens aplicáveis** | C# e Visual Basic

| Valor | Descrição | Aplicada 
| ------------- |:-------------|:-------------|
| verdadeiro | Prefira expressão de união nula a verificação do operador ternário.| **C#:** <br>`var v = x ?? y;` <br><br> **Visual Basic:** <br> `Dim v = If(x, y)`
| False | Prefira verificação do operador ternário a expressão de união nula. | **C#:** <br>`var v = x != null ? x : y; // or`<br>`var v = x == null ? y : x;` <br><br> **Visual Basic:** <br>`Dim v = If(x Is Nothing, y, x) ' or`<br> `Dim v = If(x IsNot Nothing, x, y)`

#### <a name="example-editorconfig-file"></a>Exemplo de arquivo editorconfig:
```
# CSharp and VisualBasic code style settings:
[*.cs, *.vb]
dotnet_style_coalesce_expression = true:suggestion
``` 

### <a name="expression_level_null_propogation">Propagação nula na verificação "null" (IDE0031)</a>
|  Nome da opção | `dotnet_style_null_propagation` |
| ------------- |:-------------:|
| **Linguagens aplicáveis** | C# e Visual Basic

| Valor | Descrição | Aplicada 
| ------------- |:-------------|:-------------|
| verdadeiro | Prefira usar o operador condicional nulo sempre que possível.| **C#:** <br>`var v = o?.ToString();` <br><br> **Visual Basic:** <br> `Dim v = o?.ToString()`
| False | Prefira usar verificação nula ternária quando possível. | **C#:** <br>`var v = o == null ? null : o.ToString(); // or`<br>`var v = o != null ? o.String() : null;` <br><br> **Visual Basic:** <br>`Dim v = If(o Is Nothing, Nothing, o.ToString()) ' or`<br> `Dim v = If(o IsNot Nothing, o.ToString(), Nothing)`

#### <a name="example-editorconfig-file"></a>Exemplo de arquivo editorconfig:
```
# CSharp and VisualBasic code style settings:
[*.cs, *.vb]
dotnet_style_null_propagation = true:suggestion
``` 

# <a name="csharp_codestyle">Configurações de estilo de código CSharp</a>
## <a name="var">"var" e Tipos Explícitos</a>
### <a name="var_built_in">"var" para tipos internos (IDE0007, IDE0008)</a>
|  Nome da opção | `csharp_style_var_for_built_in_types` |
| ------------- |:-------------:|
| **Linguagens aplicáveis** | C#

| Valor | Descrição | Aplicada 
| ------------- |:-------------|:-------------|
| verdadeiro | Prefira que `var` seja usado para tipos de sistemas internos, como `int`.| **C#:** <br>`var x = 5;`
| False | Prefira que `var` não seja usado para tipos de sistemas internos, como `int`. | **C#:** <br>`int x = 5;`

#### <a name="example-editorconfig-file"></a>Exemplo de arquivo editorconfig:
```
# CSharp code style settings:
[*.cs]
csharp_style_var_for_built_in_types = true:suggestion
``` 

### <a name="var_apparent">"var" quando o tipo é aparente (IDE0007, IDE0008)</a>
|  Nome da opção | `csharp_style_var_when_type_is_apparent` |
| ------------- |:-------------:|
| **Linguagens aplicáveis** | C#

| Valor | Descrição | Aplicada 
| ------------- |:-------------|:-------------|
| verdadeiro | Prefira `var` quando o tipo já tiver sido mencionado no lado direito de uma expressão de declaração.| **C#:** <br>`var obj = new C();`
| False | Prefira não usar `var` quando o tipo já tiver sido mencionado no lado direito de uma expressão de declaração. | **C#:** <br>`C obj = new C();`

#### <a name="example-editorconfig-file"></a>Exemplo de arquivo editorconfig:
```
# CSharp code style settings:
[*.cs]
csharp_style_var_when_type_is_apparent = true:suggestion
``` 

### <a name="var_elsewhere">"var" em outro lugar (IDE0007, IDE0008) </a>
|  Nome da opção | `csharp_style_var_elsewhere` |
| ------------- |:-------------:|
| **Linguagens aplicáveis** | C#

| Valor | Descrição | Aplicada 
| ------------- |:-------------|:-------------|
| verdadeiro | Prefira `var` em todos os casos, exceto se substituído por outra regra de estilo de código.| **C#:** <br>`var f = this.Init();`
| False | Prefira não usar var em todos os casos, exceto se substituído por outra regra de estilo de código.| **C#:** <br>`bool f = this.Init();`

#### <a name="example-editorconfig-file"></a>Exemplo de arquivo editorconfig:
```
# CSharp code style settings:
[*.cs]
csharp_style_var_elsewhere = true:suggestion
``` 

##<a name="expression_bodied_members">Membros aptos para expressão</a>
### <a name="expression_bodied_members_methods">Métodos (IDE0022)</a>
|  Nome da opção | `csharp_style_expression_bodied_methods` |
| ------------- |:-------------:|
| **Linguagens aplicáveis** | C# 6.0+

| Valor | Descrição | Aplicada 
| ------------- |:-------------|:-------------|
| verdadeiro | Prefira membros de expressão incorporada para métodos.| **C#:** <br>`public int GetAge() => this.Age;`
| False | Não prefira membros de expressão incorporada para métodos.| **C#:** <br>`public int GetAge() { return this.Age; }`

#### <a name="example-editorconfig-file"></a>Exemplo de arquivo editorconfig:
```
# CSharp code style settings:
[*.cs]
csharp_style_expression_bodied_methods = false:none
``` 

### <a name="expression_bodied_members_constructors">Construtores (IDE0021)</a>
|  Nome da opção | `csharp_style_expression_bodied_constructors` |
| ------------- |:-------------:|
| **Linguagens aplicáveis** | C# 6.0+

| Valor | Descrição | Aplicada 
| ------------- |:-------------|:-------------|
| verdadeiro | Prefira membros de expressão incorporada para construtores.| **C#:** <br>`public Customer(int age) => Age = age;`
| False | Não prefira membros de expressão incorporada para construtores.| **C#:** <br>`public Customer(int age) { Age = age; }`

#### <a name="example-editorconfig-file"></a>Exemplo de arquivo editorconfig:
```
# CSharp code style settings:
[*.cs]
csharp_style_expression_bodied_constructors = false:none
``` 

### <a name="expression_bodied_members_operators">Operadores (IDE0023, IDE0024)</a>
|  Nome da opção | `csharp_style_expression_bodied_operators` |
| ------------- |:-------------:|
| **Linguagens aplicáveis** | C# 6.0+

| Valor | Descrição | Aplicada 
| ------------- |:-------------|:-------------|
| verdadeiro | Prefira membros de expressão incorporada para operadores.| **C#:** <br>`public static ComplexNumber operator +(ComplexNumber c1, ComplexNumber c2)`<br>`=> new ComplexNumber(c1.Real + c2.Real, c1.Imaginary + c2.Imaginary);`
| False | Não prefira membros de expressão incorporada para operadores.| **C#:** <br>`public static ComplexNumber operator +(ComplexNumber c1, ComplexNumber c2)`<br>`{ return new ComplexNumber(c1.Real + c2.Real, c1.Imaginary + c2.Imaginary); }`

#### <a name="example-editorconfig-file"></a>Exemplo de arquivo editorconfig:
```
# CSharp code style settings:
[*.cs]
csharp_style_expression_bodied_operators = false:none
``` 

### <a name="expression_bodied_members_properties">Propriedades (IDE0025)</a>
|  Nome da opção | `csharp_style_expression_bodied_properties` |
| ------------- |:-------------:|
| **Linguagens aplicáveis** | C# 7.0+

| Valor | Descrição | Aplicada 
| ------------- |:-------------|:-------------|
| verdadeiro | Prefira membros de expressão incorporada para propriedades.| **C#:** <br>`public int Age => _age;`
| False | Não prefira membros de expressão incorporada para propriedades.| **C#:** <br>`public int Age { get { return _age; }}`

#### <a name="example-editorconfig-file"></a>Exemplo de arquivo editorconfig:
```
# CSharp code style settings:
[*.cs]
csharp_style_expression_bodied_properties = false:none
``` 

### <a name="expression_bodied_members_indexers">Indexadores (IDE0026)</a>
|  Nome da opção | `csharp_style_expression_bodied_indexers` |
| ------------- |:-------------:|
| **Linguagens aplicáveis** | C# 7.0+

| Valor | Descrição | Aplicada 
| ------------- |:-------------|:-------------|
| verdadeiro | Prefira membros de expressão incorporada para indexadores.| **C#:** <br>`public T this[int i] => _value[i];`
| False | Não prefira membros de expressão incorporada para indexadores.| **C#:** <br>`public T this[int i] { get { return _values[i]; } }`

#### <a name="example-editorconfig-file"></a>Exemplo de arquivo editorconfig:
```
# CSharp code style settings:
[*.cs]
csharp_style_expression_bodied_indexers = false:none
``` 

### <a name="expression_bodied_members_accessors">Acessadores (IDE0027)</a>
|  Nome da opção | `csharp_style_expression_bodied_accessors` |
| ------------- |:-------------:|
| **Linguagens aplicáveis** | C# 7.0+

| Valor | Descrição | Aplicada 
| ------------- |:-------------|:-------------|
| verdadeiro | Prefira membros de expressão incorporada para acessadores.| **C#:** <br>`public int Age { get => _age; set => _age = value; }`
| False | Não prefira membros de expressão incorporada para acessadores.| **C#:** <br>`public int Age { get { return _age; } set { _age = value; } }`

#### <a name="example-editorconfig-file"></a>Exemplo de arquivo editorconfig:
```
# CSharp code style settings:
[*.cs]
csharp_style_expression_bodied_accessors = false:none
``` 

## <a name="pattern_matching">Correspondência de padrões</a>
### <a name="pattern_matching_is_cast">Verificação "is" com "cast" (IDE0020)</a>
|  Nome da opção | `csharp_style_pattern_matching_over_is_with_cast_check` |
| ------------- |:-------------:|
| **Linguagens aplicáveis** | C# 7.0+

| Valor | Descrição | Aplicada 
| ------------- |:-------------|:-------------|
| verdadeiro | Prefira a correspondência de padrões a expressões `is` com conversões de tipo.| **C#:** <br>`if (o is int i) {...}`
| False | Prefira expressões `is` com conversões de tipo a correspondência de padrões.| **C#:** <br>`if (o is int) {var i = (int)o; ... }`

#### <a name="example-editorconfig-file"></a>Exemplo de arquivo editorconfig:
```
# CSharp code style settings:
[*.cs]
csharp_style_pattern_matching_over_is_with_cast_check = true:suggestion
```

### <a name="pattern_matching_as_null">Verificação "as" com "null" (IDE0019)</a>
|  Nome da opção | `csharp_style_pattern_matching_over_as_with_null_check` |
| ------------- |:-------------:|
| **Linguagens aplicáveis** | C# 7.0+

| Valor | Descrição | Aplicada 
| ------------- |:-------------|:-------------|
| verdadeiro | Prefira correspondência de padrões a expressões `as` com verificações nulas para determinar se algo é de um tipo específico.| **C#:** <br>`if (o is string s) {...}`
| False | Prefira expressões `as` com verificações de null a correspondência de padrões para determinar se algo é de um tipo específico.| **C#:** <br>`var s = o as string; if (s != null) {...}`

#### <a name="example-editorconfig-file"></a>Exemplo de arquivo editorconfig:
```
# CSharp code style settings:
[*.cs]
csharp_style_pattern_matching_over_as_with_null_check = true:suggestion
```

### <a name="inlined_variable_declarations">Declarações de variável embutida (IDE0018)</a>
|  Nome da opção | `csharp_style_inlined_variable_declaration` |
| ------------- |:-------------:|
| **Linguagens aplicáveis** | C#

| Valor | Descrição | Aplicada 
| ------------- |:-------------|:-------------|
| verdadeiro | Prefira que as variáveis `out` sejam declaradas embutidas quando possível. | **C#:** <br>`if (int.TryParse(value, out int i) {...}`
| False | Prefira que as variáveis `out` sejam declaradas explicitamente.| **C#:** <br>`int i; if (int.TryParse(value, out i) {...}`

#### <a name="example-editorconfig-file"></a>Exemplo de arquivo editorconfig:
```
# CSharp code style settings:
[*.cs]
csharp_style_inlined_variable_declaration = true:suggestion
```
## <a name="expression_level_csharp">Preferências de nível de expressão</a>
### <a name="expression_level_default">Simplificar expressões `default` (IDE0034) </a>
|  Nome da opção | `csharp_prefer_simple_default_expression` |
| ------------- |:-------------:|
| **Linguagens aplicáveis** | C# 7.1+ e Visual Basic

| Valor | Descrição | Aplicada 
| ------------- |:-------------|:-------------|
| verdadeiro | Prefira `default` a `default(T)` | **C#:** <br>`void DoWork(CancellationToken cancellationToken = default){ ... }`
| False | Prefira. | **C#:** <br>`void DoWork(CancellationToken cancellationToken = default(CancellationToken)){ ... }`

#### <a name="example-editorconfig-file"></a>Exemplo de arquivo editorconfig:
```
# CSharp and VisualBasic code style settings:
[*.cs]
csharp_prefer_simple_default_expression = true:suggestion
``` 

## <a name="null_checking">Preferências da verificação "null"</a>
### <a name="null_checking_throw_expressions">Expressões throw (IDE0016)</a>
|  Nome da opção | `csharp_style_throw_expression` |
| ------------- |:-------------:|
| **Linguagens aplicáveis** | C# 7.0+

| Valor | Descrição | Aplicada 
| ------------- |:-------------|:-------------|
| verdadeiro | Prefira usar expressões throw a usar instruções throw. | **C#:** <br>`this.s = ss ?? throw new ArgumentNullException(nameof(s));`
| False | Prefira usar instruções throw a usar expressões throw.| **C#:** <br>`if (s==null) {throw new ArgumentNullException(nameof(s));} this.s = s;`

#### <a name="example-editorconfig-file"></a>Exemplo de arquivo editorconfig:
```
# CSharp code style settings:
[*.cs]
csharp_style_throw_expression = true:suggestion
```

### <a name="null_checking_conditional_delegate_calls">Prefira chamadas de delegados condicionais (IDE0041)</a>
|  Nome da opção | `csharp_style_conditional_delegate_call` |
| ------------- |:-------------:|
| **Linguagens aplicáveis** | C#

| Valor | Descrição | Aplicada 
| ------------- |:-------------|:-------------|
| verdadeiro | Prefira usar a operação de união condicional (`?.`) ao invocar um lambda a executar uma verificação nula. | **C#:** <br>`func?.Invoke(args);`
| False | Prefira realizar uma verificação nula antes de invocar um lambda a usar o operador de união condicional (`?.`).| **C#:** <br>`if (func!=null) { func(args); }`

#### <a name="example-editorconfig-file"></a>Exemplo de arquivo editorconfig:
```
# CSharp code style settings:
[*.cs]
csharp_style_conditional_delegate_call = false:suggestion
```

# <a name="formatting"> Formatação de Regras </a>
## <a name="overview"></a>Visão Geral
**Formatação de Regra:**
`options_name = false|true`

Para opções de formatação, você deve especificar **true** (preferir esta opção) ou **false** (não preferir esta opção) exceto em alguns casos em que você deve especificar as condições às quais você deseja que a regra seja aplicada.

## <a name="net-formatting-options"></a>Opções de Formatação .NET

- **[Configurações de Formatação .NET](#usings)**
    - [Organizar Usos](#usings)
        - [Classificar as Diretivas do Sistema Primeiro](#usings_sort_system_first)
- **[Configurações de Formatação C#](#newline)**
    - [Opções de Nova Linha](#newline)
        - [Nova Linha Antes da Chave de Abertura (`{`)](#newline_before_brace)
        - [Nova Linha Antes `else`](#newline_before_else)
        - [Nova Linha Antes `catch`](#newline_before_catch)
        - [Nova Linha Antes `finally`](#newline_before_finally)
        - [Nova Linha Antes dos Membros em Inicializadores de Objetos](#newline_before_object)
        - [Nova Linha Antes dos Membros nos Tipos Anônimos](#newline_before_anonymous)
        - [Nova Linha Antes dos Membros em Cláusulas de Expressão de Consulta](#newline_before_query)
    - [Opções de Recuo](#indent)
        - [Recuar `switch` Conteúdo de Caso](#indent_switch)
        - [Posicionamento do Rótulo](#label)
    - [Opções de Espaçamento](#spacing)
        - [Espaço Após a Conversão](#space_after_cast)
        - [Espaço Após Palavras-chaves em Instruções de Fluxo de Controle](#space_control_flow)
        - [Espaço Entre Parênteses de Lista de Parâmetros de Declaração de Método](#space_parameter_list)
        - [Espaço Dentro dos Parênteses para a Lista de Argumentos de Chamada do Método](#space_method_call)
        - [Espaço Dentro dos Parênteses para Outras Opções](#space_other)
    - [Opções de Disposição](#wrapping)
        - [Deixar Instruções e Declarações de Membros na Mesma Linha](#wrapping_statement)
        - [Deixar Bloco em uma Linha Única](#wrapping_block)

## <a name="usings">Organizar Usos</a>
### <a name="usings_sort_system_first">Classificar as Diretivas do Sistema Primeiro</a>
|  Nome da opção | `dotnet_sort_system_directives_first` |
| ------------- |:-------------:|
| **Linguagens aplicáveis** | C# e Visual Basic

| Valor | Descrição | Aplicada 
| ------------- |:-------------|:-------------|
| verdadeiro | Classificar os usos do Sistema.* em ordem alfabética e colocá-los antes de outros usos.| **C#:** <br>`using System.Collections.Generic;`<br> `using System.Threading.Tasks;`<br> `using Octokit;`
| False | Não há nenhum requisito na classificação de usos | **C#:** <br>`using System.Collections.Generic;`<br> `using Octokit;` <br> `using System.Threading.Tasks;`

#### <a name="example-editorconfig-file"></a>Exemplo de arquivo editorconfig:
```
# .NET formatting settings:
[*.cs, *.vb]
dotnet_sort_system_directives_first = true
``` 

# <a name="csharp_formatting">Configurações de Formatação C#</a>
## <a name="newline">Opções de Nova Linha</a>
### <a name="newline_before_brace"> Nova Linha Antes da Chave de Abertura (`{`)</a>
|  Nome da opção | `csharp_new_line_before_open_brace` |
| ------------- |:-------------:|
| **Linguagens aplicáveis** | C#

| Valor | Descrição 
| ------------- |:-------------|
| acessadores, métodos_anônimos, tipos_anônimos, blocos_de_controle, eventos, indexadores, lambdas, funções_locais, métodos, coleção_de_objetos, propriedades, tipos. (Para várias, separe com ','). | Requer que as chaves estejam em uma nova linha para as expressões de determinadas (estilo Allman) |
| all | Requer que as chaves estejam em uma nova linha para todas as expressões (Allman) |
| nenhum | Requer que as chaves estejam na mesma linha para todas as expressões (K&R) |

#### <a name="applied"></a>Aplicado:
```csharp
// csharp_new_line_before_open_brace = all
void MyMethod() 
{
    if (...) 
    {
        ...
    }
}
```

```csharp
// csharp_new_line_before_open_brace = none
void MyMethod() {
    if (...) {
        ...
    }
}
```

#### <a name="example-editorconfig-file"></a>Exemplo de arquivo editorconfig:
```
# CSharp formatting settings:
[*.cs]
csharp_new_line_before_open_brace = methods, properties, control_blocks, types
``` 

### <a name="newline_before_else"> Nova Linha Antes `else`</a>
|  Nome da opção | `csharp_new_line_before_else` |
| ------------- |:-------------:|
| **Linguagens aplicáveis** | C#

| Valor | Descrição 
| ------------- |:-------------|
| verdadeiro | Insira as instruções `else` em uma nova linha.  |
| False | Insira as instruções `else` na mesma linha.  |

#### <a name="applied"></a>Aplicado:
```csharp
// csharp_new_line_before_else = true
if (...) {
    ...
}
else {
    ...
}
```

```csharp
// csharp_new_line_before_else = false
if (...) {
    ...
} else {
    ...
}
```

#### <a name="example-editorconfig-file"></a>Exemplo de arquivo editorconfig:
```
# CSharp formatting settings:
[*.cs]
csharp_new_line_before_else = true
``` 

### <a name="newline_before_catch"> Nova Linha Antes `catch`</a>
|  Nome da opção | `csharp_new_line_before_catch` |
| ------------- |:-------------:|
| **Linguagens aplicáveis** | C#

| Valor | Descrição 
| ------------- |:-------------|
| verdadeiro | Insira as instruções `catch` em uma nova linha.  |
| False | Insira as instruções `catch` na mesma linha. |

#### <a name="applied"></a>Aplicado:
```csharp
// csharp_new_line_before_catch = true
try {
    ...
}
catch (Exception e) {
    ...
}
```

```csharp
// csharp_new_line_before_catch = false
try {
    ...
} catch (Exception e) {
    ...
}
```

#### <a name="example-editorconfig-file"></a>Exemplo de arquivo editorconfig:
```
# CSharp formatting settings:
[*.cs]
csharp_new_line_before_catch = true
``` 

### <a name="newline_before_finally"> Nova Linha Antes `finally`</a>
|  Nome da opção | `csharp_new_line_before_catch` |
| ------------- |:-------------:|
| **Linguagens aplicáveis** | C#

| Valor | Descrição 
| ------------- |:-------------|
| verdadeiro | Exigir que as instruções `finally` estejam em uma nova linha após a chave de fechamento.  |
| False | Exigir que as instruções `finally` estejam na mesma linha como a chave de fechamento.  |

#### <a name="applied"></a>Aplicado:
```csharp
// csharp_new_line_before_finally = true
try {
    ...
}
catch (Exception e) {
    ...
}
finally {
    ...
}
```

```csharp
// csharp_new_line_before_finally = false
try {
    ...
} catch (Exception e) {
    ...
} finally {
    ...
}
```

#### <a name="example-editorconfig-file"></a>Exemplo de arquivo editorconfig:
```
# CSharp formatting settings:
[*.cs]
csharp_new_line_before_finally = true
``` 

### <a name="newline_before_object"> Nova Linha Antes dos Membros em Inicializadores de Objetos</a>
|  Nome da opção | `csharp_new_line_before_members_in_object_initializers` |
| ------------- |:-------------:|
| **Linguagens aplicáveis** | C#

| Valor | Descrição 
| ------------- |:-------------|
| verdadeiro | Exigir que membros dos inicializadores de objetos estejam em linhas separadas.  |
| False | Exigir que membros dos inicializadores de objetos estejam na mesma linha.  |

#### <a name="applied"></a>Aplicado:
```csharp
// csharp_new_line_before_members_in_object_initializers = true
var z = new B()
{
    A = 3,
    B = 4
}
```

```csharp
// csharp_new_line_before_members_in_object_initializers = false
var z = new B()
{
    A = 3, B = 4
}
```

#### <a name="example-editorconfig-file"></a>Exemplo de arquivo editorconfig:
```
# CSharp formatting settings:
[*.cs]
csharp_new_line_before_members_in_object_initializers = true
``` 

### <a name="newline_before_anonymous"> Nova Linha Antes dos Membros nos Tipos Anônimos</a>
|  Nome da opção | `csharp_new_line_before_members_in_anonymous_types` |
| ------------- |:-------------:|
| **Linguagens aplicáveis** | C#

| Valor | Descrição 
| ------------- |:-------------|
| verdadeiro | Exigir que membros de tipos anônimos estejam em linhas separadas.  |
| False | Exigir que membros de tipos anônimos estejam na mesma linha.  |

#### <a name="applied"></a>Aplicado:
```csharp
// csharp_new_line_before_members_in_anonymous_types = true
var z = new
{
    A = 3,
    B = 4
}
```

```csharp
// csharp_new_line_before_members_in_anonymous_types = false
var z = new
{
    A = 3, B = 4
}
```

#### <a name="example-editorconfig-file"></a>Exemplo de arquivo editorconfig:
```
# CSharp formatting settings:
[*.cs]
csharp_new_line_before_members_in_anonymous_types = true
``` 

### <a name="newline_before_query">Nova Linha Antes dos Membros em Cláusulas de Expressão de Consulta</a>
|  Nome da opção | `csharp_new_line_within_query_expression_clauses` |
| ------------- |:-------------:|
| **Linguagens aplicáveis** | C#

| Valor | Descrição 
| ------------- |:-------------|
| verdadeiro | Exigir que elementos das cláusulas de expressão de consulta estejam em linhas separadas.  |
| False | Exigir que elementos das cláusulas de expressão de consulta estejam na mesma linha.  |

#### <a name="applied"></a>Aplicado:
```csharp
// csharp_new_line_within_query_expression_clauses = true
var q = from a in e
        from b in e
        select a * b;
```

```csharp
// csharp_new_line_within_query_expression_clauses = false
var q = from a in e from b in e
        select a * b;
```

#### <a name="example-editorconfig-file"></a>Exemplo de arquivo editorconfig:
```
# CSharp formatting settings:
[*.cs]
csharp_new_line_within_query_expression_clauses = true
``` 

## <a name="indent">Opções de Recuo</a>
### <a name="indent_switch"> Recuar `switch` Conteúdo de Caso </a>
|  Nome da opção | `csharp_indent_case_contents` |
| ------------- |:-------------:|
| **Linguagens aplicáveis** | C#

| Valor | Descrição 
| ------------- |:-------------|
| verdadeiro | Recuar `switch` conteúdo de caso  |
| False | Não recuar `switch` conteúdo de caso |

#### <a name="applied"></a>Aplicado:
```csharp
// csharp_indent_case_contents = true
switch(c) {
    case Color.Red:
        Console.WriteLine("The color is red");
        break;
    case Color.Blue:
        Console.WriteLine("The color is blue");
        break;
    default:
        Console.WriteLine("The color is unknown.");
        break;
}
```

```csharp
// csharp_indent_case_contents = false
switch(c) {
    case Color.Red:
    Console.WriteLine("The color is red");
    break;
    case Color.Blue:
    Console.WriteLine("The color is blue");
    break;
    default:
    Console.WriteLine("The color is unknown.");
    break;
}
```

#### <a name="example-editorconfig-file"></a>Exemplo de arquivo editorconfig:
```
# CSharp formatting settings:
[*.cs]
csharp_indent_case_contents = true
``` 

### <a name="label">Posicionamento do Rótulo</a>
|  Nome da opção | `csharp_indent_labels` |
| ------------- |:-------------:|
| **Linguagens aplicáveis** | C#

| Valor | Descrição 
| ------------- |:-------------|
| one_less | Os rótulos são posicionados em um recuo a menos do que o contexto atual |
| no_change | Os rótulos são posicionados no mesmo recuo do contexto atual |

#### <a name="applied"></a>Aplicado:
```csharp
// csharp_indent_labels = one_less
private string MyMethod(...) 
{
    if (...) {
        goto error;
    }
error:
    throw new Exception(...);
}

```

```csharp
// csharp_indent_labels= no_change
private string MyMethod(...) 
{
    if (...) {
        goto error;
    }
    error:
    throw new Exception(...);
}
```

#### <a name="example-editorconfig-file"></a>Exemplo de arquivo editorconfig:
```
# CSharp formatting settings:
[*.cs]
csharp_indent_labels = one_less
``` 

## <a name="spacing">Opções de Espaçamento</a>
### <a name="space_after_cast"> Espaço Após a Conversão </a>
|  Nome da opção | `csharp_space_after_cast` |
| ------------- |:-------------:|
| **Linguagens aplicáveis** | C#

| Valor | Descrição | Aplicada |
| ------------- |:-------------|:-------------|
| verdadeiro | Requer um espaço entre uma conversão e o valor  | **C#:** <br>`int y = (int) x;`
| False | Não requer nenhum espaço entre a conversão e o valor | **C#:** <br>`int y = (int)x;`

#### <a name="example-editorconfig-file"></a>Exemplo de arquivo editorconfig:
```
# CSharp formatting settings:
[*.cs]
csharp_space_after_cast = true
``` 

### <a name="space_control_flow"> Espaço Após Palavras-chaves em Instruções de Fluxo de Controle </a>
|  Nome da opção | `csharp_space_after_keywords_in_control_flow_statements` |
| ------------- |:-------------:|
| **Linguagens aplicáveis** | C#

| Valor | Descrição | Aplicada |
| ------------- |:-------------|:-------------|
| verdadeiro | Requer um espaço após uma palavra-chave | **C#:** <br>`for (int i;i<x;i++) { ... }`
| False | Não requer nenhum espaço após uma palavra-chave | **C#:** <br>`for(int i;i<x;i++) { ... }`

#### <a name="example-editorconfig-file"></a>Exemplo de arquivo editorconfig:
```
# CSharp formatting settings:
[*.cs]
csharp_space_after_keywords_in_control_flow_statements = true
``` 

### <a name="space_parameter_list"> Espaço Entre Parênteses de Lista de Argumentos de Declaração de Método </a>
|  Nome da opção | `csharp_space_between_method_declaration_parameter_list_parentheses` |
| ------------- |:-------------:|
| **Linguagens aplicáveis** | C#

| Valor | Descrição | Aplicada |
| ------------- |:-------------|:-------------|
| verdadeiro | Requer um espaço após uma palavra-chave | **C#:** <br>`void Bark( int x ) { ... }`
| False | Não requer nenhum espaço após uma palavra-chave | **C#:** <br>`void Bark(int x) { ... }`

#### <a name="example-editorconfig-file"></a>Exemplo de arquivo editorconfig:
```
# CSharp formatting settings:
[*.cs]
csharp_space_between_method_declaration_parameter_list_parentheses = true
```

### <a name="space_method_call"> Espaço Dentro dos Parênteses para a Lista de Argumentos de Chamada do Método</a>
|  Nome da opção | `csharp_space_between_method_call_parameter_list_parentheses` |
| ------------- |:-------------:|
| **Linguagens aplicáveis** | C#

| Valor | Descrição | Aplicada |
| ------------- |:-------------|:-------------|
| true | Inserir espaço entre parênteses das instruções de fluxo de controle | **C#:** <br>`MyMethod( argument );`
| false | Inserir espaço entre os parênteses das expressões | **C#:** <br>`MyMethod(argument);`

#### <a name="example-editorconfig-file"></a>Exemplo de arquivo editorconfig:
```
# CSharp formatting settings:
[*.cs]
csharp_space_between_method_call_parameter_list_parentheses = control_flow_statements, type_casts
```  

### <a name="space_other"> Espaço Dentro dos Parênteses para Outras Opções </a>
|  Nome da opção | `csharp_space_between_parentheses` |
| ------------- |:-------------:|
| **Linguagens aplicáveis** | C#

| Valor | Descrição | Aplicada |
| ------------- |:-------------|:-------------|
| control_flow_statements | Inserir espaço entre parênteses das instruções de fluxo de controle | **C#:** <br>`for( int i;i<x;i++ ) { ... }`
| expressões | Inserir espaço entre os parênteses das expressões | **C#:** <br>`var z = ( x * y ) - ( ( y - x ) * 3);`
| type_casts | Inserir espaço entre os parênteses nas conversões de tipo | **C#:**<br>`int y = ( int )x;`

#### <a name="example-editorconfig-file"></a>Exemplo de arquivo editorconfig:
```
# CSharp formatting settings:
[*.cs]
csharp_space_between_parentheses = control_flow_statements, type_casts
``` 

## <a name="wrapping">Opções de Disposição</a>
### <a name="wrapping_statement">Deixar Instruções e Declarações de Membros na Mesma Linha</a>
|  Nome da opção | `csharp_preserve_single_line_statements` |
| ------------- |:-------------:|
| **Linguagens aplicáveis** | C#

| Valor | Descrição |
| ------------- |:-------------|
| verdadeiro | Deixar instruções e declarações de membros na mesma linha  | 
| False | Deixar instruções e declarações de membros em linhas diferentes | 

#### <a name="applied"></a>Aplicada
```csharp
//csharp_preserve_single_line_statements = true
int i = 0; string name = "John";
```

```csharp
//csharp_preserve_single_line_statements = false
int i = 0; 
string name = "John";
```

#### <a name="example-editorconfig-file"></a>Exemplo de arquivo editorconfig:
```
# CSharp formatting settings:
[*.cs]
csharp_preserve_single_line_statements = true
``` 

### <a name="wrapping_block">Deixar Bloco em uma Linha Única</a>
|  Nome da opção | `csharp_preserve_single_line_blocks` |
| ------------- |:-------------:|
| **Linguagens aplicáveis** | C#

| Valor | Descrição |
| ------------- |:-------------|
| verdadeiro | Deixar bloco em uma linha única | 
| False | Deixar bloco em linhas separadas | 

#### <a name="applied"></a>Aplicada
```csharp
//csharp_preserve_single_line_blocks = true
public int Foo { get; set; }
```

```csharp
//csharp_preserve_single_line_blocks = false
public int MyProperty
{ 
    get; set;
}
```

#### <a name="example-editorconfig-file"></a>Exemplo de arquivo editorconfig:
```
# CSharp formatting settings:
[*.cs]
csharp_preserve_single_line_blocks = true
``` 

# <a name="naming"> Convenções de Nomenclatura </a>
## <a name="overview"></a>Visão Geral
**Formatação de Regra:**<br>
namingRuleTitle:<br>
`dotnet_naming_rule.<namingRuleTitle>.symbols = <symbolTitle>`<br>
`dotnet_naming_rule.<namingRuleTitle>.style = <styleTitle>`<br>
`dotnet_naming_rule.<namingRuleTitle>.severity = none|suggestion|warning|error`<br>
<br>
symbolTitle:<br>
`dotnet_naming_symbols.<symbolTitle>.applicable_kinds = class, struct, interface, enum, property, method, field, event, namespace, delegate, type_parameter`<br>
`dotnet_naming_symbols.<symbolTitle>.applicable_accessibilities = public, internal, private, protected, protected_internal`<br>
`dotnet_naming_symbols.<symbolTitle>.required_modifiers = abstract, async, const, readonly, static`<br>
<br>
styleTitle:<br>
`dotnet_naming_style.<styleTitle>.capitalization = pascal_case|camel_case|first_word_upper|all_upper|all_lower`<br>
`dotnet_naming_style.<styleTitle>.required_prefix = string`<br>
`dotnet_naming_style.<styleTitle>.required_suffix = string`<br>
`dotnet_naming_style.<styleTitle>.word_separator = string`<br>

## <a name="writing-a-naming-convention"></a>Escrever Convenção de Nomenclatura
Para convenções de nomenclatura, especifique os **símbolos**, **estilo** e um **gravidade**. As convenções de nomenclatura devem ser ordenadas da mais específica à menos específica. A primeira regra encontrada que pode ser aplicada, será a única regra aplicada. 

### <a name="severity"></a>Severidade
Estas são opções válidas para a gravidade de uma regra de estilo de nomenclatura `none`, `silent`, `suggestion`, `warning`, `error`.

 `none` e `silent` são sinônimos e significam que nenhuma indicação de nenhum tipo deve ser mostrada para o usuário. Isso tem o efeito de desabilitar essa regra.

 `suggestion` significa que o usuário verá o seguinte em errorlist: e o seguinte no IDE. A gravidade da `suggetion` permitirá que a regra de nomenclatura seja executada, mas não causará uma falha na compilação.

Severidade | efeito
------------ | -------------
nenhum/silencioso | Não mostre nada ao usuário quando esse estilo não estiver sendo seguido. No entanto, os recursos de geração de código serão gerados nesse estilo. 
sugestão | Quando esse estilo não estiver sendo seguido, mostre-o para o usuário como uma sugestão (pontos subjacentes nos dois primeiros caracteres).
aviso | Quando esse estilo não estiver sendo seguido, mostre um aviso do compilador.
erro | Quando esse estilo não estiver sendo seguido, mostre um erro do compilador.

### <a name="symbol-specification"></a>Especificação de Símbolo
Identifique _quais_ símbolos _com que_ modificadores e _em qual_ nível de acessibilidade a regra de nomenclatura deve ser aplicada.

|  Nome da opção | `dotnet_naming_rule.<namingRuleTitle>.symbols` |
| ------------- |:-------------:|
|  | `dotnet_naming_symbols.<symbolTitle>.applicable_kinds`
|  | `dotnet_naming_symbols.<symbolTitle>.applicable_accessibilities`
|  | `dotnet_naming_symbols.<symbolTitle>.required_modifiers`

| Símbolo | Acessibilidade | Modificadores
| ------------- |------------- |------------- |
| `*` | `*` |  `abstract` | 
| `class` | `public` |  `must_inherit` | `async` | 
| `struct` | `internal` (C#) /  | `const` | 
| `interface` | `friend` (Visual Basic) | `readonly` | 
| `enum` | `private`  | `static` | 
| `property` | `protected` | `shared` |
| `method` |`protected_internal` (C#) | |
| `field` | `protected_friend` (Visual Basic) | |
| `event` | | |
| `delegate` | | |

#### <a name="example-editorconfig-file"></a>Exemplo de arquivo editorconfig:
```
# CSharp formatting settings:
[*.cs]
dotnet_naming_rule.async_methods_end_in_async.symbols = any_async_methods

dotnet_naming_symbols.any_async_methods.applicable_kinds = method
dotnet_naming_symbols.any_async_methods.applicable_accessibilities = *
dotnet_naming_symbols.any_async_methods.required_modifiers = async
``` 

### <a name="style-specification"></a>Especificação de Estilo
Identifique o estilo de nomenclatura para aplicar aos símbolos.

|  Nome da opção | `dotnet_naming_rule.<namingRuleTitle>.style = <styleTitle>` |
| ------------- |:-------------:|
|  | `dotnet_naming_style.<styleTitle>.capitalization`|
|  | `dotnet_naming_style.<styleTitle>.required_prefix`|
|  | `dotnet_naming_style.<styleTitle>.required_suffix`|
|  | `dotnet_naming_style.<styleTitle>.word_separator`|


| Estilo | Descrição |
| ------------- |:-------------:|
| Prefixo | Caracteres necessários que devem aparecer antes do identificador. |
| Sufixo | Caracteres necessários que devem aparecer após o identificador. |
| Separador de Palavras | Separador necessário entre as palavras no identificador. |
| Uso de maiúsculas |`pascal_case`, `camel_case`, `first_word_upper`, `all_upper`, `all_lower` | 

#### <a name="example-editorconfig-file"></a>Exemplo de arquivo editorconfig:
```
# CSharp formatting settings:
[*.cs]
dotnet_naming_rule.async_methods_end_in_async.style = end_in_async

dotnet_naming_style.end_in_async.required_suffix = Async
dotnet_naming_style.end_in_async.capitalization = pascal_case
``` 

### <a name="example-naming-convention"></a>Exemplo de Convenção de Nomenclatura
```
# CSharp formatting settings:
[*.cs]
dotnet_naming_rule.async_methods_end_in_async.symbols  = any_async_methods
dotnet_naming_rule.async_methods_end_in_async.style    = end_in_async
dotnet_naming_rule.async_methods_end_in_async.severity = suggestion

dotnet_naming_symbols.any_async_methods.applicable_kinds           = method
dotnet_naming_symbols.any_async_methods.applicable_accessibilities = *
dotnet_naming_symbols.any_async_methods.required_modifiers         = async

dotnet_naming_style.end_in_async.required_suffix = Async
dotnet_naming_style.end_in_async.capitalization  = pascal_case
``` 

