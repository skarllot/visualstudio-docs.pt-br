---
title: Elemento TemplateContent (modelos do Visual Studio) | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#TemplateContent
helpviewer_keywords:
- TemplateContent element [Visual Studio project templates]
ms.assetid: 90ae401c-b294-49ac-98da-e0d274f5bebb
caps.latest.revision: 14
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
ms.openlocfilehash: 2edfc899416e44a28c020bc9c3cc2fe367d81fce
ms.lasthandoff: 02/22/2017

---
# <a name="templatecontent-element-visual-studio-templates"></a>Elemento TemplateContent (modelos do Visual Studio)
Especifica o conteúdo do modelo.  
  
 \<VSTemplate >  
 \<TemplateContent >  
  
## <a name="syntax"></a>Sintaxe  
  
```  
<TemplateContent>  
    ...  
</TemplateContent>  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|[BuildOnLoad](../extensibility/buildprojectonload-visual-studio-templates.md)|Especifica se a criação da solução quando um projeto é criado a partir do modelo.|  
  
### <a name="child-elements"></a>Elementos filho  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[ProjectCollection](../extensibility/projectcollection-element-visual-studio-templates.md)|Elemento opcional.<br /><br /> Especifica a organização e o conteúdo de modelos de vários projetos.|  
|[Projeto](../extensibility/project-element-visual-studio-templates.md)|Elemento opcional.<br /><br /> Especifica os arquivos ou diretórios para adicionar ao projeto.|  
|[Referências](../extensibility/references-element-visual-studio-templates.md)|Elemento opcional.<br /><br /> Especifica as referências de assembly necessárias para um modelo de item.|  
|[Item de projeto](../extensibility/projectitem-element-visual-studio-item-templates.md)|Elemento opcional.<br /><br /> Especifica um arquivo contido no modelo.|  
|[CustomParameters](../extensibility/customparameters-element-visual-studio-templates.md)|Elemento opcional.<br /><br /> Especifica os parâmetros personalizados que devem ser usados quando um projeto ou item é criado a partir do modelo.|  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[VSTemplate](../extensibility/vstemplate-element-visual-studio-templates.md)|Elemento obrigatório.<br /><br /> Contém todos os metadados para o modelo de projeto, o modelo de item ou o starter kit.|  
  
## <a name="remarks"></a>Comentários  
 `TemplateContent`é um elemento necessário.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra os metadados para um modelo de projeto para um [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] aplicativo.  
  
```  
<VSTemplate Type="Project" Version="3.0.0"  
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
    <TemplateData>  
        <Name>My template</Name>  
        <Description>A basic starter kit</Description>  
        <Icon>TemplateIcon.ico</Icon>  
        <ProjectType>CSharp</ProjectType>  
    </TemplateData>  
    <TemplateContent>  
        <Project File="MyStarterKit.csproj">  
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
 [Criando modelos de projeto e de item](../ide/creating-project-and-item-templates.md)
