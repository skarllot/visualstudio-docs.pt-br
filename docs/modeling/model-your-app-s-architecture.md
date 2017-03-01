---
title: Modelo de arquitetura do aplicativo | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- UML, modeling architecture
ms.assetid: aedce746-9df5-49e1-9662-67eb1b83d313
caps.latest.revision: 19
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
ms.openlocfilehash: 76db1dddef5b5a2ab7eca8f7d097d164896fe3a2
ms.lasthandoff: 02/22/2017

---
# <a name="model-your-app39s-architecture"></a>Modelo de arquitetura do aplicativo
Para ajudar a garantir que seu aplicativo ou sistema de software atenda aos seus usuários precisa, você pode criar modelos no Visual Studio como parte de sua descrição da estrutura geral e o comportamento do seu aplicativo ou sistema de software. Usando modelos, você também pode descrever padrões que são usados durante o projeto. Esses modelos de ajudarão-lo a compreender a arquitetura existente, discuta as alterações e comunique suas intenções claramente.  
  
 Para ver quais versões do Visual Studio oferecer suporte a esse recurso, consulte [suporte de versão para a arquitetura e ferramentas de modelagem](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).  
  
 A finalidade de um modelo é para reduzir as ambiguidades que ocorrem nas descrições de linguagem natural e para ajudar você e seus colegas para visualizar o design e discutir designs alternativos. Um modelo deve ser usado junto com outros documentos ou discussões. Por si só, um modelo não representa uma especificação completa da arquitetura.  
  
> [!NOTE]
>  Ao longo deste tópico, "sistema" significa que o software que você está desenvolvendo. Pode ser uma grande coleção de muitos componentes de hardware e software, ou um único aplicativo ou uma parte de um aplicativo.  
  
 A arquitetura de um sistema pode ser dividida em duas áreas:  
  
-   [Design de alto nível](#Structure). Descreve os principais componentes e como eles interagem entre si para atender a cada requisito. Se o sistema for grande, cada componente pode ter seu próprio design de alto nível que mostra como ele é composto de componentes menores.  
  
-   [Padrões de design](#Patterns) e convenções usadas em todo o design dos componentes. Um padrão descreve uma abordagem específica para alcançar uma meta de programação. Usando os mesmos padrões durante um projeto, sua equipe pode reduzir o custo de fazer alterações e desenvolvimento de software novo.  
  
##  <a name="a-namestructurea-high-level-design"></a><a name="Structure"></a>Design de alto nível  
 Um design de alto nível descreve os principais componentes do seu sistema e como eles interagem entre si para atingir as metas do design. As atividades na lista a seguir são envolvidas no desenvolvimento de design de alto nível, embora não necessariamente em uma sequência específica.  
  
 Se você estiver atualizando o código existente, você pode começar descrevendo os principais componentes. Certifique-se de entender as alterações para os requisitos do usuário e adicionar ou modificar as interações entre os componentes. Se você estiver desenvolvendo um novo sistema, comece a Noções básicas sobre os principais recursos das necessidades dos usuários. Você pode, em seguida, explore as sequências de interações para os casos de uso principal e, em seguida, consolidar as sequências em um projeto de componente.  
  
 Em cada caso, ele é útil para desenvolver as atividades diferentes em paralelo e desenvolver código e testes mais cedo. Evite tentar concluir um dos seguintes aspectos antes de começar outra. Normalmente, os requisitos e seu conhecimento sobre a melhor maneira de criar o sistema serão alterado enquanto você estiver gravando e testando o código. Portanto, você deve começar a compreender e codificar os principais recursos do seu design e os requisitos. Preencha os detalhes em iterações posteriores do projeto.  
  
-   [Noções básicas sobre os requisitos de](#Requirements). O ponto de partida de qualquer design é uma compreensão clara de necessidades dos usuários.  
  
-   [Padrões de arquitetura](#BigDecisions). As escolhas feitas sobre tecnologias e principais elementos de arquitetura do sistema.  
  
-   Modelo de dados dos componentes e Interfaces. Você pode desenhar diagramas de classe para descrever as informações que são passadas entre componentes e armazenadas dentro dos componentes.  
  
##  <a name="a-namerequirementsa-understanding-the-requirements"></a><a name="Requirements"></a>Noções básicas sobre os requisitos  
 O design de alto nível de um aplicativo completo com mais eficiência é desenvolvido junto com um modelo de requisitos ou outra descrição das necessidades dos usuários. Para obter mais informações sobre modelos de requisitos, consulte [requisitos de usuário do modelo](../modeling/model-user-requirements.md).  
  
 Se o sistema que você está desenvolvendo um componente em um sistema maior, parte ou todas as suas necessidades podem ser incorporadas em interfaces programáticas.  
  
 O modelo de requisitos fornece essas informações essenciais:  
  
-   Interfaces fornecidas. Uma interface fornecida lista os serviços ou operações que o sistema ou o componente deve fornecer a seus usuários, independentemente de estarem usuários humanos ou outros componentes de software.  
  
-   Interfaces necessárias. Uma interface necessária lista os serviços ou operações que pode usar o sistema ou componente. Em alguns casos, você será capaz de criar todos esses serviços como parte do seu próprio sistema. Em outros casos, especialmente se você estiver criando um componente que pode ser combinado com outros componentes em muitas configurações, a interface necessária será definida pela considerações externas.  
  
-   Qualidade de serviço. O desempenho, segurança, robustez e outros objetivos e restrições que o sistema deve atender.  
  
 O modelo de requisitos é gravado do ponto de vista dos usuários do seu sistema, independentemente de estarem pessoas ou outros componentes de software. Eles sabem nada sobre o funcionamento interno do sistema. Por outro lado, sua meta em um modelo de arquitetura é descrever o funcionamento interno e mostrar como os usuários atendem às necessidades.  
  
 Manter os requisitos e modelos arquitetônicos separados é útil porque facilita discutir os requisitos com os usuários. Ele também ajuda refatorar o design e considere arquiteturas alternativas, manter os requisitos inalterada.  
  
 A quantidade de detalhes que devem ser colocadas em um requisitos ou um modelo de arquitetura depende da escala do projeto e o tamanho e a distribuição da equipe. Uma equipe pequena em um projeto de curto pode ir não mais do que fazer um rascunho de um diagrama de classe os conceitos de negócios e alguns padrões de design; um projeto grande distribuído em mais de uma região seria necessário muito mais detalhes.  
  
##  <a name="a-namebigdecisionsa-architectural-patterns"></a><a name="BigDecisions"></a>Padrões de arquitetura  
 No início do desenvolvimento de um, você precisa escolher as tecnologias principais e os elementos dos quais depende o design. As áreas em que devem ser feitas essas opções incluem o seguinte:  
  
-   Base de opções de tecnologia, como a escolha entre um banco de dados e um sistema de arquivos e a escolha entre um aplicativo de rede e um cliente Web e assim por diante.  
  
-   Opções de estruturas, como uma escolha entre o Windows Workflow Foundation ou ADO.NET Entity Framework.  
  
-   Opções de método de integração, por exemplo, entre um barramento de serviço corporativo ou um canal de ponto a ponto.  
  
 Essas opções frequentemente são determinadas pela qualidade de serviço, como dimensionamento e flexibilidade e podem ser feitas antes que os requisitos detalhados são conhecidos. Em um sistema grande, a configuração de hardware e software são altamente inter-relacionadas.  
  
 As seleções feitas afetam como usar e interpretar o modelo de arquitetura. Por exemplo, em um sistema que usa um banco de dados, associações em um diagrama de classe podem representar relações ou chaves estrangeiras no banco de dados, enquanto em um sistema baseado em arquivos XML, as associações podem indicar referências cruzadas que usem o XPath. Em um sistema distribuído, mensagens em um diagrama de sequência podem representar mensagens em uma conexão; em um aplicativo independente, podem representar chamadas de função.  
  
##  <a name="a-namepatternsa-design-patterns"></a><a name="Patterns"></a>Padrões de design  
 Um padrão de design é um resumo de como criar um aspecto específico do software, especialmente para um que se repete em diferentes partes do sistema. Adotando uma abordagem uniforme em todo o projeto, você pode reduzir o custo de design, garantir a consistência na interface do usuário e reduzir o custo compreensão e alterar o código.  
  
 Alguns padrões de design geral como observador são bem conhecidos e amplamente aplicável. Além disso, há padrões que são aplicáveis apenas para seu projeto. Por exemplo, em um sistema de vendas na Web, haverá diversas operações no código onde as alterações são feitas para o pedido do cliente. Para garantir que o estado do pedido é exibido corretamente em cada estágio, todas essas operações devem seguir um protocolo específico para atualizar o banco de dados.  
  
 Parte do trabalho de arquitetura de software é determinar quais padrões devem ser adotada em design. Isso geralmente é uma tarefa em andamento, porque novos padrões e melhorias para os padrões existentes serão descobertas conforme o andamento do projeto. É útil organizar o plano de desenvolvimento para que você exerça cada um de seus padrões de design principal mais cedo.  
  
 A maioria dos padrões de design podem ser incorporados em parte no código do framework. Parte do padrão pode ser reduzido para exigir que o desenvolvedor use classes específicos ou componentes, como uma camada de acesso de banco de dados que garante que o banco de dados é tratado corretamente.  
  
 Um padrão de design é descrito em um documento e normalmente inclui as seguintes partes:  
  
-   Nome.  
  
-   Descrição do contexto em que é aplicável. Que critérios devem fazer com que um desenvolvedor aplicar esse padrão?  
  
-   Breve explicação do problema que ele resolve.  
  
-   Modelo de partes mais importantes e suas relações. Estes podem ser componentes e classes ou interfaces com associações e dependências entre eles. Os elementos normalmente se enquadram em duas categorias:  
  
-   Convenções de nomenclatura.  
  
-   Descrição de como o padrão resolve o problema.  
  
-   Descrição de variações que os desenvolvedores podem ser capazes de adotar.  
  
## <a name="see-also"></a>Consulte também  
 [Visualizar código](../modeling/visualize-code.md)   
 [Requisitos do modelo de usuário](../modeling/model-user-requirements.md)   
 [Desenvolver testes de um modelo](../modeling/develop-tests-from-a-model.md)   
 [Usar modelos no processo de desenvolvimento](../modeling/use-models-in-your-development-process.md)
