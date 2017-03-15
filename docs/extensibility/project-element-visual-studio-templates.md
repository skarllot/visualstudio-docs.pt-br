---
title: Projeto (modelos do Visual Studio) elemento | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#Project
helpviewer_keywords:
- Project element [Visual Studio Templates]
- <Project> element [Visual Studio Templates]
ms.assetid: 1da15ea6-26e2-462b-a03e-584ef4996579
caps.latest.revision: 16
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
ms.openlocfilehash: f2995f6486ebb8d3e305c70c03fb543fab04b67a
ms.lasthandoff: 02/22/2017

---
# <a name="project-element-visual-studio-templates"></a>Elemento de projeto (Modelos do Visual Studio)
Especifica os arquivos ou diretórios a serem adicionados ao projeto.  
  
 \<VSTemplate >  
 \<TemplateContent >  
 \<Project>  
  
## <a name="syntax"></a>Sintaxe  
  
```  
<Project  
    File="MyProject.proj"  
    TargetFileName="MyTargetProject.proj"  
    ReplaceParameters="true/false">  
    IgnoreProjectParameter="$myCustomParameter$"  
        ...  
</Project>  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|`File`|Atributo obrigatório.<br /><br /> Especifica o nome do arquivo de projeto no arquivo. zip de modelo.|  
|`ReplaceParameters`|Atributo opcional.<br /><br /> Um valor booleano que especifica se o arquivo de projeto tem valores de parâmetro devem ser substituídos quando um projeto é criado a partir do modelo. O valor padrão é `false`.|  
|`TargetFileName`|Atributo opcional.<br /><br /> Especifica o nome do arquivo de projeto quando um projeto é criado a partir do modelo.|  
|`IgnoreProjectParameter`|Atributo opcional.<br /><br /> Especifica se o projeto deve ser adicionado à solução atual. Se o valor de parâmetro personalizado, "$*myCustomParameter*$" existe no arquivo de substituição de parâmetro, o projeto é criado, mas não é adicionado como parte da solução atualmente aberta.|  
  
### <a name="child-elements"></a>Elementos filho  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[Pasta](../extensibility/folder-element-visual-studio-project-templates.md)|Elemento opcional.<br /><br /> Especifica uma pasta para adicionar ao projeto.|  
|[Item de projeto](../extensibility/projectitem-element-visual-studio-project-templates.md)|Elemento opcional.<br /><br /> Especifica um arquivo a ser adicionado a um projeto.|  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[TemplateContent](../extensibility/templatecontent-element-visual-studio-templates.md)|Elemento obrigatório.|  
  
## <a name="remarks"></a>Comentários  
 O `Project` é um elemento filho opcional de `TemplateContent`.  
  
 O `Project` é usado para especificar um projeto e, portanto, só é válido em modelos de projeto.  
  
 `Project`elementos podem ter [pasta](../extensibility/folder-element-visual-studio-project-templates.md) elementos filhos ou [ProjectItem](../extensibility/projectitem-element-visual-studio-project-templates.md) elementos filhos, mas não uma mistura de ambos `Folder` e `ProjectItem` elementos filhos.  
  
 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]Renomeia automaticamente o nome do arquivo de projeto com base no nome inserido pelo usuário no **novo projeto** caixa de diálogo. Use o `TargetFileName` se você desejar fornecer um nome de arquivo alternativo para os arquivos de projeto criados com o modelo de atributo.  
  
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
 [Criando modelos de projeto e Item](../ide/creating-project-and-item-templates.md)   
 [Elemento ProjectItem (modelos de projeto do Visual Studio)](../extensibility/projectitem-element-visual-studio-project-templates.md)   
 [Elemento de pasta (modelos de projeto do Visual Studio)](../extensibility/folder-element-visual-studio-project-templates.md)
