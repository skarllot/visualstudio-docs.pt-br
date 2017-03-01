---
title: "Sobre linguagens específicas do domínio | Documentos do Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Domain-Specific Language
ms.assetid: 29e5b6f2-ece4-4f3b-ab08-5f957418702f
caps.latest.revision: 26
author: alancameronwills
ms.author: awills
manager: douge
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 3bab0e785dfccddb7d182864a01146fe697b4247
ms.lasthandoff: 02/22/2017

---
# <a name="about-domain-specific-languages"></a>Sobre linguagens específicas do domínio
Ao contrário de uma linguagem de finalidade geral, como c# ou UML, uma linguagem específica do domínio (DSL) destina-se para expressar declarações em um determinado problema de espaço ou domínio.  
  
 DSLs conhecidas incluem expressões regulares e SQL. Cada DSL é muito melhor do que uma linguagem de finalidade geral para descrever as operações em cadeias de caracteres de texto ou um banco de dados, mas muito pior para descrever ideias que estão fora de seu próprio escopo. Setores individuais também têm suas próprias DSLs. Por exemplo, na indústria de telecomunicações, chame descrição idiomas são amplamente usados para especificar a sequência dos estados em uma chamada telefônica e air seguem setor padrão que DSL é usado para descrever as reservas de voo.  
  
 Sua empresa e seu projeto também lidam com conjuntos especial de conceitos que podem ser descritos com uma DSL. Por exemplo, você poderia definir uma DSL para um desses aplicativos:  
  
-   Plano de caminhos de navegação em um site da Web.  
  
-   Diagramas de fiação para componentes eletrônicos.  
  
-   Redes de belts transportadora e bagagem tratamento equipamentos de um aeroporto.  
  
 Ao projetar uma DSL, defina uma *classe de domínio* para cada um dos conceitos importantes do domínio, como uma mesa check-in do aeroporto, lamp ou página da Web. Definir *relações de domínio* como hiperlink, fios ou uma esteira para vincular os conceitos.  
  
 Criarem usuários de sua DSL *modelos.* Os modelos são *instâncias* da DSL. Por exemplo, eles descrevem um site específico ou a ligação de um determinado dispositivo ou a sistema em um aeroporto específico de manipulação de bagagem.  
  
 Os usuários podem exibir um modelo como um diagrama ou um Windows form. Modelos também podem ser exibidos como XML, que é como eles são armazenados. Ao definir uma DSL, você define como as instâncias de cada classe de domínio e a relação aparecer na tela do usuário. Uma DSL típica é exibida como uma coleção de ícones ou retângulos conectados por setas.  
  
 A figura a seguir mostra um modelo pequeno em uma DSL diagramática:  
  
 ![Modelo de árvore da família Tudor](../modeling/media/tudor_familytreemodel.png "Tudor_FamilyTreeModel")  
  
## <a name="what-you-can-do-with-dsls"></a>O que você pode fazer com as DSLs  
 Um aplicativo típico de uma DSL é gerar o código do programa ou outros artefatos. Quando você define sua DSL, você pode definir *modelos de texto* que ler um modelo da DSL e gerar arquivos de texto.  
  
 Por exemplo, você poderia escrever modelos que tenham um plano de aeroporto e geram a parte do software para bagagem tratamento, bem como alguns dos documentos de usuário que descrevem o plano.  
  
 Quando você tiver definido uma DSL, você pode distribuí-lo a outros usuários podem instalá-lo em seus próprios computadores. Os usuários de sua DSL podem criar e editar modelos em [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
 Você também pode definir comandos de menu e outras ferramentas que ajudam os usuários editar DSL, restrições de validação para ajudar a garantir que a DSL é usada corretamente e modelos de item que ajudam os usuários a criarem novas instâncias. Você pode envolver um ou mais DSLs com suas ferramentas e outros [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] extensões como um pacote integrado.  
  
 Normalmente, uma linguagem específica do domínio é criada quando uma equipe de desenvolvimento precisa gravar um código semelhante para vários produtos. Por exemplo, uma empresa especializada em sistemas de manuseio de bagagem pode definir uma DSL de faixa de bagagem do qual eles podem gerar algum código para cada instalação. Os benefícios da DSL são que ele podem ser compreendidos pelos clientes, que o código gerado a partir dele é confiável e que o sistema pode ser atualizado rapidamente se alterarem às necessidades dos clientes.  
  
 [!INCLUDE[dsl](../modeling/includes/dsl_md.md)]permite criar uma linguagem específica do domínio que tem seu próprio designer gráfico e seu próprio notação do diagrama e, em seguida, usar a linguagem para gerar código-fonte apropriado para cada projeto.  
  
## <a name="domain-specific-development"></a>Desenvolvimento específico de domínio  
 Desenvolvimento específico de domínio é o processo de identificar as partes de seus aplicativos que podem ser modelados usando uma linguagem específica do domínio e, em seguida, construindo a linguagem e implantá-lo para desenvolvedores de aplicativos. Os desenvolvedores usam a linguagem específica do domínio para construir modelos que são específicos para seus aplicativos, use os modelos para gerar código-fonte e, em seguida, use o código-fonte para desenvolver os aplicativos.  
  
## <a name="aspects-of-graphical-domain-specific-development"></a>Aspectos do desenvolvimento do gráfico específica do domínio  
 Uma linguagem específica do domínio gráfica deve incluir os seguintes recursos:  
  
-   Notation  
  
-   Modelo de domínio  
  
-   Geração de artefato  
  
-   Serialização  
  
-   Integração com o Visual Studio  
  
### <a name="notation"></a>Notation  
 Uma linguagem específica do domínio deve ter um conjunto de elementos que podem ser facilmente definidos e estendidos para representar construções específicas do domínio razoavelmente pequeno. Uma notação consiste em formas, que representam os elementos, e conectores, que representam as relações entre os elementos em uma superfície de Diagrama gráfico. Em [!INCLUDE[dsl](../modeling/includes/dsl_md.md)], as formas podem ser estendidas e refinadas para representar os elementos da sua linguagem específica do domínio.  
  
### <a name="domain-model"></a>Modelo de domínio  
 Uma linguagem específica do domínio deve combinar o conjunto de elementos e as relações entre eles em uma gramática coerente. Ele também deve definir se combinações de elementos e relações são válidas. Por exemplo, linguagens de programação normalmente impedem herança circular, em que uma classe é derivada de uma segunda classe e a segunda classe é derivada da classe primeiro. Restrições também podem ser usadas para expressar a lógica de negócios, por exemplo, uma pessoa não pode ser um dependente de si próprio. [!INCLUDE[dsl](../modeling/includes/dsl_md.md)]usa restrições para expressar os tipos de restrições que exigem mais linguagens específicas de domínio.  
  
### <a name="artifact-generation"></a>Geração de artefato  
 Um dos principais motivos de uma linguagem específica do domínio é gerar um artefato, por exemplo, código-fonte, um arquivo XML ou outros dados utilizáveis. Normalmente, uma alteração no modelo significa que uma alteração no artefato. Você pode usar [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] para gerar artefatos e gerá-los novamente quando você alterar o modelo.  
  
### <a name="serialization"></a>Serialização  
 Uma linguagem específica do domínio deve ser persistida em alguma forma que pode ser editada, salvo, fechada e recarregada. [!INCLUDE[dsl](../modeling/includes/dsl_md.md)]usa um formato XML que permite definir e personalizar como sua linguagem específica do domínio é serializada ou persistente.  
  
### <a name="integration-with-visual-studio"></a>Integração com o Visual Studio  
 Porque [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] está hospedado no [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], ele estende muitas [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] janelas e controles. Ele também permite personalizar o comportamento dos comandos de menu, itens de caixa de ferramentas e outros elementos da interface do usuário.  
  
 Você também pode criar um adaptador de barramento de modelo para sua linguagem específica do domínio. Este adaptador permite que um modelo de referência e elementos dentro de um modelo e permite que você escrever código que pode acessar e atualizar uma instância da DSL. Usando o poderoso mecanismo de barramento de modelo, você pode escrever [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] extensões funcionem com vários modelos. Você também pode escrever aplicativos independentes que trabalham com modelos. Para obter mais informações, consulte [integrando modelos usando o Visual Studio Modelbus](../modeling/integrating-models-by-using-visual-studio-modelbus.md).  
  
## <a name="benefits-of-domain-specific-development"></a>Benefícios de desenvolvimento específico de domínio  
 Uma linguagem específica do domínio pode fornecer os seguintes benefícios:  
  
-   Contém as construções que se ajuste exatamente o problema de espaço.  
  
     Ao contrário de linguagens de finalidade geral, uma linguagem específica do domínio consiste em elementos e relações que representam diretamente a lógica do espaço de problema. Por exemplo, um aplicativo da apólice de seguro deve incluir elementos de políticas e declarações. Uma linguagem específica do domínio torna mais fácil de criar o aplicativo e localizar e corrigir erros de lógica.  
  
-   Permite que não-desenvolvedores e as pessoas que não conhecem o domínio entender o design geral.  
  
     Usando uma linguagem específica do domínio gráfica, você pode criar uma representação visual do domínio para que não desenvolvedores possam entender facilmente o design do aplicativo.  
  
-   Torna mais fácil criar um protótipo do aplicativo final.  
  
     Os desenvolvedores podem usar o código que gera o modelo para criar um aplicativo de protótipo que eles podem mostrar aos clientes.  
  
## <a name="the-process-of-domain-specific-development"></a>O processo de desenvolvimento específico de domínio  
 A maioria das equipes de desenvolvimento de software que usam linguagens específicas de domínio siga estas etapas para criar e usar seus modelos:  
  
-   A equipe distingue as partes de variável do domínio das partes que nunca mudam.  
  
-   Os desenvolvedores escrever código para as partes fixas e deixe os pontos de extensão para as partes de variável.  
  
-   O gerente de desenvolvimento de software ou o arquiteto cria uma linguagem específica do domínio que incorpora os padrões de design de uma parte fixa do domínio e os pontos de extensão para as partes de variável.  
  
-   O gerente de desenvolvimento de software ou o arquiteto implanta a linguagem específica do domínio para os desenvolvedores de vários aplicativos que produz a equipe.  
  
-   Todo desenvolvedor cria um modelo que se aplica ao aplicativo específico.
