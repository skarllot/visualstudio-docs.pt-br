---
title: "Visão geral de integração do controle de origem | Documentos do Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- source control [Visual Studio SDK], about source control
ms.assetid: 3a46e4eb-e677-49c3-8647-d927d035a19a
caps.latest.revision: 16
ms.author: gregvanl
manager: ghogen
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
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: d3facc06885ef927448eb506ff2f4aa5c04ce85f
ms.lasthandoff: 02/22/2017

---
# <a name="source-control-integration-overview"></a>Visão geral de integração de controle de origem
Esta seção compara as duas formas de integrar o controle de origem do Visual Studio; um controle da fonte de plug-in e um VSPackage que fornece uma solução de controle de origem e destaca os novos recursos de controle de origem. O Visual Studio permite manual alternando VSPackages de controle de origem e plug-ins de controle de origem, bem como a comutação automática baseados em soluções.  
  
## <a name="source-control-integration"></a>Integração de controle do código-fonte  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]oferece suporte a dois tipos de opções de integração de controle de origem. Todas as versões do [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], você ainda pode integrar um plug-in baseado na fonte de controle de plug-in API (anteriormente também conhecida como API MSSCCI), que fornece a funcionalidade de controle do código-fonte básica usando a interface de usuário (IU) do Visual Studio fonte controle. Um controle de origem VSPackage, por outro lado, fornece uma integração profunda nova, [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] caminho adequado para a integração de controle de origem que exige um alto nível de sofisticação e autonomia em seu modelo de controle de origem.  
  
 ![Visão geral do controle de origem](~/extensibility/internals/media/sourcectnrloverview.gif "SourceCtnrlOverview")  
  
## <a name="source-control-plug-in"></a>Plug-in de Controle do Código-fonte  
 Todas as versões do Visual Studio oferecem suporte a API de plug-in de controle de fonte especificação versão 1.2 como um caminho de integração. Um implementador de plug-in de controle de origem grava uma DLL que implementa as funções de API de plug-in de controle de origem para integração de controle do código-fonte e o registro conforme descrito em [criar um plug-in de controle de origem](../../extensibility/internals/creating-a-source-control-plug-in.md). Nessa abordagem, o ambiente de desenvolvimento integrado (IDE) usa o [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] interface do usuário para as caixas de diálogo, como check-in, check-out, páginas de propriedades de ferramentas/opções, barras de ferramentas e glifos de controle de origem. Conformidade estrita com a API de plug-in de controle de origem assegura uma fácil integração com o Visual Studio e uma experiência sem problemas para o usuário. Isso significa que o plug-in de controle de origem deve implementar a maioria das funções e dos retornos de chamada detalhados na API.  
  
 Para implementar um plug-in usando a API de plug-in de controle de origem de controle de origem, siga estas etapas:  
  
1.  Criar uma DLL que implementa as funções especificadas na [Plug-ins de controle de origem](../../extensibility/source-control-plug-ins.md).  
  
2.  Registrar a DLL, tornando as entradas de registro apropriadas (descrito na [como: instalar um plug-in de controle de origem](../../extensibility/internals/how-to-install-a-source-control-plug-in.md)).  
  
3.  Criar um auxiliar de interface do usuário e exibição quando solicitado pelo pacote de adaptador de controle de origem (o componente Visual Studio que lida com a funcionalidade de controle do código-fonte por meio de plug-ins de controle de origem)  
  
 Em resposta a um comando de controle de origem, o IDE do Visual Studio apresenta uma IU padrão para as operações básicas e, em seguida, passa as informações para o controle de origem plug-in por meio de funções definidas na API de plug-in de controle de origem. Para opções avançadas, o plug-in de controle de origem pode ser chamado em para apresentar sua própria interface do usuário, por exemplo, navegar para um projeto de controle do código-fonte. Isso significa que o usuário pode ser apresentado com dois estilos possivelmente diferentes da interface do usuário ao lidar com controle de origem: a interface do usuário que apresenta o Visual Studio e a interface do usuário que apresenta o plug-in de controle de origem. Isso é mais perceptível com operações de controle do código-fonte avançadas.  
  
### <a name="drawbacks-to-implementing-a-source-control-plug-in"></a>Desvantagens para implementar um plug-in de controle de origem  
  
-   Recursos avançados, o usuário poderá ver dois estilos diferentes de interfaces, levando a possível confusão.  
  
-   O plug-in de controle de origem está restrita ao modelo de controle de origem indicado pela API de plug-in de controle de origem.  
  
-   A API de plug-in de controle de origem pode ser muito restritiva para alguns cenários de controle de origem.  
  
### <a name="advantages-to-implementing-a-source-control-plug-in"></a>Vantagens para implementar um plug-in de controle de origem  
  
-   O Visual Studio fornece toda a interface do usuário para todas as operações de controle de origem básico para que o plug-in de controle de origem não tem que implementar a interface de usuário potencialmente complexo.  
  
-   Devido a API estrita, o plug-in de controle de origem pode prontamente interagir com programas de controle de origem externa para fornecer a funcionalidade mais ampla; O Visual Studio, não importa muito bem como a funcionalidade de controle do código-fonte é realizada, apenas que ela é realizada de acordo com a API de plug-in de controle de origem.  
  
-   É mais fácil implementar um plug-in que um controle de origem VSPackage de controle de origem.  
  
## <a name="source-control-vspackage"></a>VSPackage de controle de origem  
 [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)]permite uma integração profunda no Visual Studio com controle total da funcionalidade de controle do código-fonte e substituição completa da interface do usuário de controle de origem fornecido pelo Visual Studio. Um controle de fonte VSPackage é registrado com o Visual Studio e fornece funcionalidade de controle do código-fonte. Embora vários VSPackages de controle de origem pode ser registrado com o Visual Studio, somente um deles pode ser ativo a qualquer momento. Um controle de origem VSPackage tem controle total sobre a aparência e funcionalidade de controle do código-fonte no Visual Studio enquanto ele está ativo. Todos os outro controle de origem VSPackages que podem ser registrados no sistema inativo e não exibirá nenhuma interface de usuário em todos os.  
  
 Implementar um controle de origem VSPackage requer uma estratégia "tudo ou nada". O criador de um controle de origem VSPackage deve investir uma quantidade significativa de esforço na implementação de um número de interfaces de controle de origem e novos elementos de interface do usuário (caixas de diálogo, menus e barras de ferramentas) para cobrir a funcionalidade de controle de origem inteiro. Consulte [criar um VSPackage de controle de origem](../../extensibility/internals/creating-a-source-control-vspackage.md) para obter mais detalhes.  
  
### <a name="drawbacks-to-implementing-a-source-control-vspackage"></a>Desvantagens para implementar um VSPackage de controle de origem  
  
-   O VSPackage deve implementar várias interfaces complexas para integrar com êxito com o Visual Studio.  
  
-   O VSPackage deve fornecer todos os a interface do usuário necessário para o controle de origem; O Visual Studio não fornecerá nenhuma assistência nessa área.  
  
-   Um controle de fonte VSPackage está intimamente ligado ao Visual Studio e não pode operar com programas autônomos, portanto funcionalidade não pode ser facilmente compartilhada com uma versão do programa de controle de origem externa.  
  
### <a name="advantages-to-implementing-a-source-control-vspackage"></a>Vantagens para a implementação de um VSPackage de controle de origem  
  
-   Como o VSPackage possui funcionalidade e controle total sobre o controle do código-fonte da interface do usuário, o usuário é apresentado com uma interface uniforme para controle de origem.  
  
-   O VSPackage não está limitado a um modelo de controle de origem em particular.  
  
## <a name="see-also"></a>Consulte também  
 [Controle de origem](../../extensibility/internals/source-control.md)   
 [Criando um controle da fonte de plug-in](../../extensibility/internals/creating-a-source-control-plug-in.md)   
 [Criando um VSPackage de controle de origem](../../extensibility/internals/creating-a-source-control-vspackage.md)   
 [O que há de novo no controle de origem](../../extensibility/internals/what-s-new-in-source-control.md)
