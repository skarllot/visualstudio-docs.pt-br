---
title: Elemento Import (MSBuild) | Microsoft Docs
ms.custom: 
ms.date: 03/13/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#Import
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- Import element [MSBuild]
- <Import> element [MSBuild]
ms.assetid: 3bfecaf1-69fd-4008-b651-c9dafd4389d9
caps.latest.revision: 29
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Human Translation
ms.sourcegitcommit: 79460291e91f0659df0a4241e17616e55187a0e2
ms.openlocfilehash: 234ab5c3b232ff64d4076e1663bff18fe53a2f70
ms.lasthandoff: 02/22/2017

---
# <a name="import-element-msbuild"></a>Elemento Import (MSBuild)
Importa o conteúdo de um arquivo de projeto para outro arquivo de projeto.  

 \<Project>  
 \<Import>  

## <a name="syntax"></a>Sintaxe  

```  
<Import Project="ProjectPath"  
    Condition="'String A'=='String B'" />  
```  

## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  

### <a name="attributes"></a>Atributos  

|Atributo|Descrição|  
|---------------|-----------------|  
|`Project`|Atributo obrigatório.<br /><br /> O caminho do arquivo de projeto para importar. O caminho pode incluir caracteres curinga. Os arquivos correspondentes são importados na ordem de classificação. Usando esse recurso, você pode adicionar o código a um projeto simplesmente adicionando o arquivo de código para um diretório.|  
|`Condition`|Atributo opcional.<br /><br /> Uma condição a ser avaliada. Para obter mais informações, consulte [Condições](../msbuild/msbuild-conditions.md).|  

### <a name="child-elements"></a>Elementos filho  
 Nenhum  

### <a name="parent-elements"></a>Elementos pai  

|Elemento|Descrição|  
|-------------|-----------------|  
|[Projeto](../msbuild/project-element-msbuild.md)|Elemento raiz necessário de um arquivo de projeto [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)].|  
|[ImportGroup](../msbuild/importgroup-element.md)|Contém uma coleção de elementos `Import` agrupados em uma condição opcional.|  

## <a name="remarks"></a>Comentários  
 Ao usar o elemento `Import`, você pode reutilizar o código que é comum a vários arquivos de projeto. Isso facilita a manutenção do código porque as atualizações feitas no código compartilhado são propagadas a todos os projetos o importam.  

 Por convenção, os arquivos de projeto importados compartilhados são salvos como arquivos .targets, mas são arquivos de projeto [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] padrão. [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] não impede a importação de um projeto que tem uma extensão de nome de arquivo diferente, mas recomendamos que você use a extensão .targets para manter a consistência.  

 Caminhos relativos em projetos importados são interpretados em relação ao diretório do projeto de importação. Portanto, se um arquivo de projeto for importado em vários arquivos de projeto em locais diferentes, os caminhos relativos no arquivo de projeto importado serão interpretados de maneira diferente para cada projeto importado.  

 Todas as propriedades [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] reservadas relacionadas ao arquivo de projeto, por exemplo, `MSBuildProjectDirectory` e `MSBuildProjectFile`, que sejam referenciadas em um projeto importado são valores atribuídos com base no arquivo de projeto de importação.  

 Se o projeto importado não tiver um atributo `DefaultTargets`, os projetos importados serão inspecionados na ordem em que forem importados e o valor do primeiro atributo `DefaultTargets` descoberto será usado. Por exemplo, se ProjectA importa ProjectB e ProjectC (nessa ordem) e ProjectB importa ProjectD, o [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] procura primeiro pelo `DefaultTargets` especificado em ProjectA, em seguida, ProjectB, depois, ProjectD e, finalmente, ProjectC.  

 O esquema de um projeto importado é idêntico ao de um projeto padrão. Embora [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] possa criar um projeto importado, isso é improvável porque um projeto importado normalmente não contém informações sobre quais propriedades configurar ou a ordem na qual executar os destinos. O projeto importado depende do projeto para o qual ele é importado para fornecer essas informações.  

> [!NOTE]
>  Embora instruções de importação condicional funcionam na linha de comando MSBuilds, elas não funcionam com o MSBuild no ambiente de desenvolvimento integrado (IDE) do [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Importações condicionais são avaliadas usando os valores de configuração e plataforma que são definidos quando o projeto é carregado. Se forem feitas alterações subsequentes que exigem uma reavaliação das condições no arquivo de projeto, por exemplo, alterando a plataforma, o [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] reavalia as condições em itens e propriedades, mas não em importações. Como a condicional de importação não é reavaliada, a importação é ignorada.  
>   
>  Para solucionar esse problema, coloque importações condicionais nos arquivos .targets ou coloque o código em um bloco condicional, como um bloco [Elemento Choose (MSBuild)](../msbuild/choose-element-msbuild.md).  

## <a name="wildcards"></a>Curingas  
 No .NET Framework 4, o MSBuild permite caracteres curinga no atributo Projeto. Quando houver caracteres curinga, todas as correspondências encontradas são classificadas (para capacidade de reprodução) e, em seguida, elas são importadas na ordem como se a ordem tivesse sido definida explicitamente.  

 Isso é útil se você quiser oferecer um ponto de extensibilidade para que outra pessoa possa importar um arquivo sem exigir que você adicione explicitamente o nome do arquivo ao arquivo de importação. Para essa finalidade, o Microsoft.Common.Targets contém a seguinte linha na parte superior do arquivo.  

```xml  
<Import Project="$(MSBuildExtensionsPath)\$(MSBuildToolsVersion)\$(MSBuildThisFile)\ImportBefore\*" Condition="'$(ImportByWildcardBeforeMicrosoftCommonTargets)' == 'true' and exists('$(MSBuildExtensionsPath)\$(MSBuildToolsVersion)\$(MSBuildThisFile)\ImportBefore')"/>  
```  

## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra um projeto que tem vários itens e propriedades e importa um arquivo de projeto geral.  

```xml  
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

## <a name="see-also"></a>Consulte também  
 [Referência do esquema de arquivos de projeto](../msbuild/msbuild-project-file-schema-reference.md)   
 [Como usar o mesmo destino em vários arquivos de projeto](../msbuild/how-to-use-the-same-target-in-multiple-project-files.md)

