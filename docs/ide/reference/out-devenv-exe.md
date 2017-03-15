---
title: -Out (devenv.exe) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- errors [Visual Studio], builds
- Devenv, /out switch
- builds [Visual Studio], logs
- error logs [Visual Studio], command-line build errors
- error logs [Visual Studio]
- /out Devenv switch
- out Devenv switch
- builds [Visual Studio], errors
- output files, build errors
ms.assetid: 9002d8c2-36d4-451c-b489-8f01932f31f7
caps.latest.revision: 11
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
ms.openlocfilehash: 3c537a6a6b2b438f38b5856995c46265706576e0
ms.lasthandoff: 02/22/2017

---
# <a name="out-devenvexe"></a>/Out (devenv.exe)
Especifica um arquivo para armazenar e exibir erros quando você executa, compila, recompila ou implanta uma solução.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
devenv /out FileName  
```  
  
## <a name="arguments"></a>Arguments  
 `FileName`  
 Necessário. O caminho e o nome do arquivo para receber erros ao compilar um arquivo executável.  
  
## <a name="remarks"></a>Comentários  
 Se for especificado um nome de arquivo não exista, o arquivo será criado automaticamente. Se o arquivo já existir, os resultados serão anexados ao conteúdo existente do arquivo.  
  
 Erros de build de linha de comando são exibidos na janela **Comando** e a exibição do Gerenciador de Soluções da Janela de **Saída**. Essa opção é útil se você estiver executando compilações autônomas e precisar ver os resultados.  
  
## <a name="example"></a>Exemplo  
 Este exemplo executa `MySolution` e grava os erros no arquivo `MyErrorLog.txt`.  
  
```  
devenv /run "C:\Documents and Settings\someuser\My Documents\Visual Studio\Projects\MySolution\MySolution.sln" /out "C:\MyErrorLog.txt"  
```  
  
## <a name="see-also"></a>Consulte também  
 [Opções de linha de comando devenv](../../ide/reference/devenv-command-line-switches.md)   
 [/Run (devenv.exe)](../../ide/reference/run-devenv-exe.md)   
 [/Build (devenv.exe)](../../ide/reference/build-devenv-exe.md)   
 [/Rebuild (devenv.exe)](../../ide/reference/rebuild-devenv-exe.md)   
 [/Deploy (devenv.exe)](../../ide/reference/deploy-devenv-exe.md)
