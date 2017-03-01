---
title: "Cenário: Alterar o design usando visualização e modelagem | Documentos do Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-devops-techdebt
ms.tgt_pltfrm: 
ms.topic: get-started-article
helpviewer_keywords:
- code visualization [Visual Studio ALM]
- modeling software [Visual Studio ALM]
- software modeling [Visual Studio ALM]
- walkthroughs [Visual Studio ALM], visualizing code
- walkthrough [Visual Studio ALM], visualizing code
- walkthrough [Visual Studio ALM], modeling software
- walkthroughs [Visual Studio ALM], modeling software
ms.assetid: ccc80825-a4a0-44fa-a0bb-f95254785a3b
caps.latest.revision: 61
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
ms.sourcegitcommit: 3d07f82ea737449fee6dfa04a61e195654ba35fa
ms.openlocfilehash: 4f46bc8e8b4dd476e90ebd122895bb354d967795
ms.lasthandoff: 02/22/2017

---
# <a name="scenario-change-your-design-using-visualization-and-modeling"></a>Cenário: alterar o design usando visualização e modelagem
Certifique-se de que o seu sistema de software atenda às necessidades de usuários usando a visualização e modelagem de ferramentas no Visual Studio.
Use ferramentas como mapas de código, diagramas de dependência e diagramas de classe para:  
  
 Para ver quais versões do Visual Studio oferecem suporte a cada ferramenta, consulte [suporte de versão para a arquitetura e ferramentas de modelagem](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).  
  
-   Esclarecer os processos de negócios e requisitos dos usuários.  
  
-   Visualize e explore o código existente.  
  
-   Descreva as alterações a um sistema existente.  
  
-   Verifique se o sistema atende aos seus requisitos.  
  
-   Manter o código consistente com o design.  
  
 Este passo a passo:  
  
-   Descreve como essas ferramentas podem trazer benefícios para seu projeto de software.  
  
-   Mostra como você pode usar essas ferramentas, independentemente sua abordagem de desenvolvimento, com um cenário de exemplo.  
  
 Para obter mais informações sobre essas ferramentas e os cenários que oferecem suporte a eles, consulte:  
  
-   [Análise e modelagem de arquitetura](../modeling/analyze-and-model-your-architecture.md)  
  
-   [Visualizar código](../modeling/visualize-code.md)  
  
##  <a name="a-namescenariooverviewa-scenario-overview"></a><a name="ScenarioOverview"></a>Visão geral do cenário  
 Este cenário descreve episódios dos ciclos de vida de desenvolvimento de software de duas empresas fictícios: jantar agora e Editora Zulu. Jantar agora fornece um serviço de entrega refeição baseado na Web em Seattle. Os clientes podem solicitar refeições e pagá-los no site da Web agora jantar. Os pedidos, em seguida, são enviados para o restaurante local apropriado para entrega. Zulu Publishing, uma empresa em Nova York, executa várias empresas off e na Web. Por exemplo, executarem um site da Web onde os clientes podem postar resenhas de restaurantes.  
  
 Zulu recentemente adquirida jantar agora e quer fazer as seguintes alterações:  
  
-   Integre seus sites da Web, adicionando recursos de análise do restaurante para jantar agora.  
  
-   Substitua o sistema de pagamento do jantar agora por do Zulu.  
  
-   Expanda o serviço jantar agora toda a região.  
  
 Jantar agora usa o SCRUM e eXtreme Programming. Eles têm cobertura de teste muito alta e não há suporte para muito pouco código. Minimizar riscos pela criação de pequenas, mas versões de trabalho de um sistema e, em seguida, adicionando funcionalidade incrementalmente. Eles desenvolverem seu código ao longo de iterações curtos e frequentes. Isso permite que eles absorver alterações com confiança, refatorar o código com frequência e evitar "big design logo de início".  
  
 Zulu mantém um conjunto muito maior e mais complexo de sistemas, alguns dos quais são mais de 40 anos de idade. Eles são muito cuidados ao fazer alterações devido à complexidade e escopo do código herdado. Eles seguem um processo de desenvolvimento mais rigoroso, preferindo para criar soluções detalhadas e documentar as alterações que ocorrem durante o desenvolvimento e design.  
  
 Ambas as equipes usam diagramas de modelagem no Visual Studio para ajudá-los a desenvolver sistemas que atendam às necessidades dos usuários. Eles usam o Team Foundation Server juntamente com outras ferramentas para ajudá-los a planejar, organizar e gerenciar seus trabalhos.  
  
 Para obter mais informações sobre o Team Foundation Server, consulte:  
  
-   [Planejamento e acompanhamento de trabalho](#PlanningTracking)  
  
-   [Testes, validação e fazer check-in de código atualizado](#TestValidateCheckInCode)  
  
##  <a name="a-namemodelingdiagramstoolsa-roles-of-architecture-and-modeling-diagrams-in-software-development"></a><a name="ModelingDiagramsTools"></a>Funções de arquitetura e modelagem diagramas no desenvolvimento de Software  
 A tabela a seguir descreve as funções que essas ferramentas podem desempenhar durante várias e várias fases do ciclo de vida de desenvolvimento de software:  
  
||**Requisitos de usuário de modelagem**|**Modelagem de processo empresarial**|**Arquitetura de sistema < / Design**|**Visualização de código < / exploração**|**Verificação**|  
|------|------------------------------------|-----------------------------------|--------------------------------------|------------------------------------------|----------------------|  
|Diagrama de linguagem específica do domínio (DSL)|Sim|Sim|Sim|||  
|Diagrama de dependência, validação da camada|||Sim|Sim|Sim|  
|Mapa de código|||Sim|Sim|Sim|  
|Class Designer (base)||||Sim||  
  
Para desenhar diagramas de dependência, você deve criar um projeto de modelagem como parte de uma solução existente ou um novo. Esses diagramas devem ser criados no projeto de modelagem.
Itens em diagramas de dependência estão localizados no projeto de modelagem, mas elas não são armazenadas no modelo comum. Mapas de código e diagramas de classe .NET criados a partir de código existem fora do projeto de modelagem.  
  
 Consulte:  
  
-   [Crie diagramas de dependência de seu código](../modeling/create-layer-diagrams-from-your-code.md)  
  
-   [Mapear as dependências nas soluções](../modeling/map-dependencies-across-your-solutions.md)  
  
-   [Como adicionar diagramas de classe a projetos (Designer de Classe)](../ide/how-to-add-class-diagrams-to-projects-class-designer.md)  
  
-   [SDK de Modelagem para Visual Studio – linguagens específicas de domínio](../modeling/modeling-sdk-for-visual-studio-domain-specific-languages.md)  

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]
  
 Ambas as equipes também usam a validação de dependência para certificar-se de que o código em desenvolvimento permaneça consistente com o design.  
  
 Consulte:  
  
-   [Manter o código consistente com o Design](#ValidatingCode)  
  
-   [Descreve a arquitetura lógica: diagramas de dependência](#DescribeLayers)  
  
-   [Validar código com diagramas de dependência](../modeling/validate-code-with-layer-diagrams.md)  
  
    > [!NOTE]
    >  Algumas versões do Visual Studio dão suporte a validação de dependência e versões somente leitura de mapas de código para visualização e modelagem. Para ver quais versões do Visual Studio oferecer suporte a esse recurso, consulte [suporte de versão para a arquitetura e ferramentas de modelagem](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).  
  
##  <a name="a-nameunderstandingcommunicatinga-understanding-and-communicating-information-about-the-system"></a><a name="UnderstandingCommunicating"></a>Compreender e comunicar informações sobre o sistema  
 Há uma ordem prescrita para usar a modelagem diagramas, para que possa usá-los como eles se ajustam com suas necessidades ou a abordagem do Visual Studio. Geralmente, as equipes rever seus modelos iterativamente e com frequência em todo o projeto. Cada diagrama oferece vantagens específicas para ajudá-lo a entender, descrever e comunicar diferentes aspectos do sistema em desenvolvimento.  
  
 Agora o jantar e Zulu se comunicar entre si e com os participantes do projeto usando diagramas como sua linguagem comum. Por exemplo, jantar agora usa diagramas para executar estas tarefas:  
  
-   Visualize o código existente.  
  
-   Se comunicam Zulu sobre histórias de usuários novos ou atualizados.  
  
-   Identificar as alterações que são necessários para suportar as histórias de usuários novos ou atualizados.  
  
 Zulu usa diagramas para executar estas tarefas:  
  
-   Saiba mais sobre o processo de negócios jantar agora.  
  
-   Entenda o design do sistema.  
  
-   Se comunicam com jantar agora sobre os requisitos de usuário novo ou atualizado.  
  
-   Atualizações do documento para o sistema.  
  
 Os diagramas são integrados com o Team Foundation Server para que as equipes podem planejar, gerenciar e acompanhar seu trabalho mais facilmente. Por exemplo, usar modelos para identificar casos de teste e tarefas de desenvolvimento e estimar o trabalho. Zulu links Team Foundation Server itens de trabalho a elementos de modelo para que eles podem monitorar o progresso e certifique-se de que o sistema atende aos requisitos dos usuários. Por exemplo, eles vinculam casos de uso para itens de trabalho de caso de teste para poder ver que os casos de uso são atendidos quando todos os testes passarem.  
  
 Antes de equipes check-in de suas alterações, elas validam o código no design e os testes executando compilações que incluem validação de dependência e testes automatizados. Isso ajuda a garantir que o código atualizado não entrem em conflito com o design e anteriormente interromper a funcionalidade de trabalho.  
  
 Consulte:  
  
-   [Identificar alterações ao sistema existente](#DeterminingChanges)  
  
-   [Manter o código consistente com o design](#ValidatingCode)  
  
-   [Dicas gerais para criar e usar modelos](#GeneralTips)  
  
-   [Planejamento e acompanhamento de trabalho](#PlanningTracking)  
  
-   [Testes, validação e fazer check-in de código atualizado](#TestValidateCheckInCode)  

###  <a name="a-namedeterminingchangesa-identifying-changes-to-the-existing-system"></a><a name="DeterminingChanges"></a>Identificar alterações ao sistema existente  
 Jantar agora deve estimar o custo de atender o novo requisito. Isso depende em parte quanto esta alteração irá afetar outras partes do sistema. Para compreender isso, um dos desenvolvedores jantar agora cria esses mapas e diagramas de código existente:  
  
|**Mapa ou diagrama**|**programas**|  
|------------------------|---------------|  
|*Mapa de código*<br /><br /> Consulte:<br /><br /> -   [Mapear dependências em suas soluções](../modeling/map-dependencies-across-your-solutions.md)<br />-   [Procurar e reorganizar mapas de código](../modeling/browse-and-rearrange-code-maps.md)<br />-   [Personalizar os mapas de código editando os arquivos DGML](../modeling/customize-code-maps-by-editing-the-dgml-files.md)|Dependências e outras relações no código.<br /><br /> Por exemplo, jantar agora pode começar analisando mapas de código de assembly para uma visão geral de assemblies e suas dependências. Eles podem detalhar os mapas para explorar os namespaces e classes desses assemblies.<br /><br /> Jantar agora também pode criar mapas para explorar a áreas específicas e outros tipos de relações no código. Eles usam o Gerenciador de soluções para localizar e selecionar as áreas e as relações de seu interesse.|  
|*Diagrama de classes base*<br /><br /> Consulte [como: Adicionar diagramas de classe a projetos (Designer de classe)](../ide/how-to-add-class-diagrams-to-projects-class-designer.md).|Classes existentes no código|  
  
 Por exemplo, o desenvolvedor cria um mapa de código. Ela ajusta seu escopo para se concentrar nas áreas que serão afetadas pelo novo cenário. Essas áreas são selecionadas e realçadas no mapa:  
  
 ![Gráfico de dependência de Namespace](../modeling/media/namespace_reviewsystem.png "Namespace_ReviewSystem")  
  
 **Mapa de código de Namespace**  
  
 O desenvolvedor expande os namespaces selecionados para ver suas classes, métodos e relações:  
  
 ![Gráfico de dependência de namespace expandido](../modeling/media/dep_reviewsystem.png "Dep_ReviewSystem")  
  
 **Mapa de código de namespace expandido com links de grupo cruzado visíveis**  
  
 O desenvolvedor examina o código para localizar as classes afetados e métodos. Para ver os efeitos de cada alteração à medida que você faz deles, regenerar os mapas de código após cada alteração. Consulte [Visualizar código](../modeling/visualize-code.md).  
  
 Para descrever as alterações para outras partes do sistema, como componentes ou interações, a equipe pode desenhar esses elementos em quadros de comunicações. Eles também podem desenhar os diagramas a seguir no Visual Studio para que os detalhes podem ser capturados, gerenciados e compreendidos por ambas as equipes:  
  
|**Diagramas**|**Descreve**|  
|------------------|-------------------|  
|*Diagrama de classes base*<br /><br /> Consulte [como: Adicionar diagramas de classe a projetos (Designer de classe)](../ide/how-to-add-class-diagrams-to-projects-class-designer.md).|Classes existentes no código.|  
  
###  <a name="a-namevalidatingcodea-keeping-code-consistent-with-the-design"></a><a name="ValidatingCode"></a>Manter o código consistente com o Design  
 Jantar agora deve se certificar de que o código atualizado permaneça consistente com o design. Eles criar diagramas de dependência que descrevem as camadas de funcionalidade no sistema, especifique as dependências permitidas entre os artefatos de solução-las e associar a essas camadas.  
  
|**Diagrama**|**Descreve**|  
|-----------------|-------------------|  
|*Diagrama de dependência*<br /><br /> Consulte:<br /><br /> -   [Crie diagramas de dependência de seu código](../modeling/create-layer-diagrams-from-your-code.md)<br />-   [Diagramas de dependência: referência](../modeling/layer-diagrams-reference.md)<br />-   [Diagramas de dependência: diretrizes](../modeling/layer-diagrams-guidelines.md)<br />-   [Validar código com diagramas de dependência](../modeling/validate-code-with-layer-diagrams.md)|A arquitetura lógica do código.<br /><br /> Um diagrama de dependência organiza e mapeia os artefatos em um [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] solução abstrair grupos chamados *camadas*. Essas camadas identificam as funções, tarefas ou funções que executam esses artefatos no sistema.<br /><br /> Diagramas de camada são úteis para descrever o design desejado do sistema e validação de código em evolução em relação a esse design.<br /><br /> Para criar camadas, arraste itens do Gerenciador de soluções, mapas de código, modo de exibição de classe e Pesquisador de objetos. Para desenhar novas camadas, use a caixa de ferramentas ou clique com botão direito da superfície do diagrama.<br /><br /> Para exibir dependências existentes, clique com botão direito da superfície do diagrama de camada e, em seguida, clique em **gerar dependências**. Para especificar dependências pretendidas, desenhe novas dependências.|  
  
 Por exemplo, o diagrama de dependência a seguir descreve as dependências entre camadas e o número de artefatos que estão associados com cada camada:  
  
 ![Diagrama de dependência do sistema de pagamento integrado](../modeling/media/layer_integrated_dnlucerne.png "Layer_Integrated_DNLucerne")  
  
 **Diagrama de dependência**  
  
 Para certificar-se de que está em conflito com o design não ocorram durante o desenvolvimento de código, os usos de equipes validação de dependência em compilações que são executados no Team Foundation Build. Eles também criar uma tarefa MSBuild personalizada para exigir validação de dependência em suas operações de check-in. Eles usam relatórios de compilação para coletar erros de validação.  
  
 Consulte:  
  
-   [Definir o processo de compilação](http://msdn.microsoft.com/Library/61593e10-d24b-492f-b19a-af4d85abea6b)  
  
-   [Usar um processo de compilação de check-in para validar alterações](http://msdn.microsoft.com/Library/9cfc8b9c-1023-40fd-8ab5-1b1bd9c172ec)  
  
-   [Personalizar o modelo de processo de compilação](http://msdn.microsoft.com/Library/b94c58f2-ae6f-4245-bedb-82cd114f6039)  
  
###  <a name="a-namegeneraltipsa-general-tips-for-creating-and-using-models"></a><a name="GeneralTips"></a>Dicas gerais para criar e usar modelos  
  
-   A maioria dos diagramas consistem em nós que são conectados por linhas. Para cada tipo de diagrama, a caixa de ferramentas fornece tipos diferentes de nós e linhas.  
  
     Para abrir a caixa de ferramentas, no **exibição** menu, clique em **ferramentas**.  
  
-   Para criar um nó, arraste-o da caixa de ferramentas para o diagrama. Determinados tipos de nós devem ser arrastados para nós existentes. Por exemplo, em um diagrama de componente, uma nova porta deve ser adicionada a um componente existente.  
  
-   Para criar uma linha ou uma conexão, clique na ferramenta apropriada na caixa de ferramentas, clique no nó de origem e, em seguida, clique no nó de destino. Algumas linhas podem ser criadas somente entre determinados tipos de nós. Quando você move o ponteiro sobre uma possível origem ou destino, o ponteiro indica se é possível criar uma conexão.  
  
###  <a name="a-nameplanningtrackinga-planning-and-tracking-work"></a><a name="PlanningTracking"></a>Planejamento e acompanhamento de trabalho  
 Diagramas de modelagem do Visual Studio são integrados com o Team Foundation Server para que você pode planejar, gerenciar e controlar o trabalho mais facilmente. Ambas as equipes usam modelos para identificar casos de teste e tarefas de desenvolvimento e estimar o trabalho. Zulu cria e links Team Foundation Server itens de trabalho a elementos de modelo, como casos de uso ou componentes. Isso ajuda a monitorar seu progresso e rastrear o trabalho para os requisitos dos usuários. Isso ajuda a garantir que as alterações continuem a atender a esses requisitos.  
  
 Como seus trabalhos em andamento, a atualização de equipes itens de trabalho para refletir o tempo gastam por eles em suas tarefas. Eles também monitorar e relatar o status em seu trabalho, usando os seguintes recursos do Team Foundation Server:  
  
-   Diário *relatórios burndown* que mostram se eles concluirá o trabalho planejado no tempo esperado. Elas geram outros relatórios semelhantes do Team Foundation Server para acompanhar o andamento de bugs.  
  
-   Um *planilha iteração* que usa o Microsoft Excel para ajudar a equipe de monitorar e equilibrar a carga de trabalho entre seus membros. Esta planilha está vinculada ao Team Foundation Server e fornece o foco para discussão durante suas reuniões regulares de progresso.  
  
-   A *painel de desenvolvimento* que usa o Office Project para manter a equipe informado sobre informações importantes do projeto.  
  
 Consulte:  
  
-   [Acompanhar o trabalho usando o Visual Studio Team Services ou o Team Foundation Server](http://msdn.microsoft.com/Library/52aa8bc9-fc7e-4fae-9946-2ab255ca7503)  
  
-   [Gráficos, painéis e relatórios para o Visual Studio ALM](http://msdn.microsoft.com/Library/1f28ba6c-c5e5-46d3-9209-ede24ae78e48)  
  
-   [Criar sua lista de pendências e tarefas usando o Project](http://msdn.microsoft.com/Library/be5cef4f-755f-4ffe-8dd7-876d1e02c330)  
  
###  <a name="a-nametestvalidatecheckincodea-testing-validating-and-checking-in-code"></a><a name="TestValidateCheckInCode"></a>Testes, validação e verificando no código  
 Como as equipes concluir cada tarefa, eles verificar seu código no controle de versão do Team Foundation e recebem lembretes do Team Foundation Server, caso eles tenham esquecido. Antes do Team Foundation Server aceita seus check-ins, as equipes de executam testes de unidade e validação de dependência para verificar o código em relação a seus casos de teste e o design. Usar o Team Foundation Server para executar compilações, testes de unidade automatizados e validação de dependência regularmente. Isso ajuda a garantir que o código atenda aos seguintes critérios:  
  
-   Ele funciona.  
  
-   Ele não separa anteriormente código funcional.  
  
-   Ele não está em conflito com o design.  
  
 Jantar agora tem uma grande coleção de testes automatizados, que Zulu pode reutilizar porque quase tudo ainda se aplicam. Zulu também pode criar esses testes e adicionar novos para cobrir a nova funcionalidade. Ambos também usam o Visual Studio para executar testes manuais.  
  
 Para certificar-se de que o código está de acordo com o design, as equipes configure suas compilações no Team Foundation Build para incluir validação de dependência. Se ocorrerem conflitos, um relatório é gerado com os detalhes.  
  
 Consulte:  
  
-   [Testando o aplicativo](https://www.visualstudio.com/docs/test/overview)  
  
-   [Validar o sistema durante o desenvolvimento](../modeling/validate-your-system-during-development.md)  
  
-   [Usar controle de versão](http://go.microsoft.com/fwlink/?LinkID=525605)  
  
-   [Compilar o aplicativo](http://msdn.microsoft.com/Library/a971b0f9-7c28-479d-a37b-8fd7e27ef692)  
  
##  <a name="a-nameupdatingsystema-updating-the-system-using-visualization-and-modeling"></a><a name="UpdatingSystem"></a>Atualizando a sistema usando visualização e modelagem  
 Zulu e o jantar agora devem integrar seus sistemas de pagamento. As seções a seguir mostram que os diagramas de modelagem no Visual Studio ajudá-los a executar essa tarefa:  
  
-   [Visualizar o código existente: Mapas de código](#VisualizeCode)  
  
-   [Definir um glossário de tipos: diagramas de classe](#DefineClasses)  
  
-   [Descreve a arquitetura lógica: diagramas de dependência](#DescribeLayers)  
  
 Consulte:  
  
-   [Visualizar código](../modeling/visualize-code.md)  
  
-   [Usar modelos no processo de desenvolvimento](../modeling/use-models-in-your-development-process.md)  
  
-   [Modelar a arquitetura do aplicativo](../modeling/model-your-app-s-architecture.md)  
 
###  <a name="a-namevisualizecodea-visualize-existing-code-code-maps"></a><a name="VisualizeCode"></a>Visualizar o código existente: Mapas de código  
 Mapas de código mostram a organização atual e as relações no código. Itens são representados por *nós* no mapa, e as relações são representadas por *links*. Mapas de código podem ajudá-lo a realizar os seguintes tipos de tarefas:  
  
-   Explore o código não familiar.  
  
-   Compreenda onde e como uma alteração proposta pode afetar o código existente.  
  
-   Encontre áreas de complexidade, dependências naturais ou padrões ou outras áreas que podem se beneficiar de aperfeiçoamento.  
  
 Por exemplo, jantar agora deve estimar o custo de atualização de componente PaymentProcessing. Isso depende em parte quanto esta alteração irá afetar outras partes do sistema. Para ajudá-los a compreender isso, um dos desenvolvedores jantar agora gera mapas de código do código e ajusta o foco de escopo nas áreas que podem ser afetados pela alteração.  
  
 O mapa a seguir mostra as dependências entre a classe PaymentProcessing e outras partes do sistema jantar agora, que aparecem selecionadas:  
  
 ![Gráfico de dependência para jantar agora o sistema de pagamento](../modeling/media/dep_dnpayment.png "Dep_DNPayment")  
  
 **Mapa de códigos para jantar agora o sistema de pagamento**  
  
 O desenvolvedor explora o mapa expandindo a classe PaymentProcessing e selecionando seus membros para ver as áreas que são potencialmente afetadas:  
  
 ![Métodos dentro de PaymentProcessing e dependências](../modeling/media/depgraph_expandeddn.png "DepGraph_ExpandedDN")  
  
 **Métodos na classe PaymentProcessing e suas dependências**  
  
 Elas geram o mapa a seguir para o sistema de pagamento Zulu inspecionar suas classes, métodos e dependências. A equipe vê que o sistema Zulu também pode exigir trabalho interagir com outras partes do jantar agora:  
  
 ![Gráfico de dependência para o sistema de pagamento Zulu](../modeling/media/depgraph_lucernepay.png "DepGraph_LucernePay")  
  
 **Mapa de códigos para o sistema de pagamento Zulu**  
  
 Ambas as equipes trabalham juntos para determinar as alterações que são necessários para integrar os dois sistemas. Decidir refatorar alguns códigos para que ele será mais fácil de atualizar. A classe PaymentApprover será movido para o namespace DinnerNow.Business e exige alguns novos métodos. As classes jantar agora que lidar com transações terá seu próprio namespace. As equipes de criar e usam itens de trabalho para planejar, organizar e acompanhar seu trabalho. Eles vinculam os itens de trabalho a elementos de modelo, é útil.  
  
 Após a reorganização de código, as equipes de geram um novo mapa de código para ver a estrutura atualizada e relações:  
  
 ![Gráfico de dependência com código reorganizado](../modeling/media/depgraph_integrated.png "DepGraph_Integrated")  
  
 **Mapa de código com código reorganizado**  
  
 Este mapa mostra que a classe PaymentApprover está no namespace DinnerNow.Business e tem alguns novos métodos. As classes de transação jantar agora agora tem seu próprio namespace PaymentSystem, o que torna mais fácil lidar com esse código mais tarde.  
  
#### <a name="creating-a-code-map"></a>Criar um mapa de código  
  
-   Para obter uma visão geral do código-fonte, siga estas etapas para gerar um mapa de código:  
  
     Sobre o **arquitetura** menu, clique em **gerar mapa de código para solução**.  
  
     Para obter uma visão geral do código compilado, crie um mapa de código em branco e arraste arquivos binários ou arquivos de assembly para a superfície do mapa.  
  
-   Para explorar o código específico ou itens de solução, use o Gerenciador de soluções para selecionar itens e relações que você deseja visualizar. Você pode gerar um novo mapa ou adicionar itens selecionados a um mapa existente. Consulte [mapear dependências em suas soluções](../modeling/map-dependencies-across-your-solutions.md).  
  
-   Para ajudá-lo a explorar o mapa, reorganize o layout para que ele se ajusta os tipos de tarefas que você deseja executar.  
  
     Por exemplo, para visualizar as camadas no código, selecione um layout de árvore. Consulte [procurar e reorganizar mapas de código](../modeling/browse-and-rearrange-code-maps.md).  
  
#### <a name="summary-strengths-of-code-maps"></a>Resumo: Os pontos fortes de mapas de código  
 Mapas de código ajudarão-lo:  
  
-   Saiba mais sobre a organização e as relações no código existente.  
  
-   Identificar áreas que podem ser afetadas por uma alteração proposta.  
  
-   Encontre áreas de complexidade, padrões, camadas ou outras áreas que você possa melhorar para facilitar a manutenção, alterar e reutilizar o código.  
  
#### <a name="relationship-to-other-diagrams"></a>Relação com Outros Diagramas  
  
|**Diagrama**|**Descreve**|  
|-----------------|-------------------|  
|Diagrama de dependência|A arquitetura lógica do sistema. Use a validação de dependência para certificar-se de que o código permaneça consistente com o design.<br /><br /> Para ajudá-lo a identificar dependencys existentes ou dependencys pretendidas, crie um mapa de código e agrupar itens relacionados. Para criar um diagrama de dependência, consulte:<br /><br /> -   [Crie diagramas de dependência de seu código](../modeling/create-layer-diagrams-from-your-code.md)<br />-   [Diagramas de dependência: diretrizes](../modeling/layer-diagrams-guidelines.md)|  
|Diagrama de classe (base)|Classes existentes no código para um projeto específico.<br /><br /> Para visualizar e modificar uma classe existente no código, use o Class Designer.<br /><br /> Consulte [como: Adicionar diagramas de classe a projetos (Designer de classe)](../ide/how-to-add-class-diagrams-to-projects-class-designer.md).|  
  
###  <a name="a-namedefineclassesa-define-a-glossary-of-types-class-diagrams"></a><a name="DefineClasses"></a>Definir um glossário de tipos: diagramas de classe  
 Diagramas de classe definem as entidades, termos ou conceitos que participam do sistema e suas relações uns com os outros. Por exemplo, você pode usar esses diagramas durante o desenvolvimento para descrever os atributos e operações para cada classe, independentemente da linguagem de implementação ou estilo.  
  
 Para ajudar a Zulu descrever e discutir as entidades que participam do caso de uso do processo de pagamento, eles desenhar o diagrama de classe a seguir:  
  
 ![Processar pagamento entidades no diagrama de classe](../modeling/media/uml_payentities.png "UML_PayEntities")  
  
 **Processar pagamento entidades em um diagrama de classe**  
  
 Este diagrama mostra que um cliente pode ter muitos pedidos e formas de pagamento para ordens diferentes. BankAccount e CreditCard herdarem de pagamento.  
  
 Durante o desenvolvimento, o Zulu usa o diagrama de classe a seguir para descrever e discutir os detalhes de cada classe:  
  
 ![Processar os detalhes de entidade de pagamento em um diagrama de classe](../modeling/media/uml_payment.png "UML_Payment")  
  
 **Detalhes de pagamento do processo no diagrama de classe**  
    
#### <a name="drawing-a-class-diagram"></a>Desenho de um diagrama de classes  
 Um diagrama de classes tem os seguintes recursos principais:  
  
-   Tipos como classes, interfaces e enumerações:  
  
    -   A *classe* é a definição de objetos que compartilham características estruturais ou comportamentos específicas.  
  
    -   Um *interface* define uma parte do comportamento visível externamente de um objeto.  
  
    -   Um *enumeração* é um classificador que contém uma lista de valores literais.  
  
-   *Atributos* são valores de um determinado tipo que descrevem cada instância de um *classificador*. Um classificador é um nome geral para tipos, componentes, casos de uso e até mesmo atores.  
  
-   *Operações* métodos ou funções que podem ser executadas por instâncias de um classificador.  
  
-   Um *associação* indica algum tipo de relação entre dois classificadores.  
  
    -   Um *agregação* é uma associação que indica uma propriedade compartilhada entre classificadores.  
  
    -   A *composição* é uma associação que indica uma relação de parte de inteiro entre classificadores.  
  
     Para mostrar agregações ou composições, defina o **agregação** propriedade em uma associação. **Compartilhado** mostra as agregações e **composto** mostra composições.  
  
-   A *dependência* indica alterando a definição de um classificador que pode alterar a definição de outro classificador.  
  
-   A *generalização* indica que um classificador específico herda parte de sua definição de um classificador geral. A *percepção* indica que uma classe implementa as operações e atributos oferecidos por uma interface.  
  
     Para criar essas relações, use o **herança** ferramenta. Como alternativa, uma percepção pode ser representada como um *lollipop*.  
  
-   *Pacotes* são grupos de classificadores, associações, linhas, componentes e outros pacotes. *Importação* relações indicam que um pacote inclui todas as definições de outro pacote.  
  
 Como ponto de partida para explorar e discutir as classes existentes, você pode usar o Class Designer para criar diagramas de classe no código.  
  
-   [Como adicionar diagramas de classe a projetos (Designer de Classe)](../ide/how-to-add-class-diagrams-to-projects-class-designer.md)  
  
#### <a name="summary-strengths-of-class-diagrams"></a>Resumo: Os pontos fortes de diagramas de classe  
 Diagramas de classe ajudam a definir:  
  
-   Um Glossário comum de termos para usar ao abordar as necessidades dos usuários e as entidades que participam do sistema. Consulte [requisitos de usuário do modelo](../modeling/model-user-requirements.md).  
  
-   Tipos que são usados por partes do sistema, como componentes, independentemente de sua implementação. Consulte [modelo de arquitetura do aplicativo](../modeling/model-your-app-s-architecture.md).  
  
-   Relações, como dependências entre tipos. Por exemplo, você pode mostrar que um tipo pode ser associado a várias instâncias de outro tipo.  
  
#### <a name="relationship-to-other-diagrams"></a>Relação com Outros Diagramas  
  
|**Diagrama**|**Descrição**|  
|-----------------|---------------------|  
|Diagrama de dependência|Defina a arquitetura lógica do sistema que diz respeito às classes.<br /><br /> Use a validação de dependência para certificar-se de que o código permaneça consistente com o design.<br /><br /> Consulte:<br /><br /> -   [Crie diagramas de dependência de seu código](../modeling/create-layer-diagrams-from-your-code.md)<br />-   [Diagramas de dependência: referência](../modeling/layer-diagrams-reference.md)<br />-   [Diagramas de dependência: diretrizes](../modeling/layer-diagrams-guidelines.md)<br />-   [Validar código com diagramas de dependência](../modeling/validate-code-with-layer-diagrams.md)|  
|Mapa de código|Visualize a organização e as relações no código existente.<br /><br /> Para identificar a classes, seus relacionamentos e seus métodos, crie um mapa de código que mostra esses elementos.<br /><br /> Consulte:<br /><br /> -   [Mapear dependências em suas soluções](../modeling/map-dependencies-across-your-solutions.md)|  
  
###  <a name="a-namedescribelayersa-describe-the-logical-architecture-dependency-diagrams"></a><a name="DescribeLayers"></a>Descreve a arquitetura lógica: diagramas de dependência  
 Diagramas de dependência descrevem a arquitetura lógica de um sistema, organizando os artefatos em sua solução em grupos abstratos, ou *camadas*. Artefatos podem ser muitas coisas como namespaces, projetos, classes, métodos e assim por diante. Camadas representam e descrevem as funções ou tarefas que executam os artefatos no sistema. Você também pode incluir validação da camada em sua compilação e operações de verificação para certificar-se de que o código permaneça consistente com seu design.  
  
 Para manter o código consistente com o design, jantar agora e Zulu usam o seguinte diagrama de dependência para validar o código conforme ele evolui:  
  
 ![Diagrama de dependência do sistema de pagamento integrado](../modeling/media/layer_integrated_dnlucerne.png "Layer_Integrated_DNLucerne")  
  
 **Diagrama de dependência para jantar agora integrado ao Zulu**  
  
 As camadas neste diagrama vinculam os artefatos de solução de jantar agora e Zulu correspondentes. Por exemplo, os links de camada comercial para o namespace DinnerNow.Business e seus membros, que agora incluem a classe PaymentApprover. Os links da camada de acesso aos recursos para o namespace DinnerNow.Data. As setas ou *dependências*, especifique que a camada de negócios pode usar a funcionalidade na camada de acesso aos recursos. Como as equipes de atualizam seu código, validação de camada é executada regularmente para detectar conflitos, conforme elas ocorrem e para ajudar as equipes a resolvê-los imediatamente.  
  
 As equipes trabalham juntos para integrar incrementalmente e testar os dois sistemas. Primeiro verifique se PaymentApprover e o restante do jantar agora funcionam entre si com êxito antes de lidar com PaymentProcessing.  
  
 O mapa de código a seguir mostra as novas chamadas entre o jantar agora e PaymentApprover:  
  
 ![Gráfico de dependência atualizado com o sistema integrado](../modeling/media/depgraph_intsystem.png "DepGraph_IntSystem")  
  
 **Mapa de código com chamadas de método atualizado**  
  
 Depois que confirmarem que o sistema funciona conforme o esperado, comentários jantar agora o código PaymentProcessing. Os relatórios de validação de camada são limpos e o mapa de código resultante mostra que não há mais dependências PaymentProcessing existem:  
  
 ![Gráfico de dependência sem PaymentProcessing](../modeling/media/depgraph_nomore.png "DepGraph_NoMore")  
  
 **Mapa de código sem PaymentProcessing**  
  
#### <a name="drawing-a-dependency-diagram"></a>Desenho de um diagrama de dependência  
 Um diagrama de dependência tem os seguintes recursos principais:  
  
-   *Camadas* descrevem grupos lógicos de artefatos.  
  
-   A *link* é uma associação entre uma camada e um artefato.  
  
     Para criar camadas de artefatos, arraste itens do Gerenciador de soluções, mapas de código, modo de exibição de classe ou Pesquisador de objetos. Para desenhar novas camadas e, em seguida, vinculá-las aos artefatos, use a caixa de ferramentas ou clique na superfície de diagrama para criar as camadas e arraste itens para essas camadas.  
  
     O número em uma camada mostra o número de artefatos que estão vinculados à camada. Esses artefatos podem ser namespaces, projetos, classes, métodos e assim por diante. Quando você interpretar o número de artefatos em uma camada, lembre-se de:  
  
    -   Se uma camada estiver vinculada a um artefato que contenha outros artefatos, mas não estiver vinculada diretamente a outros artefatos, o número incluirá apenas o artefato vinculado. No entanto, os outros artefatos estão incluídos para análise durante a validação da camada.  
  
         Por exemplo, se uma camada estiver vinculada a um único namespace, o número de artefatos vinculados será 1, mesmo se o namespace contiver classes. Se a camada também tiver links para cada classe no namespace, o número incluirá as classes vinculadas.  
  
    -   Se uma camada contiver outras camadas vinculadas a artefatos, a camada de contêiner também estará vinculada a esses artefatos, mesmo que o número na camada de contêiner não inclua esses artefatos.  
  
     Para ver os artefatos que estão vinculados a uma camada, clique com botão direito a dependência e, em seguida, clique em **Exibir Links** abrir **Gerenciador de camadas**.  
  
-   A *dependência* indica que uma camada pode usar a funcionalidade em outra camada, mas não vice-versa. A *dependência bidirecional* indica que uma camada pode usar a funcionalidade em outra camada e vice-versa.  
  
     Para exibir as dependências existentes no diagrama de dependência, clique com botão direito da superfície do diagrama e, em seguida, clique em **gerar dependências**. Para descrever dependências pretendidas, desenhe novos.  
  
 Consulte:  
  
-   [Crie diagramas de dependência de seu código](../modeling/create-layer-diagrams-from-your-code.md)  
  
-   [Diagramas de dependência: referência](../modeling/layer-diagrams-reference.md)  
  
-   [Diagramas de dependência: diretrizes](../modeling/layer-diagrams-guidelines.md)  
  
-   [Validar código com diagramas de dependência](../modeling/validate-code-with-layer-diagrams.md)  
  
#### <a name="summary-strengths-of-dependency-diagrams"></a>Resumo: Os pontos fortes dos diagramas de dependência  
 Diagramas de dependência ajudarão-lo:  
  
-   Descreva a arquitetura lógica de um sistema de acordo com a funcionalidade de seus artefatos.  
  
-   Certifique-se de que o código em desenvolvimento está de acordo com o projeto especificado.  
  
#### <a name="relationship-to-other-diagrams"></a>Relação com Outros Diagramas  
  
|**Diagrama**|**Descrição**|  
|-----------------|---------------------|  
|Mapa de código|Visualize a organização e as relações no código existente.<br /><br /> Para criar camadas, gerar um mapa de código e agrupe os itens do mapa como camadas potenciais. Arraste os grupos do mapa para o diagrama de dependência.<br /><br /> Consulte:<br /><br /> -   [Mapear dependências em suas soluções](../modeling/map-dependencies-across-your-solutions.md)<br />-   [Procurar e reorganizar mapas de código](../modeling/browse-and-rearrange-code-maps.md)|  
  
## <a name="external-resources"></a>Recursos externos  
  
|**Categoria**|**Links**|  
|------------------|---------------|  
|**Fóruns**|-   [Visualização do Visual Studio < / ferramentas de modelagem](http://go.microsoft.com/fwlink/?LinkId=184720)<br />-   [Visualização do Visual Studio < / modelagem SDK (ferramentas DSL)](http://go.microsoft.com/fwlink/?LinkId=184721)|  
  
## <a name="see-also"></a>Consulte também  
 [Visualizar código](../modeling/visualize-code.md)   
 [Usar modelos no processo de desenvolvimento](../modeling/use-models-in-your-development-process.md)   
 [Usar modelos no desenvolvimento ágil](http://msdn.microsoft.com/en-us/592ac27c-3d3e-454a-9c38-b76658ed137f)   
 [Validar o sistema durante o desenvolvimento](../modeling/validate-your-system-during-development.md)   

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]
 

