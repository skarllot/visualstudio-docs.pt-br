---
title: Elemento SortOrder (modelos do Visual Studio) | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#SortOrder
helpviewer_keywords:
- SortOrder element [Visual Studio Templates]
- <SortOrder> element [Visual Studio Templates]
ms.assetid: 151932c1-f08a-4f78-a8d0-bd2f32211a9c
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
ms.openlocfilehash: 33cb09e74363ae2ad96b2b83c04089fda70c0cee
ms.lasthandoff: 02/22/2017

---
# <a name="sortorder-element-visual-studio-templates"></a>Elemento SortOrder (modelos do Visual Studio)
Especifica um valor que é usado para organizar o modelo, entre outros modelos na mesma categoria, como ele aparece no **novo projeto** ou **Adicionar Novo Item** caixa de diálogo.  
  
 \<VSTemplate >  
 \<TemplateData >  
 \<Ordem de classificação >  
  
## <a name="syntax"></a>Sintaxe  
  
```  
<SortOrder> ... </SortOrder>  
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
  
 Um `integer` que representa o valor de ordem de classificação.  
  
## <a name="remarks"></a>Comentários  
 `SortOrder` é um elemento opcional. O valor padrão é 100 e todos os valores devem ser múltiplos de 10.  
  
 O `SortOrder` elemento é ignorado para modelos criados pelo usuário. Todos os modelos criados pelo usuário são classificados em ordem alfabética.  
  
 Os modelos que têm valores de ordem de classificação baixa aparecem no **novo projeto** ou **Novo Item adicionar** caixa de diálogo antes de modelos que têm valores de ordem de classificação alta.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir ilustra os metadados de um padrão [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] modelo de classe.  
  
```  
<VSTemplate Type="Item" Version="3.0.0"  
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
    <TemplateData>  
        <Name>MyClass</Name>  
        <Description>My custom C# class template.</Description>  
        <Icon>Icon.ico</Icon>  
        <ProjectType>CSharp</ProjectType>  
        <SortOrder>290</SortOrder>  
        <DefaultName>MyClass</DefaultName>  
    </TemplateData>  
    <TemplateContent>  
        <ProjectItem>MyClass.cs</ProjectItem>  
    </TemplateContent>  
</VSTemplate>  
```  
  
 Neste exemplo, o `SortOrder` elemento é relativamente alto. É provável que outros [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] modelos de item terá uma `SortOrder` valor menor do que `290` e será exibido antes que esse modelo no **Novo Item** caixa de diálogo.  
  
## <a name="see-also"></a>Consulte também  
 [Referência de esquema de modelo do Visual Studio](../extensibility/visual-studio-template-schema-reference.md)   
 [Criando modelos de projeto e de item](../ide/creating-project-and-item-templates.md)
