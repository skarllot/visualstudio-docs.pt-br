---
title: Elemento LocalizedName (esquema do pacote de idioma VSIX) | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 57b7f502-3b04-42d9-90d5-f57772a7c757
caps.latest.revision: 7
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
ms.openlocfilehash: 1afb8ee548bf193ea1b10a925b16f484f60c3af4
ms.lasthandoff: 02/22/2017

---
# <a name="localizedname-element-vsix-language-pack-schema"></a>Elemento LocalizedName (VSIX esquema do pacote de idioma)
Necessário. O nome localizado da extensão a ser instalado.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
<Name>Localized name of the extension</Name>  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|Nenhum||  
  
### <a name="child-elements"></a>Elementos filho  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|Nenhum||  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[Elemento de LanguagePack VSIX](../extensibility/vsixlanguagepack-element-vsix-language-pack-schema.md)|Necessário. Fornece o elemento raiz para um pacote de idiomas do VSIX.|  
  
## <a name="text-value"></a>Valor de texto  
 Necessário. O nome do pacote de idioma no idioma de destino.  
  
## <a name="element-information"></a>Informações do elemento  
  
|||  
|-|-|  
|espaço de nome|http://schemas.microsoft.com/Developer/VSX-Schema-LP/2010|  
|Nome do esquema|Esquema de pacote de idiomas do VSIX|  
|Arquivo de validação|VSIXLanguagePackSchema.xsd|  
|Pode ser vazio|Não aplicável|  
  
## <a name="see-also"></a>Consulte também  
 [Referência de esquema de pacote de idioma do VSX](../extensibility/vsx-language-pack-schema-reference.md)   
 [Localizando pacotes VSIX](../extensibility/localizing-vsix-packages.md)   
 [Referência da extensão do esquema 1.0 VSIX](http://msdn.microsoft.com/en-us/76e410ec-b1fb-4652-ac98-4a4c52e09a2b)
