---
title: Comando Localizar nos Arquivos | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- edit.findinfiles
helpviewer_keywords:
- Edit.FindInFiles command
- find in files command
ms.assetid: 2fc78bfe-b339-4599-97f9-4cafd8a194d9
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
ms.openlocfilehash: cefbcb214cb6ed8f66afc2303ebb760f5cbeb281
ms.lasthandoff: 02/22/2017

---
# <a name="find-in-files-command"></a>Comando Localizar nos Arquivos
Pesquise arquivos usando um subconjunto das opções disponíveis na guia **Localizar nos Arquivos** da janela **Localizar e Substituir**.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
Edit.FindinFiles findwhat [/case] [/ext:extensions]  
[/lookin:searchpath] [/names] [/options] [/reset] [/stop] [/sub]  
[/text2] [/wild|/regex] [/word]  
```  
  
## <a name="arguments"></a>Arguments  
 `findwhat`  
 Necessário. O texto a ser correspondido.  
  
## <a name="switches"></a>Opções  
 /case ou /c  
 Opcional. As correspondências ocorrerão somente se os caracteres maiúsculos e minúsculos corresponderem exatamente aos especificados no argumento `findwhat`.  
  
 /ext: `extensions`  
 Opcional. Especifica as extensões de arquivo para os arquivos a serem pesquisados. Se não forem especificadas, a extensão anterior será usada, caso uma tenha sido inserida.  
  
 /lookin: `searchpath`  
 Opcional. Diretório a pesquisar. Se o caminho contiver espaços, coloque todo o caminho entre aspas.  
  
 /names ou /n  
 Opcional. Exibe uma lista de nomes de arquivos que contêm correspondências.  
  
 /options ou /t  
 Opcional. Exibe uma lista das configurações atuais da opção de localização e não realiza uma pesquisa.  
  
 /regex ou /r  
 Opcional. Usa caracteres especiais predefinidos no argumento `findwhat` como notações que representam padrões de texto, em vez de caracteres literais. Para obter uma lista completa de caracteres de expressão regular, consulte [Expressões Regulares](../../ide/using-regular-expressions-in-visual-studio.md).  
  
 /reset ou /e  
 Opcional. Retorna as opções de localização para suas configurações padrão e não realiza uma pesquisa.  
  
 /stop  
 Opcional. Interromperá a operação de pesquisa atual se houver uma em andamento. Pesquisar ignorará todos os outros argumentos quando `/stop` tiver sido especificado. Por exemplo, para interromper a pesquisa atual, você digitaria o seguinte:  
  
```  
>Edit.FindinFiles /stop  
```  
  
 /sub ou /s  
 Opcional. Procura as subpastas dentro do diretório especificado no argumento /lookin:`searchpath`.  
  
 /text2 ou /2  
 Opcional. Exibe os resultados da pesquisa na janela Localizar Resultados 2.  
  
 /wild ou /l  
 Opcional. Usa caracteres especiais predefinidos no argumento `findwhat` como notações para representar um caractere ou uma sequência de caracteres.  
  
 /word ou /w  
 Opcional. Pesquisa somente palavras inteiras.  
  
## <a name="example"></a>Exemplo  
 Este exemplo procura btnCancel em todos os arquivos .cls localizados na pasta "Meus Projetos do Visual Studio" e exibe as informações de correspondência na Janela Localizar Resultados 2.  
  
```  
>Edit.FindinFiles btnCancel /lookin:"c:/My Visual Studio Projects" /ext:*.cls /text2  
```  
  
## <a name="see-also"></a>Consulte também  
 [Localizar nos Arquivos](../../ide/find-in-files.md)   
 [Janela Comando](../../ide/reference/command-window.md)   
 [Caixa Localizar/Comando](../../ide/find-command-box.md)   
 [Comandos do Visual Studio](../../ide/reference/visual-studio-commands.md)   
 [Aliases de comando do Visual Studio](../../ide/reference/visual-studio-command-aliases.md)
