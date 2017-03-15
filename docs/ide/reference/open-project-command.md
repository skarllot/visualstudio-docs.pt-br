---
title: Comando Abrir Projeto | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- file.openproject
helpviewer_keywords:
- op command
- File.OpenProject command
- Open Project command
ms.assetid: baa85f86-041b-49f4-9ced-0c397dc180e1
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
ms.openlocfilehash: fe7e8e95aa623b26dadfe36c342245a43bf9a722
ms.lasthandoff: 02/22/2017

---
# <a name="open-project-command"></a>Comando Abrir Projeto
Abre um projeto existente.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
File.OpenProject filename  
```  
  
## <a name="arguments"></a>Arguments  
 `filename`  
 Necessário. O nome de arquivo e caminho completo do projeto a abrir.  
  
 A sintaxe para o argumento `filename` requer que os caminhos que contêm espaços usem aspas.  
  
## <a name="remarks"></a>Comentários  
 O preenchimento automático tenta localizar o caminho e o nome do arquivo corretos enquanto você digita.  
  
 Esse comando não está disponível durante a depuração.  
  
## <a name="example"></a>Exemplo  
 Este exemplo abre o projeto [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)], Test1.  
  
```  
>File.OpenProject "C:\My Projects\Test1\Test1.vbproj"  
```  
  
## <a name="see-also"></a>Consulte também  
 [Comandos do Visual Studio](../../ide/reference/visual-studio-commands.md)   
 [Janela Comando](../../ide/reference/command-window.md)   
 [Caixa Localizar/Comando](../../ide/find-command-box.md)   
 [Aliases de comando do Visual Studio](../../ide/reference/visual-studio-command-aliases.md)
