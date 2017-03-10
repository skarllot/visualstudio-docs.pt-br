---
title: "Gera&#231;&#227;o de c&#243;digo, compila&#231;&#227;o e conven&#231;&#245;es de nomenclatura no Microsoft Fakes | Microsoft Docs"
ms.custom: ""
ms.date: "12/13/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 20221de4-2a9e-4787-b99a-b5855bb90872
caps.latest.revision: 16
caps.handback.revision: 16
ms.author: "mlearned"
manager: "douge"
---
# Gera&#231;&#227;o de c&#243;digo, compila&#231;&#227;o e conven&#231;&#245;es de nomenclatura no Microsoft Fakes
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Este tópico aborda problemas e opções de compilação e geração de código de falsificações e descreve as convenções de nomenclatura para tipos, membros e parâmetros Fakes gerados.  
  
 **Requisitos**  
  
-   O Visual Studio Enterprise  
  
##  <a name="BKMK_In_this_topic"></a> Neste tópico  
 [Geração de código e compilação](#BKMK_Code_generation_and_compilation)  
  
-   [Configurando a geração de código de stubs](#BKMK_Configuring_code_generation_of_stubs) • [Filtragem de tipo](#BKMK_Type_filtering) • [Classes concretas arrancar e métodos virtuais](#BKMK_Stubbing_concrete_classes_and_virtual_methods) • [Tipos internos](#BKMK_Internal_types) • [Otimizando os tempos de compilação](#BKMK_Optimizing_build_times) • [Evitando opostos de nome de assembly](#BKMK_Avoiding_assembly_name_clashing)  
  
 [Convenções de nomenclatura do Fakes](#BKMK_Fakes_naming_conventions)  
  
-   [Tipo de correção e convenções de nomenclatura do tipo de stub](#BKMK_Shim_type_and_stub_type_naming_conventions) • [Shim delegado stub ou propriedade de campo delegate convenções de nomenclatura](#BKMK_Shim_delegate_property_or_stub_delegate_field_naming_conventions) • [Convenções de nomenclatura de tipo de parâmetro](#BKMK_Parameter_type_naming_conventions) • [Regras recursiva](#BKMK_Recursive_rules)  
  
 [Recursos externos](#BKMK_External_resources)  
  
-   [Diretriz](#BKMK_Guidance)  
  
##  <a name="BKMK_Code_generation_and_compilation"></a> Geração de código e compilação  
  
###  <a name="BKMK_Configuring_code_generation_of_stubs"></a> Configurando a geração de código de stubs  
 A geração de tipos de stub é configurada em um arquivo XML que tem a extensão de arquivo .fakes.  O Fakes framework integra\-se no processo de compilação por meio de tarefas MSBuild personalizadas e detecta esses arquivos em tempo de compilação.  O gerador de código Fakes os tipos de stub é compilado em um assembly e adiciona a referência ao projeto.  
  
 O exemplo a seguir ilustra os tipos de stub definidos em FileSystem.dll:  
  
```xml  
<Fakes xmlns="http://schemas.microsoft.com/fakes/2011/">  
    <Assembly Name="FileSystem"/>  
</Fakes>  
  
```  
  
###  <a name="BKMK_Type_filtering"></a> Filtragem de tipo  
 Filtros podem ser definidos no arquivo .fakes para restringir os tipos devem ser oculto.  Você pode adicionar um número ilimitado de limpar, adicionar, remover elementos sob o elemento StubGeneration para criar a lista de tipos selecionados.  
  
 Por exemplo, esse arquivo .fakes gera os stubs para tipos em namespaces do System.IO e de sistema, mas exclui qualquer tipo que contém "Manipulam" no sistema:  
  
```xml  
<Fakes xmlns="http://schemas.microsoft.com/fakes/2011/">  
  <Assembly Name="mscorlib" />  
  <!-- user code -->  
  <StubGeneration>  
    <Clear />  
    <Add Namespace="System!" />  
    <Add Namespace="System.IO!"/>  
    <Remove TypeName="Handle" />  
  </StubGeneration>  
  <!-- /user code -->  
</Fakes>  
```  
  
 As cadeias de caracteres do filtro usam uma gramática simple para definir como a correspondência deve ser feita:  
  
-   Filtros diferenciam maiúsculas de minúsculas por padrão. filtros de executam uma correspondência de subcadeia de caracteres:  
  
     `el` corresponde a "hello"  
  
-   Adicionando `!` ao final do filtro fará com que seja precisa correspondência diferencia maiúsculas de minúsculas:  
  
     `el!` não corresponde a "hello"  
  
     `hello!` corresponde a "hello"  
  
-   Adicionando `*` ao final do filtro tornará correspondem ao prefixo da cadeia de caracteres:  
  
     `el*` não corresponde a "hello"  
  
     `he*` corresponde a "hello"  
  
-   Vários filtros em uma lista separada por ponto e vírgula são combinados como uma disjunção:  
  
     `el;wo` corresponde a "hello" e "world"  
  
###  <a name="BKMK_Stubbing_concrete_classes_and_virtual_methods"></a> Classes concretas arrancar e métodos virtuais  
 Por padrão, os tipos de stub são gerados para todas as classes não lacrados.  É possível restringir os tipos de stub para classes abstratas por meio do arquivo de configuração .fakes:  
  
```xml  
<Fakes xmlns="http://schemas.microsoft.com/fakes/2011/">  
  <Assembly Name="mscorlib" />  
  <!-- user code -->  
  <StubGeneration>  
    <Types>  
      <Clear />  
      <Add AbstractClasses="true"/>  
    </Types>  
  </StubGeneration>  
  <!-- /user code -->  
</Fakes>  
```  
  
###  <a name="BKMK_Internal_types"></a> Tipos internos  
 O gerador de código Fakes gerará shim tipos e tipos para tipos que são visíveis para o assembly de Fakes gerado de stub.  Para tornar os tipos internos de um assembly com shims visível falsificações e seu conjunto de teste, adicione  <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> atributos para o código de assembly com shims que proporciona visibilidade para o assembly de Fakes gerado e o assembly de teste.  Veja um exemplo:  
  
```c#  
// FileSystem\AssemblyInfo.cs  
[assembly: InternalsVisibleTo("FileSystem.Fakes")]  
[assembly: InternalsVisibleTo("FileSystem.Tests")]  
```  
  
 **Tipos internos em assemblies fortemente nomeados**  
  
 Se o assembly com shims é nomeado e você quiser acesso interno tipos do assembly:  
  
-   Seu conjunto de teste e o assembly do Fakes devem ser nomeadas.  
  
-   Você deve adicionar as chaves públicas do teste e Fakes assembly para o **InternalsVisibleToAttribute** atributos em assemblies com shims.  Aqui está como nossos atributos de exemplo no código de assembly com shims ficaria quando o assembly com shims é nomeado:  
  
    ```c#  
    // FileSystem\AssemblyInfo.cs  
    [assembly: InternalsVisibleTo("FileSystem.Fakes",  
        PublicKey=<Fakes_assembly_public_key>)]  
    [assembly: InternalsVisibleTo("FileSystem.Tests",  
        PublicKey=<Test_assembly_public_key>)]  
    ```  
  
 Se o assembly com shims um nome forte, o framework Fakes automaticamente fortemente assinará o assembly de Fakes gerado.  Você precisa forte assinar o assembly de teste.  Consulte [Criando e usando assemblies de nomes fortes](../Topic/Creating%20and%20Using%20Strong-Named%20Assemblies.md).  
  
 A estrutura de falsificações usa a mesma chave para assinar assemblies gerados tudo, então você pode usar este trecho de código como ponto de partida para adicionar o **InternalsVisibleTo** atributo para o assembly de fakes para seu código de assembly com shims.  
  
```c#  
[assembly: InternalsVisibleTo("FileSystem.Fakes, PublicKey=0024000004800000940000000602000000240000525341310004000001000100e92decb949446f688ab9f6973436c535bf50acd1fd580495aae3f875aa4e4f663ca77908c63b7f0996977cb98fcfdb35e05aa2c842002703cad835473caac5ef14107e3a7fae01120a96558785f48319f66daabc862872b2c53f5ac11fa335c0165e202b4c011334c7bc8f4c4e570cf255190f4e3e2cbc9137ca57cb687947bc")]  
```  
  
 Você pode especificar uma chave pública diferente para o assembly de Fakes, como uma chave você criou para o assembly com shims, especificando o caminho completo para o **.snk** arquivo que contém a chave alternativa a `KeyFile` valor de atributo a `Fakes`\\`Compilation` elemento o **.fakes** arquivo.  Por exemplo:  
  
```xml  
<-- FileSystem.Fakes.fakes -->  
<Fakes ...>  
  <Compilation KeyFile="full_path_to_the_alternate_snk_file" />  
</Fakes>  
  
```  
  
 Em seguida, você deve usar a chave pública da alternativa **.snk** arquivo como o segundo parâmetro do atributo InternalVisibleTo para o assembly de Fakes no código de assembly com shims:  
  
```c#  
// FileSystem\AssemblyInfo.cs  
[assembly: InternalsVisibleTo("FileSystem.Fakes",  
    PublicKey=<Alternate_public_key>)]  
[assembly: InternalsVisibleTo("FileSystem.Tests",  
    PublicKey=<Test_assembly_public_key>)]  
```  
  
 No exemplo acima, os valores `Alternate_public_key` e `Test_assembly_public_key` podem ser os mesmos.  
  
###  <a name="BKMK_Optimizing_build_times"></a> Otimizando os tempos de compilação  
 A compilação de assemblies Fakes pode aumentar significativamente o tempo de compilação.  Você pode minimizar o tempo de compilação gerando os assemblies de falsificações para assemblies de sistema do .NET e assemblies de terceiros em um projeto separado de centralizado.  Como esses assemblies raramente são alteradas na sua máquina, é possível reutilizar os assemblies Fakes gerados em outros projetos.  
  
 De seus projetos de teste de unidade, você pode simplesmente colocar uma referência aos assemblies compilados Fakes que são colocados em FakesAssemblies na pasta do projeto.  
  
1.  Crie uma nova biblioteca de classe com a versão de tempo de execução do .NET correspondente seus projetos de teste.  Vamos chamá\-lo Fakes.Prebuild.  Remova o arquivo Class1. cs no projeto, não é necessário.  
  
2.  Adicione referência a todo o sistema e os assemblies de terceiros para que precisa Fakes.  
  
3.  Adicionar um arquivo de .fakes para cada um dos assemblies e compilar.  
  
4.  De seu projeto de teste  
  
    -   Certifique\-se de que você tem uma referência para a DLL de runtime Fakes:  
  
         C:\\Program Files\\Microsoft Visual Studio 12.0\\Common7\\IDE\\PublicAssemblies\\Microsoft.QualityTools.Testing.Fakes.dll  
  
    -   Para cada assembly que você criou Fakes para, adicione uma referência ao arquivo de DLL correspondente na pasta Fakes.Prebuild\\FakesAssemblies do seu projeto.  
  
###  <a name="BKMK_Avoiding_assembly_name_clashing"></a> Evitando opostos de nome de assembly  
 Em um ambiente do Team Build, todas as saídas de compilação são mescladas em um único diretório.  No caso de vários projetos usando falsificações, pode acontecer que Fakes assemblies de versão diferente substituam uns aos outros.  Por exemplo, TestProject1 fakes mscorlib. dll do .NET Framework 2.0 e TestProject2 fakes mscorlib. dll para o .NET Framework 4 poderia produzir a um mscorlib. Assembly de Fakes Fakes.dll.  
  
 Para evitar esse problema, falsificações deverá criar automaticamente nomes de assembly de Fakes versão qualificado para referências de projeto ao adicionar os arquivos .fakes.  Um nome de assembly de Fakes versão qualificada incorpora um número de versão ao criar o nome do assembly de Fakes:  
  
 Dado um assembly MyAssembly e uma versão 1.2.3.4, o nome do assembly de Fakes é MyAssembly.1.2.3.4.Fakes.  
  
 Você pode alterar ou remover essa versão editando o o atributo de versão do elemento Assembly o .fakes:  
  
```xml  
attribute of the Assembly element in the .fakes:  
<Fakes ...>  
  <Assembly Name="MyAssembly" Version="1.2.3.4" />  
  ...  
</Fakes>  
  
```  
  
##  <a name="BKMK_Fakes_naming_conventions"></a> Convenções de nomenclatura do Fakes  
  
###  <a name="BKMK_Shim_type_and_stub_type_naming_conventions"></a> Tipo de correção e convenções de nomenclatura do tipo de stub  
 **Namespaces**  
  
-   . Fakes sufixo for adicionado ao namespace.  
  
     Por exemplo, `System.Fakes` namespace contém os tipos de correção do namespace System.  
  
-   Global.Fakes contém o tipo de correção do namespace vazio.  
  
 **Nomes de tipo**  
  
-   Prefixo de correção é adicionado ao nome do tipo para criar o nome do tipo de correção.  
  
     Por exemplo, ShimExample é o tipo de correção do tipo de exemplo.  
  
-   Prefixo de stub é adicionado ao nome do tipo para criar o nome do tipo de stub.  
  
     Por exemplo, StubIExample é o tipo de stub do tipo IExample.  
  
 **Argumentos de tipo e estruturas de tipo aninhado**  
  
-   Argumentos de tipo genéricos são copiados.  
  
-   Estrutura do tipo aninhado é copiada para os tipos de correção.  
  
###  <a name="BKMK_Shim_delegate_property_or_stub_delegate_field_naming_conventions"></a> Shim delegado stub ou propriedade de campo delegate convenções de nomenclatura  
 **Regras básicas** campo de nomenclatura, a partir de um nome vazio:  
  
-   O nome do método é anexado.  
  
-   Se o nome do método é uma implementação de interface explícita, os pontos são removidos.  
  
-   Se o método é genérico, `Of`*n* é acrescentado onde *n* é o número de argumentos de método genérico.  
  
 **Nomes de método especial** como propriedade getter ou setters são tratados como descrito na tabela a seguir.  
  
|Se o método é...|Exemplo|Nome do método anexado|  
|----------------------|-------------|----------------------------|  
|Um **construtor**|`.ctor`|`Constructor`|  
|Estático **construtor**|`.cctor`|`StaticConstructor`|  
|Um **acessador** com método nome composto de duas partes separadas por "\_" \(como getters de propriedade\)|*kind\_name* \(comuns maiúsculas, mas não impostas por ECMA\)|*NameKind*, onde ambas as partes foram colocadas em maiúsculas e trocadas|  
||Getter de propriedade `Prop`|`PropGet`|  
||Setter da propriedade `Prop`|`PropSet`|  
||Adicionador de eventos|`Add`|  
||Ferramenta de remoção do evento|`Remove`|  
|Um **operador** composta de duas partes|`op_name`|`NameOp`|  
|Por exemplo: operador \+|`op_Add`|`AddOp`|  
|Para uma **operador de conversão**, o tipo de retorno é anexado.|`T op_Implicit`|`ImplicitOpT`|  
  
 **Observações**  
  
-   **Getters e setters de indexadores** são tratados de maneira semelhante à propriedade.  O nome padrão de um indexador é `Item`.  
  
-   **Tipo de parâmetro** nomes são transformados e concatenados.  
  
-   **Tipo de retorno** será ignorado a menos que haja uma ambiguidade de sobrecarga.  Se esse for o caso, o tipo de retorno é acrescentado ao final do nome  
  
###  <a name="BKMK_Parameter_type_naming_conventions"></a> Convenções de nomenclatura de tipo de parâmetro  
  
|Dado|É a cadeia de caracteres acrescentada...|  
|----------|----------------------------------------------|  
|A **type** `T`|T<br /><br /> O namespace, estrutura aninhada e genéricos dir sinais diacríticos são descartados.|  
|Um **parâmetro out** `out T`|`TOut`|  
|Um **parâmetro ref** `ref T`|`TRef`|  
|Um **tipo de matriz** `T[]`|`TArray`|  
|Um **matriz multidimensional** tipo `T[ , , ]`|`T3`|  
|Um **ponteiro** tipo `T*`|`TPtr`|  
|Um **tipo genérico** `T<R1, …>`|`TOfR1`|  
|Um **argumento de tipo genérico** `!i` de tipo `C<TType>`|`Ti`|  
|Um **argumento do método genérico** `!!i` do método `M<MMethod>`|`Mi`|  
|Um **aninhadas de tipo** `N.T`|`N` é acrescentado, em seguida `T`|  
  
###  <a name="BKMK_Recursive_rules"></a> Regras recursiva  
 As seguintes regras são aplicadas recursivamente:  
  
-   Como Fakes usa c\# para gerar os assemblies de falsificações, qualquer caractere que produza um token inválido do c\# é escape "\_" \(sublinhado\).  
  
-   Se um nome resultante corresponde a qualquer membro do tipo declarativo, um esquema de numeração é usado, acrescentando um contador de dois dígitos, começando em 01.  
  
##  <a name="BKMK_External_resources"></a> Recursos externos  
  
###  <a name="BKMK_Guidance"></a> Diretriz  
 [Teste para entrega contínua com o Visual Studio 2012 – capítulo 2: testes de unidade: Testando o interior](http://go.microsoft.com/fwlink/?LinkID=255188)  
  
## Consulte também  
 [Isolando código em teste com falsificação da Microsoft](../test/isolating-code-under-test-with-microsoft-fakes.md)