---
title: Desenvolver testes de um modelo | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- tests and requirements
ms.assetid: 40f87192-ba85-4552-8804-314a678261ae
caps.latest.revision: 20
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
ms.sourcegitcommit: 08aabdfe0e268f93ef7723076375b7f65b15ccf3
ms.openlocfilehash: b7cb109d11669f411b5ca3bdf3c4c32a63ac53a1
ms.lasthandoff: 02/22/2017

---
# <a name="develop-tests-from-a-model"></a>Desenvolver testes por meio de um modelo
Você pode usar requisitos e modelos de arquitetura para ajudá-lo a organizar os testes do seu sistema e seus componentes. Essa prática ajuda a garantir que você testar os requisitos que são importantes para os usuários e outros participantes e ajuda a atualizar os testes rapidamente quando os requisitos são alterados. Se você usar [!INCLUDE[TCMext](../misc/includes/tcmext_md.md)], você também pode manter os links entre os modelos e os testes.  
  
 Para ver quais versões do Visual Studio oferecem suporte a esses recursos, consulte [suporte de versão para a arquitetura e ferramentas de modelagem](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).  
  
## <a name="system-and-subsystem-testing"></a>Sistema e teste de subsistema  
 *Testes de sistema,* também conhecido como *testes de aceitação*, significa testar se as necessidades dos usuários estão sendo atendidas. Esses testes estão preocupados com o comportamento visível externamente do sistema em vez do design interno.  
  
 Testes de sistema são muito valiosos quando estender ou recriar um sistema. Eles ajudam a evitar introduzir bugs quando você alterar o código.  
  
 Quando você planejar qualquer alteração ou a extensão de um sistema, é útil começar com um conjunto de testes de sistema que são executados em um sistema existente. Em seguida, você pode estender ou ajustar os testes para testar os novos requisitos, faça as alterações no código e executar novamente o conjunto completo de testes.  
  
 Ao desenvolver um novo sistema, você pode começar a criar testes tão logo o desenvolvimento começa. Definindo testes antes de desenvolver cada recurso, você pode capturar as discussões de requisitos de uma maneira muito específica.  
  
 Testes de subsistema aplicam os mesmos princípios para os principais componentes de um sistema. Cada componente é testado separadamente de outros componentes. Subsistema de testes de foco no comportamento visível em interfaces de usuário ou a API do componente.  
  
## <a name="deriving-system-tests-from-a-requirements-model"></a>Derivando de testes de sistema de um modelo de requisitos  
 Você pode criar e manter uma relação entre testes de sistema e um modelo de requisitos. Para estabelecer essa relação, você pode escrever testes correspondentes para os principais elementos do modelo de requisitos. Visual Studio ajuda você a manter essa relação, permitindo que você crie links entre os testes e as partes do modelo. Para obter mais informações sobre modelos de requisitos, consulte [requisitos de usuário do modelo](../modeling/model-user-requirements.md).  
  
### <a name="write-tests-for-each-use-case"></a>Escrever testes para cada caso de uso  
 Se você usar [!INCLUDE[TCMext](../misc/includes/tcmext_md.md)], você pode criar um grupo de testes para cada caso de uso que você definiu em seu modelo de requisitos. Por exemplo, se você tiver um caso de uso ordem refeição, que inclui criar pedido e Adicionar Item à ordem, você pode criar testes para ambos os geral e mais detalhada desses casos de uso. 
  
 Essas diretrizes podem ser úteis:  
  
-   Cada caso de uso deve ter vários testes, para caminhos principais e resultados excepcionais.  
  
-   Quando você descrever um caso de uso no modelo de requisitos, é mais importante definir seu pós-condição, ou seja, a meta é obtida de descrever detalhadamente os procedimentos do usuário segue para atingir a meta. Por exemplo, pós-condição da ordem refeição pode ser que um restaurante está preparando uma refeição para um cliente e que o cliente paga. A pós-condição é o critério que os testes devem verificar.  
  
-   Base testes separados nas cláusulas separados da pós-condição. Por exemplo, crie testes separados para notificar o restaurante do pedido e para fazer o pagamento do cliente. Essa separação tem estas vantagens:  
  
    -   Alterações em diferentes aspectos dos requisitos de ocorrerem com frequência independentemente. Separando os testes em diferentes aspectos dessa maneira, você facilitam atualizar os testes quando requisitos mudam.  
  
    -   Se o plano de desenvolvimento implementa um aspecto do caso de uso antes de outro, você pode habilitar os testes separadamente à medida que progride de desenvolvimento.  
  
-   Quando você criar os testes, separe a escolha de dados de teste do código ou script que determina se a pós-condição foi atingida. Por exemplo, um teste de uma função aritmético simple pode ser: entrada 4; Verifique se a saída é 2. Em vez disso, criar o script como: escolha uma entrada; Multiplique o resultado por si só e verifique se o resultado é a entrada original. Esse estilo permite variar as entradas de teste sem alterar o corpo principal do teste.  
  
#### <a name="linking-tests-to-use-cases"></a>Testes de vinculação para casos de uso  
 Se você estiver usando [!INCLUDE[TCMlong](../modeling/includes/tcmlong_md.md)] para criar e executar os testes, você pode organizar seus testes em itens de trabalho de história de usuário, caso de uso ou requisito. Você pode vincular esses itens de trabalho a casos de uso em seu modelo. Isso permite que você rapidamente rastrear alterações de requisitos para testes e ajuda a acompanhar o progresso de cada caso de uso.  
  
###### <a name="to-link-tests-to-a-use-case"></a>Para vincular testes a um caso de uso  
  
1.  Em [!INCLUDE[TCMlong](../modeling/includes/tcmlong_md.md)], criar um requisito e um conjunto de testes de base nele.
  
     O requisito que você cria é um item de trabalho em [!INCLUDE[vstsTfsShort](../modeling/includes/vststfsshort_md.md)]. Pode ser um item de trabalho de caso de uso, requisitos ou história de usuário, dependendo do modelo de processo que usa seu projeto com [!INCLUDE[esprfound](../code-quality/includes/esprfound_md.md)]. Para obter mais informações, consulte [acompanhar o trabalho usando o Visual Studio Team Services ou o Team Foundation Server](http://msdn.microsoft.com/Library/52aa8bc9-fc7e-4fae-9946-2ab255ca7503).  
  
2.  Vincule ao item de trabalho de requisito para um ou mais casos de uso em seu modelo.  
  
     Em um diagrama de caso de uso, clique em um caso de uso e, em seguida, clique em **Link para o Item de trabalho**. Para obter mais informações, consulte [vincular elementos de modelo e itens de trabalho](../modeling/link-model-elements-and-work-items.md).  
  
3.  Adicione ao conjunto de testes, casos de teste que verificam se os casos de uso.  
  
 Normalmente, cada item de trabalho de requisito ou história de usuário vinculará a vários casos de uso em seu modelo e cada caso de uso vinculará a várias histórias ou requisitos. Isso ocorre porque cada história de usuário ou requisito abrange um conjunto de tarefas que desenvolver vários casos de uso. Por exemplo, em uma iteração inicial do projeto, você pode desenvolver a história de usuário básico no qual um cliente pode escolher itens de um catálogo e entregues. Em uma iteração mais recente, a história pode ser que o usuário paga quando concluir a ordem e o fornecedor recebe o dinheiro depois que ele envia as mercadorias.  Cada história adiciona uma cláusula para pós-condição do caso de uso de produtos de ordem.  
  
 Você pode criar links separados dos requisitos para as cláusulas da pós-condição escrevendo as cláusulas em comentários separados no diagrama de caso de uso. Você pode vincular cada comentário ao item de trabalho requisito e o comentário do link para o caso de uso no diagrama.  
  
### <a name="base-tests-on-the-requirements-types"></a>Testes de base nos tipos de requisitos  
 Os tipos, que é, as classes, interfaces e enumerações, de um modelo de requisitos descrevem os conceitos e as relações em termos de como os usuários pensam e se comunicar sobre seus negócios. Ele exclui tipos preocupado apenas com o design interno do sistema.  
  
 Os testes em termos desses tipos de requisitos de design. Essa prática ajuda a garantir que, quando as alterações nos requisitos são discutidas, é fácil relacionar as alterações para as alterações necessárias nos testes. Ele possibilita discutir os testes e seus resultados pretendidos diretamente com os usuários finais e outros participantes. Isso significa que os usuários precisam pode ser mantidos fora do processo de desenvolvimento e evita o design acidental dos testes em torno de possíveis falhas no design.  
  
 Testes manuais, essa prática envolve respeitando o vocabulário do modelo requisitos nos scripts de teste. Para testes automatizados, essa prática envolve usando diagramas de classe a requisitos como base para seu código de teste e criar acessador e atualizador funções para vincular o modelo de requisito no código.  
  
 Por exemplo, requisitos de um modelo pode incluir tipos de Menu, o Item de Menu, Order e associações entre elas. Esse modelo representa as informações que são armazenadas e tratadas pela refeição sistema de pedidos, mas não representam as complexidades de sua implementação. O sistema em funcionamento, pode haver vários realizações diferentes de cada tipo, em bancos de dados, nas interfaces do usuário e nas APIs. Em um sistema distribuído, pode haver diversas variantes de cada instância armazenada em diferentes partes do sistema ao mesmo tempo.  
  
 Para testar um caso de uso, como adicionar Item à ordem, um método de teste pode incluir código semelhante a este:  
  
```  
Order order = … ; // set up an order  
// Store prior state:  
int countBefore = order.MenuItems.Count;   
// Perform use case:  
MenuItem chosenItem = …; // choose an item  
AddItemToOrder (chosenItem, order);   
// Verify part of postcondition:  
int countAfter = order.MenuItems.Count;  
Assert (countAfter == countBefore = 1);   
```  
  
 Observe que esse método de teste usa as classes do modelo de requisitos. Associações e atributos são realizados como propriedades .NET.  
  
 Para fazer isso funcionar, as propriedades das classes devem ser definidas como somente leitura funções ou acessadores, que acessa o sistema para recuperar informações sobre seu estado atual. Métodos que simulam casos de uso como AddItemToOrder deve unidade do sistema por meio de sua API ou através de uma camada abaixo de sua interface do usuário. Os construtores de objetos de teste como Order e MenuItem também devem unidade do sistema para criar itens correspondentes dentro do sistema.  
  
 Muitos dos acessadores e atualizadores já estarão disponíveis por meio de API normal do aplicativo. Mas algumas funções adicionais podem ter a serem gravados para permitir que os testes. Esses atualizadores e os acessadores adicionais também são conhecidas como 'teste instrumentation'. Porque eles dependem o design interno do sistema, é responsabilidade dos desenvolvedores do sistema para fornecer a eles, enquanto os testadores escrever o código dos testes em termos de modelo de requisitos.  
  
 Ao escrever testes automatizados, você pode usar testes genéricos para encapsular os acessadores e atualizadores.
  
### <a name="tests-for-business-rules"></a>Testes de regras de negócio  
 Alguns requisitos não estão diretamente relacionados a qualquer um caso de uso. Por exemplo, a empresa DinnerNow permite que os clientes escolham entre muitos Menus, mas requer que cada ordem, todos os itens deverão ser de um único Menu escolhido. Essa regra de negócio pode ser expresso como uma constante sobre as associações entre os pedidos, Menus e itens no modelo de classe de requisitos.  
  
 Uma regra invariável desse tipo controla não apenas todos os casos de uso que são definidos no momento, mas também quaisquer outros casos de uso que serão definidos posteriormente. Portanto, é útil para gravá-la separadamente de qualquer caso de uso e testá-lo separadamente dos casos de uso.  
  
## <a name="deriving-subsystem-tests-from-models"></a>Derivando de testes de subsistema de modelos  
 O design de alto nível de um sistema grande, você pode identificar componentes ou subsistemas. Elas representam partes que podem ser criados separadamente, localizados em diferentes computadores ou são módulos reutilizáveis que podem ser combinados de diversas maneiras. 
  
 Você pode aplicar a cada componente principal os mesmos princípios que você usa em todo o sistema. Em um projeto grande, cada componente pode ter seu próprio modelo de requisitos. Em projetos menores, um modelo de arquitetura ou design de alto nível pode ser criado para mostrar os principais componentes e suas interações. Para obter mais informações, consulte [modelo de arquitetura do aplicativo](../modeling/model-your-app-s-architecture.md).  
  
 Em ambos os casos, você pode estabelecer uma relação entre os elementos de modelo e os testes de subsistema da mesma maneira como você faria entre o modelo de requisitos e os testes do sistema.  
  
### <a name="isolate-components-with-provided-and-required-interfaces"></a>Isolar componentes com Interfaces fornecidas e obrigatórias  
 É útil para identificar todas as dependências que tem um componente em outras partes do seu sistema ou serviços externos e para representar esses como Interfaces necessárias. Neste exercício geralmente leva a alguma reformulação que deixa o componente facilmente separáveis e muito mais separado do resto do seu design.  
  
 Aproveitar essa desassociação é que o componente pode ser executado para teste, substituindo por objetos fictícios os serviços que normalmente usa. Esses são os componentes que são configurados para fins de teste. Um componente fictício fornece a interface que requer o componente, respondendo a consultas com dados simulados. Os componentes de simulações fazem parte de uma estrutura de teste completo que você pode se conectar a todas as interfaces do componente.  
  
 Um benefício dos testes de simulação é que você pode desenvolver seu componente enquanto os outros componentes cujos usará os serviços ainda estão em desenvolvimento.  
  
## <a name="maintain-the-relationships-between-tests-and-model"></a>Manter as relações entre testes e modelo  
 Em um projeto típico que executa uma iteração em algumas semanas, uma análise dos requisitos é mantida próximo ao início de cada iteração. A reunião aborda os recursos que devem ser entregues na próxima iteração. Um modelo de requisitos pode ser usado para ajudar a discutir os conceitos, os cenários e as sequências de ações que serão desenvolvidas. As partes interessadas no negócio definir prioridades, os desenvolvedores fazem estimativas e os testadores assegurar que o comportamento esperado de cada recurso é capturado corretamente.  
  
 Escrita de testes é a maneira mais eficiente para definir um requisito, e também é uma maneira eficiente de garantir que uma pessoa tenha uma compreensão clara de que é necessário. No entanto, enquanto em escrever testes leva muito tempo para fazer durante um workshop de especificação, criação de modelos pode ser feito muito mais rapidamente.  
  
 Do ponto de vista teste, um modelo de requisitos pode ser visto como uma abreviação para os testes. Portanto, é importante manter a relação entre os testes e o modelo em todo o projeto.  
  
##  <a name="a-nameattachinga-attaching-test-cases-to-model-elements"></a><a name="Attaching"></a>Anexando casos de teste para elementos de modelo  
 Se seu projeto usa [!INCLUDE[TCMlong](../modeling/includes/tcmlong_md.md)], você pode vincular testes para os elementos em seu modelo. Isso permite que você localize rapidamente os testes afetados por uma alteração nos requisitos e ajuda você a acompanhar a extensão à qual um requisito foi concretizado.  
  
 Você pode vincular testes para todos os tipos de elemento. Aqui estão alguns exemplos:  
  
-   Vincule um caso de uso para os testes que exercitem ele.  
  
-   Gravar as cláusulas de pós-condição casos de uso ou meta para comentários que estão vinculados ao caso de uso, e depois vincule testes para cada comentário.  
  
-   Escrever regras de invariáveis nos comentários em diagramas de classe ou diagramas de atividade e vinculá-las para testes.  
  
-   Testes de link para um diagrama de atividade, ou atividades individuais.  
  
-   Vincule um conjunto de testes para o componente ou o subsistema que ele testa.  
  
#### <a name="to-link-tests-to-a-model-element-or-relationship"></a>Para vincular testes a um elemento de modelo ou a relação  
  
1.  Em [!INCLUDE[TCMlong](../modeling/includes/tcmlong_md.md)], criar um requisito e um conjunto de testes de base nele. 
  
     O requisito que você cria é um item de trabalho em [!INCLUDE[vstsTfsShort](../modeling/includes/vststfsshort_md.md)]. Pode ser um item de trabalho de caso de uso, requisitos ou história de usuário, dependendo do modelo de processo que usa seu projeto com [!INCLUDE[esprfound](../code-quality/includes/esprfound_md.md)]. Para obter mais informações, consulte [acompanhar o trabalho usando o Visual Studio Team Services ou o Team Foundation Server](http://msdn.microsoft.com/Library/52aa8bc9-fc7e-4fae-9946-2ab255ca7503).  
  
2.  Vincule ao item de trabalho de requisito para um ou mais elementos em seu modelo.  
  
     Em um diagrama de modelagem, clique um elemento, o comentário ou a relação e, em seguida, clique em **Link para o Item de trabalho**. Para obter mais informações, consulte [vincular elementos de modelo e itens de trabalho](../modeling/link-model-elements-and-work-items.md).  
  
3.  Adicione ao conjunto de testes, casos de teste que verifique se o requisito expressado no elemento de modelo.  
  
## <a name="see-also"></a>Consulte também  
 [Criar modelos para o seu aplicativo](../modeling/create-models-for-your-app.md)   
 [Requisitos do modelo de usuário](../modeling/model-user-requirements.md)   
 [Modelo de arquitetura do aplicativo](../modeling/model-your-app-s-architecture.md)   
 [Análise e modelagem de arquitetura](../modeling/analyze-and-model-your-architecture.md)

