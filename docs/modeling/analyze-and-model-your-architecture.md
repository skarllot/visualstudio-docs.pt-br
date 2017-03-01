---
title: Analisar e sua arquitetura de modelo | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-devops-techdebt
ms.tgt_pltfrm: 
ms.topic: get-started-article
helpviewer_keywords:
- Visual Studio Ultimate, exploring code
- Visual Studio Ultimate, visualizing code
- diagrams - modeling
- Visual Studio ALM, modeling
- application, design
- architecture
- code visualization
- application design
- applications, architecture
- code exploration
- Visual Studio ALM, exploring code
- modeling
- application architecture
- application, modeling
- applications, modeling
- architecture [Visual Studio ALM], modeling
- application modeling
- Visual Studio Ultimate, modeling
- architecture [Visual Studio Ultimate], modeling
- application, architecture
- Visual Studio ALM, visualizing code
- applications, designing
ms.assetid: c9f04cfa-72bd-419d-a952-616eed01472e
caps.latest.revision: 127
author: alexhomer1
ms.author: ahomer
manager: douge
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
translationtype: Machine Translation
ms.sourcegitcommit: 98d1214d1cda81102f9e03a8ce8b83886aa2c0ec
ms.openlocfilehash: 78217396085aa5531ec2cbdd5dff522201287777
ms.lasthandoff: 02/22/2017

---
# <a name="analyze-and-model-your-architecture"></a>Analisar e modelar a sua arquitetura
Verifique se que seu aplicativo atende aos requisitos de arquitetura usando a arquitetura do Visual Studio e ferramentas para projetar e modelar seu aplicativo de modelagem. 

* Entenda o código de programa existente mais facilmente usando o Visual Studio para visualizar a estrutura do código, comportamento e relações. 

* Treinar sua equipe na necessidade de respeitar as dependências de arquitetura.  
  
* Crie modelos em diferentes níveis de detalhe em todo o ciclo de vida do aplicativo como parte do processo de desenvolvimento.

Consulte [cenário: alterar o design usando visualização e modelagem](../modeling/scenario-change-your-design-using-visualization-and-modeling.md).  
  
## <a name="to"></a>Para  
  
|||  
|-|-|  
|**Visualizar código**:<br /><br /> -Consulte a organização e as relações do código Criando mapas de código. Visualize dependências entre assemblies, namespaces, classes, métodos e assim por diante.<br />-Consulte a estrutura de classes e membros para um projeto específico com a criação de diagramas de classe no código.<br />-Encontre conflitos entre o código e o seu design com a criação de diagramas de dependência para validar o código.|-   [Visualizar código](../modeling/visualize-code.md)<br />-   [Trabalhando com Classes e outros tipos (Designer de classe)](../ide/working-with-classes-and-other-types-class-designer.md)<br />-   [Vídeo: Entender a estrutura do código com mapas de código do Visual Studio 2015](https://channel9.msdn.com/Events/Visual-Studio/Connect-event-2015/502)<br />-   [Vídeo: Validar suas dependências de arquitetura em tempo real](https://sec.ch9.ms/sessions/69613110-c334-4f25-bb36-08e5a93456b5/170ValidateArchitectureDependenciesWithVisualStudio.mp4)|  
|**Definir a arquitetura**:<br /><br /> -Definir e impor restrições sobre dependências entre os componentes do seu código com a criação de diagramas de dependência.|-   [Vídeo: Validar dependências de arquitetura com o Visual Studio (Channel 9)](https://channel9.msdn.com/Events/Connect/2016/170)|  
|**Validar o seu sistema com os requisitos e o objetivo de design:**<br /><br /> -Validar dependências de código com diagramas de dependência que descrevem a arquitetura pretendida e evitar alterações entrarem em conflito com o design.|-   [Vídeo: Validar dependências de arquitetura com o Visual Studio (Channel 9)](https://channel9.msdn.com/Events/Connect/2016/170)|  
|**Compartilhar modelos, diagramas e mapas de código usando o controle de versão do Team Foundation**:<br /><br /> -Coloque mapas de código, projetos e diagramas deoendency sob controle de versão do Team Foundation para poder compartilhá-los.|Quando você tiver vários usuários que trabalham com esses itens sob controle de versão do Team Foundation, use estas diretrizes para ajudá-lo a evitar problemas de controle de versão:<br /><br /> -   [Gerenciar modelos e diagramas sob controle de versão](../modeling/manage-models-and-diagrams-under-version-control.md)|  
|**Personalizar modelos e diagramas**:<br /><br /> -Crie suas próprias linguagens específicas de domínio.|-   [SDK de modelagem para Visual Studio - linguagens específicas de domínio](../modeling/modeling-sdk-for-visual-studio-domain-specific-languages.md)|  
|**Gerar texto usando modelos T4**:<br /><br /> -Usar blocos de texto e a lógica de controle dentro de modelos para gerar arquivos de texto.<br /> -Compilação de modelo T4 com o MSBuild incluído no Visual Studio|-   [Geração de código e modelos de texto T4](../modeling/code-generation-and-t4-text-templates.md)|

Para ver quais versões do Visual Studio oferecem suporte a cada recurso, consulte [suporte à versão de arquitetura e ferramentas de modelagem](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport)  
  
## <a name="types-of-models-and-their-uses"></a>Tipos de modelos e seus usos  
  
|**O tipo de modelo e os usos mais comuns**|  
|-------------------------------------|  
|**Mapas de código**<br /><br /> Mapas de código ajudam você a ver a organização e as relações no seu código.<br /><br /> Usos típicos:<br /><br /> -Examine o código do programa para que você possa entender melhor a sua estrutura e suas dependências, como atualizá-lo e estimar o custo de alterações propostas.<br /><br /> Consulte:<br /><br /> -   [Mapear dependências em suas soluções](../modeling/map-dependencies-across-your-solutions.md)<br />-   [Use mapas de código para depurar seus aplicativos](../modeling/use-code-maps-to-debug-your-applications.md)<br />-   [Localizar possíveis problemas usando analisadores de mapa de código](../modeling/find-potential-problems-using-code-map-analyzers.md)|  
|**Diagrama de dependência**<br /><br /> Diagramas de dependência permitem que você defina a estrutura de um aplicativo como um conjunto de camadas ou blocos com dependências explícitas. Você pode executar a validação para detectar conflitos entre dependências no código e descrito em um diagrama de dependência.<br /><br /> Usos típicos:<br /><br /> -Estabilize a estrutura do aplicativo por meio de várias alterações durante sua vida útil.<br />-Detecte conflitos de dependência não intencionais antes de verificar as alterações no código.<br /><br /> Consulte:<br /><br /> -   [Crie diagramas de dependência de seu código](../modeling/create-layer-diagrams-from-your-code.md)<br />-   [Diagramas de dependência: referência](../modeling/layer-diagrams-reference.md)<br />-   [Validar código com diagramas de dependência](../modeling/validate-code-with-layer-diagrams.md)|  
|**Linguagem específica do domínio (DSL)**<br /><br /> Uma DSL é uma notação que você cria para uma finalidade específica. No Visual Studio, é geralmente gráfica.<br /><br /> Usos típicos:<br /><br /> -Gerar ou configurar as partes do aplicativo. Trabalho é necessário para desenvolver as ferramentas e a notação. O resultado pode ser mais adequado para seu domínio do que uma personalização UML.<br />-Para projetos grandes ou linhas de produtos, onde o investimento em DSL e suas ferramentas de desenvolvimento é retornado pelo seu uso em mais de um projeto.<br /><br /> Consulte:<br /><br /> -   [SDK de modelagem para Visual Studio - linguagens específicas de domínio](../modeling/modeling-sdk-for-visual-studio-domain-specific-languages.md)|  
  
## <a name="where-can-i-get-more-information"></a>Onde posso obter mais informações?  
  
[Visualização do Visual Studio < / Fórum das ferramentas de modelagem](http://go.microsoft.com/fwlink/?LinkId=184720)  
  
## <a name="see-also"></a>Consulte também  
 [O que há de novo](../modeling/what-s-new-for-design-in-visual-studio.md)   
 [Operações de desenvolvimento e gerenciamento de ciclo de vida de aplicativos](http://msdn.microsoft.com/Library/74a1f71d-7f23-4c71-8fd7-89ede614fab6)

