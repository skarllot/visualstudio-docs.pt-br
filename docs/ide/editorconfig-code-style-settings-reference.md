---
title: "Configurações de estilo de código .NET para Editorconfig | Microsoft Docs"
ms.custom: 
ms.date: 12/14/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- editor
ms.assetid: 
caps.latest.revision: 01
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
translationtype: Human Translation
ms.sourcegitcommit: 31f433b28b67dc6f3179be87cb5894b5b3f0aa4f
ms.openlocfilehash: e0fcd94f2e42f2ce8d454b9d754cfa4ad063d9e0
ms.lasthandoff: 02/22/2017

---

# <a name="net-code-style-settings-for-editorconfig"></a>Configurações de estilo de código .NET para Editorconfig

## <a name="possible-values"></a>Valores possíveis

`options_name = false|true : none|suggestion|warning|error`

Para a opção de estilo de código, é necessário especificar **true** (prefira essa opção) ou **false** (não prefira essa opção), dois-pontos (`:`) e uma gravidade (`none`, `suggestion`, `warning` ou `error`). Gravidade significa que o nível de imposição desse estilo que você deseja em sua base de código.

Severidade | efeito
------------ | -------------
nenhum | Não mostre nada ao usuário quando esse estilo não estiver sendo seguido. No entanto, os recursos de geração de código serão gerados nesse estilo. 
sugestão | Quando esse estilo não estiver sendo seguido, mostre-o para o usuário como uma sugestão (pontos subjacentes nos dois primeiros caracteres).
aviso | Quando esse estilo não estiver sendo seguido, mostre um aviso do compilador.
erro | Quando esse estilo não estiver sendo seguido, mostre um erro do compilador.

## <a name="net-code-style-options"></a>Opções de estilo de código .NET

- [Configurações de estilo de código Dotnet](#this_and_me)
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
- [Configurações de estilo de código CSharp](#csharp_codestyle)
    - ["var"](#var)
        - ["var" para tipos internos](#var_built_in)
        - ["var" quando o tipo é aparente](#var_apparent)
        - ["var" em qualquer lugar](#var_elsewhere)
    - [Membros de expressão incorporada](#expression_bodied_members)
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
    - [Preferências da verificação "null"](#null_checking)
        - [Expressões throw](#null_checking_throw_expressions)
        - [Chamadas de delegados condicionais](#null_checking_conditional_delegate_calls)

## <a name="a-namethisandmethis-and-me-qualificationa"></a><a name="this_and_me">"This." e "Me." Qualificação</a>

### <a name="a-namethisandmefieldsfieldsa"></a><a name="this_and_me_fields">Campos</a>

|  Nome da opção | `dotnet_style_qualification_for_field` |
| ------------- |:-------------:|
| **Linguagens aplicáveis** | C# e Visual Basic

| Valor | Descrição | Aplicada 
| ------------- |:-------------|:-------------|
| verdadeiro | Preferir que todos os campos não estáticos usados em métodos não estáticos sejam antecedidos por `this.` em C# ou `Me.` no Visual Basic. | **C#:** <br>`this.capacity = 0;` <br><br> **Visual Basic:** `Me.capacity = 0`
| False | Preferir que todos os campos não estáticos usados em métodos não estáticos não sejam antecedidos por `this.` em C# ou `Me.` no Visual Basic. | **C#:** <br>`capacity = 0;` <br><br> **Visual Basic:** `capacity = 0`

#### <a name="example-editorconfig-file"></a>Exemplo de arquivo editorconfig:
```
# CSharp and VisualBasic code style settings:
[*.cs,*.vb]
dotnet_style_qualification_for_field = false:suggestion
```

### <a name="a-namethisandmepropertiespropertiesa"></a><a name="this_and_me_properties">Propriedades</a>

|  Nome da opção | `dotnet_style_qualification_for_property` |
| ------------- |:-------------:|
| **Linguagens aplicáveis** | C# e Visual Basic

| Valor | Descrição | Aplicada 
| ------------- |:-------------|:-------------|
| verdadeiro | Preferir que todas as propriedades não estáticas usadas em métodos não estáticos sejam antecedidas por `this.` em C# ou `Me.` no Visual Basic.| **C#:** <br>`this.ID = 0;` <br><br> **Visual Basic:** `Me.ID = 0`
| False | Preferir que todas as propriedades não estáticas usadas em métodos não estáticos *não* sejam antecedidas por `this.` em C# ou `Me.` no Visual Basic. | **C#:** <br>`ID = 0;` <br><br> **Visual Basic:** `ID = 0`

#### <a name="example-editorconfig-file"></a>Exemplo de arquivo editorconfig:
```
# CSharp and VisualBasic code style settings:
[*.cs,*.vb]
dotnet_style_qualification_for_property = false:suggestion
```


### <a name="a-namethisandmemethodsmethodsa"></a><a name="this_and_me_methods">Métodos</a>
|  Nome da opção | `dotnet_style_qualification_for_method` |
| ------------- |:-------------:|
| **Linguagens aplicáveis** | C# e Visual Basic

| Valor | Descrição | Aplicada 
| ------------- |:-------------|:-------------|
| verdadeiro | Prefira que todos os métodos não estáticos chamados de dentro de métodos não estáticos sejam antecedidos por `this.` em C# e `Me.` no VB.| **C#:** <br>`this.Display();` <br><br> **Visual Basic:** `Me.Display()`
| False | Prefira que todos os métodos não estáticos chamados de dentro de métodos não estáticos *não* sejam antecedidos por `this.` em C# e `Me.` no VB. | **C#:** <br>`Display();` <br><br> **Visual Basic:** `Display()`


#### <a name="example-editorconfig-file"></a>Exemplo de arquivo editorconfig:
```
# CSharp and VisualBasic code style settings:
[*.cs, *.vb]
dotnet_style_qualification_for_method = false:suggestion
```

### <a name="a-namethisandmeeventseventsa"></a><a name="this_and_me_events">Eventos</a>
|  Nome da opção | `dotnet_style_qualification_for_event` |
| ------------- |:-------------:|
| **Linguagens aplicáveis** | C# e Visual Basic

| Valor | Descrição | Aplicada 
| ------------- |:-------------|:-------------|
| verdadeiro | Prefira que todos os eventos não estáticos referenciados de dentro de métodos não estáticos sejam antecedidos por `this.` em C# e `Me.` no VB.| **C#:** <br>`this.Elapsed += Handler;` <br><br> **Visual Basic:** `AddHandler Me.Elapsed, AddressOf Handler`
| False | Prefira que todos os eventos não estáticos referenciados de dentro de métodos não estáticos *não* sejam antecedidos por `this.` em C# e `Me.` no VB. | **C#:** <br>`Elapsed += Handler;` <br><br> **Visual Basic:** `AddHandler Elapsed, AddressOf Handler`

#### <a name="example-editorconfig-file"></a>Exemplo de arquivo editorconfig:
```
# CSharp and VisualBasic code style settings:
[*.cs, *.vb]
dotnet_style_qualification_for_event = false:suggestion
```

## <a name="language_keywords">Palavras-chave de linguagens (int, string, etc.) vs nomes de tipos de estrutura para referências de tipo </a>
### <a name="a-namelanguagekeywordsvariableslocals-parameters-and-membersa"></a><a name="language_keywords_variables">Locais, parâmetros e membros</a>
|  Nome da opção | `dotnet_style_predefined_type_for_locals_parameters_members` |
| ------------- |:-------------:|
| **Linguagens aplicáveis** | C# e Visual Basic

| Valor | Descrição | Aplicada 
| ------------- |:-------------|:-------------|
| verdadeiro | Para membros locais, de parâmetros e de tipo, prefira tipos que têm uma palavra-chave de linguagem para representá-los (`int`, `double`, `float`, `short`, `long`, `decimal`, `string`) para usar a palavra-chave a usar o nome do tipo (`Int32`, `Int64`, etc.).| **C#:** <br>`private int _member;` <br><br> **Visual Basic:** `Private _member As Integer`
| False | Para membros locais, de parâmetros e de tipo, prefira tipos que têm uma palavra-chave de linguagem para representá-los (`int`, `double`, `float`, `short`, `long`, `decimal`, `string`) para usar o nome do tipo a usar a palavra-chave (`Int32`, `Int64`, etc.).  | **C#:** <br>`private Int32 _member;` <br><br> **Visual Basic:** `Private _member As Int32`

#### <a name="example-editorconfig-file"></a>Exemplo de arquivo editorconfig:
```
# CSharp and VisualBasic code style settings:
[*.cs, *.vb]
dotnet_style_predefined_type_for_locals_parameters_members = true:suggestion
``` 

### <a name="a-namelanguagekeywordsmemberaccessmember-access-expressionsa"></a><a name="language_keywords_member_access">Expressões de acesso de membro</a>
|  Nome da opção | `dotnet_style_predefined_type_for_member_access` |
| ------------- |:-------------:|
| **Linguagens aplicáveis** | C# e Visual Basic

| Valor | Descrição | Aplicada 
| ------------- |:-------------|:-------------|
| verdadeiro | Prefira a palavra-chave sempre que uma expressão de acesso de membro for usada em um tipo com uma representação de palavra-chave (`int`, `double`, `float`, `short`, `long`, `decimal`, `string`).| **C#:** <br>`var local = int.MaxValue;` <br><br> **Visual Basic:** `Dim local = Integer.MaxValue`
| False | Prefira o nome do tipo sempre que uma expressão de acesso de membro for usada em um tipo com uma representação de palavra-chave (`int`, `double`, `float`, `short`, `long`, `decimal`, `string`). | **C#:** <br>`var local = Int32.MaxValue;` <br><br> **Visual Basic:** `Dim local = Int32.MaxValue`

#### <a name="example-editorconfig-file"></a>Exemplo de arquivo editorconfig:
```
# CSharp and VisualBasic code style settings:
[*.cs, *.vb]
dotnet_style_predefined_type_for_member_access = true:suggestion
``` 

## <a name="a-nameexpressionlevelexpression-level-preferencesa"></a><a name="expression_level">Preferências de nível de expressão</a>
### <a name="a-nameexpressionlevelobjectinitializersobject-initializersa"></a><a name="expression_level_object_initializers">Inicializadores de objeto</a>
|  Nome da opção | `dotnet_style_object_initializer` |
| ------------- |:-------------:|
| **Linguagens aplicáveis** | C# e Visual Basic

| Valor | Descrição | Aplicada 
| ------------- |:-------------|:-------------|
| verdadeiro | Prefira que objetos sejam inicializados usando inicializadores de objeto quando possível.| **C#:** <br>`var c = new Customer(){ Age = 21 };` <br><br> **Visual Basic:** `Dim c = New Customer() With { .Age = 21 }`
| False | Prefira que objetos *não* sejam inicializados usando inicializadores de objeto. | **C#:** <br>`var c = new Customer();`<br>`c.Age = 21;` <br><br> **Visual Basic:** <br>`Dim c = new Customer() `<br>`c.Age = 21`

#### <a name="example-editorconfig-file"></a>Exemplo de arquivo editorconfig:
```
# CSharp and VisualBasic code style settings:
[*.cs, *.vb]
dotnet_style_object_initializer = true:suggestion
``` 

### <a name="a-nameexpressionlevelcollectioninitializerscollection-initializersa"></a><a name="expression_level_collection_initializers">Inicializadores de coleção</a>
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

### <a name="a-nameexpressionleveltuplenamesexplicit-tuple-namesa"></a><a name="expression_level_tuple_names">Nomes de tupla explícita</a>
|  Nome da opção | `dotnet_style_explicit_tuple_names` |
| ------------- |:-------------:|
| **Linguagens aplicáveis** | C# e Visual Basic

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

### <a name="a-nameexpressionlevelnullcheckingcoalescing-expressions-in-null-checkinga"></a><a name="expression_level_null_checking">Unindo expressões em verificação "null"</a>
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

### <a name="a-nameexpressionlevelnullpropogationnull-propagation-in-null-checkinga"></a><a name="expression_level_null_propogation">Propagação nula na verificação "null"</a>
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

# <a name="a-namecsharpcodestylecsharp-code-style-settingsa"></a><a name="csharp_codestyle">Configurações de estilo de código CSharp</a>
## <a name="a-namevarvara"></a><a name="var">"var"</a>
### <a name="a-namevarbuiltinvar-for-built-in-typesa"></a><a name="var_built_in">"var" para tipos internos</a>
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

### <a name="a-namevarapparentvar-when-type-is-apparenta"></a><a name="var_apparent">"var" quando o tipo é aparente</a>
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

### <a name="a-namevarelsewherevar-elsewherea"></a><a name="var_elsewhere">"var" em qualquer lugar</a>
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

### <a name="a-nameexpressionbodiedmembersmethodsa"></a><a name="expression_bodied_members">Métodos</a>
|  Nome da opção | `csharp_style_expression_bodied_methods` |
| ------------- |:-------------:|
| **Linguagens aplicáveis** | C#

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

### <a name="a-nameexpressionbodiedmembersconstructorsconstructorsa"></a><a name="expression_bodied_members_constructors">Construtores</a>
|  Nome da opção | `csharp_style_expression_bodied_constructors` |
| ------------- |:-------------:|
| **Linguagens aplicáveis** | C#

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

### <a name="a-nameexpressionbodiedmembersoperatorsoperatorsa"></a><a name="expression_bodied_members_operators">Operadores</a>
|  Nome da opção | `csharp_style_expression_bodied_operators` |
| ------------- |:-------------:|
| **Linguagens aplicáveis** | C#

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

### <a name="a-nameexpressionbodiedmemberspropertiespropertiesa"></a><a name="expression_bodied_members_properties">Propriedades</a>
|  Nome da opção | `csharp_style_expression_bodied_properties` |
| ------------- |:-------------:|
| **Linguagens aplicáveis** | C#

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

### <a name="a-nameexpressionbodiedmembersindexersindexersa"></a><a name="expression_bodied_members_indexers">Indexadores</a>
|  Nome da opção | `csharp_style_expression_bodied_indexers` |
| ------------- |:-------------:|
| **Linguagens aplicáveis** | C#

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

### <a name="a-nameexpressionbodiedmembersaccessorsaccessorsa"></a><a name="expression_bodied_members_accessors">Acessadores</a>
|  Nome da opção | `csharp_style_expression_bodied_accessors` |
| ------------- |:-------------:|
| **Linguagens aplicáveis** | C#

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

## <a name="a-namepatternmatchingpattern-matchinga"></a><a name="pattern_matching">Correspondência de padrões</a>
### <a name="a-namepatternmatchingiscastis-with-cast-checkinga"></a><a name="pattern_matching_is_cast">verificação "is" com "cast"</a>
|  Nome da opção | `csharp_style_pattern_matching_over_is_with_cast_check` |
| ------------- |:-------------:|
| **Linguagens aplicáveis** | C#

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

### <a name="a-namepatternmatchingasnullas-with-null-checkinga"></a><a name="pattern_matching_as_null">Verificação "as" com "null"</a>
|  Nome da opção | `csharp_style_pattern_matching_over_as_with_null_check` |
| ------------- |:-------------:|
| **Linguagens aplicáveis** | C#

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

### <a name="a-nameinlinedvariabledeclarationsinlined-variable-declarationsa"></a><a name="inlined_variable_declarations">Declarações de variável embutida</a>
|  Nome da opção | `csharp_style_inlined_variable_declaration` |
| ------------- |:-------------:|
| **Linguagens aplicáveis** | C#

| Valor | Descrição | Aplicada 
| ------------- |:-------------|:-------------|
| verdadeiro | Prefira que as variáveis `out` sejam declaradas embutidas quando possível. | **C#:** <br>`if (int.TryParse(value out int i) {...}`
| False | Prefira que as variáveis `out` sejam declaradas explicitamente.| **C#:** <br>`int i; if (int.TryParse(value, out i) {...}`

#### <a name="example-editorconfig-file"></a>Exemplo de arquivo editorconfig:
```
# CSharp code style settings:
[*.cs]
csharp_style_inlined_variable_declaration = true:suggestion
```

## <a name="a-namenullcheckingnull-checking-preferencesa"></a><a name="null_checking">Preferências da verificação "null"</a>
### <a name="a-namenullcheckingthrowexpressionsthrow-expressionsa"></a><a name="null_checking_throw_expressions">Expressões throw</a>
|  Nome da opção | `csharp_style_throw_expression` |
| ------------- |:-------------:|
| **Linguagens aplicáveis** | C#

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

### <a name="a-namenullcheckingconditionaldelegatecallsprefer-conditional-delegate-callsa"></a><a name="null_checking_conditional_delegate_calls">Prefira chamadas de delegados condicionais</a>
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

