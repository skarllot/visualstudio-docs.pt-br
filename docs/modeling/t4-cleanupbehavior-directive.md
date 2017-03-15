---
title: Diretiva CleanUpBehavior T4 | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9e5a211f-a3bf-4229-bff0-7d2e45b71c64
caps.latest.revision: 2
author: alancameronwills
ms.author: awills
manager: douge
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
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 1076bc65be0b1504bf473811bc961760588e3a5a
ms.lasthandoff: 02/22/2017

---
# <a name="t4-cleanupbehavior-directive"></a>Diretiva CleanUpBehavior T4
Para excluir o appDomain depois de processar um modelo de texto, inclua a seguinte linha:  
  
```  
<#@ CleanupBehavior processor="T4VSHost" CleanupAfterProcessingtemplate="true" #>  
```  
  
 Os modelos de texto são processados em um appDomain que é separado do processo do host. Na maioria dos casos, quando um modelo de texto é processado, o appdomain é usado novamente para processar o próximo modelo. Mas se você especificar CleanupBehavior, o appDomain será excluído e o próximo modelo será processado em um novo appDomain.  
  
 Isso reduz o processamento de texto, mas pode ser útil para garantir que os recursos sejam descartados.  
  
 Essa diretiva só funciona no host do Visual Studio.
