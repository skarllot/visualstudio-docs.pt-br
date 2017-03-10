---
title: "Destinos do MSBuild | Microsoft Docs"
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
  - "MSBuild, destinos"
ms.assetid: 8060b4d2-e4a9-48cf-a437-852649ceb417
caps.latest.revision: 26
caps.handback.revision: 26
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Destinos do MSBuild
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

As tarefas do grupo de destinos juntos em uma ordem específica e permitem que o processo de compilação é acrescentado em unidades menores.  Por exemplo, um destino pode excluir todos os arquivos no diretório de saída para preparar para a compilação, enquanto outras entradas para compilar o projeto e as colocado no diretório vazia.  Para obter mais informações sobre as tarefas, consulte [ \(tarefas\)](../msbuild/msbuild-tasks.md).  
  
## Declarando destinos no Arquivo de projeto  
 Destinos são declarados em um arquivo de projeto com o elemento de [Destino](../msbuild/target-element-msbuild.md) .  Por exemplo, o XML a seguir cria um chamado destino a compilação, que chama a tarefa de CSC com o tipo de item compilar.  
  
```  
<Target Name="Construct">  
    <Csc Sources="@(Compile)" />  
</Target>  
```  
  
 Como propriedades do MSBuild, destinos podem ser reiniciados.  Por exemplo,  
  
```  
<Target Name="AfterBuild" >  
    <Message Text="First occurrence" />  
</Target>  
<Target Name="AfterBuild" >  
    <Message Text="Second occurrence" />  
</Target>  
```  
  
 Se AfterBuild executa, exibe somente a segunda ocorrência “”.  
  
## Ordem de compilação de destino  
 Destinos devem ser ordenados se a entrada a um destino depende de saída de outro destino.  Há várias maneiras de especificar a ordem em que execução de destino.  
  
-   Destinos de inicial  
  
-   Destinos de opção  
  
-   primeiro destino  
  
-   Dependências de destino  
  
-   `BeforeTargets` e `AfterTargets` MSBuild \(4,0\)  
  
 Um destino nunca tem duas vezes em uma única compilação, mesmo se um destino na compilação subseqüente depende de ele.  Quando um destino é executado, a contribuição para a compilação for concluída.  
  
 Para obter detalhes e mais informações sobre a ordem de compilação de destino, consulte [Ordem de compilação de destinos](../msbuild/target-build-order.md).  
  
## Direcionar em lotes  
 Um elemento de destino pode ter um atributo de `Outputs` que especifica metadados no formulário \(%\) de metadados.  Em esse caso, o MSBuild executa o destino uma vez para cada metadados exclusivos valor, agrupamento ou “em lotes” os itens que precisam valor de metadados.  Por exemplo,  
  
```  
<ItemGroup>  
    <Reference Include="System.Core">  
      <RequiredTargetFramework>3.5</RequiredTargetFramework>  
    </Reference>  
    <Reference Include="System.Xml.Linq">  
      <RequiredTargetFramework>3.5</RequiredTargetFramework>  
    </Reference>  
    <Reference Include="Microsoft.CSharp">  
      <RequiredTargetFramework>4.0</RequiredTargetFramework>  
    </Reference>  
</ItemGroup>  
<Target Name="AfterBuild"  
    Outputs="%(Reference.RequiredTargetFramework)">  
    <Message Text="Reference:  
      @(Reference->'%(RequiredTargetFramework)')" />  
</Target>  
```  
  
 processa em lotes os itens de referência por seus metadados de RequiredTargetFramework.  A saída de destino esta aparência:  
  
```  
Reference: 3.5;3.5  
Reference: 4.0  
  
```  
  
 Em lotes de destino é raramente usados em compilações reais.  Em lotes de tarefa é mais comuns.  Para obter mais informações, consulte [Separação em lotes](../msbuild/msbuild-batching.md).  
  
## Compilações incrementais  
 As compilações incrementais são as compilações que são otimizadas para que os destinos com arquivos de saída que são atualizados com relação aos arquivos de entrada correspondentes não sejam executados.  Um elemento de destino pode ter `Inputs` e atributos de `Outputs` , indicando que itens o destino espera como entrada, e itens que produz a seguinte saída.  
  
 Se todos os itens de saída são atualizados, o MSBuild ignora o destino, o que melhora significativamente a velocidade de compilação.  Isso é chamado de uma compilação incremental de destino.  Se apenas alguns arquivos são atualizados, o MSBuild executa o destino sem os itens atualizados.  Isso é chamado de uma compilação incremental parcial de destino.  Para obter mais informações, consulte [Compilações incrementais](../msbuild/incremental-builds.md).  
  
## Consulte também  
 [Conceitos do MSBuild](../msbuild/msbuild-concepts.md)   
 [Como usar o mesmo destino em vários arquivos de projeto](../Topic/How%20to:%20Use%20the%20Same%20Target%20in%20Multiple%20Project%20Files.md)