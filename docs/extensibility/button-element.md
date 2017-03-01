---
title: "Elemento de botão | Documentos do Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Buttons element (VSCT XML schema)
- VSCT XML schema elements, Buttons
ms.assetid: 96dccf51-2b00-4700-9d28-924b34c21ecd
caps.latest.revision: 11
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
ms.sourcegitcommit: 96b60af0e81a51b557d53c9f2bcfae9888db9640
ms.openlocfilehash: 8effd186d86cab3fcccbd2af2edcf37569e066cf
ms.lasthandoff: 02/22/2017

---
# <a name="button-element"></a>Elemento de botão
Define um elemento que o usuário pode interagir com. Botões podem ser de tipos diferentes: botão, o botão de menu e SplitDropDown.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
<Button guid="guidMyCommandSet" id="MyCommand" priority="0x102" type="button">  
  <Parent>... </Parent>  
  <Icon>... </Icon>  
  <CommandFlag>... </CommandFlag>  
  <Strings>... </Strings>  
</Button>  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|GUID|Necessário. GUID do identificador do comando GUID/ID.|  
|id|Necessário. ID do identificador do comando GUID/ID.|  
|priority|Opcional. Um valor numérico que especifica a prioridade.|  
|tipo|Opcional. Um valor enumerado que especifica o tipo de botão.<br /><br /> Se não especificado, usa o botão.<br /><br /> Botão<br /> Um comando padrão que aparece na barra de ferramentas (normalmente como um botão icônico), menus e menus de contexto.<br /><br /> Botão de menu<br /> Um item de menu que não executar um comando, mas produz outro menu.<br /><br /> SplitDropDown<br /> Controles, como os botões Desfazer e refazer na barra de ferramentas no Microsoft Word.|  
|Condição|Opcional. Consulte [atributos condicionais](../extensibility/vsct-xml-schema-conditional-attributes.md).|  
  
### <a name="child-elements"></a>Elementos filho  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[Elemento pai](../extensibility/parent-element.md)|Opcional. O elemento pai do botão.|  
|[Elemento de ícone](../extensibility/icon-element.md)|Opcional. O ícone associado ao botão.|  
|[Elemento de sinalizador de comando](../extensibility/command-flag-element.md)|Necessário. Os valores válidos de CommandFlag para um botão são da seguinte maneira.<br /><br /> -AllowParams<br /><br /> -CommandWellOnly<br /><br /> -DefaultDisabled<br /><br /> -DefaultInvisible<br /><br /> -DontCache<br /><br /> -DynamicItemStart<br /><br /> -DynamicVisibility<br /><br /> -FixMenuController<br /><br /> -IconAndText<br /><br /> -NoButtonCustomize<br /><br /> -NoCustomize<br /><br /> -NoKeyCustomize<br /><br /> -NoShowOnMenuController<br /><br /> -Pict<br /><br /> -PostExec<br /><br /> -ProfferedCmd<br /><br /> -RouteToDocs<br /><br /> -TextCascadeUseBtn<br /><br /> -TextMenuUseButton<br /><br /> -TextoAltera<br /><br /> -TextChangesButton<br /><br /> -TextContextUseButton<br /><br /> -TextMenuCtrlUseMenu<br /><br /> -TextMenuUseButton<br /><br /> -TextOnly|  
|[Elemento de cadeias de caracteres](../extensibility/strings-element.md)|Necessário. O filho [ButtonText elemento](../extensibility/buttontext-element.md) deve ser definido.|  
|Anotação|Comentário opcional.|  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[Elemento de botões](../extensibility/buttons-element.md)|Agrupa elementos Button.|  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir define um botão em um arquivo. VSCT.  

 ```xml
<Button guid="guidMenuTextCmdSet" id="cmdidMyCommand" priority="0x0100" type="Button">
    <Parent guid="guidMenuTextCmdSet" id="MyMenuGroup" />
    <Icon guid="guidImages" id="bmpPic1" />
    <CommandFlag>TextChanges</CommandFlag>
    <Strings>
          <CommandName>cmdidMyCommand</CommandName>
          <ButtonText>My Command name</ButtonText>
    </Strings>
</Button>
 ```
 
## <a name="see-also"></a>Consulte também  
 [Tabela de comando do Visual Studio (. Arquivos de VSCT)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
