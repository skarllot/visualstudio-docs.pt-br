---
title: Hierarquia de Chamada | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VS.CallHierarchy
helpviewer_keywords:
- Call Hierarchy
ms.assetid: c55bda01-d7de-4823-8f9a-1bcc37dbb74a
caps.latest.revision: 40
author: kempb
ms.author: kempb
manager: ghogen
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
translationtype: Human Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 952364e6c72b66ab8a534884c8c299561f9fd3b5
ms.lasthandoff: 02/22/2017

---
# <a name="call-hierarchy"></a>Hierarquia de chamadas
A Hierarquia de Chamada permite navegar pelo seu código exibindo todas as chamadas de e para um método, propriedade ou construtor selecionado. Isso permite compreender melhor como o código flui, bem como avaliar os efeitos das alterações no código. Você pode examinar vários níveis de código para exibir cadeias complexas de chamadas de método e pontos de entrada adicionais para o código, o que permite explorar todos os caminhos de execução possíveis.  
  
 A Hierarquia de Chamada está disponível em tempo de design, diferente da pilha de chamadas que é exibida pelo depurador.  
  
## <a name="using-call-hierarchy"></a>Usando a Hierarquia de Chamada  
 Para exibir a janela **Hierarquia de Chamada**, clique com o botão direito do mouse no nome de um método, propriedade ou chamada de construtor e, em seguida, clique em **Exibir Hierarquia de Chamada**.  
  
 O nome do membro é exibido em um painel de modo de exibição de árvore na janela **Hierarquia de Chamada**. Se você expandir o nó membro, os subnós **Chamadas para***nome do membro* e **Chamadas de***nome do membro* serão exibidos. A ilustração a seguir mostra esses nós na janela **Hierarquia de Chamada**.  
  
 ![Hierarquia de Chamada com um nó aberto](../../ide/reference/media/onenode.png "OneNode")  
Janela de Hierarquia de Chamada  
  
-   Se você expandir o nó **Chamadas para**, todos os membros que chamam o membro selecionado serão exibidos.  
  
-   Se você expandir o nó **Chamadas de**, todos os membros que são chamados pelo membro selecionado serão exibidos.  
  
 Você pode, então, expandir cada um dos membros desses subnós em nós **Chamadas para** e **Chamadas de**. Isso permite navegar pela pilha de chamadores, conforme mostrado na ilustração a seguir.  
  
 ![Hierarquia de Chamada com vários nós abertos](../../ide/media/multiplenodes.png "MultipleNodes")  
Janela de Hierarquia de Chamada  
  
 Para membros definidos como virtuais ou abstratos, um nó **Substitui o nome do método** é exibido. Para membros de interface, um nó **Implementa o nome do método** é exibido. Esses nós expansíveis aparecem no mesmo nível que os nós **Chamadas para** e **Chamadas de**.  
  
 A caixa **Escopo da Pesquisa** na barra de ferramentas contém opções para **Minha Solução**, **Projeto Atual** e **Documento Atual**.  
  
 Quando você seleciona um membro filho no painel do modo de exibição de árvore **Hierarquia de Chamada**:  
  
-   O painel de detalhes **Hierarquia de Chamada** exibe todas as linhas de código em que esse membro filho é chamado pelo membro pai.  
  
-   A **Janela de Definição de Código**, se estiver aberta, exibe o código do membro selecionado. Esta janela está disponível em C# e C++. Para obter mais informações sobre a janela, consulte [Exibindo a estrutura do código](../../ide/viewing-the-structure-of-code.md).  
  
> [!NOTE]
>  A Hierarquia de Chamada não encontra referências do grupo ao método, que incluem os locais a que um método é adicionado como manipulador de eventos ou é atribuído a um delegado. Para localizar todas as referências a um método, você pode usar o comando **Localizar Todas as Referências**.  
  
## <a name="shortcut-menu-items"></a>Itens do menu de atalho  
 A tabela a seguir descreve várias opções de menu de atalho que são disponibilizadas quando você clica com o botão direito do mouse em um nó no painel do modo de exibição de árvore.  
  
|Item de menu de contexto|Descrição|  
|-----------------------|-----------------|  
|**Adicionar como Nova Raiz**|Adiciona o nó selecionado ao painel do modo de exibição de árvore como um novo nó raiz. Isso permite concentrar sua atenção em uma subárvore específica.|  
|**Remover Raiz**|Remove o nó raiz selecionado do painel do modo de exibição de árvore. Esta opção está disponível somente de um nó raiz.<br /><br /> Você também pode usar o botão de barra de ferramentas **Remover Raiz** para remover o nó raiz selecionado.|  
|**Ir para Definição**|Executa o comando Ir para Definição no nó selecionado. Isso leva até a definição original de uma chamada de membro ou definição de variável.<br /><br /> Para executar o comando Ir para Definição, você também pode clicar duas vezes no nó selecionado ou pressionar F12 no nó selecionado.|  
|**Localizar Todas as Referências**|Executa o comando Localizar Todas as Referências no nó selecionado. Isso localiza todas as linhas de código em seu projeto que fazem referência a uma classe ou membro.<br /><br /> Também é possível usar SHIFT + F12 para executar o comando Localizar Todas as Referências no nó selecionado.|  
|**Copiar**|Copia o conteúdo do nó selecionado (mas não de seus subnós).|  
|**Atualizar**|Recolhe o nó selecionado de forma que expandi-lo novamente exibe informações atualizadas.|
