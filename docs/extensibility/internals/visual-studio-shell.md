---
title: Shell do Visual Studio | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- shell, Visual Studio
- Visual Studio, shell
ms.assetid: cb124ef4-1a6b-4bfe-bfbf-295ef9c07f36
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
ms.openlocfilehash: 77f226d17b12c97615a885457caa8bd7414872f8
ms.lasthandoff: 02/22/2017

---
# <a name="visual-studio-shell"></a>Shell do Visual Studio
O [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] shell é o principal agente de integração do [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. O shell fornece a funcionalidade necessária para habilitar os VSPackages compartilhar serviços comuns. Como o objetivo estrutural da [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] é casaco principal funcionalidade em VSPackages, o shell é uma estrutura para fornecer funcionalidade básica e suporte a comunicação entre seu componente VSPackages.  
  
## <a name="shell-responsibilities"></a>Responsabilidades do shell  
 O shell tem as seguintes responsabilidades principais:  
  
-   Elementos básicos de suporte (por meio de interfaces COM) da interface do usuário (IU). Isso inclui barras de ferramentas e menus padrão, janelas filho de interface de documentos múltiplos (MDI), ou quadros de janela de documento e quadros de janela de ferramenta e suporte de encaixe.  
  
-   Manter uma lista de todos os documentos abertos em uma tabela de documento (RDT) em execução para coordenar a persistência de documentos e a garantia de que um documento não pode ser aberto em mais de uma forma ou em formas incompatíveis.  
  
-   Suporte a interface de roteamento de comando e manipulação de comandos, `IOleCommandTarget`.  
  
-   Carregando os VSPackages em momentos apropriados. Carregamento de atraso de um VSPackage é necessário para melhorar o desempenho do shell.  
  
-   Gerenciando determinados serviços compartilhados, como <xref:Microsoft.VisualStudio.Shell.Interop.SVsShell>, que fornece a funcionalidade básica do shell, e <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>, que fornece a funcionalidade básica windowing.</xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell> </xref:Microsoft.VisualStudio.Shell.Interop.SVsShell>  
  
-   Gerenciando os arquivos de solução (. sln). Soluções conter grupos de projetos relacionados, semelhantes aos arquivos de espaço de trabalho (. dsw) no Visual C++ 6.0.  
  
-   Seleção de todo o shell de rastreamento, o contexto e moeda. O shell rastreia os seguintes tipos de itens:  
  
    -   O projeto atual  
  
    -   O item de projeto atual ou ItemID atual<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy></xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>  
  
    -   A seleção atual para o **propriedades** janela ou`SelectionContainer`  
  
    -   O contexto de interface do usuário IDs ou CmdUIGuids que controlam a visibilidade das barras de ferramentas, menus e comandos  
  
    -   Os elementos atualmente ativos, como a janela ativa, o documento e o Gerenciador de desfazer  
  
    -   Os atributos do contexto do usuário que orientam a Ajuda dinâmica  
  
 O shell também faz uma mediação comunicação entre serviços atuais e VSPackages instalados. Ele suporta os principais recursos do shell e torna disponíveis para todos os VSPackages integrados no [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Esses recursos principais incluem os seguintes itens:  
  
-   **Sobre** tela inicial e de caixa de diálogo  
  
-   **Adicionar novo e Adicionar Item existente** caixas de diálogo  
  
-   **Exibição de classe** janela e **Pesquisador de objetos**  
  
-   **Referências** caixa de diálogo  
  
-   **Estrutura de tópicos de documentos** janela  
  
-   **Ajuda dinâmica** janela  
  
-   **Localizar** e **substituir**  
  
-   **Abra o projeto** e **abrir arquivo** caixas de diálogo no **novo** menu  
  
-   **Opções de** na caixa de diálogo de **ferramentas** menu  
  
-   **Propriedades** janela  
  
-   **Gerenciador de Soluções**  
  
-   **Lista de tarefas** janela  
  
-   **Caixa de Ferramentas**  
  
## <a name="see-also"></a>Consulte também  
 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget></xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy></xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>   
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsShell></xref:Microsoft.VisualStudio.Shell.Interop.SVsShell>   
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell></xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>   
 [VSPackages](../../extensibility/internals/vspackages.md)
