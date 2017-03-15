---
title: Elemento ProjectSubType (modelos do Visual Studio) | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#ProjectSubType
helpviewer_keywords:
- ProjectSubType element [Visual Studio Templates]
- <ProjectSubType> element [Visual Studio Templates]
ms.assetid: f6895cd4-3e95-4f0e-aa9e-8c7750f46ed4
caps.latest.revision: 13
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
ms.openlocfilehash: 0735d1e412b926de698e32568b97358b3574303b
ms.lasthandoff: 02/22/2017

---
# <a name="projectsubtype-element-visual-studio-templates"></a>Elemento ProjectSubType (modelos do Visual Studio)
Classifica o modelo em uma subcategoria do valor especificado no `ProjectType` elemento.  
  
 \<VSTemplate >  
 \<TemplateData >  
 \<ProjectSubType >  
  
## <a name="syntax"></a>Sintaxe  
  
```  
<ProjectSubType> SubType </ProjectSubType>  
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
  
 Esse valor Especifica a subcategoria do modelo.  
  
## <a name="remarks"></a>Comentários  
 O `ProjectSubType` é um elemento filho opcional de `TemplateData`.  
  
 O `ProjectSubType` elemento fornece uma subcategoria para o [ProjectType](../extensibility/projecttype-element-visual-studio-templates.md) elemento. Esse valor pode incluir:  
  
-   `SmartDevice-NETCFv1`: Especifica que o modelo se destina a [!INCLUDE[Compact](../extensibility/includes/compact_md.md)] versão 1.0.  
  
-   `SmartDevice-NETCFv2`: Especifica que os destinos tempalate o [!INCLUDE[Compact](../extensibility/includes/compact_md.md)] versão 2.0.  
  
 Se um modelo contém um `ProjectType` elemento com um valor de `Web`, o `ProjectSubType` elemento Especifica a linguagem de programação do modelo. Esse elemento pode ter os seguintes valores:  
  
-   `CSharp`: Especifica que o modelo cria um [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] projeto Web ou item.  
  
-   `VisualBasic`: Especifica que o modelo cria um [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] projeto Web ou item.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra os metadados para um modelo de projeto para um [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] direcionamento do aplicativo de dispositivo de [!INCLUDE[Compact](../extensibility/includes/compact_md.md)] versão 2.0.  
  
```  
<VSTemplate Type="Project" Version="3.0.0"  
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
    <TemplateData>  
        <Name>My template</Name>  
        <Description>A basic device template</Description>  
        <Icon>TemplateIcon.ico</Icon>  
        <ProjectType>CSharp</ProjectType>  
        <ProjectSubType>SmartDevice-NETCFv2</ProjectSubType>  
    </TemplateData>  
    <TemplateContent>  
        <Project File="MyTemplate.csproj">  
            <ProjectItem>Form1.cs<ProjectItem>  
            <ProjectItem>Form1.Designer.cs</ProjectItem>  
            <ProjectItem>Program.cs</ProjectItem>  
            <ProjectItem>Properties\AssemblyInfo.cs</ProjectItem>  
            <ProjectItem>Properties\Resources.resx</ProjectItem>  
            <ProjectItem>Properties\Resources.Designer.cs</ProjectItem>  
            <ProjectItem>Properties\Settings.settings</ProjectItem>  
            <ProjectItem>Properties\Settings.Designer.cs</ProjectItem>  
        </Project>  
    </TemplateContent>  
</VSTemplate>  
```  
  
## <a name="see-also"></a>Consulte também  
 [Referência de esquema de modelo do Visual Studio](../extensibility/visual-studio-template-schema-reference.md)   
 [Criando modelos de projeto e Item](../ide/creating-project-and-item-templates.md)   
 [Elemento ProjectType (modelos do Visual Studio)](../extensibility/projecttype-element-visual-studio-templates.md)
