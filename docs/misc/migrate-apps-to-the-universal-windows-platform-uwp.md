---
title: "Migrar aplicativos para a UWP (Plataforma Universal do Windows) | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 5279ab9b-71d9-4be5-81f6-a1f24b06f5fb
caps.latest.revision: 19
caps.handback.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Migrar aplicativos para a UWP (Plataforma Universal do Windows)
Faça as alterações manuais necessárias em seus arquivos de projeto existente para aplicativos da Windows Store 8.1, aplicativos Windows Phone 8.1 ou Windows Universal aplicativos criados com o Visual Studio 2015 RC, para que eles podem ser usados com o Visual Studio 2015 RTM. \(Se você tiver um aplicativo universal do Windows 8.1 com um projeto de aplicativo do Windows e o projeto do Windows Phone, você precisará seguir as etapas para migrar cada projeto.\)  
  
 Com a plataforma Windows Universal, agora é possível direcionar seu aplicativo para um ou mais famílias de dispositivos. Se você quiser obter mais informações sobre aplicativos universais Windows, dê uma olhada isso [guia plataforma](https://msdn.microsoft.com/library/windows/apps/dn894631.aspx).  
  
-   [Migrar seu C existente \/VB aplicativos da Windows Store 8.1 ou Windows Phone 8.1](#MigrateCSharp) usar a plataforma Windows Universal.  
  
-   [Migrar seu banco de dados existente do C\+\+ Windows Store 8.1 ou aplicativos do Windows Phone 8.1](#MigrateCPlusPlus) usar a plataforma Windows Universal.  
  
-   [Alterações necessárias para aplicativos universais Windows existentes criados com o Visual Studio 2015 RC](#PreviousVersions).  
  
-   [Alterações necessárias para projetos de teste de unidade existente para aplicativos Windows universais criados com o Visual Studio 2015 RC](#MigrateUnitTest).  
  
 Se você não quiser fazer todas essas alterações, saiba como [seus aplicativos existentes da porta](http://msdn.microsoft.com/library/windows/apps/xaml/mt238321.aspx) para um novo projeto Windows Universal.  
  
##  <a name="MigrateCSharp"></a> Migrar seus aplicativos de Windows Store 8.1 ou Windows Phone 8.1 da \/VB de C para utilizar a plataforma Windows Universal  
  
#### Migrar seus arquivos de projeto C \/VB  
  
1.  Para localizar qual plataforma Windows Universal você instalou, abra essa pasta: **\\Program Files \(x86\)\\Windows Kits\\10\\Platforms\\UAP**. Ela contém uma lista de pastas para cada plataforma Windows Universal que está instalado. O nome da pasta é a versão da plataforma Windows Universal que você instalou. Por exemplo, este dispositivo Windows 10 tem versão 10.0.10240.0 da plataforma Windows Universal instalada.  
  
     ![Open the folder to view the versions installed](../misc/media/uap_uwpversions.png "UAP\_UWPVersions")  
  
     Mais de uma versão da plataforma Windows Universal pode ser instalada. É recomendável que você use a versão mais recente para seu aplicativo.  
  
2.  Usando o Explorador de arquivos, vá para a pasta onde o projeto UWP está armazenado. Crie um arquivo. JSON nessa pasta. Nomeie o arquivo: project.json e, em seguida, adicione o seguinte conteúdo a esse arquivo:  
  
    ```json  
    { "dependencies": { "Microsoft.ApplicationInsights": "1.0.0", "Microsoft.ApplicationInsights.PersistenceChannel": "1.0.0", "Microsoft.ApplicationInsights.WindowsApps": "1.0.0", "Microsoft.NETCore.UniversalWindowsPlatform": "5.0.0" }, "frameworks": { "uap10.0": {} }, "runtimes": { "win10-arm": {}, "win10-arm-aot": {}, "win10-x86": {}, "win10-x86-aot": {}, "win10-x64": {}, "win10-x64-aot": {} } }  
  
    ```  
  
3.  Crie um arquivo chamado default.rd.xml com o seguinte conteúdo. Se você tiver um projeto do VB, adicione esse arquivo para o diretório My Project para seu projeto. Se você tiver um projeto c\#, adicione esse arquivo para o diretório de propriedades do projeto.  
  
    ```xml  
    <?xml version="1.0"?> <!-- This file contains Runtime Directives used by .NET Native. The defaults here are suitable for most developers. However, you can modify these parameters to modify the behavior of the .NET Native optimizer. Runtime Directives are documented at http://go.microsoft.com/fwlink/?LinkID=391919 To fully enable reflection for App1.MyClass and all of its public/private members <Type Name="App1.MyClass" Dynamic="Required All"/> To enable dynamic creation of the specific instantiation of AppClass<T> over System.Int32 <TypeInstantiation Name="App1.AppClass" Arguments="System.Int32" Activate="Required Public" /> Using the Namespace directive to apply reflection policy to all the types in a particular namespace <Namespace Name="DataClasses.ViewModels" Seralize="All" /> --> <Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata"><Application> <!-- An Assembly element with Name="*Application*" applies to all assemblies in the application package. The asterisks are not wildcards. --> <Assembly Dynamic="Required All" Name="*Application*"/> <!-- Add your application specific runtime directives here. --> </Application></Directives>  
    ```  
  
4.  Abra a solução que contém o aplicativo da Windows Store 8.1 existente ou um aplicativo do Windows Phone 8.1 no Visual Studio.  
  
5.  Clique com o projeto existente para seu aplicativo no Solution Explorer e selecione **Descarregar projeto**. Depois que o projeto é descarregado, clique novamente o arquivo de projeto e escolha Editar o arquivo. csproj ou. vbproj.  
  
     ![Right click the project and choose Edit](../misc/media/uap_editproject.png "UAP\_EditProject")  
  
6.  Localize o elemento \< PropertyGroup \> que contém o elemento \< TargetPlatformVersion \> com um valor de 8.1. Siga as etapas a seguir para o elemento \< PropertyGroup \>:  
  
    1.  Defina o valor do elemento \< Platform \> para: **x86**.  
  
    2.  Adicione um elemento \< TargetPlatformIdentifier \> e defina seu valor como: **UAP**.  
  
    3.  Altere o valor existente do elemento \< TargetPlatformVersion \> como o valor da versão de plataforma Windows Universal que você instalou. Além disso, adicione um elemento \< TargetPlatformMinVersion \> e dar a ele o mesmo valor.  
  
    4.  Altere o valor do elemento \< MinimumVisualStudioVersion \> para: **14**.  
  
    5.  Substitua o elemento \< ProjectTypeGuids \>, conforme mostrado abaixo:  
  
         Para c\#:  
  
        ```xml  
        <ProjectTypeGuids>{A5A43C5B-DE2A-4C0C-9213-0A381AF9435A};{FAE04EC0-301F-11D3-BF4B-00C04F79EFBC}</ProjectTypeGuids>  
        ```  
  
         Para o VB:  
  
        ```xml  
        <ProjectTypeGuids>{A5A43C5B-DE2A-4C0C-9213-0A381AF9435A};{F184B08F-C81C-45F6-A57F-5ABD9991F28F}</ProjectTypeGuids>  
        ```  
  
    6.  Adicione um elemento \< EnableDotNetNativeCompatibleProfile \> e defina seu valor como: **true**.  
  
    7.  A escala do ativo padrão para aplicativos universais Windows é 200. Se seu projeto inclui ativos não dimensionados em 200, você precisará adicionar um elemento \< UapDefaultAssetScale \> com o valor da escala de seus ativos para essa PropertyGroup. Saiba mais sobre [ativos e escalas](http://msdn.microsoft.com/library/jj679352.aspx).  
  
         Agora o elemento \< PropertyGroup \> deve ser semelhante a este exemplo:  
  
        ```xml  
        <PropertyGroup> … <Platform Condition=" '$(Platform)' == '' ">x86</Platform> <TargetPlatformVersion>10.0.10240.0</TargetPlatformVersion> <TargetPlatformMinVersion>10.0.10240.0</TargetPlatformMinVersion> <TargetPlatformIdentifier>UAP</TargetPlatformIdentifier> <MinimumVisualStudioVersion>14</MinimumVisualStudioVersion> <ProjectTypeGuids>{A5A43C5B-DE2A-4C0C-9213-0A381AF9435A};{FAE04EC0-301F-11D3-BF4B-00C04F79EFBC}</ProjectTypeGuids> <EnableDotNetNativeCompatibleProfile>true</EnableDotNetNativeCompatibleProfile> <UapDefaultAssetScale>100</UapDefaultAssetScale> … </PropertyGroup>  
        ```  
  
7.  Substitua todas as instâncias de 12.0 14.0 para refletir a versão do Visual Studio que você está usando. Como essas instâncias:  
  
    ```xml  
    <Project Tools Version="14.0" DefaultTargets="Build" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    ```  
  
    ```  
    <PropertyGroup Condition=" '$(VisualStudioVersion)' == '' or '$(VisualStudioVersion)' < '14.0' "> <VisualStudioVersion>14.0</VisualStudioVersion>  
    ```  
  
8.  Localize elementos \< PropertyGroup \> configurados para a plataforma AnyCPU como parte do atributo Condition. Remova esses elementos e todos os seus filhos. Não há suporte para AnyCPU para aplicativos Windows 10 no Visual Studio de 2015. Por exemplo, você deve remover elementos \< PropertyGroup \> como esses aqui:  
  
    ```xml  
    <PropertyGroup Condition=" '$(Configuration)|$(Platform)' == 'Debug|AnyCPU' "> <PlatformTarget>AnyCPU</PlatformTarget> <DebugSymbols>true</DebugSymbols> <DebugType>full</DebugType> <Optimize>false</Optimize> <OutputPath>bin\Debug\</OutputPath> <DefineConstants>DEBUG;TRACE;NETFX_CORE;WINDOWS_UAP</DefineConstants> <ErrorReport>prompt</ErrorReport> <WarningLevel>4</WarningLevel> </PropertyGroup> <PropertyGroup Condition=" '$(Configuration)|$(Platform)' == 'Release|AnyCPU' "> <PlatformTarget>AnyCPU</PlatformTarget> <DebugType>pdbonly</DebugType> <Optimize>true</Optimize> <OutputPath>bin\Release\</OutputPath> <DefineConstants>TRACE;NETFX_CORE;WINDOWS_UAP</DefineConstants> <ErrorReport>prompt</ErrorReport> <WarningLevel>4</WarningLevel> </PropertyGroup>  
    ```  
  
9. Para cada elemento \< PropertyGroup \> restante, verifique se o elemento tem um atributo de condição com uma configuração de versão. Se ele faz, mas ele não contém um elemento \< UseDotNetNativeToolchain \>, adicione um. Defina o valor para o elemento \< UseDotNetNativeToolchain \> como true, como este:  
  
    ```xml  
    <PropertyGroup Condition="'$(Configuration)|$(Platform)' == 'Release|x64'"> <OutputPath>bin\x64\Release\</OutputPath> <DefineConstants>TRACE;NETFX_CORE;WINDOWS_UAP</DefineConstants> <Optimize>true</Optimize> <NoWarn>;2008</NoWarn> <DebugType>pdbonly</DebugType> <PlatformTarget>x64</PlatformTarget> <UseVSHostingProcess>false</UseVSHostingProcess> <ErrorReport>prompt</ErrorReport> <Prefer32Bit>true</Prefer32Bit> <UseDotNetNativeToolchain>true</UseDotNetNativeToolchain> </PropertyGroup>  
    ```  
  
10. Para o Windows Phone projetos, remova o elemento \< PropertyGroup \> que contém um elemento \< TargetPlatformIdentifier \> com um valor de WindowsPhoneApp. Também removerá todos os filhos desse elemento:  
  
    ```xml  
    <PropertyGroup Condition=" '$(TargetPlatformIdentifier)' == '' "> <TargetPlatformIdentifier>WindowsPhoneApp</TargetPlatformIdentifier> </PropertyGroup>  
    ```  
  
11. Localize o elemento \< ItemGroup \> que contém o elemento \< AppxManifest \>. Adicione o seguinte \< None \> elemento como um filho do elemento \< ItemGroup \>:  
  
    ```xml  
    <None Include="project.json" />  
    ```  
  
12. Localize o elemento \< ItemGroup \> que contém outros recursos que são adicionados ao seu projeto, como arquivos do logotipo. PNG \(\< Include\="Assets\\Logo.scale\-100.png conteúdo" \/ \>\). Adicione o seguinte elemento filho \< conteúdo \> para este elemento \< ItemGroup \>:  
  
     **Para c\#:**  
  
    ```xml  
    <Content Include="Properties\default.rd.xml" />  
    ```  
  
     **Para o VB:**  
  
    ```xml  
    <Content Include="My Project\default.rd.xml" />  
    ```  
  
13. Localize o elemento \< ItemGroup \> que inclui elementos de filhos \< Reference \> para pacotes do NuGet. Anote os pacotes do NuGet usar porque será necessário baixá\-los com o NuGet package manager após o recarregamento de seu projeto. Remova este \< ItemGroup \> junto com seus filhos. Por exemplo, um projeto UWP poderia ter os seguintes pacotes do NuGet que precisam ser removidos:  
  
    ```xml  
    <ItemGroup> <Reference Include="Microsoft.ApplicationInsights, Version=0.14.3.177, Culture=neutral, PublicKeyToken=31bf3856ad364e35, processorArchitecture=MSIL"> <HintPath>..\packages\Microsoft.ApplicationInsights.0.14.3-build00177\lib\portable-win81+wpa81\Microsoft.ApplicationInsights.dll</HintPath> <Private>True</Private> </Reference> <Reference Include="Microsoft.ApplicationInsights.Extensibility.Windows, Version=0.14.3.177, Culture=neutral, PublicKeyToken=31bf3856ad364e35, processorArchitecture=MSIL"> <HintPath>..\packages\Microsoft.ApplicationInsights.WindowsApps.0.14.3-build00177\lib\win81\Microsoft.ApplicationInsights.Extensibility.Windows.dll</HintPath> <Private>True</Private> </Reference> <Reference Include="Microsoft.ApplicationInsights.PersistenceChannel, Version=0.14.3.186, Culture=neutral, PublicKeyToken=31bf3856ad364e35, processorArchitecture=MSIL"> <HintPath>..\packages\Microsoft.ApplicationInsights.PersistenceChannel.0.14.3-build00177\lib\portable-win81+wpa81\Microsoft.ApplicationInsights.PersistenceChannel.dll</HintPath> <Private>True</Private> </Reference> <Reference Include="System.Numerics.Vectors, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a, processorArchitecture=MSIL"> <HintPath>..\packages\System.Numerics.Vectors.4.0.0\lib\win8\System.Numerics.Vectors.dll</HintPath> <Private>True</Private> </Reference> <Reference Include="System.Numerics.Vectors.WindowsRuntime, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a, processorArchitecture=MSIL"> <HintPath>..\packages\System.Numerics.Vectors.4.0.0\lib\win8\System.Numerics.Vectors.WindowsRuntime.dll</HintPath> <Private>True</Private> </Reference> </ItemGroup>  
    ```  
  
14. Salve suas alterações.  
  
15. Feche o arquivo. csproj ou. vbproj.  
  
16. Com o botão direito no projeto no Solution Explorer e escolha Recarregar projeto no menu de contexto. Todos os arquivos no seu projeto agora devem ser exibidos no Gerenciador de soluções.  
  
17. Use o Gerenciador do NuGet para adicionar os pacotes que você excluiu de volta em uma etapa anterior.  
  
     Agora você precisa seguir as etapas para [atualizar os arquivos de manifesto de pacote](#PackageManifest) para todos os seus projetos da Windows Store 8.1 ou Windows Phone 8.1.  
  
##  <a name="MigrateCPlusPlus"></a> Migrar seus aplicativos da Windows Store C\+\+ 8.1 ou Windows Phone 8.1 para usar a plataforma Windows Universal  
  
#### Migrar seus arquivos de projeto C\+\+  
  
1.  Para localizar qual plataforma Windows Universal você instalou, abra essa pasta: **\\Program Files \(x86\)\\Windows Kits\\10\\Platforms\\UAP**. Ela contém uma lista de pastas para cada plataforma Windows Universal que está instalado. O nome da pasta é a versão da plataforma Windows Universal que você instalou. Por exemplo, este dispositivo Windows 10 tem versão 10.0.10240.0 da plataforma Windows Universal instalada.  
  
     ![Open the folder to view the versions installed](../misc/media/uap_uwpversions.png "UAP\_UWPVersions")  
  
     Mais de uma versão da plataforma Windows Universal pode ser instalada. É recomendável que você use a versão mais recente para seu aplicativo.  
  
2.  Abra a solução que contém o aplicativo da Windows Store 8.1 C\+\+ existente ou um aplicativo do Windows Phone 8.1 no Visual Studio.  
  
     Clique com o projeto existente no Gerenciador de soluções e selecione **Descarregar projeto**. Depois que o projeto é descarregado, clique novamente o arquivo de projeto e escolha Editar o arquivo. vcxproj.  
  
     ![Right&#45;click project file and choose to edit](../misc/media/uap_editcplusproject.png "UAP\_EditCPlusProject")  
  
3.  Localize o elemento \< PropertyGroup \> que contém o elemento \< ApplicationTypeRevision \> com um valor de 8.1. Siga as etapas a seguir para o elemento \< PropertyGroup \>:  
  
    1.  Adicione um elemento \< WindowsTargetPlatformVersion \> e um elemento \< WindowsTargetPlatformMinVersion \> e lhes o valor da versão de plataforma Windows Universal que você instalou.  
  
    2.  Atualize o valor do elemento ApplicationTypeRevision do 8.1 10.0.  
  
    3.  Altere o valor do elemento \< MinimumVisualStudioVersion \> para: 14.  
  
    4.  Adicione um elemento \< EnableDotNetNativeCompatibleProfile \> e defina seu valor como: true.  
  
    5.  A escala do ativo padrão para aplicativos universais Windows é 200. Se seu projeto inclui ativos não dimensionados em 200, você precisará adicionar um elemento \< UapDefaultAssetScale \> com o valor da escala de seus ativos para essa PropertyGroup. Saiba mais sobre [ativos e escalas](http://msdn.microsoft.com/library/jj679352.aspx).  
  
    6.  Para o Windows Phone projetos somente, altere o valor de \< ApplicationType \> do Windows Phone para Windows Store.  
  
         Agora o elemento \< PropertyGroup \> deve ser semelhante a este exemplo:  
  
        ```xml  
        <PropertyGroup> … <WindowsTargetPlatformVersion>10.0.10240.0</WindowsTargetPlatformVersion> <WindowsTargetPlatformMinVersion>10.0.10240.0</WindowsTargetPlatformMinVersion> <ApplicationType>Windows Store</ApplicationType> <ApplicationTypeRevision>10.0</ApplicationTypeRevision> <MinimumVisualStudioVersion>14</MinimumVisualStudioVersion> <EnableDotNetNativeCompatibleProfile>true</EnableDotNetNativeCompatibleProfile> <UapDefaultAssetScale>100</UapDefaultAssetScale> … </PropertyGroup>  
        ```  
  
4.  Altere todas as instâncias do elemento \< PlatformToolset \> para que o valor v140. Por exemplo:  
  
    ```xml  
    <PropertyGroup Condition="'$(Configuration)|$(Platform)'=='Release|Win32'" Label="Configuration"> <ConfigurationType>Application</ConfigurationType> <UseDebugLibraries>false</UseDebugLibraries> <WholeProgramOptimization>true</WholeProgramOptimization> <PlatformToolset>v140</PlatformToolset> <UseDotNetNativeToolchain>true</UseDotNetNativeToolchain> </PropertyGroup>  
    ```  
  
5.  Para cada elemento \< PropertyGroup \> restante, verifique se o elemento tem um atributo de condição com uma configuração de versão. Se ele faz, mas ele não contém um elemento \< UseDotNetNativeToolchain \>, adicione um. Defina o valor para o elemento \< UseDotNetNativeToolchain \> como true, como este:  
  
    ```xml  
    <PropertyGroup Condition="'$(Configuration)|$(Platform)'=='Release|X64'" Label="Configuration"> <ConfigurationType>Application</ConfigurationType> <UseDebugLibraries>false</UseDebugLibraries> <WholeProgramOptimization>true</WholeProgramOptimization> <PlatformToolset>v140</PlatformToolset> <UseDotNetNativeToolchain>true</UseDotNetNativeToolchain> </PropertyGroup>  
  
    ```  
  
6.  Salve suas alterações. Feche o arquivo de projeto.  
  
7.  Em seu arquivo de projeto no Solution Explorer e escolha Recarregar projeto no menu de contexto. Todos os arquivos no seu projeto agora devem ser exibidos no Gerenciador de soluções.  
  
     Agora você precisa seguir as etapas para [atualizar os arquivos de manifesto de pacote](#PackageManifest) para todos os seus projetos da Windows Store 8.1 ou Windows Phone 8.1.  
  
##  <a name="PackageManifest"></a> Atualizar o arquivo de manifesto de pacote para projetos de todos os Windows Store 8.1 ou Windows Phone 8.1  
 Você deve atualizar o arquivo de manifesto de pacote para cada projeto na solução.  
  
#### Atualizar o arquivo de manifesto de pacote  
  
1.  Abra o arquivo appxmanifest em seu projeto. Você precisa editar o arquivo appxmanifest para cada um dos projetos da Windows Store e Windows Phone.  
  
2.  Você precisa atualizar o elemento \< Package \> com os esquemas de novos com base em seu tipo de projeto existente. Primeiro remova os esquemas abaixo com base na existência de um projeto da Windows Store ou Windows Phone.  
  
     **Antigo para o projeto da Windows Store:** o elemento \< Package \> será semelhante a este.  
  
    ```xml  
    <Package xmlns="http://schemas.microsoft.com/appx/2010/manifest" xmlns:m2="http://schemas.microsoft.com/appx/2013/manifest">  
  
    ```  
  
     **Projeto antigo para Windows Phone:** o elemento \< Package \> será semelhante a este.  
  
    ```xml  
    <Package xmlns="http://schemas.microsoft.com/appx/2010/manifest" xmlns:m2="http://schemas.microsoft.com/appx/2013/manifest" xmlns:m3="http://schemas.microsoft.com/appx/2014/manifest" xmlns:mp="http://schemas.microsoft.com/appx/2014/phone/manifest">  
    ```  
  
     **Novo para a plataforma Windows Universal:** adicionar esquemas abaixo para o elemento \< Package \>. Remova quaisquer prefixos de identificador de namespace associado a elementos para os esquemas que você acabou de remover. Atualize a propriedade IgnorableNamespaces: uap mp. O elemento \< Package \> Novo deve ser semelhante a este.  
  
    ```xml  
    <Package xmlns="http://schemas.microsoft.com/appx/manifest/foundation/windows10" xmlns:uap="http://schemas.microsoft.com/appx/manifest/uap/windows10" xmlns:mp="http://schemas.microsoft.com/appx/2014/phone/manifest" IgnorableNamespaces= "uap mp">  
  
    ```  
  
3.  Adicione um elemento filho de \< dependências \> para o elemento \< Package \>. Em seguida, adicione um elemento filho de \< TargetDeviceFamily \> para este elemento \< dependências \> com atributos de nome e MinVersion MaxVersionTested. Fornecer o valor de atributo Name: Windows.Universal. Conceda ao MinVersion e MaxVersionTested o valor da versão da plataforma Windows Universal que você instalou. Esse elemento deve ser semelhante a esta:  
  
    ```xml  
    <Dependencies> <TargetDeviceFamily Name="Windows.Universal" MinVersion="10.0.10069.0" MaxVersionTested="10.0.10069.0" /> </Dependencies>  
    ```  
  
4.  **Para a Windows Store apenas:** você precisa adicionar um elemento filho de \< mp:PhoneIdentity \> para o elemento \< Package \>. Adicione um atributo de PhoneProductId e um atributo PhonePublisherId. Defina PhoneProductId para ter o mesmo valor que o atributo Name no elemento \< identidade \>. Defina o valor de PhonePublishedId como: 00000000\-0000\-0000\-0000\-000000000000. Como este:  
  
    ```xml  
    <Identity Name="aa3815a1-2d97-4c71-8c99-578135b28cd8" Publisher="CN=xxxxxxxx" Version="1.0.0.0" /> <mp:PhoneIdentity PhoneProductId="aa3815a1-2d97-4c71-8c99-578135b28cd8" PhonePublisherId="00000000-0000-0000-0000-000000000000"/>  
    ```  
  
5.  Localize o elemento \< pré\-requisitos \> e excluir esse elemento e todos os elementos filho que ele tem.  
  
6.  Adicionar o **uap** namespace para os seguintes elementos \< recurso \>: escala, DXFeatureLevel. Por exemplo:  
  
    ```xml  
    <Resources> <Resource Language="en-us"/> <Resource uap:Scale="180"/> <Resource uap:DXFeatureLevel="dx11"/> </Resources>  
  
    ```  
  
7.  Adicionar o **uap** namespace para os seguintes elementos \< recurso \>: documentsLibrary, picturesLibrary, videosLibrary, musicLibrary, enterpriseAuthentication, sharedUserCertificates, removableStorage, compromissos e contatos. Por exemplo:  
  
    ```xml  
    <Capabilities> <uap:Capability Name="documentsLibrary"/> <uap:Capability Name="removableStorage"/> </Capabilities>  
  
    ```  
  
8.  Adicionar o **uap** namespace para o elemento \< VisualElements \> e qualquer de seus elementos filho. Por exemplo:  
  
    ```xml  
    <uap:VisualElements DisplayName="My WWA App" Square150x150Logo="images/150x150.png" Square44x44Logo="images/44x44.png" Description="My WWA App" BackgroundColor="#777777"> <uap:SplashScreen Image="images/splash.png"/> </uap:VisualElements>  
  
    ```  
  
     **Só se aplica a Windows Store:** os nomes de tamanho de bloco foram alterados. Altere os atributos no elemento \< VisualElements \> para refletir novos tamanhos de bloco convergentes. 71 x 71, se torna 70 x 70 e 30 x 30 se torna 44 x 44.  
  
     **Antigo:** nomes de tamanho de bloco  
  
    ```xml  
    <m2:VisualElements … Square30x30Logo="Assets\SmallLogo.png" …> <m2:DefaultTile … Square70x70Logo="images/70x70.png"> </m2:VisualElements>  
  
    ```  
  
     **Novo:** nomes de tamanho de bloco  
  
    ```xml  
    <uap:VisualElements … Square44x44Logo="Assets\SmallLogo.png" …> <uap:DefaultTile … Square71x71Logo="images/70x70.png"> </uap:VisualElements>  
  
    ```  
  
9. Adicionar o **uap** namespace \< ApplicationContentUriRules \> e todos os seus elementos filho. Por exemplo:  
  
    ```xml  
    <uap:ApplicationContentUriRules> <uap:Rule Type="include" Match="https://www.microsoft.com/"/> <uap:Rule Type="exclude" Match="*.pdf"/> </uap:ApplicationContentUriRules>  
  
    ```  
  
10. Adicionar o **uap** namespace para os seguintes elementos \< extensão \> e todos os seus elementos filho: windows.accountPictureProvide, windows.alarm, windows.appointmentsProvider windows.autoPlayContent, windows.autoPlayDevice, windows.cachedFileUpdate, windows.cameraSettings, windows.fileOpenPicker, windows.fileTypeAssociation, windows.fileSavePicke, windows.lockScreenCall, windows.printTaskSettings, windows.protocol, windows.search, windows.shareTarget. Por exemplo:  
  
    ```xml  
    <Extensions> <uap:Extension Category="windows.alarm"/> <uap:Extension Category="windows.search" EntryPoint="MyActivateableClassId.baz"/> <uap:Extension Category="windows.protocol"> <uap:Protocol Name="mailto" DesiredView="useHalf"> <uap:DisplayName>MailTo Protocol</uap:DisplayName> </uap:Protocol> </uap:Extension> </Extensions>  
  
    ```  
  
11. Adicionar o **uap** namespace para tarefas em segundo plano do tipo chatMessageNotification. Por exemplo:  
  
    ```xml  
    <Extension Category="windows.backgroundTasks" EntryPoint="Fabrikam.BackgroundTask" Executable="MyBackground.exe"> <BackgroundTasks ServerName="MyBackgroundTasks"> <uap:Task Type="chatMessageNotification"/> </BackgroundTasks> </Extension>  
  
    ```  
  
12. Altere as dependências do framework. Adicionar um nome de editor para todos os elementos \< PackageDependency \> e especificar um MinVersion se ela já não estiver especificada.  
  
     **Antigo:** elemento \< PackageDependency \>  
  
    ```xml  
    <Dependencies> <PackageDependency Name="Microsoft.VCLibs.120.00" /> </Dependencies>  
  
    ```  
  
     **Novo:** elemento \< PackageDependency \>  
  
    ```xml  
    <Dependencies> <PackageDependency Name="Microsoft.VCLibs.120.00" Publisher="CN=Microsoft Corporation, O=Microsoft Corporation, L=Redmond, S=Washington, C=US" MinVersion="12.0.30113.0" /> </Dependencies>  
  
    ```  
  
     Use os valores apropriados do publicador e MinVersion para a estrutura real que você está usando. Lembre\-se de que esses nomes podem ser alteradas Windows 10.  
  
13. Substitua as tarefas do tipo de plano de fundo gattCharacteristicNotification e rfcommConnection uma tarefa de tipo Bluetooth. Por exemplo:  
  
     **ANTIGO:**  
  
    ```xml  
    <Extension Category="windows.backgroundTasks" EntryPoint="Fabrikam.BackgroundTask" Executable="MyBackground.exe"> <BackgroundTasks ServerName="MyBackgroundTasks"> <Task Type="rfcommConnection"/> <Task Type="gattCharacteristicNotification"/> </BackgroundTasks> </Extension>  
    ```  
  
     **Novo:** tarefa de tipo com Bluetooth.  
  
    ```xml  
    <Extension Category="windows.backgroundTasks" EntryPoint="Fabrikam.BackgroundTask" Executable="MyBackground.exe"> <BackgroundTasks ServerName="MyBackgroundTasks"> <Task Type="bluetooth"/> </BackgroundTasks> </Extension>  
    ```  
  
14. Substitua o bluetooth.rfcomm de recursos do dispositivo Bluetooth e bluetooth.genericAttributeProfile com um recurso genérico do Bluetooth. Por exemplo:  
  
     **ANTIGO:**  
  
    ```xml  
    <Capabilities> <m2:DeviceCapability Name="bluetooth.rfcomm"> <m2:Device Id="any"> <m2:Function Type="serviceId:34B1CF4D-1069-4AD6-89B6-E161D79BE4D8"/> </m2:Device> </m2:DeviceCapability> <m2:DeviceCapability Name="bluetooth.genericAttributeProfile"> <m2:Device Id="any"> <m2:Function Type="name:heartRate"/> </m2:Device> </m2:DeviceCapability> </Capabilities>  
    ```  
  
     **Novo:** substituído por um recurso genérico do Bluetooth.  
  
    ```xml  
    <Capabilities> <uap:DeviceCapability Name="bluetooth"/> </Capabilities>  
  
    ```  
  
15. Remova todos os elementos preteridos.  
  
    1.  Esses atributos para \< VisualElements \> foram preteridos e devem ser removidos:  
  
        -   Os atributos de \< VisualElements \>: ForegroundText, ToastCapable  
  
        -   O atributo \< DefaultTile \> DefaultSize  
  
        -   O elemento \< ApplicationView \>  
  
         Por exemplo:  
  
        ```xml  
        <m2:VisualElements … ForegroundText="dark" ToastCapable="true"> <m2:DefaultTile DefaultSize="square150x150Logo"/> <m2:ApplicationView MinWidth="width320"/> </m2:VisualElements>  
  
        ```  
  
    2.  Remova todos os elementos sob essas extensões e extensões de windows.contactPicker e Windows.contact.  
  
16. Salve o arquivo appxmanifest. Em seguida, feche o Visual Studio.  
  
17. É necessário remover alguns arquivos ocultos antes que você pode reabrir a solução.  
  
    1.  Abra o Explorador de arquivos, clique em **exibição** na barra de ferramentas e selecione **itens ocultos** e **extensões de nome de arquivo**. Abra essa pasta em seu computador: \< caminho para o local de sua solução \> \\.vs\\{Project nome} \\v14. Se houver um arquivo com uma extensão de arquivo. suo, excluí\-lo.  
  
    2.  Agora volte para a pasta onde se encontra sua solução. Abra as pastas para projetos existentes em sua solução. Se um arquivo dentro de qualquer uma dessas pastas de projeto tem um. csproj.user ou. vbproj.user extensão, exclua\-o.  
  
         Agora você pode reabrir a solução no Visual Studio. Você está pronto para código, compilar e depurar seu aplicativo usando a plataforma Windows Universal.  
  
         Saiba como [adaptar seu código](https://msdn.microsoft.com/library/windows/apps/dn954974.aspx) para tirar proveito do que há de novo com a plataforma Windows Universal.  
  
##  <a name="PreviousVersions"></a> Alterações necessárias para aplicativos universais Windows existentes criados com o Visual Studio 2015 RC  
 Se você tiver criado aplicativos universais Windows 10 com Visual Studio 2015 RC, você precisa redirecionar seu projeto para usar a versão da plataforma Windows Universal instalado com a versão mais recente do Visual Studio de 2015. Não há suporte para qualquer versão anterior. As alterações necessárias são diferentes dependendo da linguagem usada para criar seu aplicativo:  
  
-   [C \/VB aplicativos](#RCUpdate10CSharp)  
  
-   [Aplicativos do C\+\+](#RCUpdate10CPlusPlus)  
  
###  <a name="RCUpdate10CSharp"></a> Atualize seus projetos \/VB C para usar a plataforma Windows Universal mais recente  
 Quando você abre sua solução para o seu aplicativo existente, você verá que o aplicativo requer uma atualização:  
  
 ![View your project in Solution Explorer](../misc/media/uwp_updaterequired.png "UWP\_UpdateRequired")  
  
 Se você optar por recarregar esse projeto no Gerenciador de soluções, você verá essa caixa de diálogo:  
  
 ![Retarget your app to use the correct SDK](../misc/media/missingsdkforuap.png "MissingSDKforUAP")  
  
 Como o SDK da plataforma Windows Universal para o seu projeto é agora sem suporte, não será possível instalá\-lo. Clique em OK e, em seguida, siga as etapas abaixo.  
  
##### Atualize seus projetos \/VB C para usar a plataforma Windows Universal mais recente  
  
1.  Para localizar qual plataforma Windows Universal você instalou, abra essa pasta: **\\Program Files \(x86\)\\Windows Kits\\10\\Platforms\\UAP**. Ela contém uma lista de pastas para cada plataforma Windows Universal que está instalado. O nome da pasta é a versão da plataforma Windows Universal que você instalou. Por exemplo, este dispositivo Windows 10 tem versão 10.0.10240.0 da plataforma Windows Universal instalada.  
  
     ![Open the folder to view the versions installed](../misc/media/uap_uwpversions.png "UAP\_UWPVersions")  
  
     Mais de uma versão da plataforma Windows Universal pode ser instalada. É recomendável que você use a versão mais recente para seu aplicativo.  
  
2.  Usando o Explorador de arquivos, vá para a pasta onde o projeto UWP está armazenado. Exclua o arquivo Packages e criar um novo arquivo. JSON nessa pasta. Nomeie o arquivo: project.json e, em seguida, adicione o seguinte conteúdo a esse arquivo:  
  
    ```json  
  
    { "dependencies": { "Microsoft.ApplicationInsights": "1.0.0", "Microsoft.ApplicationInsights.PersistenceChannel": "1.0.0", "Microsoft.ApplicationInsights.WindowsApps": "1.0.0", "Microsoft.NETCore.UniversalWindowsPlatform": "5.0.0" }, "frameworks": { "uap10.0": {} }, "runtimes": { "win10-arm": {}, "win10-arm-aot": {}, "win10-x86": {}, "win10-x86-aot": {}, "win10-x64": {}, "win10-x64-aot": {} } }  
  
    ```  
  
3.  Com o Visual Studio, abra a solução que contém seu aplicativo do Windows Universal de \/VB C. Você verá que o seu arquivo de projeto \(arquivo. csproj ou. vbproj\) precisa ser atualizado. Com o botão direito do arquivo de projeto e escolha Editar esse arquivo.  
  
     ![Right click the project and choose Edit](../misc/media/uap_editproject.png "UAP\_EditProject")  
  
4.  Localize o elemento \< PropertyGroup \> que contém \< TargetPlatformVersion \> e \< TargetPlatformMinVersion \> elementos. Altere o valor existente de \< TargetPlatformVersion \> e \< TargetPlatformMinVersion \> elementos para ter a mesma versão da plataforma Windows Universal que você instalou.  
  
     A escala do ativo padrão para aplicativos universais Windows é 200. Projetos criados com ativos do Visual Studio 2015 RC incluídos dimensionados em 100, você precisará adicionar um elemento \< UapDefaultAssetScale \> com um valor de 100 a este PropertyGroup. Saiba mais sobre [ativos e escalas](http://msdn.microsoft.com/library/jj679352.aspx).  
  
5.  Se você tiver adicionado todas as referências a UWP SDKs de extensão \(por exemplo: o Windows Mobile SDK\), você precisará atualizar a versão do SDK. Por exemplo, esse elemento \< SDKReference \>:  
  
    ```xml  
    <SDKReference Include="WindowsMobile, Version=10.0.0.1"> <Name>Microsoft Mobile Extension SDK for Universal App Platform</Name> </SDKReference>  
  
    ```  
  
     Deve ser alterada para isso:  
  
    ```xml  
    <SDKReference Include="WindowsMobile, Version=10.0.10240.0"> <Name>Microsoft Mobile Extension SDK for Universal App Platform</Name> </SDKReference>  
  
    ```  
  
6.  Localize o elemento \< destino \> com um atributo de nome que tem o valor: EnsureNuGetPackageBuildImports. Exclua esse elemento e todos os seus filhos.  
  
    ```xml  
    <Target Name="EnsureNuGetPackageBuildImports" BeforeTargets="PrepareForBuild"> <PropertyGroup> <ErrorText>This project references NuGet package(s) that are missing on this computer. Use NuGet Package Restore to download them.  For more information, see http://go.microsoft.com/fwlink/?LinkID=322105. The missing file is {0}.</ErrorText> </PropertyGroup> <Error Condition="!Exists('..\packages\Microsoft.Diagnostics.Tracing.EventSource.Redist.1.1.16-beta\build\portable-net45+win8+wpa81\Microsoft.Diagnostics.Tracing.EventSource.Redist.targets')" Text="$([System.String]::Format('$(ErrorText)', '..\packages\Microsoft.Diagnostics.Tracing.EventSource.Redist.1.1.16-beta\build\portable-net45+win8+wpa81\Microsoft.Diagnostics.Tracing.EventSource.Redist.targets'))" /> <Error Condition="!Exists('..\packages\Microsoft.ApplicationInsights.0.14.3-build00177\build\portable-win81+wpa81\Microsoft.ApplicationInsights.targets')" Text="$([System.String]::Format('$(ErrorText)', '..\packages\Microsoft.ApplicationInsights.0.14.3-build00177\build\portable-win81+wpa81\Microsoft.ApplicationInsights.targets'))" /> </Target>  
    ```  
  
7.  Localizar e excluir os elementos \< Import \> com atributos de projeto e a condição que fazem referência a Microsoft.Diagnostics.Tracing.EventSource e applicationinsights, assim:  
  
    ```xml  
    <Import Project="..\packages\Microsoft.Diagnostics.Tracing.EventSource.Redist.1.1.16-beta\build\portable-net45+win8+wpa81\Microsoft.Diagnostics.Tracing.EventSource.Redist.targets" Condition="Exists('..\packages\Microsoft.Diagnostics.Tracing.EventSource.Redist.1.1.16-beta\build\portable-net45+win8+wpa81\Microsoft.Diagnostics.Tracing.EventSource.Redist.targets')" /> <Import Project="..\packages\Microsoft.ApplicationInsights.0.14.3-build00177\build\portable-win81+wpa81\Microsoft.ApplicationInsights.targets" Condition="Exists('..\packages\Microsoft.ApplicationInsights.0.14.3-build00177\build\portable-win81+wpa81\Microsoft.ApplicationInsights.targets')" />  
  
    ```  
  
8.  Localizar \< ItemGroup \> com elementos de filhos \< Reference \> para pacotes do NuGet. Anote os pacotes do NuGet referenciados, pois você precisará dessas informações para uma etapa futura. Uma diferença significativa entre o formato do projeto Windows 10 entre o Visual Studio 2015 RC e RTM do Visual Studio 2015 é que usa o formato RTM [NuGet](http://docs.nuget.org/) versão 3.  
  
     Remova \< ItemGroup \> e todos os seus filhos. Por exemplo, um projeto UWP criado com o Visual Studio RC terá os seguintes pacotes do NuGet que precisam ser removidos:  
  
    ```xml  
    <ItemGroup> <Reference Include="Microsoft.ApplicationInsights, Version=0.14.3.177, Culture=neutral, PublicKeyToken=31bf3856ad364e35, processorArchitecture=MSIL"> <HintPath>..\packages\Microsoft.ApplicationInsights.0.14.3-build00177\lib\portable-win81+wpa81\Microsoft.ApplicationInsights.dll</HintPath> <Private>True</Private> </Reference> <Reference Include="Microsoft.ApplicationInsights.Extensibility.Windows, Version=0.14.3.177, Culture=neutral, PublicKeyToken=31bf3856ad364e35, processorArchitecture=MSIL"> <HintPath>..\packages\Microsoft.ApplicationInsights.WindowsApps.0.14.3-build00177\lib\win81\Microsoft.ApplicationInsights.Extensibility.Windows.dll</HintPath> <Private>True</Private> </Reference> <Reference Include="Microsoft.ApplicationInsights.PersistenceChannel, Version=0.14.3.186, Culture=neutral, PublicKeyToken=31bf3856ad364e35, processorArchitecture=MSIL"> <HintPath>..\packages\Microsoft.ApplicationInsights.PersistenceChannel.0.14.3-build00177\lib\portable-win81+wpa81\Microsoft.ApplicationInsights.PersistenceChannel.dll</HintPath> <Private>True</Private> </Reference> <Reference Include="System.Numerics.Vectors, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a, processorArchitecture=MSIL"> <HintPath>..\packages\System.Numerics.Vectors.4.0.0\lib\win8\System.Numerics.Vectors.dll</HintPath> <Private>True</Private> </Reference> <Reference Include="System.Numerics.Vectors.WindowsRuntime, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a, processorArchitecture=MSIL"> <HintPath>..\packages\System.Numerics.Vectors.4.0.0\lib\win8\System.Numerics.Vectors.WindowsRuntime.dll</HintPath> <Private>True</Private> </Reference> </ItemGroup>  
  
    ```  
  
9. Localize o elemento \< ItemGroup \> que contém um elemento \< AppxManifest \>. Se não houver um \< None \> elemento com um atributo de inclusão definido como: Packages, excluí\-la. Além disso, adicione um \< None \> elemento com um inclusão de atributo e defina seu valor como: project.json.  
  
10. Salve suas alterações. Feche o arquivo de projeto.  
  
11. Em seu arquivo de projeto no Solution Explorer e escolha Recarregar projeto no menu de contexto. Todos os arquivos no seu projeto agora devem ser exibidos no Gerenciador de soluções.  
  
12. Selecione o arquivo applicationinsights. config no Solution Explorer e abra suas propriedades. Defina a propriedade Build Action para "Conteúdo" e a cópia à propriedade de diretório de saída para "Copiar se mais recente".  
  
13. Abra o arquivo appxmanifest em seu projeto.  
  
    1.  Localize o elemento \< TargetDeviceFamily \>. Altere seus atributos MinVersion e MaxVersionTested para corresponder à versão plataforma Windows Universal que você instalou. Como este:  
  
        ```xml  
        <TargetDeviceFamily Name="Windows.Universal" MinVersion="10.0.10240.0" MaxVersionTested="10.0.10240.0" />  
        ```  
  
    2.  Salve suas alterações.  
  
14. Use o Gerenciador de NuGet para adicionar os pacotes que você excluiu na etapa anterior. Uma diferença significativa entre o formato do projeto Windows 10 entre o Visual Studio 2015 RC e RTM do Visual Studio 2015 é que usa o formato RTM [NuGet](http://docs.nuget.org/) versão 3.  
  
 Agora você pode codificar, compilar e depurar seu aplicativo.  
  
 Se você tiver projetos de teste de unidade para seus aplicativos Windows universais, você também deve seguir [essas etapas](#MigrateUnitTest).  
  
###  <a name="RCUpdate10CPlusPlus"></a> Atualizar seus projetos do C\+\+ para usar a plataforma Windows Universal mais recente  
  
1.  Para localizar qual plataforma Windows Universal você instalou, abra essa pasta: **\\Program Files \(x86\)\\Windows Kits\\10\\Platforms\\UAP**. Ela contém uma lista de pastas para cada plataforma Windows Universal que está instalado. O nome da pasta é a versão da plataforma Windows Universal que você instalou. Por exemplo, este dispositivo Windows 10 tem versão 10.0.10240.0 da plataforma Windows Universal instalada.  
  
     ![Open the folder to view the versions installed](../misc/media/uap_uwpversions.png "UAP\_UWPVersions")  
  
     Mais de uma versão da plataforma Windows Universal pode ser instalada. É recomendável que você use a versão mais recente para seu aplicativo.  
  
2.  Abra a solução que contém o aplicativo Universal de Windows do C\+\+. Clique o arquivo. vcxproj do projeto e escolha descarregar o arquivo de projeto. Depois que o projeto foi descarregado, clique novamente o arquivo de projeto e escolha para editá\-lo.  
  
     ![Unload the project, then edit the project file](../misc/media/uap_editearliercplus.png "UAP\_EditEarlierCPlus")  
  
3.  Localiza todos os elementos \< PropertyGroup \> contém um atributo de condição, mas contém um elemento \< ApplicationTypeRevision \>. Atualize o valor de ApplicationTypeRevision de 8.2 para 10.0. Adicione um elemento de \< WindowsTargetPlatformMinVersion \> e \< WindowsTargetPlatformVersion \> e defina seus valores como o valor da versão de plataforma Windows Universal que você instalou.  
  
     Adicione um elemento \< EnableDotNetNativeCompatibleProfile \> e defina seu valor como verdadeiro se o elemento ainda não existir.  
  
     A escala do ativo padrão para aplicativos universais Windows é 200. Projetos criados com ativos do Visual Studio 2015 RC incluídos dimensionados em 100, você precisará adicionar um elemento \< UapDefaultAssetScale \> com um valor de 100 a este PropertyGroup. Saiba mais sobre [ativos e escalas](http://msdn.microsoft.com/library/jj679352.aspx).  
  
     Então esse elemento \< PropertyGroup \> agora será semelhante a este:  
  
    ```xml  
    <PropertyGroup Label="Globals"> … <MinimumVisualStudioVersion>14.0</MinimumVisualStudioVersion> <ApplicationType>Windows Store</ApplicationType> <ApplicationTypeRevision>10.0</ApplicationTypeRevision> <WindowsTargetPlatformVersion>10.0.10240.0</WindowsTargetPlatformVersion> <WindowsTargetPlatformMinVersion>10.0.10240.0</WindowsTargetPlatformMinVersion> <EnableDotNetNativeCompatibleProfile>true</EnableDotNetNativeCompatibleProfile> <UapDefaultAssetScale>100</UapDefaultAssetScale> </PropertyGroup>  
  
    ```  
  
4.  Para cada elemento \< PropertyGroup \> restante, verifique se o elemento tem um atributo de condição com uma configuração de versão. Se ele faz, mas ele não contém um elemento \< UseDotNetNativeToolchain \>, adicione um. Defina o valor para o elemento \< UseDotNetNativeToolchain \> como true, como este:  
  
    ```xml  
    <PropertyGroup Condition="'$(Configuration)|$(Platform)'=='Release|Win32'" Label="Configuration"> <ConfigurationType>Application</ConfigurationType> <UseDebugLibraries>false</UseDebugLibraries> <WholeProgramOptimization>true</WholeProgramOptimization> <PlatformToolset>v140</PlatformToolset> <UseDotNetNativeToolchain>true</UseDotNetNativeToolchain> </PropertyGroup>  
  
    ```  
  
5.  Você precisa atualizar o elemento \< EnableDotNetNativeCompatibleProfile \> e o elemento \< UseDotNetNativeToolchain \> para habilitar o .NET nativo, mas não é nativo do .NET habilitado nos modelos C\+\+.  
  
     Salve suas alterações. Feche o arquivo de projeto.  
  
6.  Em seu arquivo de projeto no Solution Explorer e escolha Recarregar projeto no menu de contexto. Todos os arquivos no seu projeto agora devem ser exibidos no Gerenciador de soluções.  
  
7.  Abra o arquivo appxmanifest em seu projeto.  
  
    1.  Localize o elemento \< TargetDeviceFamily \>. Altere seus atributos MinVersion e MaxVersionTested para corresponder à versão plataforma Windows Universal que você instalou. Como este:  
  
        ```xml  
        <TargetDeviceFamily Name="Windows.Universal" MinVersion="10.0.10240.0" MaxVersionTested="10.0.10240.0" />  
        ```  
  
    2.  Salve suas alterações.  
  
         Agora você pode codificar, compilar e depurar seu aplicativo.  
  
         Se você tiver projetos de teste de unidade para seus aplicativos Windows universais, você também deve seguir [essas etapas](#MigrateUnitTest).  
  
##  <a name="MigrateUnitTest"></a> Alterações necessárias para projetos de teste de unidade existente para aplicativos Windows universais criados com o Visual Studio 2015 RC  
 Se você criou a unidade de projetos de teste para aplicativos universais Windows 10 com Visual Studio 2015 RC, você precisa fazer essas alterações adicionais ao seu projeto de projetos com a versão mais recente do Visual Studio de 2015 de teste de arquivos para usá\-los. As alterações necessárias são diferentes dependendo da linguagem usada para criar seu aplicativo:  
  
-   [C \/VB aplicativos](#UnitTestRCUpdate10CSharp)  
  
-   [Aplicativos do C\+\+](#UnitTestRCUpdate10CPlusPlus)  
  
###  <a name="UnitTestRCUpdate10CSharp"></a> Atualizar seus projetos de teste de unidade \/VB C  
  
1.  Com o Visual Studio, abra a solução que contém o projeto de teste de unidade C \/VB. Altere o valor do elemento \< OuttputType \> para: AppContainerExe.  
  
    ```xml  
  
    <OutputType>AppContainerExe</OutputType>  
  
    ```  
  
2.  Substituir isso como false elemento \< EnableCoreRuntime \> \< \/ EnableCoreRuntime \> com o seguinte elemento:  
  
    ```xml  
  
    <EnableDotNetNativeCompatibleProfile>true</EnableDotNetNativeCompatibleProfile>  
  
    ```  
  
3.  Remova as seguintes linhas:  
  
    ```xml  
  
    <PropertyGroup> <AppXPackage>True</AppXPackage> <AppxPackageIncludePrivateSymbols>true</AppxPackageIncludePrivateSymbols> </PropertyGroup> <PropertyGroup Condition=" '$(Configuration)|$(Platform)' == 'Debug|AnyCPU' "> <PlatformTarget>AnyCPU</PlatformTarget> <DebugSymbols>true</DebugSymbols> <DebugType>full</DebugType> <Optimize>false</Optimize> <OutputPath>bin\Debug\</OutputPath> <DefineConstants>DEBUG;TRACE;NETFX_CORE;WINDOWS_UAP</DefineConstants> <ErrorReport>prompt</ErrorReport> <WarningLevel>4</WarningLevel> </PropertyGroup> <PropertyGroup Condition=" '$(Configuration)|$(Platform)' == 'Release|AnyCPU' "> <PlatformTarget>AnyCPU</PlatformTarget> <DebugType>pdbonly</DebugType> <Optimize>true</Optimize> <OutputPath>bin\Release\</OutputPath> <DefineConstants>TRACE;NETFX_CORE;WINDOWS_UAP</DefineConstants> <ErrorReport>prompt</ErrorReport> <WarningLevel>4</WarningLevel> </PropertyGroup>  
  
    ```  
  
4.  Adicionar isso é verdade elemento \< UseDotNetNativeToolchain \> \< \/ UseDotNetNativeToolchain \> como um elemento filho a esses grupos de propriedade:  
  
    ```xml  
  
    <PropertyGroup Condition="'$(Configuration)|$(Platform)' == 'Release|ARM'"> <PropertyGroup Condition="'$(Configuration)|$(Platform)' == 'Release|X86'"> <PropertyGroup Condition="'$(Configuration)|$(Platform)' == 'Release|X64'">  
  
    ```  
  
5.  Exclua os seguintes elementos \< ItemGroup \>:  
  
    ```xml  
  
    <ItemGroup> <Compile Include="Properties\AssemblyInfo.cs" /> <Compile Include="UnitTest.cs" /> </ItemGroup> <ItemGroup> <AppxManifest Include="Package.appxmanifest"> <SubType>Designer</SubType> </AppxManifest> <None Include="packages.config" /> <None Include="UnitTestProject1_TemporaryKey.pfx" /> </ItemGroup> <ItemGroup> <Content Include="Properties\Default.rd.xml" /> <Content Include="Assets\Logo.scale-240.png" /> <Content Include="Assets\SmallLogo.scale-240.png" /> <Content Include="Assets\SplashScreen.scale-240.png" /> <Content Include="Assets\Square71x71Logo.scale-240.png" /> <Content Include="Assets\StoreLogo.scale-240.png" /> <Content Include="Assets\WideLogo.scale-240.png" /> </ItemGroup>  
  
    ```  
  
     Substituí\-los com estes elementos:  
  
    ```xml  
  
    <ItemGroup> <Compile Include="Properties\AssemblyInfo.cs" /> <Compile Include="UnitTestApp.xaml.cs"> <DependentUpon>UnitTestApp.xaml</DependentUpon> </Compile> <Compile Include="UnitTest.cs" /> </ItemGroup> <ItemGroup> <ApplicationDefinition Include="UnitTestApp.xaml"> <Generator>MSBuild:Compile</Generator> <SubType>Designer</SubType> </ApplicationDefinition> </ItemGroup> <ItemGroup> <AppxManifest Include="Package.appxmanifest"> <SubType>Designer</SubType> </AppxManifest> <None Include="UnitTestProject1_TemporaryKey.pfx" /> </ItemGroup> <ItemGroup> <Content Include="Properties\UnitTestApp.rd.xml" /> <Content Include="Assets\LockScreenLogo.scale-200.png" /> <Content Include="Assets\SplashScreen.scale-200.png" /> <Content Include="Assets\Square150x150Logo.scale-200.png" /> <Content Include="Assets\Square44x44Logo.scale-200.png" /> <Content Include="Assets\Square44x44Logo.targetsize-24_altform-unplated.png" /> <Content Include="Assets\StoreLogo.png" /> <Content Include="Assets\Wide310x150Logo.scale-200.png" /> </ItemGroup>  
    ```  
  
6.  Crie um novo projeto de teste de unidade e copie os arquivos UnitTestApp.xaml e UnitTestApp.xaml.cs do novo projeto ao seu projeto de teste de unidade existente que você está atualizando.  
  
7.  Copie o arquivo de UnitTestApp.rd.xml da pasta propriedades do novo projeto de teste de unidade para a pasta de propriedades do seu projeto de teste de unidade existente que você está atualizando.  
  
8.  Abra o arquivo appxmanifest em seu projeto. Exclua esses elementos dela:  
  
    ```xml  
  
    <Applications> <Application Id="vstest.executionengine.universal.App" Executable="vstest.executionengine.appcontainer.uap.exe" EntryPoint="Microsoft.VisualStudio.TestPlatform.TestExecutor.AppContainer.App"> <uap:VisualElements DisplayName="UnitTestProject1" Square150x150Logo="Assets\Logo.png" Square44x44Logo="Assets\SmallLogo.png" Description="UnitTestProject1" BackgroundColor="#464646"> <uap:SplashScreen Image="Assets\SplashScreen.png" /> </uap:VisualElements> </Application> </Applications> <Capabilities> <Capability Name="internetClientServer" /> </Capabilities>  
    ```  
  
     Substitua esses elementos excluídos com os seguintes elementos. Use o valor apropriado para ProjectName com base no nome do seu projeto, em vez de UnitTestProject1 nos elementos abaixo:  
  
    ```xml  
  
    <Applications> <Application Id="vstest.executionengine.universal.App" Executable="$targetnametoken$.exe" EntryPoint="UnitTestProject1.App"> <uap:VisualElements DisplayName="UnitTestProject1" Square150x150Logo="Assets\Square150x150Logo.png" Square44x44Logo="Assets\Square44x44Logo.png" Description="UnitTestProject1" BackgroundColor="transparent"> <uap:DefaultTile Wide310x150Logo="Assets\Wide310x150Logo.png"/> <uap:SplashScreen Image="Assets\SplashScreen.png" /> </uap:VisualElements> </Application> </Applications> <Capabilities> <Capability Name="internetClient" /> </Capabilities>  
    ```  
  
 Agora você pode executar seus testes de unidade.  
  
###  <a name="UnitTestRCUpdate10CPlusPlus"></a> Atualizar seus projetos do C\+\+ para usar a plataforma Windows Universal mais recente  
  
1.  Com o Visual Studio, abra a solução que contém seu projeto de teste de unidade do C\+\+. Remova os seguintes elementos:  
  
    ```xml  
  
    <TestApplication>true</TestApplication> <AppxPackage>True</AppxPackage> <CppWindowsStoreUnitTestLibraryType>true</CppWindowsStoreUnitTestLibraryType> <EnableCoreRuntime>false</EnableCoreRuntime>  
  
    ```  
  
2.  Adicione os seguintes elementos \< ProjectConfiguration \> abaixo desse elemento \< ItemGroup rótulo \= "ProjectConfigurations" \> se ainda não estiverem nesse preenchimento:  
  
    ```xml  
  
    <ProjectConfiguration Include="Debug|x64"> <Configuration>Debug</Configuration> <Platform>x64</Platform> </ProjectConfiguration> <ProjectConfiguration Include="Release|x64"> <Configuration>Release</Configuration> <Platform>x64</Platform> </ProjectConfiguration>  
  
    ```  
  
3.  Substitua todas as ocorrências desse elemento:  
  
    ```xml  
  
    <ConfigurationType>DynamicLibrary</ConfigurationType>  
  
    ```  
  
     Com isso:  
  
    ```xml  
  
    <ConfigurationType>Application</ConfigurationType>  
  
    ```  
  
4.  Adicione esses elementos \< PropertyGroup \> se ainda não estiverem no arquivo:  
  
    ```xml  
  
    <PropertyGroup Condition="'$(Configuration)|$(Platform)'=='Debug|x64'" Label="Configuration"> <ConfigurationType>Application</ConfigurationType> <UseDebugLibraries>true</UseDebugLibraries> <PlatformToolset>v140</PlatformToolset> </PropertyGroup> <PropertyGroup Condition="'$(Configuration)|$(Platform)'=='Release|x64'" Label="Configuration"> <ConfigurationType>Application</ConfigurationType> <UseDebugLibraries>false</UseDebugLibraries> <WholeProgramOptimization>true</WholeProgramOptimization> <PlatformToolset>v140</PlatformToolset> <UseDotNetNativeToolchain>true</UseDotNetNativeToolchain> </PropertyGroup>  
  
    ```  
  
5.  Substitua todas as ocorrências desse elemento:  
  
    ```xml  
  
    <AdditionalIncludeDirectories>$(VCInstallDir)UnitTest\include;$(ProjectDir);$(IntermediateOutputPath);%(AdditionalIncludeDirectories)</AdditionalIncludeDirectories>  
    ```  
  
     Com isso:  
  
    ```xml  
  
    <AdditionalIncludeDirectories>$(VCInstallDir)UnitTest\include\UWP;$(ProjectDir);$(IntermediateOutputPath);%(AdditionalIncludeDirectories)</AdditionalIncludeDirectories>  
  
    ```  
  
6.  Substitua todas as ocorrências desse elemento:  
  
    ```xml  
  
    <AdditionalLibraryDirectories>$(VCInstallDir)UnitTest\Lib;%(AdditionalLibraryDirectories)</AdditionalLibraryDirectories>  
  
    ```  
  
     Com isso:  
  
    ```xml  
  
    <AdditionalLibraryDirectories>$(VCInstallDir)UnitTest\lib\UWP;%(AdditionalLibraryDirectories)</AdditionalLibraryDirectories>  
  
    ```  
  
7.  Adicione esses elementos \< ItemDefinitionGroup \> na seção que já contenha outros elementos \< ItemDefinitionGroup \>:  
  
    ```xml  
  
    <ItemDefinitionGroup Condition="'$(Configuration)|$(Platform)'=='Debug|x64'"> <ClCompile> <AdditionalOptions>/bigobj %(AdditionalOptions)</AdditionalOptions> <DisableSpecificWarnings>4453;28204</DisableSpecificWarnings> <AdditionalIncludeDirectories>$(VCInstallDir)UnitTest\include\UWP;$(ProjectDir);$(IntermediateOutputPath);%     (AdditionalIncludeDirectories)</AdditionalIncludeDirectories> </ClCompile> <Link> <AdditionalLibraryDirectories>$(VCInstallDir)UnitTest\lib\UWP;%(AdditionalLibraryDirectories)</AdditionalLibraryDirectories> </Link> </ItemDefinitionGroup> <ItemDefinitionGroup Condition="'$(Configuration)|$(Platform)'=='Release|x64'"> <ClCompile> <AdditionalOptions>/bigobj %(AdditionalOptions)</AdditionalOptions> <DisableSpecificWarnings>4453;28204</DisableSpecificWarnings> <AdditionalIncludeDirectories>$(VCInstallDir)UnitTest\include\UWP;$(ProjectDir);$(IntermediateOutputPath);%(AdditionalIncludeDirectories)</AdditionalIncludeDirectories> </ClCompile> <Link> <AdditionalLibraryDirectories>$(VCInstallDir)UnitTest\lib\UWP;%(AdditionalLibraryDirectories)</AdditionalLibraryDirectories> </Link> </ItemDefinitionGroup>  
  
    ```  
  
8.  Exclua o seguinte elemento \< ItemGroup \>:  
  
    ```xml  
  
    <ItemGroup> <Image Include="Assets\Logo.scale-100.png" /> <Image Include="Assets\SmallLogo.scale-100.png" /> <Image Include="Assets\StoreLogo.scale-100.png" /> <Image Include="Assets\SplashScreen.scale-100.png" /> <Image Include="Assets\WideLogo.scale-100.png" /> </ItemGroup>  
  
    ```  
  
     Substitua este elemento \< ItemGroup \>:  
  
    ```xml  
  
    <ItemGroup> <Image Include="Assets\LockScreenLogo.scale-200.png" /> <Image Include="Assets\SplashScreen.scale-200.png" /> <Image Include="Assets\Square44x44Logo.scale-200.png" /> <Image Include="Assets\Square44x44Logo.targetsize-24_altform-unplated.png" /> <Image Include="Assets\Square150x150Logo.scale-200.png" /> <Image Include="Assets\StoreLogo.png" /> <Image Include="Assets\Wide310x150Logo.scale-200.png" /> </ItemGroup>  
  
    ```  
  
9. Exclua o seguinte elemento \< ItemGroup \>:  
  
    ```xml  
  
    <ItemGroup> <ClInclude Include="pch.h" /> </ItemGroup>  
    ```  
  
     Substitua esses elementos \< ItemGroup \>:  
  
    ```xml  
  
    <ItemGroup> <ClInclude Include="pch.h" /> <ClInclude Include="UnitTestApp.xaml.h"> <DependentUpon>UnitTestApp.xaml</DependentUpon> </ClInclude> </ItemGroup> <ItemGroup> <ApplicationDefinition Include="UnitTestApp.xaml"> <SubType>Designer</SubType> </ApplicationDefinition> </ItemGroup>  
  
    ```  
  
10. Exclua o elemento a seguir:  
  
    ```xml  
    <ClCompile Include="UnitTest.cpp"/>  
    ```  
  
     Substitua esses elementos \< CICompile \>:  
  
    ```xml  
  
    <ClCompile Include="UnitTestApp.xaml.cpp"> <DependentUpon>UnitTestApp.xaml</DependentUpon> </ClCompile> <ClCompile Include="UnitTest.cpp"/>  
  
    ```  
  
11. Adicione esse elemento:  
  
    ```xml  
    <Import Project="$(VCTargetsPath)\Microsoft.Cpp.targets" />  
    ```  
  
     Acima deste elemento no arquivo:  
  
    ```xml  
  
    <ItemGroup> <Xml Include="UnitTestApp.rd.xml" /> </ItemGroup>  
    ```  
  
12. Criar um novo projeto C\+\+ do teste de unidade e copie os arquivos UnitTestApp.xaml, UnitTestApp.xaml.cpp, UnitTestApp.xaml.h e UnitTestApp.rd.xml do projeto ao seu projeto existente que você está atualizando.  
  
13. Abra o arquivo appxmanifest em seu projeto. Exclua esses elementos dela:  
  
    ```xml  
  
    <Applications> <Application Id="vstest.executionengine.universal.App" Executable="vstest.executionengine.appcontainer.uap.exe" EntryPoint="Microsoft.VisualStudio.TestPlatform.TestExecutor.AppContainer.App"> <uap:VisualElements DisplayName="UnitTestProject1" Square150x150Logo="Assets\Logo.png" Square44x44Logo="Assets\SmallLogo.png" Description="UnitTestProject1" BackgroundColor="#464646"> <uap:SplashScreen Image="Assets\SplashScreen.png" /> </uap:VisualElements> </Application> </Applications> <Capabilities> <Capability Name="internetClientServer" /> </Capabilities>  
  
    ```  
  
     Substitua esses elementos excluídos com os seguintes elementos. Use o valor apropriado para ProjectName com base no nome do seu projeto, em vez de UnitTestProject1 nos elementos abaixo:  
  
    ```xml  
  
    <Applications> <Application Id="vstest.executionengine.universal.App" Executable="$targetnametoken$.exe" EntryPoint="UnitTestProject1.App"> <uap:VisualElements DisplayName="UnitTestProject1" Square150x150Logo="Assets\Square150x150Logo.png" Square44x44Logo="Assets\Square44x44Logo.png" Description="UnitTestProject1" BackgroundColor="transparent"> <uap:DefaultTile Wide310x150Logo="Assets\Wide310x150Logo.png"/> <uap:SplashScreen Image="Assets\SplashScreen.png" /> </uap:VisualElements> </Application> </Applications> <Capabilities> <Capability Name="internetClient" /> </Capabilities>  
  
    ```