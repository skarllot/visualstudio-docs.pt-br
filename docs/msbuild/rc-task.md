---
title: Tarefa RC | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VC.Project.VCResourceCompilerTool.UndefineProcessorDefinitions
- vc.task.rc
- VC.Project.VCResourceCompilerTool.SuppressStartupBanner
- VC.Project.VCResourceCompilerTool.NullTerminateStrings
dev_langs:
- VB
- CSharp
- C++
- jsharp
- C++
helpviewer_keywords:
- RC task (MSBuild (Visual C++))
- MSBuild (Visual C++), RC task
ms.assetid: 2fd26c75-a056-4dda-9f7e-2f90d3748d88
caps.latest.revision: 10
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
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: e01f120de085ea3a49ac262c2fd092c3ee1e179b
ms.lasthandoff: 02/22/2017

---
# <a name="rc-task"></a>Tarefa RC
Encapsula a ferramenta de Compilador de Recurso do Microsoft Windows, rc.exe. A tarefa **RC** compila recursos como cursores, ícones, bitmaps, caixas de diálogo e fontes em um arquivo de recurso (.res). Para obter mais informações, consulte “Compilador de Recursos” no site do [MSDN](http://go.microsoft.com/fwlink/?LinkId=737).  
  
## <a name="parameters"></a>Parâmetros  
 A tabela a seguir descreve os parâmetros da tarefa RCtask. A maioria dos parâmetros de tarefa e alguns conjuntos de parâmetros correspondem a uma opção de linha de comando.  
  
|Parâmetro|Descrição|  
|---------------|-----------------|  
|**AdditionalIncludeDirectories**|Parâmetro **String[]** opcional.<br /><br /> Adiciona um diretório à lista de diretórios que são pesquisados para arquivos de inclusão.<br /><br /> Para obter mais informações, consulte a opção **/I** em [Usando RC (A linha de comando RC)](http://go.microsoft.com/fwlink/?LinkId=155730) no site do MSDN.|  
|**AdditionalOptions**|Parâmetro **String** opcional.<br /><br /> Uma lista de opções ou exemplos de linha de comando: **"***/option1 /option2 /option#*". Use esse parâmetro para especificar opções de linha de comando não representadas por nenhum outro parâmetro de tarefa **RC**.<br /><br /> Para obter mais informações, consulte as opções em [Usando RC (A linha de comando RC)](http://go.microsoft.com/fwlink/?LinkId=155730) no site do MSDN.|  
|**Cultura**|Parâmetro **String** opcional.<br /><br /> Especifica uma ID de localidade que representa a cultura usada nos recursos.<br /><br /> Para obter mais informações, consulte a opção **/l** em [Usando RC (A linha de comando RC)](http://go.microsoft.com/fwlink/?LinkId=155730) no site do MSDN.|  
|**IgnoreStandardIncludePath**|Parâmetro **Boolean** opcional.<br /><br /> Se for `true`, impede que o compilador de recurso verifique a variável de ambiente INCLUDE ao procurar por arquivos de cabeçalho ou arquivos de recurso.<br /><br /> Para obter mais informações, consulte a opção **/x** em [Usando RC (A linha de comando RC)](http://go.microsoft.com/fwlink/?LinkId=155730) no site do MSDN.|  
|**NullTerminateStrings**|Parâmetro **Boolean** opcional.<br /><br /> Se for `true`, termina em nulo todas as cadeias de caracteres na tabela de cadeia de caracteres.<br /><br /> Para obter mais informações, consulte a opção **/n** em [Usando RC (A linha de comando RC)](http://go.microsoft.com/fwlink/?LinkId=155730) no site do MSDN.|  
|**PreprocessorDefinitions**|Parâmetro **String[]** opcional.<br /><br /> Defina um ou mais símbolos de pré-processador para o compilador de recurso. Especifique uma lista de símbolos de macro.<br /><br /> Para obter mais informações, consulte a opção **/d** em [Usando RC (A linha de comando RC)](http://go.microsoft.com/fwlink/?LinkId=155730) no site do MSDN. Consulte também **UndefinePreprocessorDefinitions** nessa tabela.|  
|**ResourceOutputFileName**|Parâmetro **String** opcional.<br /><br /> Especifica o nome do arquivo de recurso. Especifica um nome de arquivo de recurso.<br /><br /> Para obter mais informações, consulte a opção **/fo** em [Usando RC (A linha de comando RC)](http://go.microsoft.com/fwlink/?LinkId=155730) no site do MSDN.|  
|**ShowProgress**|Parâmetro **Boolean** opcional.<br /><br /> Se for `true`, exibe mensagens que relatam o andamento do compilador.<br /><br /> Para obter mais informações, consulte a opção **/v** em [Usando RC (A linha de comando RC)](http://go.microsoft.com/fwlink/?LinkId=155730) no site do MSDN.|  
|**Source**|Parâmetro `ITaskItem[]` obrigatório.<br /><br /> Define uma matriz de itens de arquivo de origem do MSBuild que pode ser consumida e emitida por tarefas.|  
|**SuppressStartupBanner**|Parâmetro **Boolean** opcional.<br /><br /> Se `true`, impedirá a exibição da mensagem de direitos autorais e de número de versão quando a tarefa for iniciada.<br /><br /> Para obter mais informações, digite a opção de linha de comando **/?**  e, em seguida, confira a opção **/nologo**.|  
|**TrackerLogDirectory**|Parâmetro **String** opcional.<br /><br /> Especifica o diretório de log de rastreamento.|  
|**UndefinePreprocessorDefinitions**|Cancela a definição de um símbolo de pré-processador.<br /><br /> Para obter mais informações, consulte a opção **/u** em [Usando RC (A linha de comando RC)](http://go.microsoft.com/fwlink/?LinkId=155730) no site do MSDN. Consulte também **PreprocessorDefinitions** nessa tabela.|  
  
## <a name="remarks"></a>Comentários  
  
## <a name="see-also"></a>Consulte também  
 [Referência de tarefas](../msbuild/msbuild-task-reference.md)
