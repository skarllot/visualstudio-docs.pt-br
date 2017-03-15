---
title: "Nova geração de projeto: Nos bastidores, parte&2; | Documentos do Microsoft"
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
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: c5f214774a5cf0aeb3896004632f8a2076782b14
ms.lasthandoff: 02/22/2017

---
# <a name="new-project-generation-under-the-hood-part-two"></a>Nova geração de projeto: Nos bastidores, parte&2;
Em [nova geração de projeto: sob o escopo, parte&1;](../../extensibility/internals/new-project-generation-under-the-hood-part-one.md) que vimos como o **novo projeto** caixa de diálogo caixa é preenchida. Vamos supor que você selecionou um **Visual C# Windows Application**, preenchido o **nome** e **local** caixas de texto e Okey clicado.  
  
## <a name="generating-the-solution-files"></a>Gerar os arquivos da solução  
 Escolher um modelo de aplicativo direciona [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] descompactar e abrir o arquivo. vstemplate correspondente e para iniciar um modelo para interpretar os comandos XML neste arquivo. Esses comandos criam projetos e itens de projeto na solução nova ou existente.  
  
 O modelo descompacta arquivos de origem, chamados de modelos de item, da mesma pasta. zip que contém o arquivo. vstemplate. O modelo copia esses arquivos para o novo projeto, personalizá-las adequadamente. Para obter uma visão geral dos modelos de projeto e de item, consulte [NIB: modelos do Visual Studio](http://msdn.microsoft.com/en-us/141fccaa-d68f-4155-822b-27f35dd94041).  
  
### <a name="template-parameter-replacement"></a>Substituição de parâmetro de modelo  
 Quando o modelo copia um modelo de item para um novo projeto, ele substitui quaisquer parâmetros de modelo com cadeias de caracteres para personalizar o arquivo. Um parâmetro de modelo é um símbolo especial que é precedido e seguido por um sinal de cifrão, por exemplo, $ $date.  
  
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
  
 Para obter uma lista completa dos parâmetros de modelo, consulte [parâmetros de modelo](../../ide/template-parameters.md).  
  
## <a name="a-look-inside-a-vstemplate-file"></a>Uma olhada dentro de um. Arquivos VSTemplate  
 Um arquivo. vstemplate básica tem este formato  
  
```  
<VSTemplate Version="2.0.0"     xmlns="http://schemas.microsoft.com/developer/vstemplate/2005"     Type="Project">  
    <TemplateData>  
    </TemplateData>  
    <TemplateContent>  
    </TemplateContent>  
</VSTemplate>  
```  
  
 Examinamos o \<TemplateData > seção o [nova geração de projeto: sob o escopo, parte&1;](../../extensibility/internals/new-project-generation-under-the-hood-part-one.md). As marcas nesta seção são usadas para controlar a aparência do **novo projeto** caixa de diálogo.  
  
 As marcas de \<TemplateContent > seção controle a geração de novos projetos e itens de projeto. Aqui está o \<TemplateContent > seção do arquivo na pasta \Program Visual Studio 8\Common7\IDE\ProjectTemplates\CSharp\Windows\1033\WindowsApplication.zip cswindowsapplication.vstemplate.  
  
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
  
 O parâmetro TargetFileName Especifica o nome e o caminho relativo do arquivo de projeto ou item. Isso permite criar uma estrutura de pasta para o seu projeto. Se você não especificar esse argumento, o item de projeto terá o mesmo nome que o modelo de item de projeto.  
  
 A estrutura de pastas de aplicativo Windows resultante terá esta aparência:  
  
 ![SimpleSolution](../../extensibility/internals/media/simplesolution.png "SimpleSolution")  
  
 A primeira e única \<projeto > marca as leituras de modelo:  
  
```  
<Project File="WindowsApplication.csproj" ReplaceParameters="true">  
```  
  
 Isso instrui o modelo novo projeto para criar o arquivo de projeto Simple.csproj copiando e personalizando o windowsapplication.csproj do item de modelo.  
  
### <a name="designers-and-references"></a>Designers e referências  
 Você pode ver no Solution Explorer, a pasta de propriedades está presente e contém os arquivos. Mas e quanto ao projeto referencia e dependências de arquivo de designer, como Resources.Designer.cs para resx e Form1. Designer.cs para Form1. cs?  Eles são definidos no arquivo Simple.csproj quando ele for gerado.  
  
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
  
 Você pode ver que eles são referências do seis projeto que aparecem no Gerenciador de soluções. Aqui está uma seção de outro \<ItemGroup >. Número de linhas de código ter sido excluído por motivos de clareza. Esta seção faz Settings.Designer.cs dependentes Settings:  
  
```  
<ItemGroup>  
    <Compile Include="Properties\Settings.Designer.cs">  
        <DependentUpon>Settings.settings</DependentUpon>  
    </Compile>  
</ItemGroup>  
```  
  
## <a name="see-also"></a>Consulte também  
 [Nova geração de projeto: Nos bastidores, parte&1;](../../extensibility/internals/new-project-generation-under-the-hood-part-one.md)  
 [MSBuild](../../msbuild/msbuild1.md)
