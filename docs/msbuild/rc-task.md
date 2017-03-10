---
title: "Tarefa RC | Microsoft Docs"
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
  - "VC.Project.VCResourceCompilerTool.UndefineProcessorDefinitions"
  - "vc.task.rc"
  - "VC.Project.VCResourceCompilerTool.SuppressStartupBanner"
  - "VC.Project.VCResourceCompilerTool.NullTerminateStrings"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
  - "C++"
helpviewer_keywords: 
  - "MSBuild (Visual C++), tarefa RC"
  - "tarefa RC (MSBuild (Visual C++))"
ms.assetid: 2fd26c75-a056-4dda-9f7e-2f90d3748d88
caps.latest.revision: 10
caps.handback.revision: 10
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Tarefa RC
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Ajusta a ferramenta do compilador de recurso do Microsoft Windows, rc. exe.  O **RC** tarefa compila a recursos, como, por exemplo, cursores, ícones, bitmaps, caixas de diálogo e fontes, em um arquivo de recurso \(. res\).  Para obter mais informações, consulte "Recurso compilador" no [MSDN](http://go.microsoft.com/fwlink/?LinkId=737) site da Web.  
  
## Parâmetros  
 A tabela a seguir descreve os parâmetros do RCtarefa.  A maioria dos parâmetros da tarefa e alguns conjuntos de parâmetros, correspondem a uma opção de linha de comando.  
  
|Parâmetro|Descrição|  
|---------------|---------------|  
|**AdditionalIncludeDirectories**|Opcional **String\[\]** parâmetro.<br /><br /> Adiciona uma pasta à lista de diretórios que são pesquisadas por arquivos de inclusão.<br /><br /> Para obter mais informações, consulte o **\/I** de opção em [Usando RC \(A linha de comando de RC\)](http://go.microsoft.com/fwlink/?LinkId=155730) no site do MSDN.|  
|**AdditionalOptions**|Opcional **String** parâmetro.<br /><br /> Uma lista de exemplo de linha de comando optionsor, **"***\/option\# de \/option2 \/option1*".  Use este parâmetro para especificar as opções de linha de comando que não são representadas por outros **RC** parâmetro da tarefa.<br /><br /> Para obter mais informações, consulte as opções no [Usando RC \(A linha de comando de RC\)](http://go.microsoft.com/fwlink/?LinkId=155730) no site do MSDN.|  
|**Culture**|Opcional **String** parâmetro.<br /><br /> Especifica uma identificação de localidade que representa a cultura usada nos recursos.<br /><br /> Para obter mais informações, consulte o **\/l** de opção em [Usando RC \(A linha de comando de RC\)](http://go.microsoft.com/fwlink/?LinkId=155730) no site do MSDN.|  
|**IgnoreStandardIncludePath**|Opcional **Boolean** parâmetro.<br /><br /> Se `true`, impede que o compilador de recursos verificando a variável de ambiente INCLUDE quando procura os arquivos de cabeçalho ou de recurso.<br /><br /> Para obter mais informações, consulte o **\/x** de opção em [Usando RC \(A linha de comando de RC\)](http://go.microsoft.com/fwlink/?LinkId=155730) no site do MSDN.|  
|**NullTerminateStrings**|Opcional **Boolean** parâmetro.<br /><br /> Se `true`, null\-finaliza todas as seqüências da tabela de cadeia de caracteres.<br /><br /> Para obter mais informações, consulte o **\/n** de opção em [Usando RC \(A linha de comando de RC\)](http://go.microsoft.com/fwlink/?LinkId=155730) no site do MSDN.|  
|**PreprocessorDefinitions**|Opcional **String\[\]** parâmetro.<br /><br /> Defina um ou mais símbolos de pré\-processamento para o compilador de recursos.  Especifica uma lista de símbolos de macro.<br /><br /> Para obter mais informações, consulte o **\/d** de opção em [Usando RC \(A linha de comando de RC\)](http://go.microsoft.com/fwlink/?LinkId=155730) no site do MSDN.  Consulte também **UndefinePreprocessorDefinitions** nesta tabela.|  
|**ResourceOutputFileName**|Opcional **String** parâmetro.<br /><br /> Especifica o nome do arquivo de recurso.  Especifique um nome de arquivo de recurso.<br /><br /> Para obter mais informações, consulte o **\/fo** de opção em [Usando RC \(A linha de comando de RC\)](http://go.microsoft.com/fwlink/?LinkId=155730) no site do MSDN.|  
|**ShowProgress**|Opcional **Boolean** parâmetro.<br /><br /> Se `true`, exibe mensagens que informam o andamento do compilador.<br /><br /> Para obter mais informações, consulte o **\/v** de opção em [Usando RC \(A linha de comando de RC\)](http://go.microsoft.com/fwlink/?LinkId=155730) no site do MSDN.|  
|**Source**|Obrigatório `ITaskItem[]` parâmetro.<br /><br /> Define uma matriz dos itens de arquivo de origem MSBuild que pode ser consumido e emitido por tarefas.|  
|**SuppressStartupBanner**|Opcional **Boolean** parâmetro.<br /><br /> Se `true`, impede a exibição da mensagem de número de versão e copyright quando a tarefa for iniciada.<br /><br /> Para obter mais informações, digite o **\/?** a opção de linha de comando e veja o **\/nologo** opção.|  
|**TrackerLogDirectory**|Opcional **String** parâmetro.<br /><br /> Especifica o diretório de log do controlador.|  
|**UndefinePreprocessorDefinitions**|Cancele um símbolo do pré\-processador.<br /><br /> Para obter mais informações, consulte o **\/u** de opção em [Usando RC \(A linha de comando de RC\)](http://go.microsoft.com/fwlink/?LinkId=155730) no site do MSDN.  Consulte também **PreprocessorDefinitions** nesta tabela.|  
  
## Comentários  
  
## Consulte também  
 [Referência de tarefas](../msbuild/msbuild-task-reference.md)