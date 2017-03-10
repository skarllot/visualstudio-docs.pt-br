---
title: "Tarefa XDCMake | Microsoft Docs"
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
  - "vc.task.xdcmake"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
  - "C++"
helpviewer_keywords: 
  - "MSBuild (Visual C++), tarefa XDCMake"
  - "tarefa XDCMake (MSBuild (Visual C++))"
ms.assetid: a7de9c64-903a-4a02-85f3-f37672270f25
caps.latest.revision: 7
caps.handback.revision: 7
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Tarefa XDCMake
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Delimita a ferramenta de documentação XML \(xdcmake.exe\), que mescla arquivos de comentário \(.xdc\) do documento XML em um arquivo. XML.  
  
 Um arquivo de .xdc é criado quando você fornece comentários de documentação no seu código\-fonte do Visual C\+\+ e a compilação, usando o  [\/doc](/visual-cpp/build/reference/doc-process-documentation-comments-c-cpp) opção de compilador.  Para obter mais informações, consulte [Referência XDCMake](/visual-cpp/ide/xdcmake-reference), [Páginas de propriedade da ferramenta geradora de documento XML](/visual-cpp/ide/xml-document-generator-tool-property-pages)e a opção de ajuda de linha de comando \(**\/?**\) para xdcmake.exe.  
  
## Comentários  
 Por padrão, a ferramenta xdcmake.exe oferece suporte a algumas opções de linha de comando.  Há suporte para opções adicionais quando você especifica o **\/old** a opção de linha de comando.  
  
## Parâmetros  
 A tabela a seguir descreve os parâmetros da **XDCMake** tarefa.  
  
|Parâmetro|Descrição|  
|---------------|---------------|  
|**AdditionalDocumentFile**|Opcional **String\[\]** parâmetro.<br /><br /> Especifica um ou mais arquivos de .xdc adicionais para mesclar.<br /><br /> Para obter mais informações, consulte o  **Arquivos adicionais do documento** descrição na [Páginas de propriedade da ferramenta geradora de documento XML](/visual-cpp/ide/xml-document-generator-tool-property-pages).  Consulte também o **\/old** e **\/Fs** opções de linha de comando para xdcmake.exe.|  
|**AdditionalOptions**|Opcional **String** parâmetro.<br /><br /> Uma lista de opções, conforme especificado na linha de comando.  Por exemplo, "*\/option\# de \/option2 \/option1*".  Use este parâmetro para especificar as opções que não são representadas por outros **XDCMake** parâmetro da tarefa.<br /><br /> Para obter mais informações, consulte [Referência XDCMake](/visual-cpp/ide/xdcmake-reference), [Páginas de propriedade da ferramenta geradora de documento XML](/visual-cpp/ide/xml-document-generator-tool-property-pages)e a Ajuda de linha de comando \(**\/?**\) para xdcmake.exe.|  
|**DocumentLibraryDependencies**|Opcional **Boolean** parâmetro.<br /><br /> Se `true` e o projeto atual tem uma dependência em um projeto de biblioteca estática \(. lib\) na solução, os arquivos de .xdc para o projeto biblioteca estão incluídos na saída de arquivo. XML para o projeto atual.<br /><br /> Para obter mais informações, consulte o  **As dependências da biblioteca de documentos** descrição na [Páginas de propriedade da ferramenta geradora de documento XML](/visual-cpp/ide/xml-document-generator-tool-property-pages).|  
|**OutputFile**|Opcional **String** parâmetro.<br /><br /> Substitui o nome do arquivo de saída padrão.  O nome padrão é derivado do nome do primeiro arquivo .xdc que é processado.<br /><br /> Para obter mais informações, consulte o **\/out:**`filename` de opção em [Referência XDCMake](/visual-cpp/ide/xdcmake-reference).  Consulte também o **\/old** e **\/Fo** opções de linha de comando para xdcmake.exe.|  
|**ProjectName**|Opcional **String** parâmetro.<br /><br /> O nome do projeto atual.|  
|**SlashOld**|Opcional **Boolean** parâmetro.<br /><br /> Se `true`, permite opções adicionais de xdcmake.exe.<br /><br /> Para obter mais informações, consulte o **\/old** a opção de linha de comando para xdcmake.exe.|  
|**Sources**|Obrigatório `ITaskItem[]` parâmetro.<br /><br /> Define uma matriz dos itens de arquivo de origem MSBuild que pode ser consumido e emitido por tarefas.|  
|**SuppressStartupBanner**|Opcional **Boolean** parâmetro.<br /><br /> Se `true`, impede a exibição da mensagem de número de versão e copyright quando a tarefa for iniciada.<br /><br /> Para obter mais informações, consulte o **\/nologo** de opção em [Referência XDCMake](/visual-cpp/ide/xdcmake-reference).|  
|**TrackerLogDirectory**|Opcional **String** parâmetro.<br /><br /> Especifica o diretório para o log do controlador.|  
  
## Consulte também  
 [Referência de tarefas](../msbuild/msbuild-task-reference.md)