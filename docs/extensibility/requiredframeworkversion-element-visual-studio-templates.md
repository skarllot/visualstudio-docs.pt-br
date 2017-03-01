---
title: Elemento RequiredFrameworkVersion (modelos do Visual Studio) | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- <RequiredFrameworkVersion> (Visual Studio Templates)
- RequiredFrameworkVersion (Visual Studio Templates)
ms.assetid: 08a4f609-51a5-4723-b89f-99277fb18871
caps.latest.revision: 10
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
ms.openlocfilehash: 1f2f8397505287d1c323f4b22bd99ed5ebc1a273
ms.lasthandoff: 02/22/2017

---
# <a name="requiredframeworkversion-element-visual-studio-templates"></a>Elemento RequiredFrameworkVersion (modelos do Visual Studio)
Especifica a versão mínima do .NET Framework que é exigida pelo modelo. Hierarquia de esquema.  
  
 \<VSTemplate >  
 \<TemplateData >  
 \<RequiredFrameworkVersion >  
  
## <a name="syntax"></a>Sintaxe  
  
```  
<RequiredFrameworkVersion> .... </RequiredFrameworkVersion>  
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
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Elemento obrigatório.<br /><br /> Categoriza o modelo e define como ele é exibido em qualquer um de **novo projeto** ou o **Adicionar Novo Item** caixa de diálogo.|  
  
## <a name="text-value"></a>Valor de texto  
 Um valor de texto é obrigatório.  
  
 O texto deve ser o número de versão mínima do .NET Framework que é necessário para o modelo.  
  
## <a name="remarks"></a>Comentários  
 `RequiredFrameworkVersion` é um elemento opcional. Use esse elemento se o modelo só oferece suporte a uma versão específica de mínima e versões posteriores, se houver, do .NET Framework.  
  
## <a name="see-also"></a>Consulte também  
 [Referência de esquema de modelo do Visual Studio](../extensibility/visual-studio-template-schema-reference.md)   
 [Criando modelos de projeto e Item](../ide/creating-project-and-item-templates.md)   
 [Direcionamento de uma versão específica do .NET Framework](../ide/targeting-a-specific-dotnet-framework-version.md)
