---
title: Elemento ProvideDefaultName (modelos do Visual Studio) | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#ProvideDefaultName
helpviewer_keywords:
- ProvideDefaultName element [Visual Studio project templates]
ms.assetid: 7b0e7b20-fd6b-42e2-81d0-e5100cea0528
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: cc57120b5684d8529ee20798da9deffe3726286b
ms.lasthandoff: 02/22/2017

---
# <a name="providedefaultname-element-visual-studio-templates"></a>Elemento ProvideDefaultName (modelos do Visual Studio)
Especifica se o [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] sistema de projeto irá gerar um nome padrão para o modelo de **Add New Item** ou **novo projeto** caixa de diálogo.  
  
 \<VSTemplate >  
 \<TemplateData >  
 \<ProvideDefaultName >  
  
## <a name="syntax"></a>Sintaxe  
  
```  
<ProvideDefaultName> true/false </ProvideDefaultName>  
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
  
 O texto deve ser `true` ou `false`, que indica se deve ou não gerar um nome padrão para o modelo de **Add New Item** ou **novo projeto** caixa de diálogo.  
  
## <a name="remarks"></a>Comentários  
 `ProvideDefaultName` é um elemento opcional. O valor padrão é `true`.  
  
 Se o `ProvideDefaultName` elemento é `false`, o **nome** caixas do **Adicionar Novo Item** e **novo projeto** caixas de diálogo contêm o valor `<Enter_name>`.  
  
 Use o [DefaultName](../extensibility/defaultname-element-visual-studio-templates.md) elemento para especificar o nome padrão do projeto ou item a **Adicionar Novo Item** e **novo projeto** caixas de diálogo.  
  
## <a name="example"></a>Exemplo  
 O seguinte exemplo de código define o `ProvideDefaultName` elemento `false`.  
  
```  
<VSTemplate Type="Item" Version="3.0.0"  
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
    <TemplateData>  
        <Name>MyClass</Name>  
        <Description>My custom C# class.</Description>  
        <Icon>Icon.ico</Icon>  
        <ProjectType>CSharp</ProjectType>  
        <ProvideDefaultName>false</ProvideDefaultName>  
    </TemplateData>  
    <TemplateContent>  
        <ProjectItem>MyClass.cs</ProjectItem>  
    </TemplateContent>  
</VSTemplate>  
```  
  
## <a name="see-also"></a>Consulte também  
 [Referência de esquema de modelo do Visual Studio](../extensibility/visual-studio-template-schema-reference.md)   
 [Criando modelos de projeto e de item](../ide/creating-project-and-item-templates.md)
