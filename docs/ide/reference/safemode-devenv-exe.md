---
title: -SafeMode (devenv.exe) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- /SafeMode Devenv switch
- Devenv, /SafeMode switch
- SafeMode switch
ms.assetid: b191f6a5-8f12-47ec-bcc7-b68149a22aa8
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
translationtype: Human Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 79d468d30cbbb7f69ff6f87a4809b9fe1bf957b5
ms.lasthandoff: 02/22/2017

---
# <a name="safemode-devenvexe"></a>/SafeMode (devenv.exe)
Inicia o [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] no modo de segurança, carregando apenas o ambiente e os serviços padrão.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
devenv /SafeMode   
```  
  
## <a name="remarks"></a>Comentários  
 Essa opção impede que todos os VSPackages de terceiros sejam carregados quando o [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] é iniciado, garantindo assim uma execução estável.  
  
## <a name="description"></a>Descrição  
 O exemplo a seguir inicia o [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] no modo de segurança.  
  
## <a name="code"></a>Código  
  
```  
Devenv.exe /SafeMode  
```  
  
## <a name="see-also"></a>Consulte também  
 [Opções de linha de comando devenv](../../ide/reference/devenv-command-line-switches.md)
