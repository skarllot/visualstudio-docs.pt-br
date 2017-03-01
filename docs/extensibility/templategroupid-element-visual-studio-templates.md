---
title: Elemento TemplateGroupID (modelos do Visual Studio) | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#TemplateGroupID
helpviewer_keywords:
- TemplateGroupID element [Visual Studio Templates]
- <TemplateGroupID> element [Visual Studio Templates]
ms.assetid: bce7b49a-90bc-4691-aff3-a87e209f6d83
caps.latest.revision: 18
ms.author: gregvanl
manager: ghogen
translation.priority.ht:
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
ms.openlocfilehash: f02d4daf8b686ece738e4d0c9014d6c09213782d
ms.lasthandoff: 02/22/2017

---
# <a name="templategroupid-element-visual-studio-templates"></a>Elemento TemplateGroupID (modelos do Visual Studio)
Especifica o tipo de projeto de um modelo de item aparecerá no. Esse elemento é significativo quando [ShowByDefault (modelos do Visual Studio)](../extensibility/showbydefault-visual-studio-templates.md) é definido como `false`. Quando [ShowByDefault (modelos do Visual Studio)](../extensibility/showbydefault-visual-studio-templates.md) é definido como `true`, um modelo de item estará disponível em todos os tipos de projeto.  
  
 \<VSTemplate >  
 \<TemplateData >  
 \<TemplateGroupID >  
  
## <a name="syntax"></a>Sintaxe  
  
```  
<TemplateGroupID> ... </TemplateGroupID>  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
 Nenhum.  
  
### <a name="child-elements"></a>Elementos filho  
 nenhuma.  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Categoriza o modelo e define como ele é exibido em qualquer um de **novo projeto** ou o **Adicionar Novo Item** caixa de diálogo.|  
  
## <a name="text-value"></a>Valor de texto  
 Um valor de texto é obrigatório.  
  
 O texto Especifica um identificador para uma categoria de modelos de item.  
  
## <a name="remarks"></a>Comentários  
 `TemplateGroupID`é um elemento.  
  
 O valor da `TemplateGroupID` elemento é usado junto com o registro do sistema de projeto (HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\\*\<número de versão >*\Projects\\) para modelos de filtro que aparecem no **Adicionar Novo Item** caixa de diálogo.  
  
|Valor do Visual C++|Significado|  
|------------------------|-------------|  
|Nativo do VC|Usado para projetos nativos. Também o padrão se um tipo de projeto não pode ser determinado.|  
|Gerenciado por VC|Usado para gerenciado (/ clr) projetos|  
|VC-Windows|Usado para todos os projetos destinados a plataforma do windows (nativo/gerenciado/armazenamento)|  
|WinRT nativo-UAP|Usado para projetos de armazenamento do Windows 10|  
|CodeSharing nativo|Usado para projetos de item compartilhado|  
|6.3 do WinRT-nativo|Usado para projetos Windows 8.1 Store|  
|WinRT nativo-Phone&6;.3|Usado para projetos do Windows Phone 8.1|  
|Nativo do WinRT|Usado para projetos de armazenamento do Windows 8.0|  
|VC-Android|Usado para projetos do Android|  
  
## <a name="see-also"></a>Consulte também  
 [Referência de esquema de modelo do Visual Studio](../extensibility/visual-studio-template-schema-reference.md)   
 [Criando modelos de projeto e de item](../ide/creating-project-and-item-templates.md)
