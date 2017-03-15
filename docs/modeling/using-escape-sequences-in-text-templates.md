---
title: "Usando sequências de Escape em modelos de texto | Documentos do Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- text templates, escape sequences
ms.assetid: 36fff542-2f42-460f-a2d5-03fc76817f3b
caps.latest.revision: 29
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
ms.openlocfilehash: ec3ab3bf44b632403bea594fa2294c3cf79414b3
ms.lasthandoff: 02/22/2017

---
# <a name="using-escape-sequences-in-text-templates"></a>Usando sequências de escape em modelos de texto
Você pode usar sequências de escape em modelos de texto para gerar marcas de modelo de texto e (em código c# somente) para caracteres de controle e as aspas.  
  
 Para imprimir as marcas de abertura e fechamento de um bloco de código padrão para o arquivo de saída, escape as marcas da seguinte maneira:  
  
```  
\<# ... \#>  
```  
  
 Você pode fazer o mesmo com marcas de bloco outro texto modelo diretiva e código.  
  
 Se um bloco de texto inclui cadeias de caracteres usadas para sair de marcas de modelo de texto, você pode usar as seguintes sequências de escape:  
  
-   Se uma marca de modelo de texto é precedida por um número par de escape (\\) o modelo de caracteres analisador irá incluir metade os caracteres de escape e incluem a sequência como uma marca de modelo de texto. Por exemplo, se houver quatro caracteres de escape no modelo de texto, haverá dois "\\" caracteres no arquivo gerado.  
  
-   Se a marca de modelo de texto é precedida por um número ímpar de escape (\\) caracteres, o analisador de modelo incluirá metade do "\\" caracteres mais a marca em si (\<# ou #>). A marca não é considerada para ser uma marca de modelo de texto.  
  
-   Se um escape (\\) caractere aparece em qualquer lugar em qualquer sequência diferente de onde ela ignora a um caractere de controle ou (em c# somente), o caractere será gerado diretamente.  
  
## <a name="see-also"></a>Consulte também  
 [Como gerar modelos com base em modelos usando sequências de escape](../modeling/how-to-generate-templates-from-templates-by-using-escape-sequences.md)
