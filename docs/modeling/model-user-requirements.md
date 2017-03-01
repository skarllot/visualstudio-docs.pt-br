---
title: "Modelo de requisitos do usuário | Documentos do Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- requirements
- stories
ms.assetid: 359900f8-6d69-493d-bfdf-2c9069c74a26
caps.latest.revision: 28
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
ms.sourcegitcommit: 08aabdfe0e268f93ef7723076375b7f65b15ccf3
ms.openlocfilehash: 60866c46920bb85927498992082763f9e34b4137
ms.lasthandoff: 02/22/2017

---
# <a name="model-user-requirements"></a>Requisitos de usuário do modelo
Visual Studio o ajuda a entender, discutir e se comunicar suas necessidades de usuários por desenhar diagramas sobre suas atividades e a parte um sistema desempenha na ajudando a atingir suas metas. Um modelo de requisitos é um conjunto desses diagramas, cada um deles se concentra em um aspecto das necessidades dos usuários. Para uma demonstração em vídeo, consulte: [modelagem do domínio de negócios](http://channel9.msdn.com/posts/clinted/UML-with-VS-2010-Part-3-Modeling-the-Business-Domain/).  
  
 Para ver quais versões do Visual Studio oferecem suporte a cada tipo de modelo, consulte [suporte de versão para a arquitetura e ferramentas de modelagem](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).  
  
 Um modelo de requisitos ajuda você a:  
  
-   Focalizar o comportamento do sistema externo, separadamente do seu design interno.  
  
-   Descrever os usuários e das partes interessadas precisa com muito menos ambiguidade do que em idioma natural.  
  
-   Defina um consistente Glossário de termos que pode ser usado por usuários, desenvolvedores e testadores.  
  
-   Reduza as lacunas e inconsistências nos requisitos.  
  
-   Reduza o trabalho necessário para responder a alterações de requisitos.  
  
-   Planeje a ordem na qual os recursos serão desenvolvidos.  
  
-   Use os modelos como base para testes de sistema, fazendo uma relação clara entre os testes e os requisitos. Quando os requisitos são alterados, essa relação ajuda a atualizar os testes corretamente. Isso garante que o sistema atende os requisitos de novo.  
  
 Um modelo de requisitos fornece o maior benefício se você usá-lo para discussões de foco com os usuários ou seus representantes e revisitá-lo no início de cada iteração. Não é necessário concluí-lo detalhadamente antes de escrever código. Um aplicativo de trabalho parcialmente, mesmo se muito mais simplificado, geralmente constitui a base mais interessantes para discussão sobre os requisitos de usuários. O modelo é uma maneira eficiente de resumir os resultados dessas discussões. Para obter mais informações, consulte [usar modelos no processo de desenvolvimento](../modeling/use-models-in-your-development-process.md).  
  
> [!NOTE]
>  Durante esses tópicos, "sistema" significa que o sistema ou o aplicativo que você está desenvolvendo. Pode ser uma grande coleção de muitos componentes de hardware e software; ou um único aplicativo; ou um componente de software dentro de um sistema maior. Em cada caso, o modelo de requisitos descreve o comportamento que é visível fora do sistema, seja por meio de uma interface do usuário ou a API.  
  
## <a name="common-tasks"></a>Tarefas comuns  
 Você pode criar várias exibições diferentes dos requisitos dos usuários.  Cada modo de exibição fornece um tipo específico de informações.  Quando você cria esses modos de exibição, é aconselhável movem frequentemente entre si. Você pode iniciar a partir de qualquer modo de exibição.  
  
|Diagrama ou documento|Ele descreve em um modelo de requisitos|Seção|  
|-------------------------|-----------------------------------------------|-------------|  
|Diagrama conceitual de classe|Glossário de tipos que são usados para descrever os requisitos; os tipos visíveis na interface do sistema.||  
|Outros documentos ou itens de trabalho|Critérios de desempenho, segurança, usabilidade e confiabilidade.|[Descrevendo a qualidade dos requisitos de serviço](#QoSRequirements)|  
|Outros documentos ou itens de trabalho|Restrições e regras não específicas a um determinado caso de uso|[Mostrando as regras de negócio](#BusinessRules)|  
  
 Observe que a maioria dos tipos de diagrama pode ser usada para outras finalidades. Para obter uma visão geral dos tipos de diagrama, consulte [criar modelos para seu aplicativo](../modeling/create-models-for-your-app.md).
  
##  <a name="a-namebusinessrulesa-showing-business-rules"></a><a name="BusinessRules"></a>Mostrando as regras de negócio  
 Uma regra de negócios é um requisito que não está associado um caso de uso específico e deve ser observado em todo o sistema.  
  
 Muitas regras de negócios são restrições nas relações entre as classes conceituais. Você pode escrever esses *estático**as regras de negócio* como comentários associados as classes relevantes em um diagrama de classe conceitual. Por exemplo:  
  
 ![Regra em comentário anexado à classe Order. ] (../modeling/media/uml_reqmcd2.png "UML_ReqmCD2")  
  
 *Regras de negócio dinâmico* restringir as sequências permitidas de eventos. Por exemplo, você deve usar um diagrama de sequência ou atividade para mostrar que um usuário deve fazer logon antes de executar outras operações em seu sistema.  
  
 No entanto, muitas regras dinâmicas podem ser mais eficiência e genericamente declaradas substituindo-os por regras estáticas. Por exemplo, você pode adicionar um atributo booleano 'Registrado no' a uma classe no modelo conceitual de classe. Você deve adicionar conectado como pós-condição do log em caso de uso e adicioná-lo como uma pré-condição para a maioria dos casos de uso. Essa abordagem permite que você evite definir todas as combinações possíveis de sequências de eventos. Também é mais flexível quando você precisa adicionar novos casos de uso para o modelo.  
  
 Observe que a opção aqui é sobre como definir os requisitos e que isso é independente de como implementar os requisitos no código do programa.  
  
 Os tópicos a seguir fornecem mais informações:  
  
|Para saber mais sobre|Ler|  
|--------------------|----------|  
|Como desenvolver código que obedece às regras de negócio|[Modelar a arquitetura do aplicativo](../modeling/model-your-app-s-architecture.md)|  
  
##  <a name="a-nameqosrequirementsa-describing-quality-of-service-requirements"></a><a name="QoSRequirements"></a>Descrevendo a qualidade dos requisitos de serviço  
 Há várias categorias de qualidade de requisito de serviço. Elas incluem o seguinte:  
  
-   Desempenho  
  
-   Segurança  
  
-   Usabilidade  
  
-   Confiabilidade  
  
-   Robustez  
  
 Você pode incluir alguns desses requisitos nas descrições de casos de uso específico. Outros requisitos não são específicos para casos de uso e com mais eficiência são gravados em um documento separado. Quando possível, é útil cumprir o vocabulário definido pelo modelo de requisitos. No exemplo a seguir, observe que as palavras principais usadas na requisição de estão os títulos dos atores, casos de uso e classes nas ilustrações anteriores:  
  
 Se um restaurante exclui um Item de Menu, enquanto um cliente estiver encomendando refeição, qualquer Item de ordem que se refere a esse Item de Menu será exibido em vermelho.  
  
 Os tópicos a seguir fornecem mais informações:  
  
|Para saber mais sobre|Ler|  
|--------------------|----------|  
|Informações mais detalhadas sobre a qualidade dos requisitos de serviço da gravação|[Diretrizes para definir a qualidade dos requisitos de serviço](http://msdn.microsoft.com/en-us/9677a437-c2cb-4ac4-8c2d-4e3350005f06)|  
|Como desenvolver código que obedeça a qualidade dos requisitos de serviço|[Modelar a arquitetura do aplicativo](../modeling/model-your-app-s-architecture.md)|  
  
## <a name="see-also"></a>Consulte também  
 [Usar modelos no processo de desenvolvimento](../modeling/use-models-in-your-development-process.md)   
 [Modelar a arquitetura do aplicativo](../modeling/model-your-app-s-architecture.md)   

