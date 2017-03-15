---
title: "Comando de caminho de símbolo | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- debug.symbolpath
helpviewer_keywords:
- symbol path command
- Debug.SymbolPath command
- SymbolPath command
ms.assetid: b697ef2d-3f5d-40df-b113-7068a5bec0d4
caps.latest.revision: 9
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
ms.openlocfilehash: c97348e44cfa60338add30e10d0d27fddc243649
ms.lasthandoff: 02/22/2017

---
# <a name="symbol-path-command"></a>Comando demarcador do Símbolo
Define a lista de diretórios para o depurador pesquisar símbolos.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
Debug.SymbolPath pathname1;pathname2;... pathnameN  
```  
  
## <a name="arguments"></a>Arguments  
 `pathname`  
 Opcional. Uma lista de caminhos delimitada por ponto-e-vírgula para que o depurador pesquise símbolos.  
  
## <a name="remarks"></a>Comentários  
 Se nenhum `pathname` for especificado, o comando listará os caminhos de símbolo atual.  
  
## <a name="example"></a>Exemplo  
 Este exemplo adiciona dois caminhos à lista de diretórios de símbolo.  
  
```  
Debug.SymbolPath C:\Symbol Path 1;C:\Symbol Path 2  
```  
  
## <a name="example"></a>Exemplo  
 Este exemplo exibe uma lista delimitada por ponto-e-vírgula dos caminhos de símbolo atuais.  
  
```  
Debug.SymbolPath  
```  
  
## <a name="see-also"></a>Consulte também  
 [Janela Comando](../../ide/reference/command-window.md)   
 [Comandos do Visual Studio](../../ide/reference/visual-studio-commands.md)
