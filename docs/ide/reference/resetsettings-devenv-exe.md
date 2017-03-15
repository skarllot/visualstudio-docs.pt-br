---
title: -ResetSettings (devenv.exe) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Devenv, /ResetSettings switch
- ResetSettings switch
- /ResetSettings Devenv switch
ms.assetid: 1d41021c-6f58-4bd5-b122-d1c995812192
caps.latest.revision: 10
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
ms.openlocfilehash: 6135730b9b3283365cd63fe5d580d718f87de6bf
ms.lasthandoff: 02/22/2017

---
# <a name="resetsettings-devenvexe"></a>/ResetSettings (devenv.exe)
Restaura [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] configurações padrão e inicia automaticamente o IDE do [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Opcionalmente, redefine as configurações para o arquivo .vssettings especificado.  
  
 As configurações padrão são determinadas pelo perfil selecionado quando [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] foi inicializado pela primeira vez.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
Devenv /ResetSettings SettingsFile  
```  
  
## <a name="arguments"></a>Arguments  
 `SettingsFile`  
 O caminho completo e o nome do arquivo .vssettings para aplicar a [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
 Para restaurar o perfil de Configurações Gerais de Desenvolvimento, use `General`.  
  
## <a name="remarks"></a>Comentários  
 Se nenhum `SettingsFile` for especificado, será solicitado que você selecione uma coleção padrão de configurações na próxima vez iniciar [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
## <a name="example"></a>Exemplo  
 A seguinte linha de comando aplica as configurações armazenadas no arquivo `MySettings.vssettings`.  
  
```  
Devenv.exe /ResetSettings "C:\My Files\MySettings.vssettings"  
```  
  
## <a name="see-also"></a>Consulte também  
 [Personalizando configurações de desenvolvimento no Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3)   
 [Opções de linha de comando devenv](../../ide/reference/devenv-command-line-switches.md)
