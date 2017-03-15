---
title: "Comando Listar Memória | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- debug.listmemory
helpviewer_keywords:
- Debug.ListMemory command
- ListMemory command
- list memory command
ms.assetid: a84de361-a6a6-4f6d-96aa-a0d4a424371e
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
ms.openlocfilehash: efc725418f333c248952ad9f505a8fc4b7b35b02
ms.lasthandoff: 02/22/2017

---
# <a name="list-memory-command"></a>Comando Listar Memória
Exibe o conteúdo do intervalo de memória especificado.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
Debug.ListMemory [/ANSI|Unicode] [/Count:number] [/Format:formattype]  
[/Hex|Signed|Unsigned] [expression]  
```  
  
## <a name="arguments"></a>Arguments  
 `expression`  
 Opcional. O endereço de memória do qual começar a exibir a memória.  
  
## <a name="switches"></a>Opções  
 /ANSI&#124;Unicode  
 Opcional. Exibe a memória como caracteres correspondentes aos bytes de memória, ANSI ou Unicode.  
  
 /Count:`number`  
 Opcional. Determina quantos bytes de memória devem ser exibidos, começando em `expression`.  
  
 /Format:`formattype`  
 Opcional. Tipo de formato para exibir informações de memória na janela **Memória**; pode ser OneByte, TwoBytes, FourBytes, EightBytes, Float (32 bits) ou Double (64 bits). Se OneByte for usado, `/Unicode` ficará não disponível.  
  
 /Hex&#124;Signed&#124;Unsigned  
 Opcional. Especifica o formato para exibir números: com sinal, sem sinal ou hexadecimal.  
  
## <a name="remarks"></a>Comentários  
 Em vez de escrever um comando **Debug.ListMemory** completo com todas as opções, você pode invocar o comando usando aliases predefinidos com determinadas opções predefinidas como valores especificados. Por exemplo, em vez de inserir:  
  
```  
>Debug.ListMemory /Format:float /Count:30 /Unicode  
```  
  
 você pode escrever:  
  
```  
>df /Count:30 /Unicode  
```  
  
 Veja uma lista dos aliases disponíveis para o comando **Debug.ListMemory**:  
  
|Alias|Comando e opções|  
|-----------|--------------------------|  
|**d**|Debug.ListMemory|  
|**da**|Debug.ListMemory /Ansi|  
|**db**|Debug.ListMemory /Format:OneByte|  
|**dc**|Debug.ListMemory /Format:FourBytes /Ansi|  
|**dd**|Debug.ListMemory /Format:FourBytes|  
|**df**|Debug.ListMemory /Format:Float|  
|**dq**|Debug.ListMemory /Format:EightBytes|  
|**du**|Debug.ListMemory /Unicode|  
  
## <a name="example"></a>Exemplo  
  
```  
>Debug.ListMemory /Format:float /Count:30 /Unicode  
```  
  
## <a name="see-also"></a>Consulte também  
 [Comando List Call Stack](../../ide/reference/list-call-stack-command.md)   
 [Comando List Threads](../../ide/reference/list-threads-command.md)   
 [Comandos do Visual Studio](../../ide/reference/visual-studio-commands.md)   
 [Janela Comando](../../ide/reference/command-window.md)   
 [Caixa Localizar/Comando](../../ide/find-command-box.md)   
 [Aliases de comando do Visual Studio](../../ide/reference/visual-studio-command-aliases.md)
