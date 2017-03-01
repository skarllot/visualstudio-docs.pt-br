---
title: Estendendo e personalizando as janelas de ferramentas | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- user interfaces, essentials
- tool windows, standard
ms.assetid: 46b2892e-7b2b-4b3f-83a7-b884f1e114ee
caps.latest.revision: 20
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
ms.openlocfilehash: 6595a36af13eb2c54ef0096ca0cc93f2a63c7053
ms.lasthandoff: 02/22/2017

---
# <a name="extending-and-customizing-tool-windows"></a>Estendendo e personalizando janelas de ferramenta
Visual Studio fornece vários tipos diferentes de janelas, por exemplo, janelas de ferramentas, janelas de documento e janelas de diálogo. Outras janelas, como a janela Propriedades, a janela de saída e a janela lista de tarefas, são tipos de janelas de ferramenta.  
  
## <a name="tool-windows"></a>Janelas de Ferramentas  
 Janelas de ferramentas do Visual Studio são geralmente somente leitura windows que não são baseados em arquivo. Nesse diferem de janelas de documento, quais arquivos são exibidos no modo de leitura / gravação. O **Toolbox**, **Solution Explorer**, **propriedades** janela, e **navegador da Web** são exemplos de janelas de ferramenta.  
  
 Para saber como criar uma janela de ferramentas simples, consulte [adicionando uma janela da ferramenta](../extensibility/adding-a-tool-window.md).  
  
 Para registrar uma janela de ferramenta com o Visual Studio, consulte [registrando uma janela da ferramenta](../extensibility/registering-a-tool-window.md).  
  
 Janelas de ferramenta são a única instância por padrão, que significa que apenas uma instância da janela de ferramenta pode ser aberto por vez. Depois que uma janela de ferramenta de instância única é aberta, ela permanecerá aberta até que o IDE seja fechado. Quando você fecha uma janela da ferramenta de instância única, altera somente sua visibilidade. Você também pode criar várias instâncias janelas de ferramentas, que várias instâncias da janela podem ser abertas simultaneamente. Consulte [criar uma janela de ferramenta várias instâncias](../extensibility/creating-a-multi-instance-tool-window.md) para obter mais informações.  
  
 Janelas de ferramenta podem ser *dinâmico*, que significa que eles são visíveis sempre que seu contexto de interface do usuário relacionado se aplica. O uso de visibilidade automática pode reduzir a desordem das janelas do IDE. Para obter mais informações, consulte [abrir uma janela de ferramenta dinâmico](../extensibility/opening-a-dynamic-tool-window.md).  
  
 Janelas de ferramentas podem ser encaixada, flutuante ou com guias na estrutura do documento. O quadro de janela de ferramenta é fornecido pelo IDE e é usado para controlar o tamanho, local, estado de encaixe e outras propriedades persistentes. O painel da janela de ferramenta exibe o conteúdo. O tamanho e local padrão se aplicam somente quando a janela da ferramenta é aberto pela primeira vez; Depois que o estado de janela de ferramenta é mantido.  
  
 Painéis de janela de ferramenta podem hospedar controles de usuário do WPF e barras de ferramentas de suporte. Você pode substituir o <xref:Microsoft.VisualStudio.Shell.WindowPane.Window%2A>propriedade para retornar o identificador do controle hospedado.</xref:Microsoft.VisualStudio.Shell.WindowPane.Window%2A>  
  
 Você pode adicionar muitos recursos diferentes para janelas de ferramenta. Por exemplo, você pode adicionar uma barra de ferramentas: [adicionar uma barra de ferramentas para uma janela de ferramenta](../extensibility/adding-a-toolbar-to-a-tool-window.md) ou um menu de atalho: [adicionar um Menu de atalho em uma janela de ferramenta](../extensibility/adding-a-shortcut-menu-in-a-tool-window.md). Você pode adicionar um controle de pesquisa que permite que você pesquise itens dentro de sua janela de ferramentas: [adicionando pesquisa a uma janela de ferramenta](../extensibility/adding-search-to-a-tool-window.md).  
  
 Você pode assinar eventos de janela de ferramenta: [inscrever-se em um evento](../extensibility/subscribing-to-an-event.md).  
  
## <a name="extending-existing-tool-windows"></a>Estendendo as janelas de ferramentas existente  
 Você pode adicionar informações sobre a janela de ferramenta para um novo **opções** página e uma nova configuração no **propriedades** página, escreva para a **lista de tarefas** e **saída** windows. Para obter mais informações, consulte [estendendo a propriedades, lista de tarefas, saída e opções Windows](../extensibility/extending-the-properties-task-list-output-and-options-windows.md) e [estendendo a propriedades, lista de tarefas, saída e opções Windows](../extensibility/extending-the-properties-task-list-output-and-options-windows.md).  
  
## <a name="modal-dialog-boxes"></a>Caixas de diálogo modais  
 Em uma extensão do Visual Studio, você deve criar caixas de diálogo modais derivando de <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow?displayProperty=fullName>, que permite que você controle e o restante da interface do usuário.</xref:Microsoft.VisualStudio.PlatformUI.DialogWindow?displayProperty=fullName> Para obter mais informações, consulte. [Criar e gerenciar caixas de diálogo modais](../extensibility/creating-and-managing-modal-dialog-boxes.md).  
  
## <a name="see-also"></a>Consulte também  
 [Criando uma extensão com uma janela de ferramentas](../extensibility/creating-an-extension-with-a-tool-window.md)
