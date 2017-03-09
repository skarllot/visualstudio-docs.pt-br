---
title: Comando Listar Registros | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- debug.listregisters
helpviewer_keywords:
- list registers command
- Debug.ListRegisters command
- ListRegisters command
ms.assetid: 19a9d789-f6c9-46b3-b1f6-4934fc33e055
caps.latest.revision: 7
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
ms.openlocfilehash: e90f448454d38e3ccd80148dffea550a35af20ec
ms.lasthandoff: 02/22/2017

---
# <a name="list-registers-command"></a>Comando Listar Registros
Exibe o valor dos registros selecionados e permite modificar a lista de registros a mostrar.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
Debug.ListRegisters [/Display [{register|registerGroup}...]] [/List]  
[/Watch [{register|registerGroup}...]]  
[/Unwatch [{register|registerGroup}...]]  
```  
  
## <a name="switches"></a>Opções  
 /Display [{`register`&#124;`registerGroup`}...]  
 Exibe os valores do `register` ou `registerGroup` especificado. Se nenhum `register` ou `registerGroup` for especificado, a lista padrão de registros será exibida. Se nenhuma opção for especificada, o comportamento será o mesmo. Por exemplo:  
  
 `Debug.ListRegisters /Display eax`  
  
 equivale a  
  
 `Debug.ListRegisters eax`  
  
 /List  
 Exibe todos os grupos de registros na lista.  
  
 /Watch [{`register`&#124;`registerGroup`}...]  
 Adiciona um ou mais valores `register` ou `registerGroup` à lista.  
  
 /Unwatch [{`register`&#124;`registerGroup`}...]  
 Remove um ou mais valores `register` ou `registerGroup` da lista.  
  
## <a name="remarks"></a>Comentários  
 O alias `r` pode ser usado no lugar de `Debug.ListRegisters`.  
  
## <a name="example"></a>Exemplo  
 Este exemplo usa o alias `Debug.ListRegisters` `r` para exibir os valores do registro de grupo `Flags`.  
  
```  
r /Display Flags  
```  
  
## <a name="see-also"></a>Consulte também  
 [Comandos do Visual Studio](../../ide/reference/visual-studio-commands.md)   
 [Noções básicas sobre depuração: janela Registros](../../debugger/debugging-basics-registers-window.md)   
 [Como usar a janela Registros](../../debugger/how-to-use-the-registers-window.md)
