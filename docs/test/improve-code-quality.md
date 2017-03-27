---
title: "Melhorar a qualidade do código"
ms.custom: na
ms.date: 02/17/2017
ms.reviewer: na
ms.suite: na
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: na
ms.topic: article
helpviewer_keywords:
- Visual Studio ALM
- team-based development
ms.assetid: 73baa961-c21f-43fe-bb92-3f59ae9b5945
caps.latest.revision: 39
ms.author: mlearned
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
translationtype: Human Translation
ms.sourcegitcommit: a42f5a30375192c89c9984e40ba0104da98d7253
ms.openlocfilehash: 2fa87621ed76fb93a9e92d558be5519d783274c5
ms.lasthandoff: 03/07/2017

---
# <a name="improve-code-quality"></a>Melhorar a qualidade do código
O que é a qualidade do código? Correção, facilidade de manutenção e até mesmo elegância estão envolvidas na criação de um código excelente. Independentemente de como você o definir, as ferramentas de teste do Visual Studio podem ajudar você e sua equipe a desenvolver e manter altos padrões de excelência de código.  
  
 **Requisitos**  
  
-   Algumas das ferramentas e recursos descritos nesta seção estão disponíveis apenas em edições específicas do Visual Studio — eles não estão universalmente disponíveis no Visual Studio. Listamos os requisitos de edição específica na documentação dessas ferramentas e recursos.  
  
## <a name="in-this-section"></a>Nesta seção  
 A tabela a seguir, você encontrará descrições das tarefas comuns e links para obter mais informações sobre como pode concluir essas tarefas com êxito.  
  
|||  
|-|-|  
|[Efetuar teste de unidade em seu código](../test/unit-test-your-code.md)|O Gerenciador de Testes facilita a integração de testes de unidade em sua prática de desenvolvimento. Você pode usar a estrutura de teste de unidade da Microsoft ou uma das várias estruturas de software livre e de terceiros.|  
|[Live Unit Testing com o Visual Studio](../test/live-unit-testing.md)|O Live Unit Testing executa testes de unidade automaticamente em segundo plano e exibe graficamente a cobertura de código e os resultados de teste no editor de código do Visual Studio.|  
|[Analisando a qualidade do aplicativo](../code-quality/analyzing-application-quality-by-using-code-analysis-tools.md)|As ferramentas de análise de código estático encontram problemas de design, uso, facilidade de manutenção e estilo no código gerenciado e C++. Muitos desses problemas podem resultar em bugs que são difíceis de reproduzir no ambiente de teste padrão.|  
|[Medindo complexidade e facilidade de manutenção do código gerenciado](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md)|As métricas de código são um conjunto de medidas de software que fornecem aos desenvolvedores uma visão melhor do código que estão desenvolvendo. As métricas incluem um índice de facilidade de manutenção para funções e classes, a complexidade ciclomática de funções, a profundidade de herança de classes e a quantidade de acoplamento entre classes.|  
  
## <a name="related-scenarios"></a>Cenários relacionados  
 [Adotando Visual Studio e Team Foundation Server para gerenciamento de ciclo de vida do aplicativo](assetId:///7ae9182f-4762-4bd3-b238-39ce987932e5)  
 Se você não estiver familiarizado com o Visual Studio Team Foundation, pode aprender mais sobre como pode usá-lo em um ambiente de desenvolvimento em equipe para melhorar a produtividade e reduzir os riscos associados ao desenvolvimento de aplicativos.  
  
 [Análise e modelagem de arquitetura](../modeling/analyze-and-model-your-architecture.md)  
 Você pode usar [!INCLUDE[vsPreExt](../test/includes/vspreext_md.md)] para gerenciar os desafios e a complexidade da criação de software. O [!INCLUDE[vsPreShort](../test/includes/vspreshort_md.md)] permite que você modele visualmente o aplicativo, como ele existe agora e como você deseja que exista no futuro. Você pode criar e manter diagramas para ajudá-lo a visualizar os modelos lógicos do seu aplicativo ao mesmo tempo que eles mapeiam para os modelos físicos, isso permite que você altere, valide e analise o software que está “em design”.  
  
 [Testando o aplicativo](https://www.visualstudio.com/docs/test/overview)  
 Você pode usar [!INCLUDE[vsPreShort](../test/includes/vspreshort_md.md)] e [!INCLUDE[vsUltShort](../test/includes/vsultshort_md.md)] para ser mais produtivo durante todo o ciclo de vida de teste. O [!INCLUDE[vsPreShort](../test/includes/vspreshort_md.md)] ou o [!INCLUDE[vsUltShort](../test/includes/vsultshort_md.md)] permite que você planeje seu esforço de teste. Você pode criar, gerenciar, editar e executar testes automáticos e manuais. Você também pode examinar o andamento dos testes com base em seu plano.  
  
 [Protegendo o aplicativo com o PreEmptive Protection – Dotfuscator](../ide/dotfuscator/index.md)  
 É possível usar o Dotfuscator Community Edition gratuito para ajudar a proteger segredos comerciais e outros tipos de IP (propriedade intelectual), reduzir a pirataria e a falsificação e proteger contra adulteração e depuração não autorizada.  O Dotfuscator protege assemblies compilados sem a necessidade de programação adicional ou até mesmo de acesso ao código-fonte.
  
 [Compilando o aplicativo](https://www.visualstudio.com/docs/build/overview)  
 Você pode usar o [!INCLUDE[esprbuild](../test/includes/esprbuild_md.md)] para criar e gerenciar builds automatizados para seu código. O [!INCLUDE[esprbuild](../test/includes/esprbuild_md.md)] permite criar servidores de destino para implantar builds. Além disso, você pode analisar tendências de build.  
  
 [Acompanhando o trabalho usando o Visual Studio Online ou o Team Foundation Server](https://www.visualstudio.com/docs/work/overview)  
 Você pode usar [!INCLUDE[vstsTfsLong](../test/includes/vststfslong_md.md)] para planejar e acompanhar seus projetos, quer você use o processo agile, o processo formal ou uma variação nesses processos. Ao planejar seus projetos, acompanhar o seu progresso em relação ao plano e fazer ajustes necessários, você pode reduzir os riscos, evitar surpresas desagradáveis e gerenciar os custos de seus projetos.
