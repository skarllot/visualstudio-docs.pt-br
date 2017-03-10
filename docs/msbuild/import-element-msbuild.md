---
title: "Elemento Import (MSBuild) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/developer/msbuild/2003#Import"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "Elemento Import [MSBuild]"
  - "elemento < import > [MSBuild]"
ms.assetid: 3bfecaf1-69fd-4008-b651-c9dafd4389d9
caps.latest.revision: 29
caps.handback.revision: 29
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Elemento Import (MSBuild)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Importa o conteúdo de um arquivo de projeto para outro arquivo de projeto.  
  
 \<Project\>  
 \<Import\>  
  
## Sintaxe  
  
```  
<Import Project="ProjectPath"  
    Condition="'String A'=='String B'" />  
```  
  
## Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### Atributos  
  
|Atributo|Descrição|  
|--------------|---------------|  
|`Project`|Atributo obrigatório.<br /><br /> O caminho do arquivo de projeto para importar. O caminho pode incluir caracteres curinga. Os arquivos correspondentes são importados em ordem classificada. Usando esse recurso, você pode adicionar código a um projeto simplesmente adicionando o arquivo de código para um diretório.|  
|`Condition`|Atributo opcional.<br /><br /> Uma condição a ser avaliada. Para obter mais informações, consulte [Condições](../msbuild/msbuild-conditions.md).|  
  
### Elementos filho  
 Nenhum  
  
### Elementos pai  
  
|Elemento|Descrição|  
|--------------|---------------|  
|[Projeto](../msbuild/project-element-msbuild.md)|Elemento raiz necessária de um [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] arquivo de projeto.|  
|[ImportGroup](../msbuild/importgroup-element.md)|Contém uma coleção de `Import` elementos agrupados em uma condição opcional.|  
  
## Comentários  
 Usando o `Import` elemento, você pode reutilizar o código que é comum a vários arquivos de projeto. Isso facilita a manutenção do código porque as atualizações feitas no código compartilhado são propagadas para todos os projetos que importação\-lo.  
  
 Por convenção, os arquivos de projeto importado compartilhado são salvos como arquivos. targets, mas são padrão [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] arquivos de projeto.[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] não impedem a importação de um projeto que tem uma extensão de nome de arquivo diferente, mas recomendamos que você use a extensão. targets para manter a consistência.  
  
 Caminhos relativos no projetos importados são interpretados relativo ao diretório do projeto de importação. Portanto, se um arquivo de projeto for importado em vários arquivos de projeto em locais diferentes, os caminhos relativos no arquivo de projeto importado serão interpretados diferente para cada projeto importado.  
  
 Todos os [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] reservados propriedades relacionadas ao arquivo de projeto, por exemplo, `MSBuildProjectDirectory` e `MSBuildProjectFile`, que são referenciados em um projeto importado são atribuídos valores com base no arquivo de projeto de importação.  
  
 Se o projeto importado não tiver um `DefaultTargets` atributo, importado projetos são inspecionados na ordem em que eles são importados e o valor do primeiro descobertos `DefaultTargets` atributo será usado. Por exemplo, se Passoum importa ProjectB e ProjectC \(nessa ordem\) e ProjectB importa ProjectD, [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] primeiro procura por `DefaultTargets` especificado em Passoum, em seguida, ProjectB, em seguida, ProjectD e, finalmente, ProjectC.  
  
 O esquema de um projeto importado é idêntico de um projeto padrão. Embora [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] pode ser capaz de criar um projeto importado, é improvável porque um projeto importado normalmente contém informações sobre quais propriedades conjunto ou a ordem na qual executar destinos. O projeto importado depende do projeto para o qual ele é importado para fornecer essas informações.  
  
> [!NOTE]
>  Embora instruções de importação condicional funcionam na linha de comando MSBuilds, eles não funcionam com o MSBuild no [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ambiente de desenvolvimento integrado \(IDE\). Importações condicionais são avaliadas usando os valores de configuração e plataforma que são definidos quando o projeto é carregado. Se forem subsequentemente feitas alterações que exigem uma reavaliação das condições no arquivo de projeto, por exemplo, alterando a plataforma [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] reavalia as condições em itens e as propriedades, mas não em imports. Como a condicional de importação não é reavaliada, a importação é ignorada.  
>   
>  Para solucionar esse problema, coloque importações condicionais nos arquivos. targets ou colocar código em um bloco condicional, como um [Elemento Choose \(MSBuild\)](../msbuild/choose-element-msbuild.md) bloco.  
  
## Caracteres curinga  
 No .NET Framework 4, o MSBuild permite curingas no atributo de projeto. Quando houver caracteres curinga, todas as correspondências encontradas são classificadas \(para capacidade de reprodução\) e, em seguida, eles são importados na ordem como se a ordem foi definida explicitamente.  
  
 Isso é útil se você desejar oferecer um ponto de extensibilidade para que outra pessoa possa importar um arquivo sem exigir que você adicione explicitamente o nome do arquivo para o arquivo de importação. Para essa finalidade, Microsoft.Common.Targets contém a seguinte linha na parte superior do arquivo.  
  
```  
<Import Project="$(MSBuildExtensionsPath)\$(MSBuildToolsVersion)\$(MSBuildThisFile)\ImportBefore\*" Condition="'$(ImportByWildcardBeforeMicrosoftCommonTargets)' == 'true' and exists('$(MSBuildExtensionsPath)\$(MSBuildToolsVersion)\$(MSBuildThisFile)\ImportBefore')"/>  
```  
  
## Exemplo  
 O exemplo a seguir mostra um projeto que tem vários itens e propriedades e importa um arquivo de projeto geral.  
  
```  
<Project DefaultTargets="Compile"  
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <PropertyGroup>  
        <resourcefile>Strings.resx</resourcefile>  
  
        <compiledresources>  
            $(O)\$(MSBuildProjectName).Strings.resources  
        </compiledresources>  
    </PropertyGroup>  
  
    <ItemGroup>  
        <CSFile Include="*.cs" />  
  
        <Reference Include="System" />  
        <Reference Include="System.Data" />  
    </ItemGroup>  
  
    <Import Project="$(CommonLocation)\General.targets" />  
</Project>  
```  
  
## Consulte também  
 [Referência do esquema de arquivos de projeto](../msbuild/msbuild-project-file-schema-reference.md)   
 [Como usar o mesmo destino em vários arquivos de projeto](../Topic/How%20to:%20Use%20the%20Same%20Target%20in%20Multiple%20Project%20Files.md)