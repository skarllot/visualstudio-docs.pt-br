---
title: "Referência de esquema de modelo do Visual Studio manifesto | Documentos do Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bc7d0a81-0df5-41a9-a912-1b30e5da1d13
caps.latest.revision: 3
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
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
ms.sourcegitcommit: 512014c5070e4314ad2b7d0e8c5c404c43f32cd9
ms.openlocfilehash: 0f4abf286dc8b1cf00e47468ddaa4831747a059d
ms.lasthandoff: 02/22/2017

---
# <a name="visual-studio-template-manifest-schema-reference"></a>Referência de esquema do manifesto de modelo do Visual Studio
Esse esquema descreve o formato dos arquivos de manifesto (.vstman) de modelo do Visual Studio gerado para os modelos de projeto ou item do Visual Studio e descreve o local e outras informações relevantes sobre o modelo.  
  
 : Porque há diretórios de modelos de projeto e de item separado, um manifesto nunca deve ter uma combinação de modelos de item e projeto.  
  
> [!IMPORTANT]
>  Esse manifesto está disponível no Visual Studio 2017.  
  
## <a name="vstemplatemanifest-element"></a>Elemento VSTemplateManifest  
 O elemento raiz do manifesto.  
  
### <a name="attributes"></a>Atributos  
  
-   **Versão**: uma cadeia de caracteres que representa a versão do manifesto do modelo. Necessário.  
  
-   **Localidade**: uma cadeia de caracteres que representa a localidade ou localidades do manifesto do modelo. O valor da localidade se aplica a todos os modelos, você deve usar um manifesto separado para cada localidade. Opcional.  
  
### <a name="child-elements"></a>Elementos filho  
  
-   **VSTemplateContainer** opcional.  
  
-   **VSTemplateDir** opcional.  
  
### <a name="parent-element"></a>Elementos pai  
 Nenhum.  
  
## <a name="vstemplatecontainer"></a>VSTemplateContainer  
 O contêiner do modelo de manifesto elementos. Um manifesto tem um contêiner de modelo para cada modelo define.  
  
### <a name="attributes"></a>Atributos  
 **VSTemplateType** : um valor de cadeia de caracteres que especifica o tipo do modelo (`"Project"`, `"Item"`, ou `"ProjectGroup"`). Necessária  
  
### <a name="child-elements"></a>Elementos filho  
  
-   **RelativePathOnDisk**: O caminho relativo do arquivo de modelo no disco. Esse local também define o posicionamento do modelo na árvore do modelo mostrado no **novo projeto** ou **Novo Item** caixa de diálogo. Para modelos implantados como um diretório e os arquivos individuais, esse caminho refere-se para o diretório que contém os arquivos de modelo. Para modelos implantados como um arquivo. zip, esse caminho deve ser o caminho para o arquivo. zip.  
  
-   **VSTemplateHeader** : um [TemplateData](../extensibility/templatedata-element-visual-studio-templates.md) elemento que descreve o cabeçalho.  
  
### <a name="parent-element"></a>Elementos pai  
 **VSTemplateManifest**  
  
## <a name="vstemplatedir"></a>VSTemplateDir  
 Descreve o diretório onde o modelo está localizado. Um manifesto pode conter vários **VSTemplateDir** entradas para fornecer o nome localizado e ordem de classificação diretórios para controlar sua aparência na árvore de categoria do modelo.  
  
 Devido a seu design, **VSTemplateDir** entradas devem ser exibidas somente em manifestos de localidade não especificados.  
  
### <a name="attributes"></a>Atributos  
 Nenhum.  
  
### <a name="child-elements"></a>Elementos filho  
  
-   **RelativePath**: O caminho do modelo. Pode haver apenas uma entrada por caminho, portanto vencerá primeiro para todos os manifestos.  
  
-   **LocalizedName**: um **NameDescriptionIcon** elemento que especifica o nome localizado. Opcional.  
  
-   **Ordem de classificação** : uma cadeia de caracteres que especifica a ordem de classificação. Opcional.  
  
-   **ParentFolderOverrideName**: O nome substituído da pasta pai. Opcional. Este elemento tem um **nome** atributo, que é um valor de cadeia de caracteres que especifica o nome.  
  
### <a name="parent-element"></a>Elementos pai  
 **VSTemplateManifest**  
  
## <a name="namedescriptionicon"></a>NameDescriptionIcon  
 Especifica o nome e a descrição, possivelmente para modelos localizados. Consulte **LocalizedName** acima.  
  
### <a name="attributes"></a>Atributos  
  
-   **Pacote**: um valor de cadeia de caracteres que especifica o pacote. Opcional.  
  
-   **ID**: um valor de cadeia de caracteres que especifica a ID. Opcional.  
  
### <a name="child-elements"></a>Elementos filho  
 Nenhum.  
  
### <a name="parent-element"></a>Elementos pai  
 **LocalizedName**  
  
## <a name="examples"></a>Exemplos  
 Este é um exemplo de um arquivo de .vstman de modelo de projeto.  
  
```xml  
<VSTemplateManifest Version="1.0" Locale="1033" xmlns="http://schemas.microsoft.com/developer/vstemplatemanifest/2015">  
  <VSTemplateContainer TemplateType="Project">  
    <RelativePathOnDisk>CSharp\1033\TestProjectTemplate</RelativePathOnDisk>  
    <TemplateFileName>TestProjectTemplate.vstemplate</TemplateFileName>  
    <VSTemplateHeader>  
      <TemplateData xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
        <Name>TestProjectTemplate</Name>  
        <Description>TestProjectTemplate</Description>  
        <Icon>TestProjectTemplate.ico</Icon>  
        <ProjectType>CSharp</ProjectType>  
        <RequiredFrameworkVersion>2.0</RequiredFrameworkVersion>  
        <SortOrder>1000</SortOrder>  
        <TemplateID>aac0aeea-7883-4003-992f-937d53d70ab1</TemplateID>  
        <CreateNewFolder>true</CreateNewFolder>  
        <DefaultName>TestProjectTemplate</DefaultName>  
        <ProvideDefaultName>true</ProvideDefaultName>  
      </TemplateData>  
    </VSTemplateHeader>  
  </VSTemplateContainer>  
</VSTemplateManifest>  
  
```  
  
 A seguir está um exemplo de um arquivo de .vstman de modelo de item.  
  
```  
VSTemplateManifest Version="1.0" Locale="1033" xmlns="http://schemas.microsoft.com/developer/vstemplatemanifest/2015">  
  <VSTemplateContainer TemplateType="Item">  
    <RelativePathOnDisk>CSharp\1033\ItemTemplate1</RelativePathOnDisk>  
    <TemplateFileName>ItemTemplate1.vstemplate</TemplateFileName>  
    <VSTemplateHeader>  
      <TemplateData xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
        <Name>ItemTemplate1</Name>  
        <Description>ItemTemplate1</Description>  
        <Icon>ItemTemplate1.ico</Icon>  
        <TemplateID>bfeadf8e-a251-4109-b605-516b88e38c8d</TemplateID>  
        <ProjectType>CSharp</ProjectType>  
        <RequiredFrameworkVersion>2.0</RequiredFrameworkVersion>  
        <NumberOfParentCategoriesToRollUp>1</NumberOfParentCategoriesToRollUp>  
        <DefaultName>Class.cs</DefaultName>  
      </TemplateData>  
    </VSTemplateHeader>  
  </VSTemplateContainer>  
</VSTemplateManifest>  
  
```
