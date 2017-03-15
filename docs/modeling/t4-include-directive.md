---
title: "T4 Diretiva de inclusão | Documentos do Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8c3de9f3-755a-47c5-a30a-65717dcaaac2
caps.latest.revision: 6
author: alancameronwills
ms.author: awills
manager: douge
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
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: d601fea177c6c42d91b467cb8ba8f36116f58062
ms.lasthandoff: 02/22/2017

---
# <a name="t4-include-directive"></a>Diretiva de inclusão T4
Em um modelo de texto no [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], você pode incluir texto de outro arquivo usando uma diretiva `<#@include#>`. Você pode colocar diretivas `include` em qualquer lugar de um modelo de texto antes do primeiro bloco de recursos da classe `<#+ ... #>`. Os arquivos incluídos também podem conter diretivas `include` e outras diretivas. Isso permite que você compartilhe código de modelo e texto constante entre modelos.  
  
## <a name="using-include-directives"></a>Usando diretivas de inclusão  
  
```  
<#@ include file="filePath" [once="true"] #>  
```  
  
-   `filePath` pode ser absoluto ou relativo ao arquivo de modelo atual.  
  
     Além disso, as extensões específicas do [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] podem especificar seus próprios diretórios para pesquisar arquivos de inclusão. Por exemplo, quando você instalou o SDK de visualização e modelagem (ferramentas DSL), a pasta a seguir é adicionada à lista de inclusão: `Program Files\Microsoft Visual Studio 10.0\Common7\IDE\Extensions\Microsoft\DSL SDK\DSL Designer\11.0\TextTemplates`.  
  
     Essas pastas de inclusão adicionais podem depender da extensão do arquivo de inclusão. Por exemplo, a pasta de inclusão das Ferramentas DSL só é acessível a arquivos de inclusão com a extensão de arquivo `.tt`  
  
-   `filePath` pode incluir variáveis de ambiente delimitadas com "%". Por exemplo:  
  
    ```  
    <#@ include file="%HOMEPATH%\MyIncludeFile.t4" #>  
    ```  
  
-   O nome de um arquivo incluído não precisa usar a extensão `".tt"`.  
  
     Você pode usar outra extensão como `".t4"` para arquivos incluídos. Isso ocorre porque, quando você adiciona um `.tt` arquivo a um projeto, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] define automaticamente seus **ferramenta personalizada** propriedade `TextTemplatingFileGenerator`. Geralmente, você não quer que os arquivos incluídos sejam transformados individualmente.  
  
     Por outro lado, você deve estar ciente de que, em alguns casos, a extensão do arquivo afeta as pastas adicionais em que os arquivos de inclusão serão pesquisados. Isso pode ser importante quando você tem um arquivo incluído que contenha outros arquivos.  
  
-   O conteúdo incluído é processado quase como se fizesse parte do modelo de texto de inclusão. Entretanto, você pode incluir um arquivo que contenha um bloco de recurso de classe `<#+...#>` mesmo se a diretiva `include` for seguida por blocos de texto comum ou de controle padrão.  
  
-   Use `once="true"` para garantir que um modelo seja incluído somente uma vez, mesmo se for invocado por mais de um arquivo de inclusão.  
  
     Isso torna recurso fácil criar uma biblioteca de trechos de código T4 reutilizáveis que podem ser incluídas em será sem se preocupar que algum outro trecho já inclui-los.  Por exemplo, suponha que você tenha uma biblioteca de trechos de código muito refinadas que lidam com processamento de modelo e geração de c#.  Por sua vez, eles são usados por alguns utilitários mais tarefas específicas, como gerar exceções, que pode ser usada de qualquer modelo mais específicas do aplicativo. Se você desenhar o gráfico de dependência, verá que alguns trechos poderiam ser incluídos várias vezes. Mas o parâmetro `once` evita as inclusões subsequentes.  
  
 **MyTextTemplate.tt:**  
  
```  
<#@ output extension=".txt" #>  
Output message 1 (from top template).  
<#@ include file="TextFile1.t4"#>  
Output message 5 (from top template).  
<#  
   GenerateMessage(6); // defined in TextFile1.t4  
   AnotherGenerateMessage(7); // defined in TextFile2.t4  
#>  
  
```  
  
 **TextFile1.t4:**  
  
```  
   Output Message 2 (from included file).  
<#@include file="TextFile2.t4" #>  
   Output Message 4 (from included file).  
<#+ // Start of class feature control block.  
void GenerateMessage(int n)  
{  
#>  
   Output Message <#= n #> (from GenerateMessage method).  
<#+  
}  
#>  
  
```  
  
 **TextFile2.t4:**  
  
```  
        Output Message 3 (from included file 2).  
<#+ // Start of class feature control block.  
void AnotherGenerateMessage(int n)  
{  
#>  
       Output Message <#= n #> (from AnotherGenerateMessage method).  
<#+  
}  
#>  
  
```  
  
 **O arquivo gerado resultante, mytexttemplate. txt:**  
  
```  
Output message 1 (from top template).  
   Output Message 2 (from included file).  
        Output Message 3 (from included file 2).  
  
   Output Message 4 (from included file).  
  
Output message 5 (from top template).  
   Output Message 6 (from GenerateMessage method).  
       Output Message 7 (from AnotherGenerateMessage method).  
  
```  
  
##  <a name="a-namemsbuilda-using-project-properties-in-msbuild-and-visual-studio"></a><a name="msbuild"></a>Usando propriedades do projeto no MSBuild e o Visual Studio  
 Embora você possa usar macros do Visual Studio como $(SolutionDir) em uma diretiva de inclusão, não funcionam no MSBuild. Se você quiser transformar modelos no computador de compilação, use as propriedades do projeto como alternativa.  
  
 Edite seu arquivo .csproj ou .vbproj para definir uma propriedade do projeto. Este exemplo define uma propriedade chamada `myIncludeFolder`:  
  
```xml  
<!-- Define a project property, myIncludeFolder: -->  
<PropertyGroup>  
    <myIncludeFolder>$(MSBuildProjectDirectory)\..\libs</myIncludeFolder>  
</PropertyGroup>  
  
<!-- Tell the MSBuild T4 task to make the property available: -->  
<ItemGroup>  
    <T4ParameterValues Include="myIncludeFolder">  
      <Value>$(myIncludeFolder)</Value>  
    </T4ParameterValues>  
  </ItemGroup>  
  
```  
  
 Agora você pode usar a propriedade do projeto em modelos de texto, que se transformam corretamente no Visual Studio e no MSBuild:  
  
```  
<#@ include file="$(myIncludeFolder)\defs.tt" #>  
```
