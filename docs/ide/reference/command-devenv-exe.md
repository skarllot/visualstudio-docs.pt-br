---
title: -Command (devenv.exe) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Devenv, /command switch
- /command Devenv switch
ms.assetid: 13c20cd6-f09d-400a-8b7b-ecc266a32cef
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
ms.sourcegitcommit: 5658ecf52637a38bc3c2a5ad9e85b2edebf7d445
ms.openlocfilehash: 76e64002e7f9caf7db8511501dd6c320b237ca65
ms.lasthandoff: 02/22/2017

---
# <a name="command-devenvexe"></a>/Command (devenv.exe)
Executa o comando especificado depois de iniciar o IDE (ambiente de desenvolvimento integrado) do [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
## <a name="syntax"></a>Sintaxe  
  
```  
devenv /command CommandName  
```  
  
## <a name="arguments"></a>Arguments  
 `CommandName`  
 Necessário. O nome completo de um comando [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ou seu alias, colocado entre aspas duplas. Para obter mais informações sobre comandos e a sintaxe de aliases, consulte [Comandos do Visual Studio](../../ide/reference/visual-studio-commands.md).  
  
## <a name="remarks"></a>Comentários  
 Após a conclusão da inicialização, o IDE executa o comando nomeado. Se você usar essa opção, o IDE não mostrará a Página Inicial do [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] na inicialização.  
  
 Se um suplemento expor um comando, será possível usar essa opção para iniciar o suplemento por meio da linha de comando. Para obter mais informações, consulte [Como controlar suplementos usando o Gerenciador de Suplementos](http://msdn.microsoft.com/Library/4f60444a-cb48-4cdb-8df4-941f6419aeeb).  
  
## <a name="example"></a>Exemplo  
 Esse exemplo inicia [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] e executa a macro Abrir Arquivos Favoritos automaticamente.  
  
```  
devenv /command "Macros.MyMacros.Module1.OpenFavoriteFiles"  
```  
  
## <a name="see-also"></a>Consulte também  
 [Opções de linha de comando devenv](../../ide/reference/devenv-command-line-switches.md)   
 [Aliases de comando do Visual Studio](../../ide/reference/visual-studio-command-aliases.md)
