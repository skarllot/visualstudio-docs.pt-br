---
title: Caracteres especiais do MSBuild | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- escape characters
- escape
- MSBuild Escape Characters
ms.assetid: 545e6a59-1093-4514-935e-78679a46fb3c
caps.latest.revision: 8
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
ms.openlocfilehash: 020b3407f9775dd95bff8dfa466167c7255e0854
ms.lasthandoff: 02/22/2017

---
# <a name="msbuild-special-characters"></a>Caracteres especiais no MSBuild
[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] reserva alguns caracteres para uso especial em contextos específicos. Você precisa apenas tais caracteres de escape se desejar usá-los literalmente no contexto no qual eles estão reservados. Por exemplo, um asterisco tem um significado especial somente nos atributos `Include` e `Exclude` de uma definição de item e, em chamadas para `CreateItem`. Se você quiser que um asterisco seja exibido como um asterisco em um desses contextos, você deve usar um caractere de escape. Nos outros contextos, basta digitar o asterisco onde você deseja que ele apareça.  
  
 Para escapar um caractere especial, use a sintaxe %*xx*, onde *xx* representa o valor hexadecimal de ASCII do caractere. Para obter mais informações, confira [Como: usar caracteres especiais no MSBuild](../msbuild/how-to-escape-special-characters-in-msbuild.md).  
  
## <a name="special-characters"></a>Caracteres especiais  
 A tabela a seguir lista os caracteres especiais do [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]:  
  
|**Caractere**|**ASCII**|**Uso reservado**|  
|-------------------|---------------|------------------------|  
|%|%25|Metadados de referência|  
|$|%24|Propriedades de referência|  
|@|%40|Listas de Itens de Referência|  
|'|%27|Condições e outras expressões|  
|;|%3B|Separador de lista|  
|?|%3F|Caractere curinga para nomes de arquivos em atributos `Include` e `Exclude`|  
|*|%2A|Caractere curinga para uso em nomes de arquivos em atributos `Include` e `Exclude`|  
  
## <a name="see-also"></a>Consulte também  
 [Conceitos avançados](../msbuild/msbuild-advanced-concepts.md)   
 [Itens](../msbuild/msbuild-items.md)
