---
title: "Compila&#231;&#245;es incrementais | Microsoft Docs"
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
  - "msbuild, compilações incrementais"
ms.assetid: 325e28c7-4838-4e3f-b672-4586adc7500c
caps.latest.revision: 8
caps.handback.revision: 8
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Compila&#231;&#245;es incrementais
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

As compilações incrementais são as compilações que são otimizadas de modo que os destinos que possuem os arquivos de saída que são atualizados com relação aos arquivos de entrada correspondentes não sejam executados.  Um elemento de destino pode ter um atributo de `Inputs` , que indica que itens o destino espera como entrada, e um atributo de `Outputs` , que indica que gerencia itens como saída.  Tentativas do MSBuild de encontrar um mapeamento entre 1 to\-1 os valores desses atributos.  Se um mapeamento 1 to\-1 existir, MSBuild compara o carimbo de data\/hora de cada item de entrada para o carimbo de data\/hora do item correspondente de saída.  Os arquivos de saída que não têm nenhum mapeamento 1 to\-1 são comparados a todos os arquivos de entrada.  Um item está sendo atualizado se seu arquivo de saída é a mesma idade ou mais recente que o arquivo de entrada ou arquivos.  
  
 Se todos os itens de saída são atualizados, MSBuild ignora o destino.  Esta *compilação incremental* de destino pode melhorar significativamente a velocidade de compilação.  Se apenas alguns arquivos são atualizados, MSBuild executa o destino mas ignora os itens atualizados, e traz assim todos os itens atualizados.  Isso é conhecido como *uma compilação incremental parcial*.  
  
 1 \- \-1 aos mapeamentos são normalmente gerados por transformações de item.  Para obter mais informações, consulte [Transformações](../msbuild/msbuild-transforms.md).  
  
 Considere o seguinte destino.  
  
```  
<Target Name="Backup" Inputs="@(Compile)"   
    Outputs="@(Compile->'$(BackupFolder)%(Identity).bak')">  
    <Copy SourceFiles="@(Compile)" DestinationFiles=  
        "@(Compile->'$(BackupFolder)%(Identity).bak')" />  
</Target>  
```  
  
 O conjunto de arquivos representados pelo tipo de item de `Compile` é copiado para um diretório alternativo.  Os arquivos de backup têm a extensão de nome de arquivo .bak.  Se os arquivos representados pelo tipo de item de `Compile` , ou os arquivos de backup correspondentes, não são excluídos ou modificado após o destino alternativa é executado, o destino alternativa é saltado em compilações subsequentes.  
  
## Inferência de saída  
 MSBuild compara os atributos de `Inputs` e de `Outputs` de um destino para determinar se o destino precisa executar.  Idealmente, o conjunto de arquivos que existe depois que uma compilação incremental estiver concluída deve permanecer o mesmo mesmo se os destinos associados são executados.  Como as propriedades e os itens que são criados ou modificados por tarefas podem afetar a compilação, MSBuild deve interpretar seus valores mesmo se o destino que os afeta é saltado.  Isso é conhecido como *inferência de saída*.  
  
 Há três casos:  
  
-   O destino tem um atributo de `Condition` que avalia a `false`.  Nesse caso, o destino não é executado, e não tem efeito na compilação.  
  
-   O destino tiver expirado e saída é executado para trazê\-las atualizados.  
  
-   O destino não tem nenhuma saída expirado e é saltado.  MSBuild avalia o destino e fazer alterações aos itens e propriedades como se o destino tivesse sido executado.  
  
 Para oferecer suporte a compilação incremental, as tarefas devem garantir que o valor do atributo de `TaskParameter` de qualquer elemento de `Output` é igual a um parâmetro de entrada de tarefas.  Eis alguns exemplos:  
  
```  
<CreateProperty Value="123">  
    <Output PropertyName="Easy" TaskParameter="Value" />  
</CreateProperty>  
```  
  
 Isso cria a propriedade fácil, que tem o valor “123 " mesmo se o destino é executado ou saltado.  
  
```  
<CreateItem Include="a.cs;b.cs">  
    <Output ItemName="Simple" TaskParameter="Include" />  
</CreateItem>  
```  
  
 Isso cria o tipo de item, que tem dois itens, a.cs “simples” e “b.cs”, mesmo se o destino é executado ou saltado.  
  
 Iniciando em MSBuild 3.5, inferência de saída é executada automaticamente em grupos de itens e de propriedade em um destino.  as tarefas de`CreateItem` não são necessárias em um destino e devem ser evitadas.  Além disso, as tarefas de `CreateProperty` devem ser usadas em um destino somente para determinar se um destino foi executado.  
  
## Determinando se um destino foi executado  
 Devido a inferência de saída, você precisa adicionar uma tarefa de `CreateProperty` a um destino examinar propriedades e itens de modo que você possa determinar se o destino foi executado.  Adicione a tarefa de `CreateProperty` de destino e dê a ela um elemento de `Output` cujo `TaskParameter` é “ValueSetByTask”.  
  
```  
<CreateProperty Value="true">  
    <Output TaskParameter="ValueSetByTask" PropertyName="CompileRan" />  
</CreateProperty>  
```  
  
 Isso cria a propriedade CompileRan e concede\-se o valor `true`, mas somente se o destino for executado.  Se o destino for saltado, CompileRan não é criado.  
  
## Consulte também  
 [Destinos](../msbuild/msbuild-targets.md)