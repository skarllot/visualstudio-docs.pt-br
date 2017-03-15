---
title: "Padrões de interação para Visual Studio | Documentos do Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a3643792-b0df-481c-bc35-576f948e04cf
caps.latest.revision: 4
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
ms.openlocfilehash: 887eda6abe0d448f1b393787b5b1bd1f960d8a93
ms.lasthandoff: 02/22/2017

---
# <a name="interaction-patterns-for-visual-studio"></a>Padrões de interação para Visual Studio
## <a name="overview"></a>Visão Geral  
 Um padrão de design, em geral, é o núcleo de um design que pode ser aplicado em situações específicas para solucionar problemas com conjuntos semelhantes de restrições. Designers de recurso e o sistema usam esses padrões de design como partida pontos, que podem ser adaptados à sua situação específica.  
  
 O Visual Studio tem uma biblioteca de padrões comuns de interação que devem ser consideradas durante a criação de novos recursos. Existem dois contextos de núcleo para nossos padrões de design: (devenv) do cliente do Visual Studio e Visual Studio Online. Para alguns problemas de design, há um padrão de todos os lugares que funciona bem em todas as situações. Em muitos casos, no entanto, a solução pode ser diferente para a interface de usuário que está sendo apresentado em um navegador e que está hospedado em um aplicativo cliente.  
  
### <a name="visual-studio-client-pattern-types"></a>Tipos de padrão do Visual Studio cliente  
  
|Tipo de padrão|Descrição|Exemplos|  
|------------------|-----------------|--------------|  
|**Padrões de nível de aplicativo**|Alto nível padrões comuns para o aplicativo, determinando ou exibindo o contexto do aplicativo e que contém a composição e padrões de controle dentro deles|-Janelas de ferramenta<br />-Windows documento|  
|**Padrões compostos**|Padrões comuns que podem se estender por padrões de aplicativo ou um padrão reconhecido composto de vários controles em uma configuração distinta|-Exibir a exibição<br />-Construtores de list<br />-Exibindo dados<br />-Notificações<br />-Validação<br />-Modelos de seleção|  
|**Padrões de controle**|Informações específicas sobre controles de baixo nível como devem se comportar|-Modos de exibição de árvore<br />-Editar dentro de um controle de grade|  
  
## <a name="application-patterns"></a>Padrões de aplicativo  
 Em um alto nível, a interface do Visual Studio inclui vários windows, caixas de diálogo, comandos e barras de ferramentas em um único IDE. A hierarquia do Visual Studio determina os menus de contexto e unidades. Os pontos de integração principais na interface do usuário do IDE são janelas de documentos, janelas de ferramentas, projetos, a estrutura do comando, o editor de texto, a caixa de ferramentas, a janela Propriedades e ferramentas > opções.  
  
 Existem padrões de uso básico para cada um dos pontos de integração principais na interface do usuário do IDE:  
  
-   [Menus e comandos para o Visual Studio](../../extensibility/ux-guidelines/menus-and-commands-for-visual-studio.md)  
  
-   [Padrões de aplicativo para o Visual Studio](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md)  
  
    -   [Interações de janela](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_WindowInteractions)  
  
    -   [Janelas de ferramenta](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_ToolWindows)  
  
    -   [Convenções do documento editor](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_DocumentEditorConventions)  
  
    -   [Caixas de diálogo](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_Dialogs)  
  
    -   [Projetos](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_Projects)  
  
## <a name="common-control-patterns"></a>Padrões de controle comum  
 Padrões de controle são principalmente sobre os controles devem se comportar. Esta é uma área em que a consistência é mais importante.  
  
 Controles mais comuns no Visual Studio devem seguir as diretrizes de Desktop Windows. Nossas diretrizes incluem apenas as áreas em que precisamos aumentar as convenções comuns com as interações do Visual Studio específicos ou locais em que podemos substituem as diretrizes inteiramente para personalizar o Visual Studio para atender às necessidades de nossos usuários sofisticados.  
  
-   [Padrões de controle comum do Visual Studio](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md)  
  
    -   [Controles comuns](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_CommonControls)  
  
    -   [Controles de texto](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_TextControls)  
  
    -   [Botões e hiperlinks](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_ButtonsAndHyperlinks)  
  
## <a name="composite-patterns"></a>Padrões compostos  
 Há várias maneiras que espera que os usuários realizem tarefas. Sempre que possível, os recursos devem ser projetados para usar esses padrões para interação e design visual.  
  
 Embora haja vários padrões compostos no Visual Studio, algumas das mais importantes com relação a consistência são:  
  
-   [Padrões compostos para o Visual Studio](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md)  
  
    -   [Interface do usuário no objeto e inspecionar](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_OnObjectUI)  
  
    -   [Modelos de seleção](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_SelectionModels)  
  
    -   [Persistência e salvar as configurações](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_PersistenceAndSavingSettings)  
  
    -   [Entrada por toque](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_TouchInput)
