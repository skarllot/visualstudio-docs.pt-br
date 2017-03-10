---
title: "Tarefa Warning | Microsoft Docs"
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
  - "http://schemas.microsoft.com/developer/msbuild/2003#Warning"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "MSBuild, tarefa Warning"
  - "tarefa Warning [MSBuild]"
ms.assetid: 96ba5507-8b43-4f54-a1d7-9b15644dd56c
caps.latest.revision: 18
caps.handback.revision: 18
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Tarefa Warning
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Logs um aviso durante uma compilação com base em uma instrução condicional avaliada.  
  
## Parâmetros  
 A tabela a seguir descreve os parâmetros da `Warning` tarefa.  
  
|Parâmetro|Descrição|  
|---------------|---------------|  
|`Code`|Opcional `String` parâmetro.<br /><br /> O código de aviso para associar o aviso.|  
|`File`|Opcional `String` parâmetro.<br /><br /> Especifica o arquivo relevante, se houver.  Se nenhum arquivo for fornecido, o arquivo que contém a tarefa de aviso é usado.|  
|`HelpKeyword`|Opcional `String` parâmetro.<br /><br /> A Ajuda palavra\-chave para associar o aviso.|  
|`Text`|Opcional `String` parâmetro.<br /><br /> O texto do aviso que [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] registra se o `Condition` parâmetro resultar em `true`.|  
  
## Comentários  
 O `Warning` tarefa permite que [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] projetos para verificar a presença de uma configuração necessária ou a propriedade antes de prosseguir com a próxima etapa de compilação.  
  
 Se a `Condition` parâmetro da `Warning` tarefa é avaliada como `true`, o valor da `Text` parâmetro é registrado e a compilação continua a executar.  Se um `Condition` parâmetro faz não exisit, o texto de aviso é registrado.  Para obter mais informações sobre o registro em log, consulte [Obtendo logs de compilação](../msbuild/obtaining-build-logs-with-msbuild.md).  
  
 Com os parâmetros listados acima, esta tarefa herda os parâmetros da <xref:Microsoft.Build.Tasks.TaskExtension> herda de classe, que por si só a <xref:Microsoft.Build.Utilities.Task> classe.  Para obter uma lista desses parâmetros adicionais e suas descrições, consulte [Classe TaskExtension \(base\)](../msbuild/taskextension-base-class.md).  
  
## Exemplo  
 O exemplo de código a seguir verifica as propriedades que são definidas na linha de comando.  Se não houver nenhum conjunto de propriedades, o projeto dispara um evento de aviso e registra o valor da `Text` parâmetro da `Warning` tarefa.  
  
```  
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
  
## Consulte também  
 [Obtendo logs de compilação](../msbuild/obtaining-build-logs-with-msbuild.md)   
 [Referência do esquema de arquivos de projeto](../msbuild/msbuild-project-file-schema-reference.md)