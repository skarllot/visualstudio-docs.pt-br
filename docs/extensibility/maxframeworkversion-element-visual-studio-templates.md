---
title: Elemento MaxFrameworkVersion (modelos do Visual Studio) | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- <MaxFrameworkVersion> Element (Visual Studio Templates)
- MaxFrameworkVersion Element (Visual Studio Templates)
ms.assetid: f732a9d3-fc29-405b-9298-01ea83fc58b8
caps.latest.revision: 9
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
ms.openlocfilehash: b32964c5ce2054d3bf78ec30cb8ee8a79b3f08e5
ms.lasthandoff: 02/22/2017

---
# <a name="maxframeworkversion-element-visual-studio-templates"></a>Elemento MaxFrameworkVersion (modelos do Visual Studio)
Especifica a versão máxima do .NET Framework que é exigido pelo modelo. Determina se o modelo é exibido no **modelos** seção o **adicionar novo projeto** com base no valor selecionado na caixa de diálogo, o **versão do Framework de destino** caixa do **adicionar novo projeto** caixa de diálogo.  
  
 \<VSTemplate >  
 \<MaxFrameworkVersion >  
  
## <a name="syntax"></a>Sintaxe  
  
```  
<MaxFrameworkVersion> ... </MaxFrameworkVersion>  
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
  
 O texto deve ser o maior número de versão do .NET Framework que é permitido pelo modelo.  
  
## <a name="remarks"></a>Comentários  
 `MaxFrameworkVersion` é um elemento opcional. O elemento a `TemplateData` seção do arquivo. vstemplate atua como um filtro para o **modelos** seção o **adicionar novo projeto** caixa de diálogo. Somente os modelos cujos requisitos do .NET Framework são inferiores `MaxFrameworkVersion` valores de elemento serão exibidos, com base no valor selecionado no **versão do Framework de destino** caixa do **adicionar novo projeto** caixa de diálogo. O `MaxFrameworkVersion` elemento deve ser omitido, a menos que é necessário, assim como não inadvertidamente, causar modelos sejam exibidas quando eles são usados com versões mais recentes do .NET Framework.  
  
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
        <MaxFrameworkVersion>3.5</MaxFrameworkVersion>  
        <DefaultName>MyClass</DefaultName>  
    </TemplateData>  
    <TemplateContent>  
        <ProjectItem>MyClass.cs</ProjectItem>  
    </TemplateContent>  
</VSTemplate>  
```  
  
 Neste exemplo, a versão máxima do .NET Framework necessária para o modelo representado por `MaxFrameworkVersion`, 3.5. O modelo acima será exibido somente quando você seleciona 3.0 ou 3.5 no **versão do Framework de destino** caixa de **adicionar novo projeto** caixa de diálogo.  
  
## <a name="see-also"></a>Consulte também  
 [Referência de esquema de modelo do Visual Studio](../extensibility/visual-studio-template-schema-reference.md)   
 [Criando modelos de projeto e de item](../ide/creating-project-and-item-templates.md)
