---
title: "Suporte para o projeto e propriedades de configuração | Documentos do Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- project properties, supporting with Visual Studio SDK
- configuration properties, suppporting with Visual Studio SDK
ms.assetid: 9fcfaa0f-7b41-4b68-82ec-7a151dca5d7e
caps.latest.revision: 25
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
ms.openlocfilehash: c15dc4b1d435427f1125bb5a70af6aa9b18b30db
ms.lasthandoff: 02/22/2017

---
# <a name="support-for-project-and-configuration-properties"></a>Suporte para o projeto e propriedades de configuração
O **propriedades** janela no [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ambiente de desenvolvimento integrado (IDE) pode exibir as propriedades do projeto e a configuração. Você pode fornecer uma página de propriedades para seu próprio tipo de projeto para que o usuário pode definir propriedades de seu aplicativo.  
  
 Selecionando um nó do projeto na **Solution Explorer** e, em seguida, clicando em **propriedades** sobre o **projeto** menu, você pode abrir uma caixa de diálogo que inclui as propriedades de projeto e a configuração. Em [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] e [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)]e tipos derivados desses idiomas, essa caixa de diálogo aparece como uma página com guias de projeto de [geral, ambiente, caixa de diálogo Opções](../../ide/reference/general-environment-options-dialog-box.md). Para obter mais informações, consulte [fora da compilação: passo a passo: expondo o projeto e as propriedades de configuração (c#)](http://msdn.microsoft.com/en-us/d850d63b-25e2-4505-9f3d-eb038d7c1d0e).  
  
 A estrutura de pacote gerenciado para projetos (MPFProj) fornece classes auxiliares para criar e gerenciar o novo sistema de projeto. Você pode encontrar a fonte de instruções de código e compilação em [MPF de projetos - Visual Studio 2013](http://mpfproj12.codeplex.com/).  
  
## <a name="persistence-of-project-and-configuration-properties"></a>Persistência de projeto e propriedades de configuração  
 Propriedades do projeto e a configuração são mantidas em um arquivo de projeto que tem uma extensão de nome de arquivo associado ao tipo de projeto, por exemplo,. csproj,. vbproj e .myproj. Projetos de linguagem geralmente usam um arquivo de modelo para gerar o arquivo de projeto. No entanto, há, na verdade, de várias maneiras para associar tipos de projeto e modelos. Para obter mais informações, consulte [NIB: modelos do Visual Studio](http://msdn.microsoft.com/en-us/141fccaa-d68f-4155-822b-27f35dd94041) e [descrição do diretório de modelo (. Arquivos Vsdir)](../../extensibility/internals/template-directory-description-dot-vsdir-files.md).  
  
 Propriedades do projeto e a configuração são criadas adicionando itens ao arquivo de modelo. Essas propriedades, em seguida, estão disponíveis para qualquer projeto criado usando o tipo de projeto que usa o modelo. [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)]projetos e o MPFProj usam o [fora da compilação: Visão geral do MSBuild](http://msdn.microsoft.com/en-us/b588fd73-a45b-4706-908f-cc131bccfbde) esquema para arquivos de modelo. Esses arquivos têm uma seção PropertyGroup para cada configuração. Propriedades de projetos normalmente são mantidas na primeira seção PropertyGroup, que tem um argumento de configuração definido como uma cadeia de caracteres nula.  
  
 O código a seguir mostra o início de um arquivo de projeto MSBuild básico.  
  
```  
<Project MSBuildVersion="2.0" DefaultTargets="Build" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  <PropertyGroup>  
    <Configuration Condition=" '$(Configuration)' == '' ">Debug</Configuration>  
    <Name>SomeProjectSix</Name>  
    <SchemaVersion>2.0</SchemaVersion>  
  </PropertyGroup>  
  <PropertyGroup Condition=" '$(Configuration)' == 'Debug' ">  
    <Optimize>false</Optimize>  
  </PropertyGroup>  
  <PropertyGroup Condition=" '$(Configuration)' == 'Release' ">  
    <Optimize>true</Optimize>  
```  
  
 No arquivo de projeto, `<Name>` e `<SchemaVersion>` são propriedades do projeto, e `<Optimize>` é uma propriedade de configuração.  
  
 É responsabilidade do projeto para persistir as propriedades do projeto e a configuração do arquivo de projeto.  
  
> [!NOTE]
>  Um projeto pode otimizar a persistência, mantendo apenas valores de propriedade diferentes dos seus valores padrão.  
  
## <a name="support-for-project-and-configuration-properties"></a>Suporte para o projeto e propriedades de configuração  
 O `Microsoft.VisualStudio.Package.SettingsPage` classe implementa as páginas de propriedades do projeto e a configuração. A implementação padrão de `SettingsPage` oferece propriedades públicas para um usuário em uma grade de propriedade genérica. O `Microsoft.VisualStudio.Package.HierarchyNode.GetPropertyPageGuids` método seleciona classes derivadas de `SettingsPage` para grades de propriedades do projeto. O `Microsoft.VisualStudio.Package.ProjectNode.GetConfigPropertyPageGuids` método seleciona classes derivadas de `SettingsPage` para grades de propriedades de configuração. O tipo de projeto deve substituir esses métodos para selecionar as páginas de propriedade apropriada.  
  
 O `SettingsPage` classe e o `Microsoft.VisualStudio.Package.ProjectNode` classe oferecer esses métodos para persistir as propriedades de projeto e a configuração:  
  
-   `Microsoft.VisualStudio.Package.ProjectNode.GetProjectProperty`e `Microsoft.VisualStudio.Package.ProjectNode.SetProjectProperty` persistir as propriedades do projeto.  
  
-   `Microsoft.VisualStudio.Package.SettingsPage.GetConfigProperty`e `Microsoft.VisualStudio.Package.SettingsPage.SetConfigProperty` persistir as propriedades de configuração.  
  
    > [!NOTE]
    >  As implementações de `Microsoft.VisualStudio.Package.SettingsPage` e `Microsoft.VisualStudio.Package.ProjectNode` classes usam o `Microsoft.Build.BuildEngine` métodos (MSBuild) para obter e definir propriedades de projeto e a configuração do arquivo de projeto.  
  
 A classe derivar de `SettingsPage` deve implementar `Microsoft.VisualStudio.Package.SettingsPage.ApplyChanges` e `Microsoft.VisualStudio.Package.SettingsPage.BindProperties` para manter propriedades do projeto ou a configuração do arquivo de projeto.  
  
## <a name="provideobjectattribute-and-registry-path"></a>ProvideObjectAttribute e o caminho do registro  
 Classes derivadas de `SettingsPage` são projetados para ser compartilhado entre os VSPackages. Para possibilitar um VSPackage criar uma classe derivada de `SettingsPage`, adicione uma `Microsoft.VisualStudio.Shell.ProvideObjectAttribute` para uma classe derivada de `Microsoft.VisualStudio.Shell.Package`.  
  
 [!code-cs[&#1; VSSDKSupportProjectConfigurationProperties](../../extensibility/internals/codesnippet/CSharp/support-for-project-and-configuration-properties_1.cs) ] 
 [!code-vb [VSSDKSupportProjectConfigurationProperties n º&1;](../../extensibility/internals/codesnippet/VisualBasic/support-for-project-and-configuration-properties_1.vb)]  
  
 O VSPackage à qual o atributo está conectado não tem importância. Quando um VSPackage é registrado com [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], a identificação de classe (CLSID) de qualquer objeto que pode ser criado é registrada para que uma chamada para <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry.CreateInstance%2A>pode crie-o.</xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry.CreateInstance%2A>  
  
 O caminho do registro de um objeto que pode ser criado é determinado pela combinação <xref:Microsoft.VisualStudio.Shell.Package.UserRegistryRoot%2A>, o word, CLSID e o guid do tipo de objeto.</xref:Microsoft.VisualStudio.Shell.Package.UserRegistryRoot%2A> Se `MyProjectPropertyPage` classe tem um guid de {3c693da2-5bca-49b3-bd95-ffe0a39dd723} e o UserRegistryRoot for HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0Exp, o caminho do registro seria HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0Exp\CLSID\\{3c693da2-5bca-49b3-bd95-ffe0a39dd723}.  
  
## <a name="project-and-configuration-property-attributes-and-layout"></a>Projeto e atributos de propriedade de configuração e o Layout  
 O <xref:System.ComponentModel.CategoryAttribute>, <xref:System.ComponentModel.DisplayNameAttribute>, e <xref:System.ComponentModel.DescriptionAttribute>atributos determinam o layout, identificando e descrição das propriedades do projeto e a configuração em uma página de propriedade genérica.</xref:System.ComponentModel.DescriptionAttribute> </xref:System.ComponentModel.DisplayNameAttribute> </xref:System.ComponentModel.CategoryAttribute> Esses atributos determinam a categoria, exibir o nome e a descrição da opção, respectivamente.  
  
> [!NOTE]
>  Atributos equivalentes, SRCategory, LocDisplayName e SRDescription, usar os recursos de cadeia de caracteres para localização e são definidos no [MPF de projetos - Visual Studio 2013](http://mpfproj12.codeplex.com/).  
  
 Considere o fragmento de código a seguir:  
  
 [!code-vb[N º&2; VSSDKSupportProjectConfigurationProperties](../../extensibility/internals/codesnippet/VisualBasic/support-for-project-and-configuration-properties_2.vb) ] 
 [!code-cs [VSSDKSupportProjectConfigurationProperties n º&2;](../../extensibility/internals/codesnippet/CSharp/support-for-project-and-configuration-properties_2.cs)]  
  
 O `MyConfigProp` propriedade configuração aparece na página de propriedades de configuração como **minha propriedade Config** na categoria de **My Category**. Se a opção for selecionada, a descrição, **minha descrição**, aparece no painel de descrição.  
  
## <a name="see-also"></a>Consulte também  
 [Não na compilação: passo a passo: expondo o projeto e propriedades de configuração (c#)](http://msdn.microsoft.com/en-us/d850d63b-25e2-4505-9f3d-eb038d7c1d0e)   
 [Adicionando e removendo páginas de propriedade](../../extensibility/adding-and-removing-property-pages.md)   
 [Estado de VSPackage](../../misc/vspackage-state.md)   
 [Projetos](../../extensibility/internals/projects.md)   
 [PONTA: Modelos do Visual Studio](http://msdn.microsoft.com/en-us/141fccaa-d68f-4155-822b-27f35dd94041)   
 [Descrição do modelo do diretório (. Arquivos Vsdir)](../../extensibility/internals/template-directory-description-dot-vsdir-files.md)
