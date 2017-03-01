---
title: Elemento VSIXLanguagePack (esquema do pacote de idioma VSIX) | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 767f5c22-8b87-49ca-92aa-a7a3f026469f
caps.latest.revision: 8
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
ms.openlocfilehash: dbf6d927c2b2a161b52cbc841f7864221de2e3ab
ms.lasthandoff: 02/22/2017

---
# <a name="vsixlanguagepack-element-vsix-language-pack-schema"></a>Elemento VSIXLanguagePack (VSIX esquema do pacote de idioma)
Necessário. Fornece o elemento raiz para um pacote de idiomas do VSIX. O pacote de idiomas do VSIX fornece informações de instalação localizado para um pacote VSIX.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
<VSIXLanguagePack>  
  <LocalizedName>...</LocalizedName>  
  <LocalizedDescription>...</LocalizedDescription>  
  <MoreInfoURL>...</MoreInfoURL>  
  <License>...</License>  
</VSIXLanguagePack>  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|`xmlns`|O namespace XML no qual o esquema de pacote de idiomas do VSIX está definido.|  
  
## <a name="xmlns-attribute"></a>Atributo xmlns  
  
|Valor|Descrição|  
|-----------|-----------------|  
|`http://schemas.microsoft.com/developer/vsx-schema-lp/2010`|Necessário. O local do arquivo que define o esquema de pacotes de idiomas.|  
  
### <a name="child-elements"></a>Elementos filho  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[Elemento LocalizedName](../extensibility/localizedname-element-vsix-language-pack-schema.md)|Necessário. O nome localizado da extensão a ser instalado.|  
|[Elemento LocalizedDescription](../extensibility/localizeddescription-element-vsix-language-pack-schema.md)|Necessário. A descrição localizada da extensão a ser instalado.|  
|[Elemento de URL para mais informações](../extensibility/moreinfourl-element-vsix-language-pack-schema.md)|Opcional. Um link para informações localizadas sobre a extensão.|  
|[Elemento de licença](../extensibility/license-element-vsix-language-pack-schema.md)|Opcional. O caminho de uma versão localizada do arquivo de licença para a extensão.|  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|Nenhum||  
  
## <a name="element-information"></a>Informações do elemento  
  
|||  
|-|-|  
|espaço de nome|http://schemas.microsoft.com/Developer/VSX-Schema-LP/2010|  
|Nome do esquema|Esquema de pacote de idiomas do VSIX|  
|Arquivo de validação|VSIXLanguagePackSchema.xsd|  
|Pode ser vazio|Não|  
  
## <a name="see-also"></a>Consulte também  
 [Referência de esquema de pacote de idioma do VSX](../extensibility/vsx-language-pack-schema-reference.md)   
 [Localizando pacotes VSIX](../extensibility/localizing-vsix-packages.md)   
 [Referência da extensão do esquema 1.0 VSIX](http://msdn.microsoft.com/en-us/76e410ec-b1fb-4652-ac98-4a4c52e09a2b)
