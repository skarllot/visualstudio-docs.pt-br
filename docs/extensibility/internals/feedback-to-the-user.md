---
title: "Comentários para o usuário | Documentos do Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- user model feedback
- environment, context
- IDE, context
- IDE, user feedback
ms.assetid: 2d472a24-3813-4f5f-9783-b491ad8a71ad
caps.latest.revision: 8
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
ms.openlocfilehash: 97de9bc43eeec693f575e17e53ca155ae9e0bb38
ms.lasthandoff: 02/22/2017

---
# <a name="feedback-to-the-user"></a>Comentários para o usuário
No [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ambiente de desenvolvimento integrado (IDE), feedback visual sobre funcionalidade disponível é com base na seleção atual do usuário e o contexto de seleção global. A tabela a seguir lista a funcionalidade que está disponível em contextos diferentes de seleção.  
  
|Contexto de seleção|Funcionalidade disponível|  
|-----------------------|-----------------------------|  
|IDE|Global|  
|Conjunto de produtos atual|Específico do produto|  
|Hierarquia ativa|Hierarquia de tipo específico|  
|Item de hierarquia ativa|Específico de tipo de item de hierarquia|  
|Documento ativo|Tipo de documento específico|  
|Janela de nível superior interface de documentos múltiplos (MDI)|Tipo de janela específicas|  
|Contexto da seleção atual|Contexto de seleção específico|  
  
 Se você apenas surgir a funcionalidade que os usuários precisam e fornecem continuamente seleção consistente e comentários de contexto do ambiente, você pode reduzir a complexidade no IDE. As seguintes regras se aplicam sempre que uma janela é aberta no IDE:  
  
-   Se a janela muda seu contexto de seleção, comentários de seleção está indicado claramente na janela e a janela Ajuda dinâmica, se exibida, é atualizada para refletir o contexto atual.  
  
-   Se a janela altera o contexto de seleção global, todos os menus de contexto específico, a janela hierarquia ativa e a barra de título do aplicativo são atualizados para refletir o contexto atual.  
  
-   A janela deve emergir propriedades para a seleção atual no **propriedades** janela e, opcionalmente, se exibida, o **páginas de propriedade** caixa de diálogo.  
  
-   Se a janela Propriedades de superfície não ou alterar o contexto de seleção global, comentários de seleção não devem permanecer na janela quando não é mais a janela ativa no IDE.  
  
-   Todas as janelas de ferramenta específica do documento continuamente devem refletir o documento ativo.  
  
-   Menus, barras de ferramentas e a barra de título do aplicativo devem refletir a janela superior interface documentos múltiplos (MDI) do cliente.  
  
 Por exemplo, quando o modo de exibição HTML de um formulário da Web dentro de um projeto de aplicativo Web do Visual Basic é aberto e o usuário seleciona um `<td>` marca, os comentários são fornecidos da seguinte maneira:  
  
-   Seleção é indicada na janela ativa e refletida no **propriedades** janela.  
  
-   Específicos do documento **Toolbox** é atualizado para refletir o documento ativo.  
  
-   O **Editor** barra de ferramentas e **tabela** menu são exibidas e a barra de título será atualizado para refletir a janela de formulário da Web.  
  
-   A janela hierarquia ativa, que é normalmente **Solution Explorer**e sua atualização de barra de título para refletir o contexto atual e o contextual **projeto** comandos de menu agora se aplicam ao projeto de aplicativo Web ativo.  
  
## <a name="see-also"></a>Consulte também  
 [Seleção e moeda no IDE](../../extensibility/internals/selection-and-currency-in-the-ide.md)   
 [Objetos de contexto da seleção](../../extensibility/internals/selection-context-objects.md)   
 [Seleção e hierarquias](../../extensibility/internals/hierarchies-and-selection.md)
