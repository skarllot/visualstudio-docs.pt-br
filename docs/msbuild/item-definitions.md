---
title: "Defini&#231;&#245;es de itens | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "msbuild, definições de item"
ms.assetid: 8e3dc223-f9e5-4974-aa0e-5dc7967419cb
caps.latest.revision: 21
caps.handback.revision: 21
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Defini&#231;&#245;es de itens
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 2,0 permite a declaração estático de itens em arquivos de projeto usando o elemento de [ItemGroup](../msbuild/itemgroup-element-msbuild.md) .  No entanto, os metadados podem ser adicionados somente em nível do item, mesmo se os metadados são idênticos para todos os itens.  Iniciando em [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 3,5, um elemento de projeto chamado [ItemDefinitionGroup](../msbuild/itemdefinitiongroup-element-msbuild.md) supera essa limitação.  *ItemDefinitionGroup* permite que você defina um conjunto de definições de item, que adicionam valores padrão de metadados para todos os itens no tipo de item chamado.  
  
 O elemento de *ItemDefinitionGroup* aparece imediatamente após o elemento de [Projeto](../msbuild/project-element-msbuild.md) do arquivo de projeto.  As definições de item fornecem a seguinte funcionalidade:  
  
-   Você pode definir metadados padrão globais para itens fora de um destino.  Isto é, os mesmos metadados aplicam\-se a todos os itens do tipo especificado.  
  
-   Os tipos de item podem ter várias definições.  Quando as especificações adicionais de metadados são adicionadas ao tipo, a especificação a mais recente tem precedência. \(Os metadados seguem a mesma ordem de importação que seguem as propriedades.\)  
  
-   Os metadados podem ser aditivos.  Por exemplo, os valores de CDefines são acumulados condicionalmente, dependendo das propriedades que estão sendo definidas.  Por exemplo, `MT;STD_CALL;DEBUG;UNICODE`.  
  
-   Os metadados podem ser removidos.  
  
-   As condições podem ser usadas para controlar a inclusão de metadados.  
  
## Valores padrão de metadados de item  
 Os metadados de item que são definidos em um ItemDefinitionGroup são apenas uma declaração de metadados padrão.  Os metadados não se aplicam a menos que você defina um item que usa um ItemGroup para conter os valores de metadados.  
  
> [!NOTE]
>  Em muitos dos exemplos neste tópico, um elemento de ItemDefinitionGroup é mostrado que mas sua definição correspondente ItemGroup é omitida para maior clareza.  
  
 Os metadados definidas explicitamente em um ItemGroup têm precedência sobre metadados em ItemDefinitionGroup.  Os metadados são aplicados em ItemDefinitionGroup somente para os metadados indefinidas em um ItemGroup.  Por exemplo:  
  
```  
<ItemDefinitionGroup>  
    <i>  
        <m>m1</m>  
        <n>n1</n>  
    </i>        
</ItemDefinitionGroup>  
<ItemGroup>  
    <i Include="a">  
        <o>o1</o>  
        <n>n2</n>  
    </i>  
</ItemGroup>  
```  
  
 Nesse exemplo, os metadados padrão “m” são aplicados ao item “i” porque os metadados “m” não são explicitamente definidos pelo item “i”.  No entanto, os metadados padrão “em” não são aplicados ao item “i” porque os metadados “em” já estão definidos pelo item “i”.  
  
> [!NOTE]
>  Os nomes de elemento XML e de parâmetro diferenciam maiúsculas de minúsculas.  Os metadados de item e nomes de item\/propriedade não diferenciam maiúsculas de minúsculas.  Portanto, os itens de ItemDefinitionGroup que têm nomes que diferem somente por casos devem ser tratados como o mesmo ItemGroup.  
  
## Fontes de valor  
 Os valores para os metadados que são definidos em um ItemDefinitionGroup podem vir de várias fontes diferentes, como segue:  
  
-   Propriedade PropertyGroup  
  
-   Item de um ItemDefinitionGroup  
  
-   O item transformações em um item de ItemDefinitionGroup  
  
-   Variável de ambiente  
  
-   Propriedade global \(de linha de comando MSBuild.exe\)  
  
-   Propriedade reservado  
  
-   Metadados conhecidos em um item de um ItemDefinitionGroup  
  
-   Seção CDATA \<\! \[CDATA \[qualquer coisa aqui é analisado\]\]\>  
  
> [!NOTE]
>  Os metadados de item de um ItemGroup não são úteis em uma declaração de metadados de ItemDefinitionGroup porque os elementos de ItemDefinitionGroup são processados antes de elementos ItemGroup.  
  
## Definições aditivas e várias  
 Quando você adiciona definições ou uso mais ItemDefinitionGroups, lembre\-se do seguinte:  
  
-   A especificação extra de metadados é adicionada ao tipo.  
  
-   A especificação a mais recente tem precedência.  
  
 Quando você tiver vários ItemDefinitionGroups, cada especificação subsequente adiciona os seus metadados para a definição anterior.  Por exemplo:  
  
```  
<ItemDefinitionGroup>  
    <i>  
        <m>m1</m>  
        <n>n1</n>  
    </i>  
</ItemDefinitionGroup>  
<ItemDefinitionGroup>  
    <i>  
        <o>o1</o>  
    </i>  
</ItemDefinitionGroup>  
```  
  
 Nesse exemplo, os metadados “o” são adicionados a “m” e “em”.  
  
 Além disso, os valores definidos anteriormente de metadados também podem ser adicionados.  Por exemplo:  
  
```  
<ItemDefinitionGroup>  
    <i>  
        <m>m1</m>  
    </i>  
</ItemDefinitionGroup>  
<ItemDefinitionGroup>  
    <i>  
        <m>%(m);m2</m>  
    </i>  
</ItemDefinitionGroup>    
```  
  
 Nesse exemplo, o valor definido anteriormente para os metadados “m” m1 \(\) é adicionado ao novo valor \(m2\), de modo que o valor final é “m1; m2”.  
  
> [!NOTE]
>  Isso também pode ocorrer no mesmo ItemDefinitionGroup.  
  
 Quando você substituir os metadados definidos anteriormente, a especificação a mais recente tem precedência.  No exemplo a seguir, o valor final dos metadados “m” go de “m1” a “m1a”.  
  
```  
<ItemDefinitionGroup>  
    <i>  
        <m>m1</m>  
    </i>  
</ItemDefinitionGroup>  
<ItemDefinitionGroup>  
    <i>  
        <m>m1a</m>  
    </i>  
</ItemDefinitionGroup>    
```  
  
## Usando condições em um ItemDefinitionGroup  
 Você pode usar condições em um ItemDefinitionGroup para controlar a inclusão de metadados.  Por exemplo:  
  
```  
<ItemDefinitionGroup Condition="'$(Configuration)'=='Debug'">  
    <i>  
        <m>m1</m>  
    </i>  
</ItemDefinitionGroup>  
```  
  
 Nesse caso, os metadados padrão “m1” no item “me” sou incluído somente se o valor da propriedade “configurações” é” depuração.  
  
> [!NOTE]
>  Somente as referências locais de metadados são suportadas em condições.  
  
 Referências para os metadados definidos em um ItemDefinitionGroup anterior são locais para o item, não grupo de definição.  Isto é, o escopo de referências é item específico.  Por exemplo:  
  
```  
<ItemDefinitionGroup>  
    <test>  
        <yes>1</yes>  
    </test>  
    <i>  
        <m Condition="'%(test.yes)'=='1'">m1</m>  
    </i>  
</ItemDefinitionGroup>  
```  
  
 Nesse exemplo, item “i” item “teste” referências em condição.  
  
## Substituindo metadados e excluindo  
 Os metadados definidos em um elemento de ItemDefinitionGroup podem ser substituídos em um elemento posterior de ItemDefinitionGroup definindo o valor de metadados para nulo.  Você também pode efetivamente excluir um item de metadados definindo a um valor vazio.  Por exemplo:  
  
```  
<ItemDefinitionGroup>  
    <i>  
        <m>m1</m>  
    </i>  
</ItemDefinitionGroup>  
<ItemDefinitionGroup>  
    <i>  
        <m></m>  
    </i>  
</ItemDefinitionGroup>  
```  
  
 O item “me” ainda contenho os metadados “m”, mas seu valor agora está vazia.  
  
## Escopo de metadados  
 ItemDefinitionGroups tem escopo global em propriedades definidas e globais onde quer que são definidos.  As definições padrão de metadados em um ItemDefinitionGroup podem ser autorreferenciais.  Por exemplo, os seguintes que usa um simples metadados referenciam:  
  
```  
<ItemDefinitionGroup>  
    <i>  
        <m>m1</m>  
        <m>%(m);m2</m>  
    </i>  
</ItemDefinitionGroup>  
```  
  
 Uma referência qualificada de metadados também pode ser usada:  
  
```  
<ItemDefinitionGroup>  
    <i>  
      <m>m1</m>  
      <m>%(i.m);m2</m>  
    </i>  
</ItemDefinitionGroup>  
```  
  
 No entanto, o seguinte é válido:  
  
```  
<ItemDefinitionGroup>  
    <i>  
        <m>m1</m>  
        <m>@(x)</m>  
    </i>  
</ItemDefinitionGroup>  
```  
  
 Iniciando em [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 3,5, ItemGroups também pode ser autorreferencial.  Por exemplo:  
  
```  
<ItemGroup>  
    <item Include="a">  
        <m>m1</m>  
        <m>%(m);m2</m>  
    </item>  
</ItemGroup>  
```  
  
## Consulte também  
 [Separação em lotes](../msbuild/msbuild-batching.md)