---
title: -Edit (devenv.exe) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Devenv, /edit switch
- /Edit Devenv swtich
ms.assetid: 02b3d6e7-a2b1-4d83-a747-aa8c2fb758b7
caps.latest.revision: 6
author: gewarren
ms.author: gewarren
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
ms.translationtype: Human Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: d2e85cae469358eef4b5dee707d84546b8de5e2f
ms.contentlocale: pt-br
ms.lasthandoff: 02/22/2017

---
# <a name="edit-devenvexe"></a>/Edit (devenv.exe)
Abre o arquivo especificado em uma instância existente do [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
## <a name="syntax"></a>Sintaxe  
  
```  
Devenv /edit [file1[ file2]]  
```  
  
## <a name="arguments"></a>Arguments  
 `file1`  
 Opcional. O arquivo a ser aberto em uma instância existente do [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Se nenhuma instância do [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] existir, uma nova instância será criada com um layout de janela simplificado, e o `file1` será aberto na nova instância.  
  
 `file2`  
 Opcional. Um ou mais arquivos adicionais a serem abertos na instância existente do [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
## <a name="remarks"></a>Comentários  
 Se nenhum arquivo for especificado e se houver uma instância existente do [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], a instância existente do [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] receberá o foco. Se nenhum arquivo for especificado e se não houver nenhuma instância existente do [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], uma nova instância do [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] será criada com um layout de janela simplificado.  
  
 Se a instância existente do [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] estiver em um estado modal, por exemplo, se a [caixa de diálogo Opções](../../ide/reference/options-dialog-box-visual-studio.md) estiver aberta, o arquivo será aberto na instância existente quando [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] sair do estado modal.  
  
## <a name="example"></a>Exemplo  
 Esse exemplo abre o arquivo `MyFile.cs` em uma instância existente do [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ou abre o arquivo em uma nova instância da [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] se ainda não existir nenhuma.  
  
```  
devenv /edit MyFile.cs  
```  
  
## <a name="see-also"></a>Consulte também  
 [Opções de linha de comando devenv](../../ide/reference/devenv-command-line-switches.md)
