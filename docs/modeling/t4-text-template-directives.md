---
title: T4 Diretivas de modelo de texto | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- text templates, import directive
- text templates, include directive
- text templates, assembly directive
- text templates, output directive
- text templates, directives
- text templates, template directive
ms.assetid: 6898ee02-ebb2-4635-a4e9-350774c13cf2
caps.latest.revision: 81
author: alancameronwills
ms.author: awills
manager: douge
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
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 63e07b4fbdc122411ccfa1db8bf78d8d3fc21ebf
ms.lasthandoff: 02/22/2017

---
# <a name="t4-text-template-directives"></a>Diretivas de modelo de texto T4
As diretivas fornecem instruções para o mecanismo de transformação do modelo de texto.  
  
 A sintaxe das diretivas é a seguinte:  
  
```  
<#@ DirectiveName [AttributeName = "AttributeValue"] ... #>  
```  
  
 Todos os valores dos atributos devem estar entre aspas duplas. Se o próprio valor contiver aspas, elas devem ser substituídas pelo caractere \.  
  
 As diretivas são normalmente os primeiros elementos de um arquivo de modelo ou de um arquivo incluído. Você não deve inseri-las em um bloco de códigos `<#...#>`, nem depois de um bloco de recursos da classe `<#+...#>`.  
  
 [Diretiva de modelo T4](../modeling/t4-template-directive.md)  
 ```  
<#@ template [language="VB"] [hostspecific="true|TrueFromBase"] [debug="true"] [inherits="templateBaseClass"] [culture="code"] [compilerOptions="options"] [visibility="internal"] [linePragmas="false"] #>  
```  
  
 [Diretiva de parâmetro T4](../modeling/t4-parameter-directive.md)  
 ```  
<#@ parameter type="Full.TypeName" name="ParameterName" #>  
```  
  
 [Diretiva de saída T4](../modeling/t4-output-directive.md)  
 ```  
<#@ output extension=".fileNameExtension" [encoding="encoding"] #>  
```  
  
 [Diretiva de assembly T4](../modeling/t4-assembly-directive.md)  
 ```  
<#@ assembly name="[assembly strong name|assembly file name]" #>  
```  
  
 [Diretiva de importação T4](../modeling/t4-import-directive.md)  
 ```  
<#@ import namespace="namespace" #>  
```  
  
 [Diretiva de inclusão T4](../modeling/t4-include-directive.md)  
 ```  
<#@ include file="filePath" #>  
```  
  
 [Diretiva CleanUpBehavior T4](../modeling/t4-cleanupbehavior-directive.md)  
 ```  
<#@ CleanupBehavior processor="T4VSHost" CleanupAfterProcessingtemplate="true" #>  
```  
  
 Além disso, você pode criar suas próprias diretivas. Para obter mais informações, consulte [criação personalizada T4 texto modelo diretiva processadores](../modeling/creating-custom-t4-text-template-directive-processors.md). Se você usar o SDK de Visualização e Modelagem para criar uma linguagem específica do domínio (DSL), um processador de diretriz será gerado como parte da DSL.
