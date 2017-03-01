---
title: Elemento VisibilityItem | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- VisibilityItem element (VSCT XML schema)
- VSCT XML schema elements, VisibilityItem
ms.assetid: 0932f551-972d-4194-84bb-426e3e4375e4
caps.latest.revision: 13
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
ms.openlocfilehash: bcd08be8b62685e4282ff1dfc03f78b179662398
ms.lasthandoff: 02/22/2017

---
# <a name="visibilityitem-element"></a>Elemento VisibilityItem
O `VisibilityItem` elemento determina a visibilidade estática de comandos e barras de ferramentas. Cada entrada identifica um comando ou menu e um contexto de interface do usuário de comando associado. O Visual Studio detecta comandos, menus e barras de ferramentas e sua visibilidade, sem carregar os VSPackages que defini-los. O IDE usa o <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.IsCmdUIContextActive%2A>método para determinar se um contexto de interface do usuário do comando está ativo.</xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.IsCmdUIContextActive%2A>  
  
 Após o VSPackage é carregado, o Visual Studio espera visibilidade de comando seja determinado por VSPackage em vez de `VisibilityItem`. Para determinar a visibilidade do comando, você pode implementar o <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.BeforeQueryStatus>manipulador de eventos ou o <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A>método, dependendo de como você implementou o comando.</xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> </xref:Microsoft.VisualStudio.Shell.OleMenuCommand.BeforeQueryStatus>  
  
 Um comando ou um menu que tem um `VisibilityItem` elemento aparece apenas quando o contexto associado está ativo. Você pode associar um único comando, um menu ou barra de ferramentas com um ou mais contextos de interface do usuário de comando, incluindo uma entrada para cada combinação de contexto do comando. Se um menu ou comando estiver associado a vários contextos de interface do usuário de comando, em seguida, o comando ou o menu é visível quando qualquer um dos contextos de interface do usuário de comando associado está ativo.  
  
 O `VisibilityItem` elemento se aplica apenas aos comandos, menus e barras de ferramentas, não a grupos. Um elemento que não tem um relacionados `VisibilityItem` elemento estará visível sempre que o menu pai está ativo.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
<VisibilityItem  
  guid ="="cmdGuidMyProductCommands"  
  id=="cmdidAddWidget"  
  context="guidNotViewSourceMode"/>  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|GUID|Necessário. O GUID do identificador do comando GUID/ID.|  
|id|Necessário. A ID do identificador do comando GUID/ID.|  
|contexto|Necessário. O contexto de interface do usuário no qual o comando é visível.|  
|Condição|Opcional. Consulte [atributos condicionais](../extensibility/vsct-xml-schema-conditional-attributes.md).|  
  
### <a name="child-elements"></a>Elementos filho  
 Nenhum  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[Elemento VisibilityConstraints](../extensibility/visibilityconstraints-element.md)|O `VisibilityConstraints` elemento determina a visibilidade estática de grupos de comandos e barras de ferramentas.|  
  
## <a name="remarks"></a>Comentários  
 Os contextos de IU do Visual Studio padrão são definidos na *caminho de instalação do SDK do Visual Studio*\VisualStudioIntegration\Common\Inc\vsshlids.h arquivo, bem como na <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids>e <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids80>classes.</xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids80> </xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids> Um conjunto mais completo de contextos de interface do usuário é definido na <xref:Microsoft.VisualStudio.VSConstants>classe.</xref:Microsoft.VisualStudio.VSConstants>  
  
## <a name="example"></a>Exemplo  
  
```  
<VisibilityConstraints>  
  <VisibilityItem guid="cmdSetGuidMyProductCommands"     id="cmdidAddWidget"  
    context="guidNotViewSourceMode"/>  
</VisibilityConstraints>  
```  
  
## <a name="see-also"></a>Consulte também  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.IsCmdUIContextActive%2A></xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.IsCmdUIContextActive%2A>   
 <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.BeforeQueryStatus></xref:Microsoft.VisualStudio.Shell.OleMenuCommand.BeforeQueryStatus>   
 <xref:Microsoft.VisualStudio.VSConstants></xref:Microsoft.VisualStudio.VSConstants>   
 <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids></xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids>   
 <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids80></xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids80>   
 [Elemento VisibilityConstraints](../extensibility/visibilityconstraints-element.md)   
 [Tabela de comando do Visual Studio (. Arquivos de VSCT)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
