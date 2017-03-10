---
title: "Substituindo as configura&#231;&#245;es de ToolsVersion | Microsoft Docs"
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
  - "MSBuild, compilando soluções com"
  - "MSBuild, substituindo a configuração ToolsVersion"
ms.assetid: ccd42c07-0fb6-4e8b-9ebb-a6a6db18aa2e
caps.latest.revision: 24
caps.handback.revision: 24
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Substituindo as configura&#231;&#245;es de ToolsVersion
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Você pode alterar o conjunto de ferramentas para projetos e soluções em uma das três maneiras:  
  
1.  usando o `/ToolsVersion` alternar \(ou `/tv`, para breve\) quando você compila o projeto ou a solução de linha de comando  
  
2.  definindo o parâmetro de `ToolsVersion` na tarefa MSBuild  
  
3.  definindo a propriedade `$(ProjectToolsVersion)` em um projeto em uma solução.  Isso permite que você compile um projeto em uma solução com uma versão de Conjunto de Ferramentas que seja diferente dos outros projetos.  
  
## Substituir as Configurações de ToolsVersion de Projetos e Soluções em Compilações da Linha de Comando  
 Embora os projetos do Visual Studio compilem normalmente com o ToolsVersion especificado no arquivo de projeto, você pode usar a opção de `/ToolsVersion` \(ou `/tv`\) na linha de comando para substituir esse valor e compilar todos os projetos e suas dependências de projeto\-a\-projeto com conjunto de ferramentas diferente.  Por exemplo:  
  
```  
msbuild.exe someproj.proj /tv:12.0 /p:Configuration=Debug  
```  
  
 Neste exemplo, todos os projetos são criados usando ToolsVersion 12.0. \(No entanto, consulte a seção “Ordem de precedência” posteriormente neste tópico.\)  
  
 Ao usar a opção de `/tv` na linha de comando, você pode opcionalmente usar a propriedade de `$(ProjectToolsVersion)` em projetos individuais para os compilar com um valor diferente de ToolsVersion dos outros projetos na solução.  
  
## Substituir as Configurações de ToolsVersion Usando o Parâmetro ToolsVersion da Tarefa MSBuild  
 A tarefa MSBuild o principal meio de um projeto compilar outro.  Para permitir que a tarefa de MSBuild compile um projeto com um ToolsVersion diferente do especificado no projeto, ele fornece um parâmetro opcional da tarefa chamado `ToolsVersion`.  O exemplo a seguir demonstra como usar este parâmetro:  
  
1.  Crie um arquivo chamado `projectA.proj` e que contenha o código a seguir:  
  
    ```  
    <Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003"  
    ToolsVersion="12.0">  
  
        <Target Name="go" >   
            <Message Text="projectA.proj" />  
            <Message Text="MSBuildToolsVersion: $(MSBuildToolsVersion)" />  
            <Message Text="MSBuildToolsPath:    $(MSBuildToolsPath)" />  
  
            <MSBuild Projects="projectB.proj"  
                ToolsVersion="2.0"  
                Targets="go" />  
        </Target>  
    </Project>  
    ```  
  
2.  Crie outro arquivo chamado `projectB.proj` e que contenha o código a seguir:  
  
    ```  
    <Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003"  
    ToolsVersion="12.0">  
  
        <Target Name="go">  
            <Message Text="projectB.proj" />  
            <Message Text="MSBuildToolsVersion: $(MSBuildToolsVersion)" />  
            <Message Text="MSBuildToolsPath:    $(MSBuildToolsPath)" />  
        </Target>  
    </Project>  
    ```  
  
3.  Digite o seguinte comando em um prompt de comando:  
  
    ```  
    msbuild projectA.proj /t:go /toolsversion:3.5  
    ```  
  
4.  A seguinte saída aparece.  Para `projectA`, a configuração `/toolsversion:3.5` na linha de comando substitui a configuração `ToolsVersion=12.0` na marca `Project`.  
  
     `ProjectB` é chamado por uma tarefa no `projectA`.  Essa tarefa tem `ToolsVersion=2.0`, que substitui as outras configurações de `ToolsVersion` para `projectB`.  
  
    ```  
    Output:  
      projectA.proj  
      MSBuildToolsVersion: 3.5  
      MSBuildToolsPath:    C:\Windows\Microsoft.NET\Framework\v3.5  
  
      projectB.proj  
      MSBuildToolsVersion: 2.0  
      MSBuildToolsPath:    C:\Windows\Microsoft.NET\Framework\v2.0.50727  
    ```  
  
## Ordem de Precedência  
 A ordem de precedência, decrescente, usada para determinar a `ToolsVersion` é:  
  
1.  O atributo `ToolsVersion` na tarefa do MSBuild usado para criar o projeto, se houver.  
  
2.  O switch `/toolsversion` \(ou `/tv`\) usado no comando msbuild.exe, se houver.  
  
3.  Se a variável de ambiente `MSBUILDTREATALLTOOLSVERSIONSASCURRENT` for definida, então use a `ToolsVersion` atual.  
  
4.  Se a variável de ambiente `MSBUILDTREATHIGHERTOOLSVERSIONASCURRENT` estiver definida e se a `ToolsVersion` definida no arquivo do projeto for maior do que a `ToolsVersion` atual, use a `ToolsVersion` atual.  
  
5.  Se a variável de ambiente `MSBUILDLEGACYDEFAULTTOOLSVERSION` for definida ou se `ToolsVersion` não for definida, então as seguintes etapas serão usadas:  
  
    1.  O atributo `ToolsVersion` do elemento [Project](../msbuild/project-element-msbuild.md) do arquivo de projeto.  Se esse atributo não existir, ele será assumido como a versão atual.  
  
    2.  A versão das ferramentas padrão no arquivo MSBuild.exe.config.  
  
    3.  A versão das ferramentas padrão no registro.  Para obter mais informações, consulte [Configurações padrão e personalizadas do Toolset](../msbuild/standard-and-custom-toolset-configurations.md).  
  
6.  Se a variável de ambiente `MSBUILDLEGACYDEFAULTTOOLSVERSION` não for definido, então as seguintes etapas serão usadas:  
  
    1.  Se a variável de ambiente `MSBUILDDEFAULTTOOLSVERSION` for definida como `ToolsVersion` que existe, use\-a.  
  
    2.  Se `DefaultOverrideToolsVersion` for definido em MSBuild.exe.config, use\-o.  
  
    3.  Se `DefaultOverrideToolsVersion` estiver definido no Registro, use\-o.  
  
    4.  Caso contrário, use `ToolsVersion`atual.  
  
## Consulte também  
 [Multiplataforma](../msbuild/msbuild-multitargeting-overview.md)   
 [Conceitos do MSBuild](../msbuild/msbuild-concepts.md)   
 [Toolset \(ToolsVersion\)](../msbuild/msbuild-toolset-toolsversion.md)   
 [Configurações padrão e personalizadas do Toolset](../msbuild/standard-and-custom-toolset-configurations.md)