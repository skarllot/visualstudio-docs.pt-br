---
title: "Adicionando extensões a definições de DSL | Documentos do Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 07e133be-92ab-4936-a02b-45d2012bd0a6
caps.latest.revision: 6
author: alancameronwills
ms.author: awills
manager: douge
translationtype: Machine Translation
ms.sourcegitcommit: 3d07f82ea737449fee6dfa04a61e195654ba35fa
ms.openlocfilehash: f335db9f22392c4d0293a51111efff88c25c3145
ms.lasthandoff: 02/22/2017

---
# <a name="adding-extensions-to-dsl-definitions"></a>Adicionando extensões a definições de DSL
Extensão de definição de DSL permite que você crie um pacote de extensões para uma linguagem específica do domínio (DSL). A extensão DSL, que está contida em um Visual Studio Integration extensão (VSIX), pode ser instalada no computador do usuário da mesma maneira como uma DSL. Os recursos adicionais podem ser ativados e desabilitados em tempo de execução dinamicamente. DSLs não precisam ser criados explicitamente para extensão e extensões podem ser criadas mais tarde ou por terceiros, sem alterar a DSL estendida.  
  
 Os recursos adicionais podem incluir o seguinte:  
  
-   Propriedades de elementos de modelo e apresentação  
  
-   Decoradores para formas e conectores  
  
-   Classes, relações, formas e conectores  
  
-   Restrições de validação  
  
-   Guias e itens de caixa de ferramentas  
  
 Um usuário de uma DSL estendido pode criar e salvar um modelo que contém as instâncias dos recursos adicionais, e eles podem ser lidos por outros usuários que instalaram a extensão apropriada. Usuários que não instalaram a extensão não podem usar os recursos adicionais, mas eles podem atualizar e salvar um modelo sem perder os recursos adicionais.  

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

## <a name="see-also"></a>Consulte também  
 [Postagens de blogs relacionados](https://blogs.msdn.microsoft.com/visualstudioalm/tag/code-index/)

