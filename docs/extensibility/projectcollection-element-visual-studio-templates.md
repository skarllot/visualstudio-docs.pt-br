---
title: Elemento ProjectCollection (modelos do Visual Studio) | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#ProjectCollection
helpviewer_keywords:
- <ProjectCollection> element [Visual Studio Templates]
- ProjectCollection element [Visual Studio Templates]
ms.assetid: deb27180-2035-49ed-b835-c47bb3cd2f8f
caps.latest.revision: 8
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
ms.openlocfilehash: 678e2660766d88845657733243324e4a72b2b108
ms.lasthandoff: 02/22/2017

---
# <a name="projectcollection-element-visual-studio-templates"></a>Elemento ProjectCollection (modelos do Visual Studio)
Especifica a organização e o conteúdo de modelos de vários projetos.  
  
 \<VSTemplate >  
 \<TemplateContent >  
 \<ProjectCollection >  
  
## <a name="syntax"></a>Sintaxe  
  
```  
<ProjectCollection>  
    <ProjectTemplateLink> ... </ProjectTemplateLink>  
    <SolutionFolder> ... </SolutionFolder>  
</ProjectCollection>  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
 Nenhum.  
  
### <a name="child-elements"></a>Elementos filho  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[ProjectTemplateLink](../extensibility/projecttemplatelink-element-visual-studio-templates.md)|Elemento opcional.<br /><br /> Especifica um projeto em um modelo de vários projetos.|  
|[SolutionFolder](../extensibility/solutionfolder-element-visual-studio-templates.md)|Elemento opcional.<br /><br /> Agrupa projetos em modelos de vários projetos.|  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[TemplateContent](../extensibility/templatecontent-element-visual-studio-templates.md)|Elemento obrigatório.<br /><br /> Especifica o conteúdo do modelo.|  
  
## <a name="remarks"></a>Comentários  
 Os modelos de vários projetos atuam como contêineres para dois ou mais projetos. O `ProjectCollection` elemento é usado para especificar os projetos contêm no modelo. Para obter mais informações sobre modelos de multiprojeto, consulte [como: criar modelos de multiprojeto](../ide/how-to-create-multi-project-templates.md).  
  
## <a name="example"></a>Exemplo  
 Esse exemplo mostra um arquivo simples .vstemplate raiz de vários projetos. Neste exemplo, o modelo contém dois projetos, `My Windows Application` e `My Class Library`. O atributo `ProjectName` no elemento `ProjectTemplateLink` define o nome do [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] para atribuir este projeto. Se o atributo `ProjectName` não existir, o nome do arquivo .vstemplate é usado como o nome do projeto.  
  
```  
<VSTemplate Version="3.0.0" Type="ProjectGroup"  
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
    <TemplateData>  
        <Name>Multi-Project Template Sample</Name>  
        <Description>An example of a multi-project template</Description>  
        <Icon>Icon.ico</Icon>  
        <ProjectType>VisualBasic</ProjectType>  
    </TemplateData>  
    <TemplateContent>  
        <ProjectCollection>  
            <ProjectTemplateLink ProjectName="My Windows Application">  
                WindowsApp\MyTemplate.vstemplate  
            </ProjectTemplateLink>  
            <ProjectTemplateLink ProjectName="My Class Library">  
                ClassLib\MyTemplate.vstemplate  
            </ProjectTemplateLink>  
        </ProjectCollection>  
    </TemplateContent>  
</VSTemplate>  
```  
  
## <a name="see-also"></a>Consulte também  
 [Referência de esquema de modelo do Visual Studio](../extensibility/visual-studio-template-schema-reference.md)   
 [Criando modelos de projeto e Item](../ide/creating-project-and-item-templates.md)   
 [Como criar modelos multiprojeto](../ide/how-to-create-multi-project-templates.md)
