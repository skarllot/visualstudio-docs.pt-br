---
title: "Tarefa MT | Microsoft Docs"
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
  - "VC.Project.VCManifestTool.ResourceOutputFileName"
  - "VC.Project.VCManifestTool.SuppressDependencyElement"
  - "VC.Project.VCManifestTool.ManifestFromManagedAssembly"
  - "VC.Project.VCManifestTool.GenerateCategoryTags"
  - "VC.Project.VCManifestTool.EnableDPIAwareness"
  - "vc.task.mt"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
  - "C++"
helpviewer_keywords: 
  - "MSBUILD (Visual C++), tarefa MT"
  - "tarefa MT (MSBuild (Visual C++))"
ms.assetid: bb94913c-1042-4968-9f08-b394518e899f
caps.latest.revision: 6
caps.handback.revision: 6
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Tarefa MT
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Ajusta a ferramenta de manifesto da Microsoft, mt.exe.  Para obter mais informações, consulte "Mt.exe" sobre o [MSDN](http://go.microsoft.com/fwlink/?LinkId=737) site da Web.  
  
## Parâmetros  
 A tabela a seguir descreve os parâmetros da **MT** tarefa.  A maioria dos parâmetros da tarefa e alguns conjuntos de parâmetros, correspondem a uma opção de linha de comando.  
  
> [!NOTE]
>  A documentação de mt.exe usa um hífen \(**\-**\) como o prefixo para opções de linha de comando, mas este tópico usa uma barra \(**\/**\).  O prefixo é aceitável.  
  
|Parâmetro|Descrição|  
|---------------|---------------|  
|**AdditionalManifestFiles**|Opcional **String\[\]** parâmetro.<br /><br /> Especifica o nome de um ou mais arquivos de manifesto.<br /><br /> Para obter mais informações, consulte o **\/manifest** de opção em "Mt.exe" no [MSDN](http://go.microsoft.com/fwlink/?LinkId=737) site da Web.|  
|**AdditionalOptions**|Opcional **String** parâmetro.<br /><br /> Uma lista de opções de linha de comando.  Por exemplo, "*\/option\# de \/option2 \/option1*".  Use este parâmetro para especificar as opções de linha de comando que não são representadas por outros **MT** parâmetro da tarefa.<br /><br /> Para obter mais informações, consulte "Mt.exe" sobre o [MSDN](http://go.microsoft.com/fwlink/?LinkId=737) site da Web.|  
|**AssemblyIdentity**|Opcional **String** parâmetro.<br /><br /> Especifica os valores de atributo da **assemblyIdentity** elemento do manifesto.  Especificar uma lista delimitada por vírgulas, onde o primeiro componente é o valor da `name` atributo, seguido por um ou mais pares nome\/valor que têm a forma,  *\< nome do atributo \> \= \<attribute\_value\>*.<br /><br /> Para obter mais informações, consulte o **\/identity** de opção em "Mt.exe" no [MSDN](http://go.microsoft.com/fwlink/?LinkId=737) site da Web.|  
|**ComponentFileName**|Opcional **String** parâmetro.<br /><br /> Especifica o nome da biblioteca de vínculo dinâmico que você pretende criar dos arquivos. rgs ou. tlb.  Este parâmetro é obrigatório se você especificar o **RegistrarScriptFile** ou **TypeLibraryFile** parâmetros da tarefa de MT.<br /><br /> Para obter mais informações, consulte o **\/dll** de opção em "Mt.exe" no [MSDN](http://go.microsoft.com/fwlink/?LinkId=737) site da Web.|  
|**DependencyInformationFile**|Opcional **String** parâmetro.<br /><br /> Especifica o arquivo das informações de dependência usado pelo Visual Studio para rastrear as informações de dependência de compilação para a ferramenta de manifesto.|  
|**EmbedManifest**|Opcional `Boolean` parâmetro.<br /><br /> Se `true`, incorpora o arquivo de manifesto do assembly.  Se `false`, cria\-se como um arquivo de manifesto autônomo.|  
|**EnableDPIAwareness**|Opcional `Boolean` parâmetro.<br /><br /> Se `true`, adiciona as informações de manifesto que marca o aplicativo como o reconhecimento de DPI.  Escrevendo um aplicativo com reconhecimento de DPI faz com que uma interface de usuário pode parecer um bom entre uma grande variedade de configurações de vídeo de alta DPI.<br /><br /> Para obter mais informações, consulte "DPI alta" sobre o [MSDN](http://go.microsoft.com/fwlink/?LinkId=737) site da Web.|  
|**GenerateCatalogFiles**|Opcional `Boolean` parâmetro.<br /><br /> Se `true`, gera arquivos de definição \(. CDF\) do catálogo.<br /><br /> Para obter mais informações, consulte o **\/makecdfs** de opção em "Mt.exe" no [MSDN](http://go.microsoft.com/fwlink/?LinkId=737) site da Web.|  
|**GenerateCategoryTags**|Opcional `Boolean` parâmetro.<br /><br /> Se `true`, faz com que as marcas de categoria a ser gerado.  Se este parâmetro for `true`, o **ManifestFromManagedAssemblyMT** também deve ser especificado o parâmetro da tarefa.<br /><br /> Para obter mais informações, consulte o **\/category** de opção em "Mt.exe" no [MSDN](http://go.microsoft.com/fwlink/?LinkId=737) site da Web.|  
|**InputResourceManifests**|Opcional **String** parâmetro.<br /><br /> O manifesto de um recurso do tipo RT\_MANIFEST que possui o identificador especificado de entrada.  Especificar um recurso do formulário,  *\<file\> \[***;****\#***\] \<resource\_id\>*, onde o opcional `resource_id` parâmetro é um número negativo e 16 bits.<br /><br /> Se nenhum `resource_id` for especificado, será usado o valor padrão CREATEPROCESS\_MANIFEST\_RESOURCE \(1\).<br /><br /> Para obter mais informações, consulte o **\/inputresource** de opção em "Mt.exe" no [MSDN](http://go.microsoft.com/fwlink/?LinkId=737) site da Web.|  
|**ManifestFromManagedAssembly**|Opcional **String** parâmetro.<br /><br /> Gera um manifesto do assembly gerenciado especificado.<br /><br /> Para obter mais informações, consulte o **\/managedassemblyname** de opção em "Mt.exe" no [MSDN](http://go.microsoft.com/fwlink/?LinkId=737) site da Web.|  
|**ManifestToIgnore**|Opcional **String** parâmetro.<br /><br /> \(Não usada\).|  
|**OutputManifestFile**|Opcional **String** parâmetro.<br /><br /> Especifica o nome do manifesto de saída.  Se este parâmetro for omitido e somente um manifesto está sendo operado no, esse manifesto é modificado no lugar.<br /><br /> Para obter mais informações, consulte o **\/out** de opção em "Mt.exe" no [MSDN](http://go.microsoft.com/fwlink/?LinkId=737) site da Web.|  
|**OutputResourceManifests**|Opcional **String** parâmetro.<br /><br /> O manifesto para um recurso do tipo RT\_MANIFEST que possui o identificador especificado de saída.  O recurso é do formulário,  *\<file\> \[***;****\#***\] \<resource\_id\>*, onde o opcional `resource_id` parâmetro é um número negativo e 16 bits.<br /><br /> Se nenhum `resource_id` for especificado, será usado o valor padrão CREATEPROCESS\_MANIFEST\_RESOURCE \(1\).<br /><br /> Para obter mais informações, consulte o **\/outputresource** de opção em "Mt.exe" no [MSDN](http://go.microsoft.com/fwlink/?LinkId=737) site da Web.|  
|**RegistrarScriptFile**|Opcional **String** parâmetro.<br /><br /> Especifica o nome do arquivo de script \(. rgs\) registrador a ser usado para o suporte de manifesto de COM sem registro.<br /><br /> Para obter mais informações, consulte o **\/rgs** de opção em "Mt.exe" no [MSDN](http://go.microsoft.com/fwlink/?LinkId=737) site da Web.|  
|**ReplacementsFile**|Opcional **String** parâmetro.<br /><br /> Especifica o arquivo que contém valores para as seqüências de caracteres substituíveis no arquivo de script \(. rgs\) do registrador.<br /><br /> Para obter mais informações, consulte o **\/replacements** de opção em "Mt.exe" no [MSDN](http://go.microsoft.com/fwlink/?LinkId=737) site da Web.|  
|**ResourceOutputFileName**|Opcional **String** parâmetro.<br /><br /> Especifica o arquivo de recurso de saída usado para incorporar o manifesto na saída do projeto.|  
|**Sources**|Opcional `ITaskItem[]` parâmetro.<br /><br /> Especifica uma lista dos arquivos de origem de manifesto, separados por espaços.<br /><br /> Para obter mais informações, consulte o **\/manifest** de opção em "Mt.exe" no [MSDN](http://go.microsoft.com/fwlink/?LinkId=737) site da Web.|  
|**SuppressDependencyElement**|Opcional `Boolean` parâmetro.<br /><br /> Se `true`, gera um manifesto sem elementos de dependência.  Se este parâmetro for `true`, também especificar o **ManifestFromManagedAssemblyMT** parâmetro da tarefa.<br /><br /> Para obter mais informações, consulte o **\/nodependency** de opção em "Mt.exe" no [MSDN](http://go.microsoft.com/fwlink/?LinkId=737) site da Web.|  
|**SuppressStartupBanner**|Opcional `Boolean` parâmetro.<br /><br /> Se `true`, impede a exibição da mensagem de número de versão e copyright quando a tarefa for iniciada.<br /><br /> Para obter mais informações, consulte o **\/nologo** de opção em "Mt.exe" no [MSDN](http://go.microsoft.com/fwlink/?LinkId=737) site da Web.|  
|**TrackerLogDirectory**|Opcional `String` parâmetro.<br /><br /> Especifica o diretório intermediário onde estão armazenados os logs de controle para esta tarefa.|  
|**TypeLibraryFile**|Opcional **String** parâmetro.<br /><br /> Especifica o nome do arquivo de biblioteca \(. tlb\) de tipo.  Se você especificar este parâmetro, especifique também o **ComponentFileNameMT** parâmetro da tarefa.<br /><br /> Para obter mais informações, consulte o **\/tlb** de opção em "Mt.exe" no [MSDN](http://go.microsoft.com/fwlink/?LinkId=737) site da Web.|  
|**UpdateFileHashes**|Opcional `Boolean` parâmetro.<br /><br /> Se `true`, calcula o valor de hash dos arquivos no caminho especificado pelo **UpdateFileHashesSearchPathMT** parâmetro da tarefa e atualiza o valor da **hash** atributo da **file** elemento do manifesto usando o valor calculado.<br /><br /> Para obter mais informações, consulte o **\/hashupdate** de opção em "Mt.exe" no [MSDN](http://go.microsoft.com/fwlink/?LinkId=737) site da Web.  Consulte também o **UpdateFileHashesSearchPath** parâmetro nesta tabela.|  
|**UpdateFileHashesSearchPath**|Opcional `String` parâmetro.<br /><br /> Especifica o caminho de pesquisa a ser usado quando os hashes de arquivo são atualizados.  Use este parâmetro com o **UpdateFileHashesMT** parâmetro da tarefa.<br /><br /> Para obter mais informações, consulte o **UpdateFileHashes** parâmetro nesta tabela.|  
|**VerboseOutput**|Opcional `Boolean` parâmetro.<br /><br /> Se `true`, exibe informações detalhadas de depuração.<br /><br /> Para obter mais informações, consulte o **\/verbose** de opção em "Mt.exe" no [MSDN](http://go.microsoft.com/fwlink/?LinkId=737) site da Web.|  
  
## Comentários  
  
## Consulte também  
 [Referência de tarefas](../msbuild/msbuild-task-reference.md)