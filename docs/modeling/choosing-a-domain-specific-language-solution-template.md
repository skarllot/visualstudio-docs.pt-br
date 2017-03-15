---
title: "Escolhendo um modelo de solução de linguagem específica do domínio | Documentos do Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Domain-Specific Language Tools, solution templates
ms.assetid: 9c05955f-1548-4df6-b09b-4b348823c237
caps.latest.revision: 24
author: alancameronwills
ms.author: awills
manager: douge
translationtype: Machine Translation
ms.sourcegitcommit: fd26c504273cae739ccbeef5e406891def732985
ms.openlocfilehash: 2a1ad374c709b9575ff8e3d46bb3d2178a1c3f95
ms.lasthandoff: 02/22/2017

---
# <a name="choosing-a-domain-specific-language-solution-template"></a>Escolhendo um modelo de solução de linguagem específica do domínio
Para criar uma solução de linguagem específica do domínio, escolha um dos modelos de solução estão disponíveis no Assistente de Designer de linguagem específica do domínio. Escolhendo o modelo que mais se assemelha a linguagem que você deseja criar, você pode minimizar as modificações que você precisa fazer a solução inicial.  
  
 Os seguintes modelos de solução estão disponíveis no Assistente de Designer de linguagem específica do domínio.  
  
|Modelo|Recursos|Descrição|  
|--------------|--------------|-----------------|  
|Diagramas de classe|-Formas do compartimento<br />-Herança de classe<br />-Herança de relacionamento<br />-Forma de herança<br />-Propriedades de relação|Use esse modelo de solução se sua linguagem específica do domínio inclui entidades e relações que têm propriedades. Este modelo cria uma linguagem específica do domínio que se parece com diagramas de classe UML. As principais entidades são classes e interfaces, junto com os relacionamentos de associação, generalização e a implementação. Uma classe ou interface aparece como uma caixa que contém uma lista de atributos.|  
|Diagramas de componente|-Portas|Use esse modelo de solução se sua linguagem específica do domínio inclui componentes, ou seja, partes de um sistema de software. Este modelo cria uma linguagem específica do domínio que se parece com diagramas de componente UML. As principais entidades são componentes e portas, que são exibidos como pequenas formas fora dos componentes.|  
|Diagramas de fluxo de tarefa|-Imagem e formas geométricas<br />-   *Raias*|Use esse modelo de solução se sua linguagem específica do domínio inclui sequências, estados ou fluxos de trabalho. Este modelo cria uma linguagem específica do domínio que se parece com diagramas de atividade UML. A entidade principal é uma atividade e a relação principal é uma transição entre atividades. O modelo inclui vários outros elementos, como estado inicial, o estado final e uma barra de sincronização.|  
|Linguagem mínima|-Uma classe e forma<br />-Uma relação e conector|Use este modelo de solução se sua linguagem específica do domínio não for parecido com os outros modelos. Este modelo cria uma linguagem específica do domínio que tem duas classes e uma relação, que são representados no **Toolbox** como **caixa** e **linha**. A classe e a relação tem uma propriedade de cadeia de caracteres de exemplo.|  
|WinForm Designer mínimo|-Um modelo pequeno.<br />-Um Windows Form que exibe o modelo.|Use este modelo para criar um aplicativo em que uma DSL é associada a um formulário do Windows, em vez de um designer gráfico.<br /><br /> O formulário que atua como a interface do usuário para o idioma está na pasta Dsl\UI.<br /><br /> Você deve compilar o projeto antes de abrir o designer de formulário.<br /><br /> Para obter mais informações, consulte [criando uma linguagem específica do domínio de Windows Forms-Based](../modeling/creating-a-windows-forms-based-domain-specific-language.md).|  
|Mínimo de WPF Designer|-Um modelo pequeno<br />-Uma interface de usuário do Windows Presentation Foundation que exibe o modelo|Use este modelo para criar um aplicativo em que uma DSL é acoplada a uma interface de usuário do WPF, em vez de um designer gráfico.<br /><br /> O designer de interface do usuário está na pasta Dsl\UI.<br /><br /> Você deve compilar o projeto antes de abrir o designer de interface do usuário.<br /><br /> Para obter mais informações, consulte [criando uma linguagem específica do domínio de WPF-Based](../modeling/creating-a-wpf-based-domain-specific-language.md).|  
|Biblioteca DSL|-Uma biblioteca mínima|Use este modelo para criar uma definição de DSL parcial que pode ser importada para outras definições de DSL.|  
  
## <a name="see-also"></a>Consulte também  
 [Visão geral das Ferramentas de Linguagem Específica de Domínio](../modeling/overview-of-domain-specific-language-tools.md)

