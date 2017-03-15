---
title: "Seleção e moeda no IDE | Documentos do Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- currency, Visual Studio IDE
- IDE, selection
- selection, Visual Studio IDE
- IDE, currency
ms.assetid: 2f6f18d1-acd8-454d-a856-9a4d81155052
caps.latest.revision: 14
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
ms.openlocfilehash: cebd83d0f4cea4d4fddea714c7e7d6504a8db9f0
ms.lasthandoff: 02/22/2017

---
# <a name="selection-and-currency-in-the-ide"></a>Seleção e moeda no IDE
O [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] o ambiente de desenvolvimento integrado (IDE) mantém informações sobre dos usuários objetos selecionados no momento usando a seleção *contexto*. Com o contexto de seleção VSPackages pode fazer parte de moeda de controle de duas maneiras:  
  
-   Propagando as informações de moeda sobre VSPackages ao IDE.  
  
-   Monitorando as seleções de usuários ativas no momento no IDE.  
  
## <a name="selection-context"></a>Contexto de seleção  
 O [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE globalmente mantém o controle de moeda IDE em seu próprio objeto de contexto de seleção global. A tabela a seguir mostra os elementos que compõem o contexto da seleção.  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|Hierarquia de atual|Normalmente, o projeto atual. uma hierarquia atual NULL indica que a solução como um todo é atual.|  
|ItemID atual|O item selecionado dentro da hierarquia atual; Quando há várias seleções em uma janela de projeto, pode haver vários itens atuais.|  
|Atual`SelectionContainer`|Contém um ou mais objetos para os quais a janela Propriedades deve exibir propriedades.|  
  
 Além disso, o ambiente mantém duas listas globais:  
  
-   Uma lista de identificadores de comando de interface do usuário ativos  
  
-   Uma lista de tipos de elemento ativo no momento.  
  
### <a name="window-types-and-selection"></a>Seleção e tipos de janelas  
 O [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE organiza windows em dois tipos gerais:  
  
-   Windows do tipo de hierarquia  
  
-   Janelas de quadro, como janelas de ferramenta e de documentos  
  
 O IDE controla moeda diferente para cada um desses tipos de janela.  
  
 A janela de tipo de projeto mais comum é o Gerenciador de soluções, que controla o IDE. Uma janela de tipo de projeto controla a hierarquia global e o ItemID do contexto da seleção global e a janela se baseia na seleção do usuário para determinar a hierarquia atual. Para windows de tipo de projeto, o ambiente fornece o serviço global <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection>por quais VSPackages pode monitorar os valores atuais de elementos abertos.</xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection> Propriedade de navegação no ambiente é controlada por esse serviço global.  
  
 Janelas de quadro, por outro lado, usam o DocObject dentro da janela de quadro para transferir o valor de SelectionContext (o trio ItemID/hierarquia/SelectionContainer). . Janelas de quadro usam o serviço <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection>para essa finalidade.</xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection> O DocObject pode enviar somente os valores para o contêiner de seleção, deixando os valores locais para a hierarquia e ItemID inalterado, como é normal para documentos de filho MDI.  
  
### <a name="events-and-currency"></a>Eventos e moeda  
 Dois tipos de eventos podem ocorrer que afetam a noção do ambiente de moeda:  
  
-   Eventos que são propagados para o nível global e alterar o contexto de seleção do quadro de janela. Exemplos desse tipo de evento incluem uma janela filho MDI aberta, uma janela de ferramenta global que está sendo aberto ou uma janela de ferramenta do tipo de projeto que está sendo aberto.  
  
-   Eventos que alteram os elementos rastreados dentro do contexto de seleção do quadro de janela. Exemplos incluem alterar seleção dentro um DocObject ou seleção em uma janela do tipo de projeto.  
  
## <a name="see-also"></a>Consulte também  
 [Objetos de contexto da seleção](../../extensibility/internals/selection-context-objects.md)   
 [Comentários para o usuário](../../extensibility/internals/feedback-to-the-user.md)
