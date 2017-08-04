---
title: "Nova geração de projeto: Nos bastidores, segunda parte | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- projects [Visual Studio], new project dialog
- projects [Visual Studio], new project generation
ms.assetid: 73ce91d8-0ab1-4a1f-bf12-4d3c49c01e13
caps.latest.revision: 14
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 5581224b17a7b42f65b69f741f984a144d78fc26
ms.openlocfilehash: 859eeac9c2fd322dcf231e9c70fe83b92b099111
ms.contentlocale: pt-br
ms.lasthandoff: 04/04/2017

---
# <a name="new-project-generation-under-the-hood-part-two"></a>Nova geração de projeto: Nos bastidores, segunda parte
Em [nova geração de projeto: sob o escopo, uma parte](../../extensibility/internals/new-project-generation-under-the-hood-part-one.md) , vimos como o **novo projeto** caixa de diálogo caixa é preenchida. Vamos supor que você selecionou um **Visual C# Windows Application**, preenchido de **nome** e **local** caixas de texto e Okey clicado.  
  
## <a name="generating-the-solution-files"></a>Gerar os arquivos de solução  
 Escolher um modelo de aplicativo direciona [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] para descompactar e abrir o arquivo. vstemplate correspondente e para iniciar um modelo para interpretar os comandos XML no arquivo. Esses comandos criam projetos e itens de projeto na solução nova ou existente.  
  
 O modelo de descompactação de arquivos de origem, chamados de modelos de item, da mesma pasta. zip que contém o arquivo. vstemplate. O modelo de copiá-los para o novo projeto, personalizá-las adequadamente. Para obter uma visão geral de modelos de projeto e item, consulte [NIB: modelos do Visual Studio](http://msdn.microsoft.com/en-us/141fccaa-d68f-4155-822b-27f35dd94041).  
  
### <a name="template-parameter-replacement"></a>Substituição de parâmetro de modelo  
 Quando o modelo de cópias de um modelo de item para um novo projeto, ele substitui quaisquer parâmetros de modelo com cadeias de caracteres para personalizar o arquivo. Um parâmetro de modelo é um símbolo especial que é precedido e seguido por um sinal de cifrão, por exemplo, $date$.  
  
 Vamos examinar um modelo de item de projeto típico. Extrair e examine Program.cs na pasta Program Files\Microsoft Visual Studio 8\Common7\IDE\ProjectTemplates\CSharp\Windows\1033\WindowsApplication.zip.  
  
```  
using System;  
using System.Collections.Generic;  
using System.Windows.Forms;  
  
namespace $safeprojectname$  
{  
    static class Program  
    {  
        // source code deleted here for brevity  
    }  
}  
```  
  
 Se você criar um novo projeto de aplicativo do Windows chamado simples, o modelo substitui o `$safeprojectname$` parâmetro com o nome do projeto.  
  
```  
using System;  
using System.Collections.Generic;  
using System.Windows.Forms;  
  
namespace Simple  
{  
    static class Program  
    {  
        // source code deleted here for brevity  
    }  
}  
```  
  
 Para ver uma lista completa dos parâmetros de modelo, consulte [Parâmetros de Modelo](../../ide/template-parameters.md).  
  
## <a name="a-look-inside-a-vstemplate-file"></a>Uma olhada dentro de um. Arquivo VSTemplate  
 Um arquivo. vstemplate básica tem este formato  
  
```  
<VSTemplate Version="2.0.0"     xmlns="http://schemas.microsoft.com/developer/vstemplate/2005"     Type="Project">  
    <TemplateData>  
    </TemplateData>  
    <TemplateContent>  
    </TemplateContent>  
</VSTemplate>  
```  
  
 Analisamos o \<TemplateData > seção o [nova geração de projeto: sob o escopo, uma parte](../../extensibility/internals/new-project-generation-under-the-hood-part-one.md). As marcas nesta seção são usadas para controlar a aparência do **novo projeto** caixa de diálogo.  
  
 As marcas de \<TemplateContent > seção controle a geração de novos projetos e itens de projeto. Aqui está o \<TemplateContent > seção do arquivo cswindowsapplication.vstemplate na pasta de 8\Common7\IDE\ProjectTemplates\CSharp\Windows\1033\WindowsApplication.zip \Program Visual Studio.  
  
```  
<TemplateContent>  
  <Project File="WindowsApplication.csproj" ReplaceParameters="true">  
    <ProjectItem ReplaceParameters="true"  
      TargetFileName="Properties\AssemblyInfo.cs">  
      AssemblyInfo.cs  
    </ProjectItem>  
    <ProjectItem TargetFileName="Properties\Resources.resx">  
      Resources.resx  
    </ProjectItem>  
    <ProjectItem ReplaceParameters="true"       TargetFileName="Properties\Resources.Designer.cs">  
      Resources.Designer.cs  
    </ProjectItem>  
    <ProjectItem TargetFileName="Properties\Settings.settings">  
      Settings.settings  
    </ProjectItem>  
    <ProjectItem ReplaceParameters="true"       TargetFileName="Properties\Settings.Designer.cs">  
      Settings.Designer.cs  
    </ProjectItem>  
    <ProjectItem ReplaceParameters="true" OpenInEditor="true">  
      Form1.cs  
    </ProjectItem>  
    <ProjectItem ReplaceParameters="true">  
      Form1.Designer.cs  
    </ProjectItem>  
    <ProjectItem ReplaceParameters="true">  
      Program.cs  
    </ProjectItem>  
  </Project>  
</TemplateContent>  
```  
  
 O \<projeto > marca controla a geração de um projeto e o \<ProjectItem > marca controla a geração de um item de projeto. Se o parâmetro ReplaceParameters for true, o modelo será personalizar todos os parâmetros de modelo no arquivo de projeto ou item. Nesse caso, todos os itens de projeto são personalizados, exceto Settings.  
  
 O parâmetro TargetFileName Especifica o nome e o caminho relativo do arquivo de projeto ou item. Isso lhe permite criar uma estrutura de pasta para o seu projeto. Se você não especificar esse argumento, o item de projeto terá o mesmo nome que o modelo de item de projeto.  
  
 A estrutura de pastas de aplicativo Windows resultante tem esta aparência:  
  
 ![SimpleSolution](../../extensibility/internals/media/simplesolution.png "SimpleSolution")  
  
 A primeira e única \<projeto > marca das leituras de modelo:  
  
```  
<Project File="WindowsApplication.csproj" ReplaceParameters="true">  
```  
  
 Isso instrui o modelo de projeto novo para criar o arquivo de projeto Simple.csproj copiando e personalizando a windowsapplication.csproj do item de modelo.  
  
### <a name="designers-and-references"></a>Designers e referências  
 Você pode ver no Gerenciador de soluções que a pasta de propriedades está presente e que contém os arquivos. Mas e o projeto referencia e dependências de arquivo do designer, como Resources.Designer.cs para resx e Form1.Designer.cs para Form1?  Eles são definidos no arquivo Simple.csproj quando ele é gerado.  
  
 Aqui está o \<ItemGroup > de Simple.csproj que cria as referências do projeto:  
  
```  
<ItemGroup>  
    <Reference Include="System" />  
    <Reference Include="System.Data" />  
    <Reference Include="System.Deployment" />  
    <Reference Include="System.Drawing" />  
    <Reference Include="System.Windows.Forms" />  
    <Reference Include="System.Xml" />  
</ItemGroup>  
```  
  
 Você pode ver que essas são as referências de seis projeto que aparecem no Gerenciador de soluções. Aqui está uma seção de outro \<ItemGroup >. Número de linhas de código tenha sido excluído para maior clareza. Esta seção faz Settings.Designer.cs Settings dependentes:  
  
```  
<ItemGroup>  
    <Compile Include="Properties\Settings.Designer.cs">  
        <DependentUpon>Settings.settings</DependentUpon>  
    </Compile>  
</ItemGroup>  
```  
  
## <a name="see-also"></a>Consulte também  
 [Nova geração de projeto: nos bastidores, parte 1](../../extensibility/internals/new-project-generation-under-the-hood-part-one.md)  
 [MSBuild](../../msbuild/msbuild.md)
