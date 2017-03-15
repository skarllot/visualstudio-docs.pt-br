---
title: Tarefa de aviso | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#Warning
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- Warning task [MSBuild]
- MSBuild, Warning task
ms.assetid: 96ba5507-8b43-4f54-a1d7-9b15644dd56c
caps.latest.revision: 18
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Human Translation
ms.sourcegitcommit: 79460291e91f0659df0a4241e17616e55187a0e2
ms.openlocfilehash: b5130191907d15a49bb52a1c522376e6d0bb3447
ms.lasthandoff: 02/22/2017

---
# <a name="warning-task"></a>Tarefa Warning
Registra um aviso durante um build com base em uma instrução condicional avaliada.  
  
## <a name="parameters"></a>Parâmetros  
 A tabela a seguir descreve os parâmetros da tarefa `Warning`.  
  
|Parâmetro|Descrição|  
|---------------|-----------------|  
|`Code`|Parâmetro `String` opcional.<br /><br /> O código de erro que será associado ao aviso.|  
|`File`|Parâmetro `String` opcional.<br /><br /> Especifica o arquivo relevante, se houver. Se nenhum arquivo for fornecido, o arquivo que contém a tarefa de aviso será usado.|  
|`HelpKeyword`|Parâmetro `String` opcional.<br /><br /> A palavra-chave Ajuda que será associada ao aviso.|  
|`Text`|Parâmetro `String` opcional.<br /><br /> O texto de aviso que [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] registra se o parâmetro `Condition` resultar em `true`.|  
  
## <a name="remarks"></a>Comentários  
 A tarefa `Warning` permite que projetos [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] verifiquem a presença de uma configuração necessária ou propriedade antes de continuar com a próxima etapa de build.  
  
 Se o parâmetro `Condition` da tarefa `Warning` for avaliada como `true`, o valor do parâmetro `Text` será registrado e o build continuará a ser executada. Se um parâmetro `Condition` não existir, o texto de aviso será registrado. Para obter mais informações sobre registro, consulte [Obter logs de build](../msbuild/obtaining-build-logs-with-msbuild.md).  
  
 Além dos parâmetros listados acima, essa tarefa herda parâmetros da classe <xref:Microsoft.Build.Tasks.TaskExtension>, que, por sua vez, herda da classe <xref:Microsoft.Build.Utilities.Task>. Para obter uma lista desses parâmetros adicionais e suas descrições, consulte [Classe base TaskExtension](../msbuild/taskextension-base-class.md).  
  
## <a name="example"></a>Exemplo  
 O exemplo de código a seguir verifica as propriedades que são definidas na linha de comando. Se nenhuma propriedade estiver definida, o projeto gerará um evento de aviso e registrará o valor do parâmetro `Text` da tarefa `Warning`.  
  
```xml  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <Target Name="ValidateCommandLine">  
        <Warning  
            Text=" The 0 property was not set on the command line."  
            Condition="'$(0)' == ''" />  
        <Warning  
            Text=" The FREEBUILD property was not set on the command line."  
            Condition="'$(FREEBUILD)' == ''" />  
    </Target>  
    ...  
</Project>  
```  
  
## <a name="see-also"></a>Consulte também  
 [Obtaining Build Logs (Obtendo logs de build)](../msbuild/obtaining-build-logs-with-msbuild.md)   
 [Referência do esquema de arquivos de projeto](../msbuild/msbuild-project-file-schema-reference.md)
