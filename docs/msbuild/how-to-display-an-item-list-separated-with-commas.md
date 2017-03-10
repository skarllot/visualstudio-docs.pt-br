---
title: "Como exibir uma lista de itens separada por v&#237;rgulas | Microsoft Docs"
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
  - "MSBuild, formatando coleções de itens"
  - "MSBuild, separando itens com ponto e vírgula"
ms.assetid: 3cae844c-7c6d-4144-82dc-efad10ba458f
caps.latest.revision: 12
caps.handback.revision: 12
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Como exibir uma lista de itens separada por v&#237;rgulas
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Quando você trabalha com o item de lista em [!INCLUDE[vstecmsbuildengine](../msbuild/includes/vstecmsbuildengine_md.md)] \([!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]\), às vezes é útil exibir o conteúdo de que essas listas de itens de uma maneira fácil de ler.  Ou então, você pode ter uma tarefa que leva a uma lista de itens separados por uma seqüência de caracteres de separador especial.  Em ambos os casos, você pode especificar uma seqüência de caracteres separadores para uma lista de itens.  
  
## Separando os itens em uma lista com vírgulas  
 Por padrão, [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] usa o ponto e vírgula para separar itens em uma lista.  Por exemplo, considere um `Message` elemento com o seguinte valor:  
  
 `<Message Text="This is my list of TXT files: @(TXTFile)"/>`  
  
 Quando o `@(TXTFile)` item de lista contém os itens de App1.txt, App2.txt e App3.txt, a mensagem é:  
  
 `This is my list of TXT files: App1.txt;App2.txt;App3.txt`  
  
 Se você quiser alterar o comportamento padrão, você pode especificar seu próprio separador.  A sintaxe para especificar um separador de lista de item é:  
  
 `@(ItemListName, '<separator>')`  
  
 O separador pode ser um único caractere ou uma seqüência de caracteres e deve ser colocado entre aspas simples.  
  
#### Para inserir uma vírgula e um espaço entre os itens  
  
-   Use a notação de item semelhante à seguinte:  
  
     `@(TXTFile, ', ')`  
  
## Exemplo  
 Neste exemplo,  [Exec](../msbuild/exec-task.md) tarefa executa a ferramenta findstr para localizar seqüências de texto especificado no arquivo, Phrases.txt.  O comando findstr, seqüências de pesquisa literal são indicadas pela **\/c:** alternar, isso o separador de item, `/c:` é inserido entre os itens a `@(Phrase)` lista de itens.  
  
 Neste exemplo, a linha de comando equivalente é:  
  
 `findstr /i /c:hello /c:world /c:msbuild phrases.txt`  
  
```  
<Project DefaultTargets = "Find"  
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003" >  
  
    <ItemGroup>  
        <Phrase Include="hello"/>  
        <Phrase Include="world"/>  
        <Phrase Include="msbuild"/>  
    </ItemGroup>  
  
    <Target Name = "Find">  
        <!-- Find some strings in a file -->  
        <Exec Command="findstr /i /c:@(Phrase, ' /c:') phrases.txt"/>  
    </Target>  
</Project>  
```  
  
## Consulte também  
 [Referência do MSBuild](../msbuild/msbuild-reference.md)   
 [Itens](../msbuild/msbuild-items.md)