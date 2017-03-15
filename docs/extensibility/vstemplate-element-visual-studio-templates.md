---
title: Elemento VSTemplate (modelos do Visual Studio) | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#VSTemplate
helpviewer_keywords:
- VSTemplate element [Visual Studio project templates]
ms.assetid: f8ac561b-3b0b-4246-9ec9-118d2447e9a9
caps.latest.revision: 20
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
ms.openlocfilehash: b07f33b696e8889d29a0cd22c243e1b69183d55e
ms.lasthandoff: 02/22/2017

---
# <a name="vstemplate-element-visual-studio-templates"></a>Elemento VSTemplate (modelos de projeto do Visual Studio)
Contém todos os metadados sobre o modelo de projeto, o modelo de item ou o starter kit.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
<VSTemplate Type="TemplateType" Version="x.x.x">  
    <TemplateData>    </TemplateData>  
    <TemplateContent>    </TemplateContent>  
    ...  
</VSTemplate>  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|`Type`|Identifica o modelo como um modelo de projeto ou um modelo de item. Esse atributo pode ter um valor de `Project` ou `Item`.|  
|`Version`|Especifica um número de versão para o modelo. Modelos de [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)] e [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] tem um `Version` valor do atributo `3.0.0`.|  
  
### <a name="child-elements"></a>Elementos filho  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Elemento obrigatório.<br /><br /> Especifica os dados que categoriza o modelo e define como ele é exibido no **novo projeto** ou **Adicionar Novo Item** caixa de diálogo.|  
|[TemplateContent](../extensibility/templatecontent-element-visual-studio-templates.md)|Elemento obrigatório.<br /><br /> Especifica o conteúdo do modelo.|  
|[WizardExtension](../extensibility/wizardextension-element-visual-studio-templates.md)|Elemento opcional.|  
|[WizardData](../extensibility/wizarddata-element-visual-studio-templates.md)|Elemento opcional.|  
  
### <a name="parent-elements"></a>Elementos pai  
 Nenhum.  
  
## <a name="remarks"></a>Comentários  
 O `VSTemplate` é o elemento raiz de arquivos. vstemplate.  
  
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
            <ProjectItem>Form1.cs</ProjectItem>  
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
