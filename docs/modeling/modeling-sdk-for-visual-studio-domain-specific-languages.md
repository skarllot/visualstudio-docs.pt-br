---
title: "SDK de modelagem para Visual Studio - linguagens específicas do domínio | Documentos do Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-devops-techdebt
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Domain-Specific Language Tools
- Domain-Specific Language
ms.assetid: 17a531e2-1964-4a9d-84fd-6fb1b4aee662
caps.latest.revision: 77
author: alancameronwills
ms.author: awills
manager: douge
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
ms.sourcegitcommit: 3d07f82ea737449fee6dfa04a61e195654ba35fa
ms.openlocfilehash: 86e70eb82260cdced1ee4d74965832fbc7fa56ab
ms.lasthandoff: 02/22/2017

---
# <a name="modeling-sdk-for-visual-studio---domain-specific-languages"></a>SDK de Modelagem para Visual Studio - linguagens específicas ao domínio
Usando o SDK de modelagem para [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], você pode criar ferramentas de desenvolvimento sofisticado baseado no modelo que você pode integrar [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Da mesma forma, você pode criar uma ou mais definições de modelo e integrá-las em um conjunto de ferramentas.  
  
 No centro do MSDK está a definição de um modelo que você cria para representar conceitos em sua área de negócios. Você pode cercar o modelo com várias ferramentas, como uma exibição diagramática, a capacidade de gerar código e outros artefatos, comandos para transformar o modelo, e a capacidade de interagir com código e os outros objetos em [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. À medida que o modelo é desenvolvido, você pode combiná-lo com outros modelos e ferramentas para formar um conjunto de ferramentas avançadas centradas em seu desenvolvimento.  
  
 O MSDK permite desenvolver rapidamente um modelo na forma de uma linguagem específica do domínio (DSL). Você começa ao usar um editor especializado para definir um esquema ou sintaxe abstrata junto com uma notação gráfica. Dessa definição, o VMSDK gera:  
  
-   Uma implementação de modelo com uma API fortemente tipada executada em um repositório baseado em transação.  
  
-   Um gerenciador baseado em árvore.  
  
-   Um editor gráfico no qual os usuários podem exibir o modelo ou partes dele que você definir.  
  
-   Métodos de serialização que salvam seus modelos em XML legível.  
  
-   Recursos para gerar código de programa e outros artefatos usando modelagem de texto.  
  
 Você pode personalizar e estender todos esses recursos. Suas extensões são integradas de tal forma que você ainda pode atualizar a definição de DSL e gerar novamente os recursos sem perder suas extensões.  
  
[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]
 
 [Postagens de blogs relacionados](https://blogs.msdn.microsoft.com/visualstudioalm/tag/code-index/)
  
 Para obter orientação sobre técnicas avançadas e solução de problemas, visite [fórum DSL < / modelagem ferramentas extensibilidade do Visual Studio](http://go.microsoft.com/fwlink/?LinkID=186074).  
  
## <a name="in-this-section"></a>Nesta seção  
 [Introdução às linguagens específicas de domínio](../modeling/getting-started-with-domain-specific-languages.md)  
  
 [Noções básicas sobre modelos, classes e relações](../modeling/understanding-models-classes-and-relationships.md)  
  
 [Como definir uma linguagem específica de domínio](../modeling/how-to-define-a-domain-specific-language.md)  
  
 [Personalizando e estendendo uma linguagem específica de domínio](../modeling/customizing-and-extending-a-domain-specific-language.md)  
  
 [Validação em uma linguagem específica de domínio](../modeling/validation-in-a-domain-specific-language.md)  
  
 [Escrevendo código para personalizar uma linguagem específica de domínio](../modeling/writing-code-to-customise-a-domain-specific-language.md)  
  
 [Gerando código com base em uma linguagem específica de domínio](../modeling/generating-code-from-a-domain-specific-language.md)  
  
 [Noções básicas do código DSL](../modeling/understanding-the-dsl-code.md)  
  
 [Personalizando o armazenamento de arquivos e a serialização XML](../modeling/customizing-file-storage-and-xml-serialization.md)  
  
 [Implantando soluções de linguagem específica de domínio](../modeling/deploying-domain-specific-language-solutions.md)  
  
 [Criando uma linguagem específica de domínio baseada no Windows Forms](../modeling/creating-a-windows-forms-based-domain-specific-language.md)  
  
 [Criando uma linguagem específica de domínio baseada no WPF](../modeling/creating-a-wpf-based-domain-specific-language.md)  
  
 [Como estender o designer de linguagem específica de domínio](../modeling/how-to-extend-the-domain-specific-language-designer.md)  
  
 [Edições do Visual Studio com suporte pelo SDK de Visualização e Modelagem](../modeling/supported-visual-studio-editions-for-visualization-amp-modeling-sdk.md)  
  
 [Como migrar uma linguagem específica de domínio para uma nova versão](../modeling/how-to-migrate-a-domain-specific-language-to-a-new-version.md)  
  
 [Referência de API do SDK de Modelagem para Visual Studio](../modeling/api-reference-for-modeling-sdk-for-visual-studio.md)

