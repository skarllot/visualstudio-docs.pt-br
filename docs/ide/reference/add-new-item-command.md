---
title: Comando Adicionar Novo Item | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- project.addnewitem
helpviewer_keywords:
- Add New Item command
- File.AddNewItem command
ms.assetid: 63b7df32-db83-463b-bbe7-7ff011fe5298
caps.latest.revision: 12
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Human Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 5962c018fba2de984fdd46df58c9c09e717d648e

---
# <a name="add-new-item-command"></a>Comando Adicionar Novo Item
Adiciona um novo item de solução, como um .htm, .css, .txt ou conjunto de quadros à solução atual e a abre.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
File.AddNewItem [filename] [/t:templatename] [/e:editorname]  
```  
  
## <a name="arguments"></a>Arguments  
 `filename`  
 Opcional. O nome de arquivo e o caminho do item a ser adicionado à solução.  
  
## <a name="switches"></a>Opções  
 /t: `templatename`  
 Opcional. Especifica o tipo de arquivo a ser criado. Se nenhum nome de modelo for fornecido, um arquivo de texto será criado por padrão.  
  
 A sintaxe do argumento /t:`templatename` espelha as informações encontradas na caixa de diálogo **Adicionar Novo Item de Solução**. É necessário inserir a categoria completa seguida pelo tipo de arquivo, separando o nome da categoria do tipo de arquivo por uma barra invertida (`\`) e delimitando toda a cadeia de caracteres entre aspas.  
  
 Por exemplo, para criar um novo arquivo de texto, insira o seguinte para o argumento /t:`templatename`.  
  
```  
/t:"General\Style Sheet"  
```  
  
 /e: `editorname`  
 Opcional. O nome do editor no qual o arquivo será aberto. Se o argumento for especificado, mas nenhum nome de editor for fornecido, a caixa de diálogo **Abrir com** será exibida.  
  
 A sintaxe do argumento /e:`editorname` usa os nomes de editor como eles são exibidos na **Caixa de diálogo Abrir Com**, entre aspas.  
  
 Por exemplo, para abrir uma folha de estilos no editor de código-fonte, insira o seguinte para o argumento /e:`editorname`.  
  
```  
/e:"Source Code (text) Editor"  
```  
  
## <a name="example"></a>Exemplo  
 Esse exemplo adiciona um novo item de solução, MyHTMLpg, à solução atual.  
  
```  
>File.AddNewItem MyHTMLpg /t:"General\HTML Page"  
```  
  
## <a name="see-also"></a>Consulte também  
 [Comandos do Visual Studio](../../ide/reference/visual-studio-commands.md)   
 [Janela Comando](../../ide/reference/command-window.md)   
 [Caixa Localizar/Comando](../../ide/find-command-box.md)   
 [Aliases de comando do Visual Studio](../../ide/reference/visual-studio-command-aliases.md)


<!--HONumber=Feb17_HO4-->


