---
title: Disponibilizar comandos | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- menus [Visual Studio SDK], commands
- best practices, menu and toolbar commands
- toolbars [Visual Studio], best practices
- menu commands, best practices
ms.assetid: 3ffc4312-c6db-4759-a946-a4bb85f4a17a
caps.latest.revision: 35
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
ms.openlocfilehash: fc73e7d391dd53bb17c2c92ac800750996e3c567
ms.lasthandoff: 02/22/2017

---
# <a name="making-commands-available"></a>Disponibilizar comandos
Quando vários VSPackages são adicionados ao Visual Studio, a interface do usuário (UI) pode ficar sobrecarregada com comandos. Você pode programar seu pacote para ajudar a minimizar esse problema, da seguinte maneira:  
  
-   Programa do pacote para que ele seja carregado apenas quando um usuário exigir.  
  
-   O pacote do programa para que os comandos são exibidos somente quando elas podem ser necessárias no contexto do estado atual do ambiente de desenvolvimento integrado (IDE).  
  
## <a name="delayed-loading"></a>Carregamento atrasado  
 A forma típica para habilitar o carregamento atrasado é projetar o VSPackage, de forma que os comandos são exibidos na interface do usuário, mas o próprio pacote não será carregado até que um usuário clica em um dos comandos. Para fazer isso, no arquivo. VSCT, crie comandos com nenhum sinalizador de comando.  
  
 O exemplo a seguir mostra a definição de um comando de menu de um arquivo. VSCT. Esse é o comando que é gerado pelo modelo de pacote Visual Studio quando o **o comando de Menu** está selecionada no modelo.  
  
```xml  
<Button guid="guidTopLevelMenuCmdSet" id="cmdidTestCommand" priority="0x0100" type="Button">  
  <Parent guid="guidTopLevelMenuCmdSet" id="MyMenuGroup" />  
  <Icon guid="guidImages" id="bmpPic1" />  
  <Strings>  
    <CommandName>cmdidTestCommand</CommandName>  
    <ButtonText>Test Command</ButtonText>  
  </Strings>  
</Button>  
  
```  
  
 No exemplo, se o grupo pai, `MyMenuGroup`, é um filho de um menu de nível superior, como o **ferramentas** menu, o comando estará visível no menu, mas o pacote que executa o comando não será carregado até que o comando é clicado por um usuário. No entanto, por programação o comando para implementar o <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>interface, você pode habilitar o pacote a ser carregado quando o primeiro é expandir o menu que contém o comando.</xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>  
  
 Observe que o carregamento atrasado também pode melhorar o desempenho de inicialização.  
  
## <a name="current-context-and-the-visibility-of-commands"></a>Contexto atual e a visibilidade de comandos  
 Você pode programar comandos VSPackage seja visível ou oculto, dependendo do estado atual dos dados VSPackage ou as ações que são relevantes no momento. Você pode habilitar o VSPackage definir o estado dos seus comandos, normalmente por meio de uma implementação do <xref:EnvDTE.IDTCommandTarget.QueryStatus%2A>método a partir do <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>interface, mas isso requer o VSPackage seja carregado antes de poder executar o código.</xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> </xref:EnvDTE.IDTCommandTarget.QueryStatus%2A> Em vez disso, recomendamos que você habilite o IDE gerenciar a visibilidade dos comandos sem carregar o pacote. Para fazer isso, no arquivo. VSCT, associar comandos com um ou mais contextos de interface do usuário em especial. Nesses contextos de interface do usuário são identificados por um GUID conhecido como um *o contexto do comando GUID*.  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]monitora as alterações resultantes de ações do usuário, como carregar um projeto ou mudar de edição para construção. Quando ocorrem alterações, a aparência do IDE automaticamente é modificada. A tabela a seguir mostra quatro principais contextos do IDE alterar que [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] monitores.  
  
|Tipo de contexto|Descrição|  
|---------------------|-----------------|  
|Tipo de projeto ativo|Para a maioria dos tipos de projeto, isso `GUID` valor é o mesmo que o GUID do VSPackage que implementa o projeto. No entanto, [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] projetos usam o tipo de projeto `GUID` como o valor.|  
|Janela ativa|Normalmente, isso é a última janela do documento ativo que estabelece o contexto de interface do usuário atual para associações de teclas. No entanto, ele também pode ser uma janela de ferramenta que tem uma tabela de associação de chave que se parece com o navegador da Web interno. Para janelas de documento com várias guias, como o editor de HTML, cada guia tem um contexto diferente do comando `GUID`.|  
|Serviço de idioma ativo|O serviço de linguagem que está associado com o arquivo que está sendo exibido em um editor de texto.|  
|Janela da ferramenta ativa|Uma janela de ferramenta que é aberto e tem o foco.|  
  
 Uma área principal de contexto quinta é o estado da interface do usuário do IDE. Contextos de interface do usuário são identificados pelo contexto do comando ativo `GUID`s, da seguinte maneira:  
  
-   <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT_SolutionBuilding></xref:Microsoft.VisualStudio.VSConstants.UICONTEXT_SolutionBuilding>  
  
-   <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT_Debugging></xref:Microsoft.VisualStudio.VSConstants.UICONTEXT_Debugging>  
  
-   <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT_Dragging></xref:Microsoft.VisualStudio.VSConstants.UICONTEXT_Dragging>  
  
-   <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT_FullScreenMode></xref:Microsoft.VisualStudio.VSConstants.UICONTEXT_FullScreenMode>  
  
-   <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT_DesignMode></xref:Microsoft.VisualStudio.VSConstants.UICONTEXT_DesignMode>  
  
-   <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT_NoSolution></xref:Microsoft.VisualStudio.VSConstants.UICONTEXT_NoSolution>  
  
-   <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT_SolutionExists></xref:Microsoft.VisualStudio.VSConstants.UICONTEXT_SolutionExists>  
  
-   <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT_EmptySolution></xref:Microsoft.VisualStudio.VSConstants.UICONTEXT_EmptySolution>  
  
-   <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT_SolutionHasSingleProject></xref:Microsoft.VisualStudio.VSConstants.UICONTEXT_SolutionHasSingleProject>  
  
-   <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT_SolutionHasMultipleProjects></xref:Microsoft.VisualStudio.VSConstants.UICONTEXT_SolutionHasMultipleProjects>  
  
-   <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT_CodeWindow></xref:Microsoft.VisualStudio.VSConstants.UICONTEXT_CodeWindow>  
  
 Esses GUIDs são marcadas como ativas ou inativas, dependendo do estado atual do IDE. Vários contextos de interface do usuário podem estar ativos ao mesmo tempo.  
  
### <a name="hiding-and-displaying-commands-based-on-context"></a>Ocultando e exibindo comandos com base no contexto  
 Você pode exibir ou ocultar um comando de pacote no IDE sem carregar o pacote propriamente dito. Para fazer isso, defina o comando no arquivo. VSCT do pacote usando o `DefaultDisabled`, `DefaultInvisible`, e `DynamicVisibility` comando sinalizadores e adicionando um ou mais [VisibilityItem](../../extensibility/visibilityitem-element.md) elementos para o [VisibilityConstraints](../../extensibility/visibilityconstraints-element.md) seção. Quando um contexto do comando especificado `GUID` se torna ativo, o comando será exibido sem carregar o pacote.  
  
### <a name="custom-context-guids"></a>GUIDs de contexto personalizados  
 Se um contexto de comando apropriado que GUID não estiver definido, você pode definir um o VSPackage e, em seguida, programá-lo para ser ativos ou inativos conforme necessário para controlar a visibilidade dos seus comandos. Use o <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection>serviço:</xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection>  
  
-   Registrar os GUIDs de contexto (chamando o <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.GetCmdUIContextCookie%2A>método).</xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.GetCmdUIContextCookie%2A>  
  
-   Obter o estado de um contexto de `GUID` (chamando o <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.IsCmdUIContextActive%2A>método).</xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.IsCmdUIContextActive%2A>  
  
-   Ativar o contexto `GUID`s e desativar (chamando o <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.SetCmdUIContext%2A>método).</xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.SetCmdUIContext%2A>  
  
    > [!CAUTION]
    >  Certifique-se de que o VSPackage não afeta o estado de qualquer contexto existente GUID porque outros VSPackages pode dependem delas.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir de um comando VSPackage demonstra a visibilidade dinâmica de um comando que é gerenciado pelo contextos de comando sem carregar o VSPackage.  
  
 O comando é definido para ser habilitado e exibido sempre que existe uma solução; ou seja, sempre que um contexto do seguinte comando GUIDs está ativo:  
  
-   <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT_EmptySolution></xref:Microsoft.VisualStudio.VSConstants.UICONTEXT_EmptySolution>  
  
-   <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT_SolutionHasMultipleProjects></xref:Microsoft.VisualStudio.VSConstants.UICONTEXT_SolutionHasMultipleProjects>  
  
-   <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT_SolutionHasSingleProject></xref:Microsoft.VisualStudio.VSConstants.UICONTEXT_SolutionHasSingleProject>  
  
 No exemplo, observe que cada sinalizador de comando é um separado [comando sinalizador](../../extensibility/command-flag-element.md) elemento.  
  
```  
<Button guid="guidDynamicVisibilityCmdSet" id="cmdidMyCommand"   
        priority="0x0100" type="Button">  
  <Parent guid="guidDynamicVisibilityCmdSet" id="MyMenuGroup" />  
  <Icon guid="guidImages" id="bmpPic1" />  
  <CommandFlag>DefaultDisabled</CommandFlag>  
  <CommandFlag>DefaultInvisible</CommandFlag>  
  <CommandFlag>DynamicVisibility</CommandFlag>  
  <Strings>  
    <CommandName>cmdidMyCommand</CommandName>  
    <ButtonText>My Command name</ButtonText>  
  </Strings>  
</Button>  
  
```  
  
 Além disso, observe que cada contexto de interface do usuário deve ser fornecido em um diferente `VisibilityItem` elemento, da seguinte maneira.  
  
```xml  
<VisibilityConstraints>  
  <VisibilityItem guid="guidDynamicVisibilityCmdSet"  
                  id="cmdidMyCommand" context="UICONTEXT_EmptySolution" />  
  <VisibilityItem guid="guidDynamicVisibilityCmdSet"  
                      id="cmdidMyCommand" context="UICONTEXT_SolutionHasSingleProject" />  
  <VisibilityItem guid="guidDynamicVisibilityCmdSet"  
                  id="cmdidMyCommand" context="UICONTEXT_SolutionHasMultipleProjects" />  
</VisibilityConstraints>  
  
```  
  
## <a name="see-also"></a>Consulte também  
 [MenuCommands Vs. OleMenuCommands](../../misc/menucommands-vs-olemenucommands.md)   
 [Como os VSPackages adicionar elementos de Interface do usuário](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [Roteamento de comando em VSPackages](../../extensibility/internals/command-routing-in-vspackages.md)   
 [Adicionar itens de Menu dinamicamente](../../extensibility/dynamically-adding-menu-items.md)
