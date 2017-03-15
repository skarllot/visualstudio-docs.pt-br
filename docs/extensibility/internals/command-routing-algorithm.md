---
title: Algoritmo de roteamento de comando | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- commands, routing
- command routing
ms.assetid: 998b616b-bd08-45cb-845f-808efb8c33bc
caps.latest.revision: 9
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
ms.openlocfilehash: e04e820b2d906af8264d7e8a6ba2fc2cc6dbd228
ms.lasthandoff: 02/22/2017

---
# <a name="command-routing-algorithm"></a>Algoritmo de roteamento de comando
No Visual Studio comandos são tratados por um número de diferentes componentes. Comandos são roteados do contexto interno, que é baseado na seleção atual, ao contexto mais externo (também conhecido como global). Para obter mais informações, consulte [disponibilidade](../../extensibility/internals/command-availability.md).  
  
## <a name="order-of-command-resolution"></a>Ordem de resolução de comando  
 Comandos são passados para os seguintes níveis de contexto do comando:  
  
1.  Suplementos: O ambiente primeiro oferece o comando para quaisquer suplementos que estão presentes.  
  
2.  Comandos de prioridade: esses comandos são registrados usando <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterPriorityCommandTarget>.</xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterPriorityCommandTarget> Eles são chamados para cada comando no Visual Studio e são chamados na ordem em que eles foram registrados.  
  
3.  Comandos de menu de contexto: um comando localizado em um menu de contexto é oferecido pela primeira vez para o destino do comando que é fornecido no menu de contexto e, depois disso para o roteamento típica.  
  
4.  Barra de ferramentas definir destinos de comando: esses destinos de comando são registrados quando você chama <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell4.SetupToolbar2%2A>.</xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell4.SetupToolbar2%2A> O `pCmdTarget` parâmetro pode ser `null`. Se não for `null`, então esse destino de comando é usado para atualizar quaisquer comandos localizados na barra de ferramentas que você está configurando. Se o shell está configurando sua barra de ferramentas, ele passa o quadro de janela como o `pCmdTarget` para que todas as atualizações para os comandos em seu fluxo de barra de ferramentas por meio do quadro de janela, mesmo quando ele não estiver em foco.  
  
5.  Janela de ferramenta: Ferramenta windows, que normalmente implementam os <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane>interface, também deve implementar o <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>interface para que o Visual Studio pode obter o destino do comando quando a janela da ferramenta é a janela ativa.</xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> </xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane> No entanto, se a janela da ferramenta que tem foco é a **projeto** janela e, em seguida, o comando é roteado para o <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>interface é o pai comum dos itens selecionados.</xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> Se esta seleção se estender por vários projetos, o comando é roteado para o <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution>hierarquia.</xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution> O <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>interface contém o <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A>e <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.ExecCommand%2A>métodos semelhantes para os comandos correspondentes no <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>interface.</xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> </xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.ExecCommand%2A> </xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A> </xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>  
  
6.  Janela de documento: Se o comando tem o sinalizador RouteToDocs definido em seu arquivo. VSCT, Visual Studio procura por um destino de comando no objeto de exibição de documento, que é uma instância de um <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane>interface ou uma instância de um objeto de documento (normalmente um <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines>interface ou um <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>interface).</xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> </xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines> </xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane> Se o objeto de exibição de documento não dá suporte para o comando, o Visual Studio encaminha o comando para o <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>interface retornado.</xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> (Isso é uma interface opcional para objetos de dados de documento).  
  
7.  Hierarquia atual: A hierarquia atual pode ser o projeto que possui a janela de documento ativa ou a hierarquia selecionada em **Solution Explorer**. O Visual Studio procura o <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>interface implementada na hierarquia atual ou ativa.</xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> A hierarquia deve oferecer suporte a comandos válidos sempre que a hierarquia está ativa, mesmo se uma janela de documento de um item de projeto tem o foco. No entanto, comandos que se aplicam somente quando **Solution Explorer** tem foco deve ter suporte usando o <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>interface e sua <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A>e <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.ExecCommand%2A>métodos.</xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.ExecCommand%2A> </xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A> </xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>  
  
     **Recortar**, **cópia**, **colar**, **excluir**, **Renomear**, **Enter**, e **DoubleClick** comandos exigem tratamento especial. Para obter informações sobre como lidar com **excluir** e **remover** comandos em hierarquias, consulte o <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyDeleteHandler>interface.</xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyDeleteHandler>  
  
8.  Global: Se um comando não foi tratado pelos contextos mencionados anteriormente, o Visual Studio tentará roteá-los para o VSPackage que possui um comando que implementa o <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>interface.</xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> Se o VSPackage já não foi carregado, ele não será carregado quando o Visual Studio chama o <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A>método.</xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> O VSPackage é carregado apenas quando o <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A>método é chamado.</xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A>  
  
## <a name="see-also"></a>Consulte também  
 [Design de comando](../../extensibility/internals/command-design.md)
