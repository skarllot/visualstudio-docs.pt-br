---
title: "Tarefa ResolveComReference | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/developer/msbuild/2003#ResolveComReference"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "MSBuild, Tarefa ResolveCOMReference"
  - "Tarefa ResolveCOMReference [MSBuild]"
ms.assetid: c9bf5fcf-6453-40ea-b50f-a212adc3e9b5
caps.latest.revision: 26
caps.handback.revision: 26
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Tarefa ResolveComReference
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Leva uma lista de um ou vários nomes de biblioteca de tipo ou .tlb arquivos e resolve essas bibliotecas de tipo em locais no disco.  
  
## Parâmetros  
 A tabela a seguir descreve os parâmetros de tarefa de `ResolveCOMReference` .  
  
|Parâmetro|Descrição|  
|---------------|---------------|  
|`DelaySign`|parâmetro opcional de `Boolean` .<br /><br /> Se `true`locais, a chave pública do assembly.  Se `false`, assina o assembly totalmente.|  
|`EnvironmentVariables`|parâmetro opcional de `String[]` .<br /><br /> Matriz de pares de variáveis de ambiente, separados por sinais de igual.  Essas variáveis são passados para o tlbimp.exe e o aximp.exe além de isso, ou substituir seletivamente a desovado, o bloco normal de ambiente.|  
|`ExecuteAsTool`|parâmetro opcional de `Boolean` .<br /><br /> Se `true`, executa tlbimp.exe e aximp.exe fora de proc apropriado do framework de destino para gerar conjuntos necessários do wrapper.  Este parâmetro permite que o multi\-targeting.|  
|`IncludeVersionInInteropName`|parâmetro opcional de `Boolean` .<br /><br /> Se `true`, a versão de typelib será incluído no nome do wrapper.  O padrão é `false`.|  
|`KeyContainer`|parâmetro opcional de `String` .<br /><br /> Especifica um contêiner que contém um chaves pública\/particular<br /><br /> par de chaves.|  
|`KeyFile`|parâmetro opcional de `String` .<br /><br /> Especifica um item que contém um chaves pública\/particular<br /><br /> par de chaves.|  
|`NoClassMembers`|parâmetro opcional de `Boolean` .|  
|`ResolvedAssemblyReferences`|parâmetro de saída opcional de <xref:Microsoft.Build.Framework.ITaskItem>`[]` .<br /><br /> Especifica as referências resolvidas do assembly.|  
|`ResolvedFiles`|parâmetro de saída opcional de <xref:Microsoft.Build.Framework.ITaskItem>`[]` .<br /><br /> Especifica os arquivos totalmente qualificados no disco locais físicos que correspondem às bibliotecas de tipo que foram fornecidas como entrada a essa tarefa.|  
|`ResolvedModules`|parâmetro opcional de <xref:Microsoft.Build.Framework.ITaskItem>`[]` .|  
|`SdkToolsPath`|parâmetro opcional de [String](assetId:///String?qualifyHint=False&autoUpgrade=True) .<br /><br /> Se `ExecuteAsTool` é `true`, este parâmetro deve ser definido para o caminho de ferramentas SDK para a versão do framework que está sendo destino.|  
|`StateFile`|parâmetro opcional de assetId:///String?qualifyHint=False&autoUpgrade=True .<br /><br /> Especifica o arquivo de cache para carimbos de data\/hora o componente COM.  Se não presentes, cada execução regenerará todos os wrappers.|  
|`TargetFrameworkVersion`|parâmetro opcional de assetId:///String?qualifyHint=False&autoUpgrade=True .<br /><br /> Especifica a versão do framework de destino do projeto.<br /><br /> O padrão é `String.Empty`.  o que significa há nenhuma filtragem para uma referência com base na estrutura de destino.|  
|`TargetProcessorArchitecture`|parâmetro opcional de assetId:///String?qualifyHint=False&autoUpgrade=True .<br /><br /> Especifica a arquitetura do processador preferencial de destino.  Passado para o sinalizador tlbimp.exe \/machine após a conversão.<br /><br /> O valor do parâmetro deve ser um membro de <xref:Microsoft.Build.Utilities.ProcessorArchitecture>.|  
|`TypeLibFiles`|parâmetro opcional de <xref:Microsoft.Build.Framework.ITaskItem>`[]` .<br /><br /> Especifica o caminho do arquivo de biblioteca de tipos para referências COM.  Os itens incluídos em este parâmetro podem conter metadados do item.  Para obter mais informações, consulte a seção “de metadados de item TypeLibFiles” abaixo.|  
|`TypeLibNames`|parâmetro opcional de <xref:Microsoft.Build.Framework.ITaskItem>`[]` .<br /><br /> Especifica os nomes de biblioteca de tipos para resolver.  Os itens incluídos em este parâmetro devem conter alguns metadados de item.  Para obter mais informações, consulte a seção “de metadados de item TypeLibNames” abaixo.|  
|`WrapperOutputDirectory`|parâmetro opcional de `String` .<br /><br /> O local no disco onde o assembly de interoperabilidade gerado é colocado.  Se os metadados de este item não for especificado, a tarefa usa o caminho absoluto do diretório onde o arquivo de projeto for encontrado.|  
  
## Comentários  
  
## Metadados de item de TypeLibNames  
 A tabela a seguir descreve os metadados de item disponíveis para itens passados para o parâmetro de `TypeLibNames` .  
  
|Metadados|Descrição|  
|---------------|---------------|  
|`GUID`|Metadados necessários de item.<br /><br /> Um GUID para a biblioteca de tipos.  Se os metadados de este item não for especificado, a tarefa falhar.|  
|`VersionMajor`|Metadados necessários de item.<br /><br /> A versão principal de biblioteca de tipo.  Se os metadados de este item não for especificado, a tarefa falhar.|  
|`VersionMinor`|Metadados necessários de item.<br /><br /> A versão secundária de biblioteca de tipo.  Se os metadados de este item não for especificado, a tarefa falhar.|  
|`LocaleIdentifier`|Metadados opcionais de item.<br /><br /> A identificação de localidade \(ou LCID\) para a biblioteca de tipos.  Isso é especificado como um valor de 32 bits que identifica o idioma preferencial humano por um usuário, por uma região, ou por um aplicativo.  Se os metadados de este item não for especificado, a tarefa usa uma identificação de localidade padrão de “0 ".|  
|`WrapperTool`|Metadados opcionais de item.<br /><br /> Especifica a ferramenta de wrapper que é usada para gerar o wrapper assembly para esta biblioteca de tipo.  Se os metadados de este item não for especificado, a tarefa usa uma ferramenta padrão de wrapper “tlbimp”.  As opções disponíveis, sem diferenciação de maiúsculas e minúsculas de typelibs são:<br /><br /> -   `Primary`: Use essa ferramenta envoltório quando você desejar usar um assembly de interoperabilidade primária já gerado para o componente COM.  Quando você usa essa ferramenta envoltório, não especificar um diretório de saída do wrapper porque isso fará com que a tarefa falhar.<br />-   `TLBImp`: Use essa ferramenta envoltório quando você desejar gerar um assembly de interoperabilidade para o componente COM.<br />-   `AXImp`: Use essa ferramenta envoltório quando você desejar gerar um assembly de interoperabilidade para um controle ActiveX.|  
  
## Metadados de item de TypeLibFiles  
 A tabela a seguir descreve os metadados de item disponíveis para itens passados para o parâmetro de `TypeLibFiles` .  
  
|Metadados|Descrição|  
|---------------|---------------|  
|`WrapperTool`|Metadados opcionais de item.<br /><br /> Especifica a ferramenta de wrapper que é usada para gerar o wrapper assembly para esta biblioteca de tipo.  Se os metadados de este item não for especificado, a tarefa usa uma ferramenta padrão de wrapper “tlbimp”.  As opções disponíveis, sem diferenciação de maiúsculas e minúsculas de typelibs são:<br /><br /> -   `Primary`: Use essa ferramenta envoltório quando você desejar usar um assembly de interoperabilidade primária já gerado para o componente COM.  Quando você usa essa ferramenta envoltório, não especificar um diretório de saída do wrapper porque isso fará com que a tarefa falhar.<br />-   `TLBImp`: Use essa ferramenta envoltório quando você desejar gerar um assembly de interoperabilidade para o componente COM.<br />-   `AXImp`: Use essa ferramenta envoltório quando você desejar gerar um assembly de interoperabilidade para um controle ActiveX.|  
  
> [!NOTE]
>  Mais informações que você fornece para identificar exclusivamente uma biblioteca de tipo, quanto maior a possibilidade que a tarefa resolvidos para o arquivo correto no disco.  
  
## Comentários  
 Além dos parâmetros listados acima, esta tarefa parâmetros herda da classe de <xref:Microsoft.Build.Utilities.Task> .  Para obter uma lista de esses parâmetros adicionais e suas descrições, consulte [Classe base Task](../msbuild/task-base-class.md).  
  
## Consulte também  
 [ \(tarefas\)](../msbuild/msbuild-tasks.md)   
 [Referência de tarefas](../msbuild/msbuild-task-reference.md)