---
title: Arquivos de resposta do MSBuild | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- response files, MSBuild
- MSBuild, response files
- MSBuild, .rsp files
- .rsp files
ms.assetid: 9f53987b-20ee-470a-ab62-fce997bb5e15
caps.latest.revision: 3
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
ms.openlocfilehash: 7c56ef2aff7261aa96e4c8f0df77a5f63a24a7d1
ms.lasthandoff: 02/22/2017

---
# <a name="msbuild-response-files"></a>Arquivos de resposta do MSBuild
Arquivos de resposta (.rsp) são arquivos de texto que contêm as opções de linha de comando MSBuild.exe. Cada opção pode estar em uma linha separada ou todas as opções podem estar em uma linha. As linhas de comentários são precedidas por um símbolo **#**. A opção **@** é usada para passar a outro arquivo de resposta para o MSBuild.exe.  
  
 O arquivo de resposta automática é um arquivo .rsp especial que o MSBuild.exe usa automaticamente ao criar um projeto. Esse arquivo, o MSBuild.rsp, deve estar no mesmo diretório que MSBuild.exe, caso contrário, ele não será localizado. Você pode editar esse arquivo para especificar opções de linha de comando padrão para MSBuild.exe. Por exemplo, caso use o mesmo agente de log sempre que compilar um projeto, você pode adicionar a opção **/logger** para MSBuild.rsp, e o MSBuild.exe usará o agente de log sempre que um projeto for compilado.  
  
## <a name="see-also"></a>Consulte também  
 [Referência do MSBuild](../msbuild/msbuild-reference.md)   
 [Referência de linha de comando](../msbuild/msbuild-command-line-reference.md)
