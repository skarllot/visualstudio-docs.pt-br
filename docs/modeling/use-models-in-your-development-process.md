---
title: Usar modelos no processo de desenvolvimento | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-devops-techdebt
ms.tgt_pltfrm: 
ms.topic: get-started-article
helpviewer_keywords:
- UML, using models
ms.assetid: a33ac8fc-4ba0-4850-b71b-014dc8674e54
caps.latest.revision: 29
author: alexhomer1
ms.author: ahomer
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
ms.sourcegitcommit: 3d07f82ea737449fee6dfa04a61e195654ba35fa
ms.openlocfilehash: 080f77253c886550dad4a10ae46409e5ac2c9506
ms.lasthandoff: 02/22/2017

---
# <a name="use-models-in-your-development-process"></a>Usar modelos no processo de desenvolvimento
No Visual Studio, você pode usar um modelo para ajudá-lo a entender e alterar um sistema, aplicativo ou componente. Um modelo pode ajudá-lo a visualizar o mundo em que o sistema funciona, esclarecer as necessidades dos usuários, definem a arquitetura do sistema, analisar o código e certifique-se de que seu código atende aos requisitos. Consulte [vídeo do Channel 9: melhorar a arquitetura com modelagem](http://go.microsoft.com/fwlink/?LinkID=252078).  
  
 Para ver quais versões do Visual Studio oferecem suporte a cada tipo de modelo, consulte [suporte de versão para a arquitetura e ferramentas de modelagem](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).  
  
## <a name="how-to-use-models"></a>Como usar modelos  
 Modelos podem ajudá-lo de várias maneiras:  
  
-   Desenho de diagramas de modelagem ajuda a esclarecer os conceitos envolvidos em requisitos, arquitetura e design de alto nível. Para obter mais informações, consulte [requisitos de usuário do modelo](../modeling/model-user-requirements.md).  
  
-   Trabalhando com modelos pode ajudá-lo a expor as inconsistências nos requisitos.  
  
-   Comunicando-se com modelos o ajuda a se comunicar conceitos importantes menor maneira ambígua com idioma natural. Para obter mais informações, consulte [modelo de arquitetura do aplicativo](../modeling/model-your-app-s-architecture.md).  
  
-   Às vezes, você pode usar modelos para gerar código ou outros artefatos, como documentos ou esquemas de banco de dados. Por exemplo, os componentes de modelagem de [!INCLUDE[vsUltShort](../code-quality/includes/vsultshort_md.md)] gerados a partir de um modelo.  Para obter mais informações, consulte [gerar e configurar o aplicativo de modelos](../modeling/generate-and-configure-your-app-from-models.md).  
  
 Você pode usar modelos em uma ampla variedade de processos, desde extreme cerimônia ágil para alta.  
  
### <a name="use-models-to-reduce-ambiguity"></a>Usar modelos para reduzir a ambiguidade  
 Linguagem de modelagem é menos ambígua de linguagem natural e é desenvolvido para expressar as ideias normalmente necessárias durante o desenvolvimento de software.  
  
 Se o projeto tiver uma equipe pequena seguindo práticas agile, você pode usar modelos para ajudar a esclarecer as histórias de usuários. Discussões com o cliente sobre suas necessidades, criando um modelo pode gerar perguntas úteis muito mais rápido e, em uma área maior do produto, que escrever código de pico ou protótipo.  
  
 Se seu projeto for grande e inclui as equipes em diferentes partes do mundo, você pode usar modelos para ajudar a comunicar os requisitos e a arquitetura muito mais eficiente do que em texto sem formatação.  
  
 Em ambos os casos a criação de um modelo quase sempre resulta em uma redução significativa no inconsistências e ambiguidades. Participantes diferentes frequentemente têm diferentes entendimentos do mundo dos negócios em que o sistema funciona e diferentes desenvolvedores frequentemente têm diferentes entendimentos do funcionamento do sistema. Usando um modelo como o foco de uma discussão geral expõe essas diferenças. Para obter mais informações sobre como usar um modelo para reduzir as inconsistências, consulte [requisitos de usuário do modelo](../modeling/model-user-requirements.md).  
  
### <a name="use-models-with-other-artifacts"></a>Usar modelos com outros artefatos  
 Um modelo não é por si só, uma especificação de requisitos ou uma arquitetura. É uma ferramenta para expressar alguns aspectos dessas coisas mais claramente, mas não todos os conceitos necessários durante o design de software podem ser expresso. Os modelos, portanto, devem ser usados junto com outros meios de comunicação, como páginas do OneNote ou parágrafos, documentos do Microsoft Office, itens de trabalho em [!INCLUDE[esprfound](../code-quality/includes/esprfound_md.md)], ou notas na parede da sala do projeto. Além do último item, todos os tipos de objeto podem ser vinculados a partes de elementos do modelo.  
  
 Outros aspectos da especificação que são normalmente usados juntamente com modelos incluem o seguinte. Dependendo da escala e o estilo do seu projeto, você pode usar vários desses aspectos ou não usar nenhum:  
  
-   Histórias de usuários. Uma história de usuário é uma breve descrição, discutida com usuários e outros participantes, de um aspecto do comportamento do sistema que será entregue em uma das iterações do projeto. Uma história de usuário típico começa "o cliente poderá..." Uma história de usuário pode apresentar um grupo de casos de uso ou pode definir as extensões de casos de uso que foram desenvolvidos anteriormente. Definir ou estender os casos de uso ajuda a tornar a história de usuário mais clara.  
  
-   Solicitações de alteração. Uma solicitação de alteração em um projeto mais formal é muito semelhante a uma história de usuário em um projeto agile. A abordagem ágil trata todos os requisitos de como as alterações para o que foi desenvolvido em iterações anteriores.  
  
-   Use a descrição do caso. Um caso de uso representa uma forma em que um usuário interage com o sistema para atingir uma meta específica. Uma descrição completa inclui o objetivo, principais e alternativas sequências de eventos e resultados excepcionais. Um diagrama de caso de uso ajuda resumir e fornecem uma visão geral dos casos de uso.  
  
-   Cenários. Um cenário é uma descrição muito detalhada de uma sequência de eventos mostrando como o sistema, os usuários e outros sistemas funcionam juntos para fornecer o valor às partes interessadas. Ele pode assumir a forma de uma slide show da interface do usuário ou um protótipo da interface do usuário. Ele pode descrever um caso de uso ou uma sequência de casos de uso.  
  
-   Glossário. Glossário de requisitos do projeto descreve as palavras com a qual os clientes discutem seu mundo. Os modelos de requisitos e a interface do usuário também devem usar esses termos. Um diagrama de classes pode ajudar a esclarecer as relações entre a maioria destes termos. Criar diagramas e glossário não só reduz a confusão entre os desenvolvedores e usuários, mas também quase sempre expõe mal-entendidos entre os participantes de negócios diferentes.  
  
-   Regras de negócios. Muitas regras de negócios podem ser expressos como invariáveis restrições sobre as associações e os atributos no modelo de classe de requisitos e restrições em diagramas de sequência.  
  
-   Design de alto nível. Descreve as principais partes e como elas se encaixam. Componente, sequência e diagramas de interface são uma parte importante de um design de alto nível.  
  
-   Padrões de design. Descreva as regras de design que são compartilhadas entre as diferentes partes do sistema.  
  
-   Especificações de teste. Scripts de teste e os designs de código de teste podem fazer bom uso de diagramas de atividade e a sequência para descrever as sequências de etapas de teste. Testes de sistema devem ser expressos em termos de modelo de requisitos para que eles podem ser alterados facilmente quando os requisitos são alterados.  
  
-   Plano de projeto. O plano de projeto ou a lista de pendências define quando cada recurso será entregue. Você pode definir cada recurso informando quais casos de uso e ela implementa ou estende as regras de negócio. Você pode se referir a casos de uso e as regras de negócios diretamente no plano, ou você pode definir um conjunto de recursos em um documento separado e usar os títulos de recursos no plano.  
  
### <a name="use-models-in-iteration-planning"></a>Usar modelos no planejamento de iteração  
 Embora todos os projetos são diferentes em sua escala e a organização, um projeto típico é planejado como uma série de iterações de entre duas e seis semanas. É importante planejar suficiente iterações para permitir que os comentários de primeiras iterações a ser usado para ajustar o escopo e os planos para iterações posteriores.  
  
 As sugestões a seguir pode ser útil para ajudar a obter os benefícios de modelagem em um projeto iterativo.  
  
#### <a name="sharpen-focus-as-each-iteration-approaches"></a>Nítido como abordagens cada iteração  
 Conforme se aproxima de cada iteração, use modelos para ajudar a definir o que deve ser entregue ao final da iteração.  
  
-   Modele tudo em detalhes nas iterações anteriores. Na primeira iteração, criar um diagrama de classes para os principais itens no glossário do usuário, desenhar um diagrama de casos de uso principal e desenhar um diagrama dos principais componentes. Não descreva qualquer um desses detalhes finos, porque o detalhe será alterado posteriormente no projeto. Use os termos definidos neste modelo para criar uma lista de recursos ou histórias de usuários principais. Atribua os recursos para iterações para aproximadamente equilibrar a carga de trabalho estimada em todo o projeto. Essas atribuições serão alterado posteriormente no projeto.  
  
-   Tente implementar versões simplificadas de todos os casos de uso mais importantes em uma iteração inicial. Estender os casos de uso em iterações posteriores. Essa abordagem ajuda a reduzir o risco de ocorrer uma falha nos requisitos ou a arquitetura muito tarde no projeto fazer nada sobre ele.  
  
-   No final de cada iteração, mantenha um workshop de requisitos para definir detalhadamente os requisitos ou histórias de usuários que serão desenvolvidas na próxima iteração. Convide usuários e partes interessadas no negócio que podem decidir prioridades, bem como desenvolvedores e testadores de sistema. Permitir três horas definir requisitos para uma iteração 2 semanas.  
  
-   O objetivo do workshop é concordar que seja realizado no final da próxima iteração de todos. Use modelos como uma das ferramentas para ajudar a esclarecer os requisitos. A saída do workshop é uma lista de pendências de iteração: ou seja, as tarefas de uma lista de desenvolvimento em [!INCLUDE[esprfound](../code-quality/includes/esprfound_md.md)] e conjuntos de teste no [!INCLUDE[TCMext](../misc/includes/tcmext_md.md)].  
  
-   O workshop de requisitos, discutiremos o design somente na medida, você precisa determinar as estimativas para as tarefas de desenvolvimento. Caso contrário, mantenha a discussão ao comportamento do sistema que os usuários podem enfrentar diretamente. Manter o modelo de requisitos separado do modelo de arquitetura.  
  
-   Os participantes não técnicos geralmente não têm problemas Noções básicas sobre diagramas UML, com a orientação de você.  
  
#### <a name="link-model-to-work-items"></a>Modelo de link a itens de trabalho  
 Após o workshop de requisitos, elaborar os detalhes do modelo de requisitos e vincular o modelo para tarefas de desenvolvimento. Você pode fazer isso vinculando itens de trabalho em [!INCLUDE[esprfound](../code-quality/includes/esprfound_md.md)] para elementos no modelo. Para saber como fazer isso, consulte [vincular elementos de modelo e itens de trabalho](../modeling/link-model-elements-and-work-items.md).  
  
 Você pode vincular qualquer elemento para itens de trabalho, mas os elementos mais úteis são os seguintes:  
  
-   Comentários que descrevem as regras de negócios ou qualidade dos requisitos de serviço. Para obter mais informações, consulte [requisitos de usuário do modelo](../modeling/model-user-requirements.md).  
  
#### <a name="link-model-to-tests"></a>Modelo de link para testes  
 Use o modelo de requisitos para orientar o design dos testes de aceitação. Crie esses testes simultaneamente com o trabalho de desenvolvimento.  
  
 Para saber mais sobre essa técnica, consulte [desenvolver testes de um modelo de](../modeling/develop-tests-from-a-model.md).  
  
#### <a name="estimate-remaining-work"></a>Estimar o trabalho restante  
 Um modelo de requisitos pode ajudar a estimar o tamanho total do projeto em relação ao tamanho de cada iteração. Avaliar o número e a complexidade de casos de uso e classes pode ajudá-lo a estimar o trabalho de desenvolvimento que serão necessário. Quando você concluiu as primeira algumas iterações, uma comparação dos requisitos abordados e ainda os requisitos para cobrir pode fornecer uma medida aproximada do custo e o escopo do restante do projeto.  
  
 No final de cada iteração, examine a atribuição de requisitos para iterações futuras. Ele pode ser útil representar o estado do seu software no final de cada iteração como um subsistema de um diagrama de caso de uso. A conversa, você pode mover os casos de uso e usar extensões casos um desses subsistemas para outro.  
  
## <a name="levels-of-abstraction"></a>Níveis de abstração  
 Os modelos têm um intervalo de abstração em relação ao software. Os modelos mais concretos representam diretamente o código do programa e os modelos mais abstratos representam conceitos comerciais que podem ou não podem ser representados no código.  
  
 Um modelo pode ser visualizado por meio de vários tipos de diagramas. Para obter informações sobre modelos e diagramas, consulte [criar modelos para seu aplicativo](../modeling/create-models-for-your-app.md).  
  
 Tipos diferentes de diagrama são úteis para descrever o design em diferentes níveis de abstração. Muitos dos tipos de diagrama são úteis em mais de um nível. Esta tabela mostra como cada tipo de diagrama pode ser usado.  
  
|Nível de design|Tipos de diagrama|  
|------------------|-------------------|  
|Processo de negócios<br /><br /> Noções básicas sobre o contexto no qual o sistema será usado o ajudará a entender o que os usuários que precisam dele.|-Diagramas de classe conceitual descrevem os conceitos de negócios usados dentro do processo de negócios.|  
|Requisitos do usuário<br /><br /> Definição de que os usuários precisam do sistema.|-Regras de negócios e a qualidade dos requisitos de serviço podem ser descritos em documentos separados.|  
|Design de nível alto<br /><br /> A estrutura geral do sistema: os principais componentes e como eles acoplar juntos.|-Diagramas de dependência descrevem como o sistema está estruturado em partes interdependentes. Você pode validar o código de programa em diagramas de dependência para garantir que ele adere à arquitetura.|  
|Análise de código<br /><br /> Diagramas podem ser gerados a partir do código.|-Diagramas de dependência mostram as dependências entre classes. Código atualizado pode ser validado em relação a um diagrama de dependência.<br />-Diagramas de classe mostram as classes no código.|  
  
## <a name="external-resources"></a>Recursos externos  
  
|**Categoria**|**Links**|  
|------------------|---------------|  
|**Vídeos**|![link para vídeo](~/data-tools/media/playvideo.gif "PlayVideo") [MSDN vídeos como faço para: como criar e usar modelos e diagramas UML (Visual Studio 2010 Ultimate)](http://go.microsoft.com/fwlink/?LinkId=214460)<br /><br /> ![link para vídeo](~/data-tools/media/playvideo.gif "PlayVideo") [Channel 9: UML com o Visual Studio 2010](http://go.microsoft.com/fwlink/?LinkID=201106)<br /><br /> ![link para vídeo](~/data-tools/media/playvideo.gif "PlayVideo") [série MSDN How Do I: ferramentas UML e extensibilidade (Visual Studio 2010 Ultimate)](http://go.microsoft.com/fwlink/?LinkID=214467)|  
|**Fóruns**|-   [Visualização do Visual Studio < / ferramentas de modelagem](http://go.microsoft.com/fwlink/?LinkId=184720)<br />-   [Visualização do Visual Studio < / modelagem SDK (ferramentas DSL)](http://go.microsoft.com/fwlink/?LinkId=184721)|  
|**Blogs**|[Visual Studio ALM + Blog Team Foundation Server](http://go.microsoft.com/fwlink/?LinkID=201340)|  
|**Diários e artigos técnicos**|[MSDN Architecture Center](http://go.microsoft.com/fwlink/?LinkId=201343)<br /><br /> [Diretrizes de ferramentas de arquitetura do Visual Studio](../modeling/visual-studio-architecture-tooling-guidance.md)|  
  
## <a name="see-also"></a>Consulte também  
 [Usar modelos no desenvolvimento ágil](http://msdn.microsoft.com/en-us/592ac27c-3d3e-454a-9c38-b76658ed137f)   
 [Criar modelos para o seu aplicativo](../modeling/create-models-for-your-app.md)   
 [Requisitos do modelo de usuário](../modeling/model-user-requirements.md)   
 [Modelo de arquitetura do aplicativo](../modeling/model-your-app-s-architecture.md)   
 [Desenvolver testes de um modelo](../modeling/develop-tests-from-a-model.md)   
 [Estruturar a solução de modelagem](../modeling/structure-your-modeling-solution.md)

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

