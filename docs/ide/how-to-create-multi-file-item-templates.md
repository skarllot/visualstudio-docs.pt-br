---
title: "Como criar modelos de item de vários arquivos | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Visual Studio templates, creating multi-file item templates
- multi-file item templates
- item templates, creating multi-file item templates
ms.assetid: fe3c4257-e383-4c80-b8af-c5c521959c33
caps.latest.revision: 12
author: kempb
ms.author: kempb
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
translationtype: Human Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 20daebf656f2d31ecc86cd46c05ed54fe42b73c3
ms.lasthandoff: 02/22/2017

---
# <a name="how-to-create-multi-file-item-templates"></a>Como criar modelos de item multiarquivo
Os modelos de item podem especificar apenas um item, mas, algumas vezes, o item é composto por vários arquivos. Por exemplo, um modelo de item do Windows Forms para Visual Basic exige os três arquivos a seguir:  
  
-   Um arquivo .vb que contém o código do formulário.  
  
-   Um arquivo .vb que contém as informações de designer do formulário.  
  
-   Um arquivo .resx que contém os recursos inseridos do formulário.  
  
 Os modelos de item de vários arquivos exigem parâmetros para garantir que as extensões de nome de arquivo corretas sejam usadas quando o item é criado no [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Se você criar um modelo de item usando o assistente **Exportar Modelo**, esses parâmetros serão gerados automaticamente, e não será necessária nenhuma edição. As etapas a seguir explicam como usar parâmetros para garantir que as extensões de nome de arquivo corretas sejam criadas.  
  
### <a name="to-manually-create-a-multi-file-item-template"></a>Para criar manualmente um modelo de item de vários arquivos  
  
1.  Crie o modelo de item como você faria com um modelo de item de vários arquivos. Para obter mais informações, consulte [Como criar modelos de item](../ide/how-to-create-item-templates.md).  
  
2.  Adicione atributos `TargetFileName` a cada elemento `ProjectItem`. Defina os valores dos atributos `TargetFileName` como $fileinputname$.*FileExtension*, em que *FileExtension* é a extensão de nome de arquivo do arquivo que está sendo incluído no modelo. Por exemplo:  
  
    ```  
    <ProjectItem TargetFileName="$fileinputname$.vb">  
        Form1.vb  
    </ProjectItem>  
    <ProjectItem TargetFileName="$fileinputname$.Designer.vb">  
        Form1.Designer.vb  
    </ProjectItem>  
    <ProjectItem TargetFileName="$fileinputname$.resx">  
        Form1.resx  
    </ProjectItem>  
    ```  
  
     Quando um item derivado deste modelo for adicionado a um projeto, os nomes de arquivo serão baseados no nome que o usuário digitou na caixa de diálogo **Adicionar Novo Item**.  
  
3.  Selecione os arquivos a serem incluídos em seu modelo, clique com o botão direito do mouse na seleção, clique em **Enviar Para** e, em seguida, clique em **Pasta Compactada (Zipada)**. Os arquivos selecionados são compactados em um arquivo .zip.  
  
4.  Coloque o arquivo .zip no local do modelo de item do usuário. Por padrão, o diretório é \Meus Documentos\Visual Studio *Versão*\Templates\ItemTemplates\\. Para obter mais informações, consulte [Como localizar e organizar modelos](../ide/how-to-locate-and-organize-project-and-item-templates.md).  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra um modelo do Windows Forms [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Quando um item é criado com base nesse modelo, os nomes dos três arquivos criados corresponderá ao nome inserido na caixa de diálogo **Adicionar Novo Item**.  
  
```  
<VSTemplate Version="2.0.0" Type="Item"  
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
    <TemplateData>  
        <Name>Multi-file Item Template</Name>  
        <Icon>Icon.ico</Icon>  
        <Description>An example of a multi-file item template</Description>  
        <ProjectType>VisualBasic</ProjectType>  
    </TemplateData>  
    <TemplateContent>  
        <ProjectItem TargetFileName="$fileinputname$.vb" SubType="Form">  
            Form1.vb  
        </ProjectItem>  
        <ProjectItem TargetFileName="$fileinputname$.Designer.vb">  
            Form1.Designer.vb  
        </ProjectItem>  
        <ProjectItem TargetFileName="$fileinputname$.resx">  
            Form1.resx  
        </ProjectItem>  
    </TemplateContent>  
</VSTemplate>  
```  
  
## <a name="see-also"></a>Consulte também  
 [Criando modelos de projeto e de item](../ide/creating-project-and-item-templates.md)   
 [Como criar modelos de item](../ide/how-to-create-item-templates.md)   
 [Parâmetros de modelo](../ide/template-parameters.md)   
 [Como substituir parâmetros em um modelo](../ide/how-to-substitute-parameters-in-a-template.md)
