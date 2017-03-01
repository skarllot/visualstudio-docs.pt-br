---
title: Elemento UsedCommand | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- UsedCommands element (VSCT XML schema)
- VSCT XML schema elements, UsedCommands
ms.assetid: 99cd05d3-644a-42ff-b289-8458cd1b20c0
caps.latest.revision: 10
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
ms.openlocfilehash: 1717061000acd21a864c29d58496546195b5dbb3
ms.lasthandoff: 02/22/2017

---
# <a name="usedcommand-element"></a>Elemento UsedCommand
Permite que um VSPackage acessem um comando que é definido em outro arquivo. VSCT. Por exemplo, se o VSPackage usa o padrão de **cópia** comando, que é definido como o [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] shell, você pode adicionar o comando a um menu ou barra de ferramentas sem implementá-lo novamente.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
<UsedCommand guid="guidMyCommandGroup" id="MyCommand" />  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|GUID|Necessário. O GUID do par identificação GUID que identifica o comando.|  
|id|Necessário. A ID do par identificação GUID que identifica o comando.|  
|Condição|Opcional. Consulte [atributos condicionais](../extensibility/vsct-xml-schema-conditional-attributes.md).|  
  
### <a name="child-elements"></a>Elementos filho  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|Nenhum||  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[Elemento UsedCommands](../extensibility/usedcommands-element.md)|Agrupa elementos de UsedCommand e outros UsedCommands agrupamentos.|  
  
## <a name="remarks"></a>Comentários  
 Adicionando um comando para o `<UsedCommands>` elemento, um VSPackage informa o [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ambiente VSPackage requer o comando. Você deve adicionar um `<UsedCommand>` elemento para qualquer comando que o pacote requer que não pode ser incluído em todas as versões e as configurações do Visual Studio. Por exemplo, se seu pacote chama um comando que é específico para o Visual C++, o comando não estará disponível para usuários do Visual Web Developer, a menos que você incluir um `<UsedCommand>` elemento para o comando.  
  
## <a name="example"></a>Exemplo  
  
```  
<UsedCommands>  
  <UsedCommand guid="guidVSStd97" id="cmdidCut"/>  
  <UsedCommand guid="guidVSStd97" id="cmdidCopy"/>  
  <UsedCommand guid="guidVSStd97" id="cmdidPaste"/>  
</UsedCommands>  
```  
  
## <a name="see-also"></a>Consulte também  
 [Elemento UsedCommands](../extensibility/usedcommands-element.md)   
 [Tabela de comando do Visual Studio (. Arquivos de VSCT)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
