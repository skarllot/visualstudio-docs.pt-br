---
title: Tarefa Erro | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#Error
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- Error task [MSBuild]
- MSBuild, Error task
ms.assetid: e96a90ee-a8ae-4e5b-8ef2-b5cf5fedd8b2
caps.latest.revision: 20
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
ms.openlocfilehash: 8318edf692f5149b506f7535bae41fa3f43e8061

---
# <a name="error-task"></a>Tarefa Error
Interrompe um build e registra um erro com base em uma instrução condicional avaliada.  
  
## <a name="parameters"></a>Parâmetros  
 A tabela a seguir descreve os parâmetros da tarefa `Error`.  
  
|Parâmetro|Descrição|  
|---------------|-----------------|  
|`Code`|Parâmetro `String` opcional.<br /><br /> O código de erro a associar ao erro.|  
|`File`|Parâmetro `String` opcional.<br /><br /> O nome do arquivo que contém o erro. Se nenhum nome de arquivo for fornecido, o arquivo que contém a tarefa de erro será usado.|  
|`HelpKeyword`|Parâmetro `String` opcional.<br /><br /> A palavra-chave Ajuda a ser associada ao erro.|  
|`Text`|Parâmetro `String` opcional.<br /><br /> O texto do erro que [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] registra se o parâmetro `Condition` resultar em `true`.|  
  
## <a name="remarks"></a>Comentários  
 A tarefa `Error` permite que projetos [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] emitam o texto de erro para agentes e interrompe a execução de build.  
  
 Se o parâmetro `Condition` avaliar `true`, o build será interrompido e um erro será registrado. Se um parâmetro `Condition` não existir, o erro será registrado e a execução de build será interrompida. Para obter mais informações sobre registro, consulte [Obter logs de build](../msbuild/obtaining-build-logs-with-msbuild.md).  
  
 Além dos parâmetros listados acima, essa tarefa herda parâmetros da classe <xref:Microsoft.Build.Tasks.TaskExtension>, que, por sua vez, herda da classe <xref:Microsoft.Build.Utilities.Task>. Para obter uma lista desses parâmetros adicionais e suas descrições, consulte [Classe base TaskExtension](../msbuild/taskextension-base-class.md).  
  
## <a name="example"></a>Exemplo  
 O exemplo de código a seguir verifica se todas as propriedades necessárias estão definidas. Se elas não estiverem definidas, o projeto gerará um evento de erro e registrará o valor do parâmetro `Text` da tarefa `Error`.  
  
```xml  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <Target Name="ValidateCommandLine">  
        <Error  
            Text=" The 0 property must be set on the command line."  
            Condition="'$(0)' == ''" />  
        <Error  
            Text="The FREEBUILD property must be set on the command line."  
            Condition="'$(FREEBUILD)' == ''" />  
    </Target>  
    ...  
</Project>  
```  
  
## <a name="see-also"></a>Consulte também  
 [Referência de tarefas](../msbuild/msbuild-task-reference.md)   
 [Obtendo Logs de Build](../msbuild/obtaining-build-logs-with-msbuild.md)


<!--HONumber=Feb17_HO4-->


