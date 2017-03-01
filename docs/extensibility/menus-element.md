---
title: Elemento de menus | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- VSCT XML schema elements, Menus
- Menus element (VSCT XML schema)
ms.assetid: d825a99b-e05c-4dd9-8933-a180216d667a
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
ms.openlocfilehash: a969260e8a8db727f69dc18c29e07815bf32c2ed
ms.lasthandoff: 02/22/2017

---
# <a name="menus-element"></a>Elemento de menus
Define todos os menus e barras de ferramentas que implementa um VSPackage.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
<Menus>  
  <Menu>... </Menu>  
  <Menu>... </Menu>  
</Menus>  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|Condição|Opcional. Consulte [atributos condicionais](../extensibility/vsct-xml-schema-conditional-attributes.md).|  
  
### <a name="child-elements"></a>Elementos filho  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[Elemento de menus](../extensibility/menus-element.md)|Define todos os menus e barras de ferramentas que implementa um VSPackage.|  
|[Elemento de menu](../extensibility/menu-element.md)|Representa um único menu ou barra de ferramentas.|  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[Elemento Commands](../extensibility/commands-element.md)|Representa a coleção de comandos no VSPackage.|  
  
## <a name="example"></a>Exemplo  
  
```  
<Commands package="guidMyPackage">  
    <Menus>  
      <Menu Condition="'%(DEBUG)' != 'true'"   
        guid="cmdSetGuidMyProductCommands" id="menuIDMainMenu"   
        priority="0x0000" type="Menu">  
        <Annotation>  
          <Documentation>this is an annotation</Documentation>  
          <AppInfo>  
            <CustomData>  
              <CustomSubElement>Some data</CustomSubElement>  
            </CustomData>  
          </AppInfo>  
        </Annotation>  
        <CommandFlag>AlwaysCreate</CommandFlag>  
        <Strings>  
          <ButtonText>MainMenu</ButtonText>  
        </Strings>  
      </Menu>  
  </Menus>  
<Commands>  
```  
  
## <a name="see-also"></a>Consulte também  
 [Como os VSPackages adicionar elementos de Interface do usuário](../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [Barras de ferramentas, Menus e comandos](../extensibility/internals/commands-menus-and-toolbars.md)
