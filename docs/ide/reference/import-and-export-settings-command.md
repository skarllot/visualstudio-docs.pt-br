---
title: Comando Import and Export Settings | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- Tools.ImportandExportSettings
helpviewer_keywords:
- Tools.ImportandExportSettings
- Import and Export Settings command
ms.assetid: 94a06468-a44d-403d-a931-77bbc9d06e56
caps.latest.revision: 5
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
ms.translationtype: Human Translation
ms.sourcegitcommit: 5ea9179ad37514ffad4876177b05150eecc22def
ms.openlocfilehash: dca11a81e650f0470c891cb79623f9cc088ea669
ms.contentlocale: pt-br
ms.lasthandoff: 05/24/2017

---
# <a name="import-and-export-settings-command"></a>Comando Importar e Exportar Configurações
Importa, exporta ou redefine configurações [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
## <a name="syntax"></a>Sintaxe  
  
```  
Tools.ImportandExportSettings [/export:filename | /import:filename | /reset]  
```  
  
## <a name="switches"></a>Opções  
 /export:`filename`  
 Opcional. Exporta as configurações atuais para o arquivo especificado.  
  
 /import:`filename`  
 Opcional. Importa as configurações no arquivo especificado.  
  
 /reset  
 Opcional. Redefine as configurações atuais.  
  
## <a name="remarks"></a>Comentários  
 Executar esse comando sem nenhuma opção abre o assistente **Importar e Exportar Configurações**. Para obter mais informações, consulte [Como: Compartilhar configurações entre computadores ou versões de Visual Studio](http://msdn.microsoft.com/en-us/1131fb10-35c1-42da-9cd8-91aa3235b882).  
  
## <a name="example"></a>Exemplo  
 O comando a seguir exporta as configurações atuais para o arquivo `MyFile.vssettings`.  
  
```  
Tools.ImportandExportSettings /export:"c:\Files\MyFile.vssettings"  
```  
  
## <a name="see-also"></a>Consulte também  
 [Personalizar o IDE do Visual Studio](../../ide/personalizing-the-visual-studio-ide.md)   
 [Comandos do Visual Studio](../../ide/reference/visual-studio-commands.md)
