---
title: "Segurança de modelos de texto | Documentos do Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- text templates, security
ms.assetid: 567a2383-7d43-4acc-af4a-cd70b7a0151e
caps.latest.revision: 23
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
ms.openlocfilehash: f56c60d6386975bf977df14c1839838ae2ccaf8a
ms.lasthandoff: 02/22/2017

---
# <a name="security-of-text-templates"></a>Segurança de modelos de texto
Modelos de texto têm as seguintes preocupações de segurança:  
  
-   Modelos de texto são vulneráveis a inserções de código arbitrário.  
  
-   Se o mecanismo que o host usa para localizar um processador de diretriz não é seguro, um processador de diretriz mal-intencionado poderia ser executado.  
  
## <a name="arbitrary-code"></a>Código arbitrário  
 Quando você escreve um modelo, você pode colocar qualquer código dentro de \<# #> marcas. Isso permite que o código arbitrário ser executado a partir de um modelo de texto.  
  
 Certifique-se de que obter modelos de fontes confiáveis. Certifique-se de avisar os usuários finais do seu aplicativo para não executar modelos que não vêm de fontes confiáveis.  
  
## <a name="malicious-directive-processor"></a>Processador de diretriz mal-intencionado  
 O mecanismo de modelo de texto interage com um host de transformação e um ou mais processadores de diretriz para transformar o texto do modelo para um arquivo de saída. Para obter mais informações, consulte [o processo de transformação de modelo de texto](../modeling/the-text-template-transformation-process.md).  
  
 Se o mecanismo que o host usa para localizar um processador de diretriz não é seguro, ele corre o risco da execução de um processador de diretriz mal-intencionado. O processador de diretriz mal-intencionado poderia fornecer código que é executado em `FullTrust` modo quando o modelo é executado. Se você criar um host de transformação do modelo de texto personalizado, você deve usar um mecanismo seguro, como o registro, para o mecanismo localizar os processadores de diretriz.
