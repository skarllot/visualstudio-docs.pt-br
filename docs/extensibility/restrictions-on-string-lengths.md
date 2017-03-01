---
title: "Restrições em comprimentos de cadeia de caracteres | Documentos do Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- source control plug-ins, restrictions on string lengths
ms.assetid: 877173d2-ca27-43b3-b1f4-8379f7c5e268
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
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
ms.openlocfilehash: bf09f770265bd35cb82d654c5833667580b4e0cd
ms.lasthandoff: 02/22/2017

---
# <a name="restrictions-on-string-lengths"></a>Restrições em comprimentos de cadeia de caracteres
A API de plug-in de controle de origem limita os comprimentos das cadeias de caracteres usadas em várias funções.  
  
## <a name="string-length-values"></a>Valores de comprimento de cadeia de caracteres  
  
|Constante|Valor|  
|--------------|-----------|  
|`SCC_NAME_LEN`|31|  
|`SCC_AUXLABEL_LEN`|31|  
|`SCC_USER_LEN`|31|  
|`SCC_PRJPATH_LEN`|300|  
  
> [!NOTE]
>  Comprimento não inclui o encerramento do `null`. Outras constantes com um sufixo "_SIZE" em vez de "_LEN" incluir espaço para encerramento do `null`.  
  
|Constante|Valor|  
|--------------|-----------|  
|SCC_NAME_SIZE|32|  
|SCC_AUXLABEL_SIZE|32|  
|SCC_USER_SIZE|32|  
|SCC_PRJPATH_SIZE|301|  
  
## <a name="see-also"></a>Consulte também  
 [Plug-ins de controle de origem](../extensibility/source-control-plug-ins.md)
