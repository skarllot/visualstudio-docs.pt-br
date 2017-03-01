---
title: Elemento KeyBinding | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- VSCT XML schema elements, KeyBindings
- KeyBinding element (VSCT XML schema)
ms.assetid: e55a1098-15df-42a9-9f87-e3a99cf437dd
caps.latest.revision: 12
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
ms.openlocfilehash: f61cb309289d77bcc5c988a070a866a0e5a105b9
ms.lasthandoff: 02/22/2017

---
# <a name="keybinding-element"></a>Elemento KeyBinding
O elemento KeyBinding Especifica atalhos de teclado para os comandos.  
  
 Comandos podem ter associações de teclas única e duplas associadas a eles. Um exemplo de uma associação de chave única é CTRL + S para o **salvar** comando. Associações de chave duplas exigem duas combinações de teclas sucessivas para disparar um comando. Um exemplo de uma associação de chave dupla é CTRL + K, CTRL + K para definir um indicador.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
<Keybinding guid="MyGuid" id="MyId" Editor="MyEditor" key1="B" key2="x" mod1="Control" mod2="Alt" />  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|GUID|Necessário.|  
|id|Necessário.|  
|editor|Necessário. O GUID do editor indica o contexto de edição para o qual este atalho de teclado estará ativo. O valor de escopo global de associação é "guidVSStd97".|  
|Key1|Necessário. Os valores válidos incluem todos os typable alfanuméricos e também valores hexadecimais de dois dígitos precedidos por 0x e VK_constants.|  
|Mod1|Opcional. Qualquer combinação de teclas CTRL, ALT e SHIFT separados por espaço.|  
|CHAVE2|Opcional. Os valores válidos incluem todos os typable alfanuméricos e também valores hexadecimais de dois dígitos precedidos por 0x e VK_constants.|  
|Mod2|Opcional. Qualquer combinação de teclas CTRL, ALT e SHIFT separados por espaço.|  
|emulador|Opcional.|  
|Condição|Opcional. Consulte [atributos condicionais](../extensibility/vsct-xml-schema-conditional-attributes.md).|  
  
### <a name="child-elements"></a>Elementos filho  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|Pai||  
|Anotação||  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[Elemento KeyBindings](../extensibility/keybindings-element.md)|Agrupa KeyBinding elementos e outros agrupamentos KeyBindings.|  
  
## <a name="example"></a>Exemplo  
  
```  
<KeyBindings>  
  <KeyBinding guid="guidWidgetPackage" id="cmdidUpdateWidget"   
    editor="guidWidgetEditor" key1="VK_F5"/>  
  <KeyBinding guid="guidWidgetPackage" id="cmdidRunWidget"   
    editor="guidWidgetEditor" key1="VK_F5" mod1="Control"/>  
</KeyBindings>  
```  
  
## <a name="see-also"></a>Consulte também  
 [Elemento KeyBindings](../extensibility/keybindings-element.md)   
 [Tabela de comando do Visual Studio (. Arquivos de VSCT)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
