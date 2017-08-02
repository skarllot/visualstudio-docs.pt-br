---
title: Arquitetura de plug-in de controle de origem | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- source control plug-ins, architecture
ms.assetid: 35351d4c-9414-409b-98fc-f2023e2426b7
caps.latest.revision: 24
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
ms.openlocfilehash: 1f935f3c96e39342dd0d435c129455260bd98478
ms.lasthandoff: 02/22/2017

---
# <a name="source-control-plug-in-architecture"></a>Arquitetura de plug-in de controle de origem
Você pode adicionar suporte a controle de origem para o [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] o ambiente de desenvolvimento integrado (IDE), implementando e anexando um plug-in de controle de origem. O IDE conecta plug-in por meio da API de plug-in de controle de origem bem definido de controle de origem. O IDE expõe os recursos de controle de versão do sistema de controle de origem, fornecendo uma interface do usuário (IU) que consiste em barras de ferramentas e comandos de menu. O plug-in de controle de origem implementa a funcionalidade de controle de origem.  
  
## <a name="source-control-plug-in-resources"></a>Recursos de plug-in de controle de origem  
 O plug-in de controle de origem fornece recursos para ajudar a criar e conectar o aplicativo de controle de versão para o [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE. O plug-in de controle de origem contém a especificação da API que deve ser implementada por um plug-in de controle de origem para que podem ser integrado a [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE. Ele também contém um exemplo de código (escrito em C++) que implementa uma esqueleto fonte plug-in demonstram implementação do controle de funções essenciais compatíveis com a API de plug-in de controle de origem.  
  
 A especificação da API de plug-in de controle de origem permite que você utilize qualquer sistema de controle de origem de sua escolha, se você criar uma DLL de controle do código-fonte com o conjunto necessário de funções implementadas de acordo com a API de plug-in de controle de origem.  
  
## <a name="components"></a>Componentes  
 O pacote de adaptador de controle de origem no diagrama é o componente do IDE que converte a solicitação do usuário para uma operação de controle de origem em uma chamada de função com suporte a plug-in de controle de origem. Para isso acontecer, o IDE e o plug-in de controle de origem devem ter uma caixa de diálogo efetiva que passa informações e para trás entre o IDE e o plug-in. Para este diálogo ocorra, ambos devem falarem o mesmo idioma. A API de plug-in de controle de origem descritos nesta documentação é o vocabulário comum para essa troca.  
  
 ![Diagrama de arquitetura de controle do código fonte](~/docs/extensibility/internals/media/vs_sccsdk_plug_in_arch.gif "vs_sccsdk_plug_in_arch")  
Diagrama de arquitetura mostrando a interação entre VS e o controle da fonte de plug-in  
  
 Conforme mostrado no diagrama da arquitetura, o [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] shell, rotulado como VS shell no diagrama, hospeda projetos de trabalho e componentes associados, como editores e do Gerenciador de soluções do usuário. O pacote de adaptador de controle de origem trata a interação entre o IDE e o plug-in de controle de origem. O pacote de adaptador de controle de origem fornece seu próprio controle da fonte de interface do usuário. Ele é a interface de usuário de nível superior que o usuário interage com para iniciar e definir o escopo de uma operação de controle de origem.  
  
 O plug-in de controle de origem pode ter sua própria interface do usuário, que pode consistir em duas partes conforme mostrado na figura. A caixa rotulada como "Fornecedor UI" representa elementos da interface de usuário personalizada fornecida por você, como um criador de plug-in de controle de origem. Estes são exibidos diretamente, o plug-in de controle de origem quando o usuário chama uma operação de controle do código-fonte avançadas. A caixa rotulada como "UI auxiliar" é um conjunto de plug-in da interface do usuário recursos de controle fonte chamados indiretamente por meio do IDE. O plug-in de controle de origem passa mensagens relacionadas a interface do usuário para o IDE por meio das funções de retorno de chamada especiais fornecidos pelo IDE. O auxiliar de interface do usuário facilita uma integração perfeita com o IDE (geralmente através do uso de um **avançado** botão) e, portanto, fornece uma experiência mais unificada do usuário final.  
  
 Um plug-in de controle de origem não pode fazer alterações para o [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] de shell e, consequentemente, o pacote de adaptador de controle de origem ou fonte de controle da interface do usuário fornecida pelo IDE. Ele deve fazer uso máximo de flexibilidade oferecida por meio da implementação de várias funções de API de plug-in de controle de origem que contribuem para uma experiência integrada para o usuário final. A seção de referência da documentação de API de plug-in de controle de origem inclui informações de alguns recursos de plug-in de controle de fonte avançadas. Para explorar esses recursos, o plug-in de controle de origem deve declarar seus recursos avançados para o IDE durante a inicialização, e ela deve implementar funções avançadas específicas para cada recurso.  
  
## <a name="see-also"></a>Consulte também  
 [Plug-ins de controle de origem](../../extensibility/source-control-plug-ins.md)   
 [Glossário](../../extensibility/source-control-plug-in-glossary.md)   
 [Criando um controle da fonte de plug-in](../../extensibility/internals/creating-a-source-control-plug-in.md)
