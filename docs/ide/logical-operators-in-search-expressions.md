---
title: "Operadores lógicos em expressões de pesquisa | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Help Viewer 2.0, logical operators in search
- logical operators in search [Help Viewer 2.0]
ms.assetid: 0c38ae7d-3e20-4d47-a020-9677cd285916
caps.latest.revision: 9
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Human Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 36df6d24923d56da9653beec94aa7f81aca9b939

---
# <a name="logical-operators-in-search-expressions"></a>Operadores lógicos em expressões de pesquisa
Usando operadores lógicos, você pode refinar a pesquisa de conteúdo criando expressões de pesquisa mais complicadas desde mais simples. Como mostra a tabela a seguir, os operadores lógicos especificam como vários termos de pesquisa devem ser combinados em uma consulta de pesquisa.  
  
> [!IMPORTANT]
>  Você deve inserir os operadores lógicos em letras maiúsculas para o mecanismo de pesquisa reconhecê-los.  
  
|Para pesquisar|Use|Exemplo|Resultado|  
|-------------------|---------|-------------|------------|  
|Ambos os termos no mesmo tópico|AND|dib AND paleta|Tópicos que contêm "dib" e "paleta".|  
|Um dos dois termos em um tópico|OU|varredura OR vetor|Tópicos que contêm "varredura" ou "vetor".|  
|Primeiro termo sem um segundo termo no mesmo tópico|NOT|"operating system" NOT DOS|Tópicos que contêm "sistema operacional", mas não "DOS".|  
|Os dois termos, próximos em um tópico|PRÓXIMO|usuário NEAR kernel|Tópicos que contêm "usuário" bastante próximo de "kernel".|  
  
## <a name="see-also"></a>Consulte também  
 [Dicas de pesquisa de texto completo](../ide/full-text-search-tips.md)   
 [Localizar informações](../ide/locate-information.md)


<!--HONumber=Feb17_HO4-->


