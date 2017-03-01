---
title: Comandos elemento | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- Commands
helpviewer_keywords:
- Commands element (VSCT XML schema)
- VSCT XML schema elements, Commands
ms.assetid: 47cf16a5-d78b-452e-86f6-b5893856dddf
caps.latest.revision: 17
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
ms.openlocfilehash: e66a26c1be307d1bdc0ad89e060db04e29747951
ms.lasthandoff: 02/22/2017

---
# <a name="commands-element"></a>Elemento Commands
Representa a coleção de comandos na barra de ferramentas VSPackage. A coleção pode ter até cinco subseções, da seguinte maneira: grupos, menus, botões, combinações e bitmaps.  
  
 Cada elemento do filho subseção, por exemplo, \<Menu >, é identificado por uma ID exclusiva que é um GUID e um par de identificador numérico. O GUID identifica o conjunto de comandos"" e é usado para agrupar comandos relacionados logicamente. O VSPackage deverá definir seu próprio conjunto de comandos para evitar colisões com as IDs de comando que são definidos por outros VSPackages.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
<Commands package="GuidMyPackage" >  
  <Menus>... </Menus>  
  <Groups>... </Groups>  
  <Buttons>... </Buttons>  
  <Combos>... </Combos>  
  <Bitmaps>... </Bitmaps>  
</Commands>  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|pacote|Um GUID que identifica o VSPackage que fornece os comandos.<br /><br /> Por exemplo, do pacote = "guidVsPackage1Pkg".|  
  
### <a name="child-elements"></a>Elementos filho  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[Elemento de menus](../extensibility/menus-element.md)|Define todos os menus que implementa um VSPackage.|  
|[Elemento Groups](../extensibility/groups-element.md)|Contém entradas que definem os grupos de comando em um VSPackage.|  
|[Elemento de botões](../extensibility/buttons-element.md)|Agrupa elementos Button.|  
|[Elemento de bitmaps](../extensibility/bitmaps-element.md)|Agrupa elementos do Bitmap.|  
|[Elemento de combinações](../extensibility/combos-element.md)|Agrupa elementos de combinação.|  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[Elemento CommandTable](../extensibility/commandtable-element.md)|Define todos os elementos que representam os comandos que um VSPackage fornece ao IDE. Elementos possíveis são itens de menu, menus, barras de ferramentas e caixas de combinação.|  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como usar um [comandos elemento](../extensibility/commands-element.md).  
  
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
