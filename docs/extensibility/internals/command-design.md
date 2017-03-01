---
title: Design de comando | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- commands
- commands, implementation
ms.assetid: 097108c3-f758-4b87-89d6-b32d12d9041a
caps.latest.revision: 34
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
ms.openlocfilehash: 105ef485b616027413cfea5799c1d452f30a5d0b
ms.lasthandoff: 02/22/2017

---
# <a name="command-design"></a>Design de comando
Quando você adicionar um comando a um VSPackage, você deve especificar onde é exibido quando ela está disponível e como deve ser tratado.  
  
## <a name="defining-commands"></a>Definindo comandos  
 Para definir novos comandos, inclua um arquivo de tabela de comando do Visual Studio (VSCT) em seu projeto de VSPackage. Se você tiver criado um VSPackage usando o modelo de pacote do Visual Studio, o projeto inclui um desses arquivos. Para obter mais informações, consulte [tabela de comando do Visual Studio (. Arquivos VSCT)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md).  
  
 Visual Studio mescla todos os arquivos. VSCT encontrar para que ele possa exibir os comandos. Como esses arquivos são distintos de VSPackage binário, Visual Studio não precisa carregar o pacote para localizar os comandos. Para obter mais informações, consulte [como VSPackages adicionar elementos Interface do usuário](../../extensibility/internals/how-vspackages-add-user-interface-elements.md).  
  
 O Visual Studio usa o <xref:Microsoft.VisualStudio.Shell.ProvideMenuResourceAttribute>atributo de registro para definir recursos do menu e comandos.</xref:Microsoft.VisualStudio.Shell.ProvideMenuResourceAttribute> Para obter mais informações, consulte [implementação](../../extensibility/internals/command-implementation.md).  
  
 Comandos podem ser alterados em tempo de execução de várias maneiras diferentes. Podem ser exibidos ou ocultos, habilitados ou desabilitados. Eles podem exibir texto diferente ou ícones ou contêm valores diferentes. Uma grande quantidade de personalização pode ser executada antes que o Visual Studio carregará o VSPackage. Para obter mais informações, consulte [como VSPackages adicionar elementos Interface do usuário](../../extensibility/internals/how-vspackages-add-user-interface-elements.md).  
  
## <a name="command-handlers"></a>Manipuladores de comandos  
 Quando você cria um comando, você deve fornecer um manipulador de eventos para executar o comando. Se o usuário seleciona o comando, ele deve ser roteado adequadamente. Roteamento de um comando significa enviá-la para o VSPackage correto para habilitar ou desabilitá-lo, ocultar ou exibi-lo e executá-lo se o usuário optar por fazer isso. Para obter mais informações, consulte [roteamento algoritmo](../../extensibility/internals/command-routing-algorithm.md).  
  
## <a name="the-visual-studio-command-environment"></a>Ambiente de comando do Visual Studio  
 Visual Studio pode hospedar qualquer número de VSPackages, e cada uma pode contribuir com seu próprio conjunto de comandos. O ambiente exibe somente os comandos que são adequados à tarefa atual. Para obter mais informações, consulte [disponibilidade](../../extensibility/internals/command-availability.md) e [seleção de objetos de contexto](../../extensibility/internals/selection-context-objects.md).  
  
 Um VSPackage que define novos comandos, menus, barras de ferramentas ou menus de atalho fornece suas informações de comando para o Visual Studio no momento da instalação por meio de entradas do registro que fazem referência a recursos em assemblies nativos ou gerenciados. Cada recurso, em seguida, faz referência a um arquivo de recurso (.cto) de dados binários, que é gerado quando você compila um arquivo da tabela de comando do Visual Studio (VSCT). Isso permite que o Visual Studio fornecer conjuntos de comandos mesclada, menus e barras de ferramentas sem precisar carregar cada VSPackage instalado.  
  
### <a name="command-organization"></a>Organização de comando  
 O ambiente posiciona comandos de menu, prioridade e grupo.  
  
-   Grupos são coleções lógicas de comandos relacionados, por exemplo, o **Recortar**, **cópia**, e **colar** grupo de comandos. Grupos são os comandos que aparecem nos menus.  
  
-   A prioridade determina a ordem na qual os comandos individuais em um grupo aparecem no menu.  
  
-   Menus atuam como contêineres para grupos.  
  
 O ambiente predefine alguns comandos, grupos e menus. Para obter mais informações, consulte [comando padrão, o grupo e o posicionamento da barra de ferramentas](../../extensibility/internals/default-command-group-and-toolbar-placement.md).  
  
 Um comando pode ser atribuído a um grupo primário. O grupo primário controla a posição do comando na estrutura do menu principal e no **personalizar** caixa de diálogo. Um comando pode aparecer em vários grupos; Por exemplo, um comando pode ser no menu principal, um menu de atalho e uma barra de ferramentas. Para obter mais informações, consulte [como VSPackages adicionar elementos Interface do usuário](../../extensibility/internals/how-vspackages-add-user-interface-elements.md).  
  
### <a name="command-routing"></a>Roteamento de comando  
 O processo de invocação e roteamento de comandos para VSPackages difere do processo de chamar métodos em instâncias de objeto.  
  
 O ambiente de rotas de comandos em sequência do contexto interno de comando (local), que é baseado na seleção atual, ao contexto mais externo (global). O contexto primeiro que é capaz de executar o comando é aquela que lida com isso. Para obter mais informações, consulte [roteamento algoritmo](../../extensibility/internals/command-routing-algorithm.md).  
  
 Na maioria dos casos, o ambiente manipula comandos usando o <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>interface.</xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> Como o esquema de roteamento de comando permite que vários objetos diferentes lidar com os comandos, <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>pode ser implementada por qualquer número de objetos; eles incluem controles Microsoft ActiveX, implementações do modo de exibição de janela, objetos de documento, hierarquias de projeto e objetos de VSPackage (para comandos globais).</xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> Em alguns casos especializados, por exemplo, roteamento comandos em uma hierarquia, o <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>interface deve ser implementada.</xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>  
  
## <a name="related-topics"></a>Tópicos relacionados  
  
|Título|Descrição|  
|-----------|-----------------|  
|[Implementação](../../extensibility/internals/command-implementation.md)|Descreve como implementar comandos em um VSPackage.|  
|[Disponibilidade](../../extensibility/internals/command-availability.md)|Descreve como o contexto do Visual Studio determina quais comandos estão disponíveis.|  
|[Algoritmo de roteamento](../../extensibility/internals/command-routing-algorithm.md)|Descreve como a arquitetura de roteamento de comando do Visual Studio permite que comandos sejam tratadas por diferentes VSPackages.|  
|[Diretrizes de posicionamento](../../extensibility/internals/command-placement-guidelines.md)|Sugere como posicionar os comandos no ambiente do Visual Studio.|  
|[Como os VSPackages adicionar elementos de Interface do usuário](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)|Descreve como os VSPackages pode utilizar melhor a arquitetura de comando do Visual Studio.|  
|[Comando padrão, o grupo e o posicionamento da barra de ferramentas](../../extensibility/internals/default-command-group-and-toolbar-placement.md)|Descreve como os VSPackages pode usar melhor os comandos que estão incluídos no Visual Studio.|  
|[Gerenciando os VSPackages](../../extensibility/managing-vspackages.md)|Descreve como o Visual Studio carregará os VSPackages.|  
|[Tabela de comando do Visual Studio (. Arquivos de VSCT)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)|Fornece informações sobre arquivos. VSCT baseado em XML, que são usados para descrever o layout e a aparência de comandos no VSPackages.|
