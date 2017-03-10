---
title: "Tarefa GenerateApplicationManifest | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/developer/msbuild/2003#GenerateApplicationManifest"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "Tarefa GenerateApplicationManifest [MSBuild]"
  - "propriedade HostInBrowser (MSBuild)"
  - "MSBuild, Tarefa GenerateApplicationManifest"
ms.assetid: a494102b-0cb2-4755-8e2a-d2c0f39fac1d
caps.latest.revision: 24
caps.handback.revision: 24
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Tarefa GenerateApplicationManifest
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Gerencia um manifesto de aplicativo do [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] ou um manifesto nativo.  Um manifesto nativo descreve um componente definindo uma identidade exclusiva para o componente e identificando todos os assemblies e os arquivos que compõem o componente.  Um manifesto de aplicativo de [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] estende um manifesto nativo indicando o ponto de entrada do aplicativo, especificando o nível de segurança do aplicativo.  
  
## Parâmetros  
 A tabela a seguir descreve os parâmetros para a tarefa `GenerateApplicationManifest`.  
  
|Parâmetro|Descrição|  
|---------------|---------------|  
|`AssemblyName`|Parâmetro opcional de `String`.<br /><br /> Especifica o campo `Name` da identidade do assembly para o manifesto gerado.  Se este parâmetro não for especificado, o nome é inferido pelos parâmetros de `EntryPoint` ou de `InputManifest`.  Se nenhum nome puder ser criado, a tarefa gerará um erro.|  
|`AssemblyVersion`|Parâmetro opcional de `String`.<br /><br /> Especifica o campo `Version` da identidade do assembly para o manifesto gerado.  Se esse parâmetro não for especificado, um valor padrão de "1.0.0.0" será usado.|  
|`ClrVersion`|Parâmetro opcional de `String`.<br /><br /> Especifica a versão mínima do CLR \(Common Language Runtime\) exigida pelo aplicativo.  O valor padrão é a versão do CLR em uso pelo sistema de compilação.  Caso a tarefa esteja gerando um manifesto nativo, esse parâmetro será ignorado.|  
|`ConfigFile`|Parâmetro opcional de <xref:Microsoft.Build.Framework.ITaskItem>`[]`.<br /><br /> Especifica o item que contém o arquivo de configuração do aplicativo.  Caso a tarefa esteja gerando um manifesto nativo, esse parâmetro será ignorado.|  
|`Dependencies`|Parâmetro opcional de <xref:Microsoft.Build.Framework.ITaskItem>`[]`.<br /><br /> Especifica uma lista de itens que define o conjunto de assemblies dependentes para o manifesto gerado.  Cada item pode ser descrito com mais detalhes por metadados de item para indicar o estado adicional de implantação e o tipo de dependência.  Para obter mais informações, consulte a seção "Metadados de Itens " a seguir.|  
|`Description`|Parâmetro opcional de `String`.<br /><br /> Especifica a descrição para o aplicativo ou componente.|  
|`EntryPoint`|Parâmetro opcional de <xref:Microsoft.Build.Framework.ITaskItem>`[]`.<br /><br /> Especifica um único item que indica o ponto de entrada para o assembly do manifesto gerado.<br /><br /> Para um manifesto de aplicativo de [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)], este parâmetro especifica o assembly que inicia quando o aplicativo é executado.|  
|`ErrorReportUrl`|Parâmetro opcional de [String](assetId:///String?qualifyHint=False&autoUpgrade=True).<br /><br /> Especifica a URL da página da Web que é exibida em caixas de diálogo durante relatórios de erro em instalações do ClickOnce.|  
|`FileAssociations`|Parâmetro opcional de <xref:Microsoft.Build.Framework.ITaskItem>`[]`.<br /><br /> Especifica uma lista de um ou mais tipos de arquivo associados ao manifesto de implantação do ClickOnce.<br /><br /> As associações de arquivos são válidas somente quando o .NET Framework 3.5 ou posterior é tido como alvo.|  
|`Files`|Parâmetro opcional de <xref:Microsoft.Build.Framework.ITaskItem>`[]`.<br /><br /> Os arquivos a serem incluídos no manifesto.  Especifique o caminho completo para cada arquivo.|  
|`HostInBrowser`|Parâmetro opcional de [Boolean](assetId:///Boolean?qualifyHint=False&autoUpgrade=True).<br /><br /> Se `true`, o aplicativo é hospedado em um navegador \(assim como os aplicativos de navegador da Web do WPF\).|  
|`IconFile`|Parâmetro opcional de <xref:Microsoft.Build.Framework.ITaskItem>`[]`.<br /><br /> Indica o arquivo de ícone do aplicativo.  O ícone do aplicativo é expresso no manifesto do aplicativo gerado e é usado para o menu Iniciar e a caixa de diálogo Adicionar\/Remover programas.  Se a entrada não for especificada, um ícone padrão será usado.  Caso a tarefa esteja gerando um manifesto nativo, esse parâmetro será ignorado.|  
|`InputManifest`|Parâmetro opcional de <xref:Microsoft.Build.Framework.ITaskItem>.<br /><br /> Indica um documento XML de entrada para servir como uma base para o gerador de manifesto.  Isso permite que dados estruturados, como segurança de aplicativo ou definições de manifesto personalizadas, sejam refletidos no manifesto de saída.  O elemento raiz no documento XML deve ser um nó de assembly no namespace asmv1.|  
|`IsolatedComReferences`|Parâmetro opcional de <xref:Microsoft.Build.Framework.ITaskItem>`[]`.<br /><br /> Especifica componentes COM a serem isolados no manifesto gerado.  Esse parâmetro oferece suporte à capacidade de isolar componentes COM para implantação "COM de Registro Gratuito".  Funciona gerando automaticamente um manifesto com definições padrão do registro COM.  No entanto, os componentes COM devem ser registrados no computador de compilação para este funcionar corretamente.|  
|`ManifestType`|Parâmetro opcional de `String`.<br /><br /> Especifica que tipo de manifesto a ser gerado.  Essa propriedade pode ter os seguintes valores:<br /><br /> -   `Native`<br />-   `ClickOnce`<br /><br /> Se esse parâmetro não for especificado, a tarefa terá como padrão `ClickOnce`.|  
|`MaxTargetPath`|Parâmetro opcional de `String`.<br /><br /> Especifica o tamanho máximo permitido de um caminho de arquivo em uma implantação de aplicativos do [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)].  Se este valor for especificado, o comprimento de cada caminho de arquivo no aplicativo será verificado com relação a esse limite.  Todos os itens que excederem o limite originarão um aviso de compilação.  Se a entrada não for especificada ou for zero, nenhuma verificação será executada.  Caso a tarefa esteja gerando um manifesto nativo, esse parâmetro será ignorado.|  
|`OSVersion`|Parâmetro opcional de `String`.<br /><br /> Especifica a versão mínima necessária do sistema operacional \(SO\) exigida pelo aplicativo.  Por exemplo, o valor "5.1.2600.0" indica que o sistema operacional é o Windows XP.  Se este parâmetro não for especificado, o valor “4.10.0.0” será usado, que indica o Windows 98 Second Edition, o sistema operacional mínimo compatível com o .NET Framework.  Caso a tarefa esteja gerando um manifesto nativo, essa entrada será ignorada.|  
|`OutputManifest`|Parâmetro de saída opcional de <xref:Microsoft.Build.Framework.ITaskItem>.<br /><br /> Especifica o nome do arquivo de manifesto de saída gerado.  Se este parâmetro não for especificado, o do arquivo de saída é inferido pela identidade do manifesto gerado.|  
|`Platform`|Parâmetro opcional de `String`.<br /><br /> Especifica a plataforma de destino do aplicativo.  Essa propriedade pode ter os seguintes valores:<br /><br /> -   `AnyCPU`<br />-   `x86`<br />-   `x64`<br />-   `Itanium`<br /><br /> Se esse parâmetro não for especificado, a tarefa terá como padrão `AnyCPU`.|  
|`Product`|Parâmetro opcional de `String`.<br /><br /> Especifica o nome do aplicativo.  Se este parâmetro não for especificado, o nome é inferido pela identidade do manifesto gerado.  Esse nome é usado para o nome de atalho no menu Iniciar e faz parte do nome que aparece na caixa de diálogo Adicionar ou Remover Programas.|  
|`Publisher`|Parâmetro opcional de `String`.<br /><br /> Especifica o editor do aplicativo.  Se este parâmetro não for especificado, o nome é inferido pelo usuário registrado, ou pela identidade do manifesto gerado.  Esse nome é usado para o nome de pasta no menu Iniciar e faz parte do nome que aparece na caixa de diálogo Adicionar ou Remover Programas.|  
|`RequiresMinimumFramework35SP1`|Parâmetro opcional de `Boolean`.<br /><br /> Se verdadeiro, o aplicativo irá requerer o .NET Framework 3.5 SP1 ou uma versão mais recente.|  
|`TargetCulture`|Parâmetro opcional de `String`.<br /><br /> Identifica a cultura do aplicativo e especifica o campo de `Language` de identidade de assembly para o manifesto gerado.  Se este parâmetro não for especificado, assume\-se que a cultura do aplicativo é invariável.|  
|`TargetFrameworkMoniker`|Parâmetro opcional de assetId:///String?qualifyHint=False&autoUpgrade=True.<br /><br /> Especifica o moniker do framework de destino.|  
|`TargetFrameworkProfile`|Parâmetro opcional de assetId:///String?qualifyHint=False&autoUpgrade=True.<br /><br /> Especifica o perfil do framework de destino.|  
|`TargetFrameworkSubset`|Parâmetro opcional de assetId:///String?qualifyHint=False&autoUpgrade=True.<br /><br /> Especifica o nome do subconjunto do .NET Framework a ser direcionado.|  
|`TargetFrameworkVersion`|Parâmetro opcional de assetId:///String?qualifyHint=False&autoUpgrade=True.<br /><br /> Especifica o .NET Framework de destino do projeto.|  
|`TrustInfoFile`|Parâmetro opcional de <xref:Microsoft.Build.Framework.ITaskItem>.<br /><br /> Indica um documento XML que especifica a segurança do aplicativo.  O elemento raiz no documento XML deve ser um nó de trustInfo no namespace asmv2.  Caso a tarefa esteja gerando um manifesto nativo, esse parâmetro será ignorado.|  
|`UseApplicationTrust`|Parâmetro opcional de assetId:///Boolean?qualifyHint=False&autoUpgrade=True.<br /><br /> Se verdadeiro, as propriedades `Product`, `Publisher`, e `SupportUrl` serão gravadas no manifesto do aplicativo.|  
  
## Comentários  
 Além dos parâmetros listados acima, essa tarefa herda parâmetros da classe <xref:Microsoft.Build.Tasks.GenerateManifestBase>, que é herdada da própria classe <xref:Microsoft.Build.Utilities.Task>.  Para uma lista de parâmetros da classe de tarefas, consulte [Classe base Task](../msbuild/task-base-class.md).  
  
 Para obter mais informações sobre como usar a tarefa `GenerateDeploymentManifest`, consulte [GenerateApplicationManifest Task](../msbuild/generateapplicationmanifest-task.md).  
  
 As entradas para dependências e arquivos podem ser decoradas posteriormente com metadados de item, de modo a especificar o estado da implantação adicional de cada item.  
  
## Metadados de itens  
  
|Nome de metadados|Descrição|  
|-----------------------|---------------|  
|`DependencyType`|Indica se a dependência está publicada e instalada com o aplicativo ou um pré\-requisito.  Esses metadados são válidos para todas as dependências, mas não são usados para arquivos.  Os valores disponíveis para esses metadados são:<br /><br /> -   `Install`<br />-   `Prerequisite`<br /><br /> Instalação é o valor padrão.|  
|`AssemblyType`|Indica se a dependência é um assembly gerenciado ou nativo.  Esses metadados são válidos para todas as dependências, mas não são usados para arquivos.  Os valores disponíveis para esses metadados são:<br /><br /> -   `Managed`<br />-   `Native`<br />-   `Unspecified`<br /><br /> `Unspecified` é o valor padrão, que indica que o gerador do manifesto determinará o tipo de assembly automaticamente.|  
|`Group`|Indica o grupo para baixar arquivos adicionais sob demanda.  O nome do grupo é definido pelo aplicativo e pode ser qualquer cadeia de caracteres.  Uma cadeia de caracteres vazia indica que o arquivo não faz parte de um grupo de download, que é o padrão.  Os arquivos que não estão em um grupo são parte do download inicial do aplicativo.  Os arquivos em um grupo são baixados somente quando são solicitados explicitamente pelo aplicativo usando <xref:System.Deployment.Application>.<br /><br /> Esses metadados são válidos para todos os arquivos onde `IsDataFile` é `false` e todas as dependências onde `DependencyType` é `Install`.|  
|`TargetPath`|Especifica como o caminho deve ser definido no manifesto gerado.  Esse atributo é válido para todos os arquivos.  Se esse atributo não for especificado, a especificação de item será usada.  Esse atributo é válido para todos os arquivos e dependências com um valor `DependencyType` de `Install`.|  
|`IsDataFile`|Um valor de metadados de `Boolean` que indica se o arquivo é ou não um arquivo de dados.  Um arquivo de dados é especial na medida em que é migrado entre atualizações do aplicativo.  Esses metadados são válidos somente para arquivos.  `False` é o valor padrão.|  
  
## Exemplo  
 Esse exemplo usa a tarefa `GenerateApplicationManifest` para gerar um manifesto de aplicativo [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] e a tarefa `GenerateDeploymentManifest` para gerar um manifesto de implantação para um aplicativo com um único assembly.  Em seguida, usa a tarefa de `SignFile` para assinar os manifestos.  
  
 Isso ilustra o cenário mais simples possível de geração de manifesto onde os manifestos [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] são gerados para um único programa.  Um nome padrão e uma identidade são inferidos do assembly para o manifesto.  
  
> [!NOTE]
>  No exemplo abaixo, todos os binários do aplicativo são predefinidos para focalizar aspectos de geração do manifesto.  Esse exemplo gera uma implantação do [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] totalmente funcional.  
  
> [!NOTE]
>  Para obter mais informações sobre a propriedade de `Thumbprint` usada na tarefa de `SignFile` neste exemplo, consulte [Tarefa SignFile](../msbuild/signfile-task.md).  
  
```  
<Project DefaultTargets="Build"  
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <ItemGroup>  
        <EntryPoint Include="SimpleWinApp.exe" />  
    </ItemGroup>  
  
    <PropertyGroup>  
        <Thumbprint>  
             <!-- Insert generated thumbprint here -->  
        </Thumbprint>  
    </PropertyGroup>  
  
    <Target Name="Build">  
  
        <GenerateApplicationManifest  
            EntryPoint="@(EntryPoint)">  
            <Output  
                ItemName="ApplicationManifest"  
                TaskParameter="OutputManifest"/>  
        </GenerateApplicationManifest>  
  
        <GenerateDeploymentManifest  
            EntryPoint="@(ApplicationManifest)">  
            <Output  
                ItemName="DeployManifest"  
                TaskParameter="OutputManifest"/>  
        </GenerateDeploymentManifest>  
  
        <SignFile  
            CertificateThumbprint="$(Thumbprint)"  
            SigningTarget="@(ApplicationManifest)"/>  
  
        <SignFile  
            CertificateThumbprint="$(Thumbprint)"  
            SigningTarget="@(DeployManifest)"/>  
  
    </Target>  
</Project>  
```  
  
## Exemplo  
 Esse exemplo usa as tarefas `GenerateApplicationManifest` e `GenerateDeploymentManifest` para gerar manifestos de aplicativo e implantação [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] para um aplicativo com um único assembly, especificando o nome e a identidade dos manifestos.  
  
 Esse exemplo é semelhante ao exemplo anterior, exceto pelo nome e pela identidade dos manifestos que são explicitamente especificados.  Além disso, esse exemplo é configurado como um aplicativo online em vez de um aplicativo instalado.  
  
> [!NOTE]
>  No exemplo abaixo, todos os binários do aplicativo são predefinidos para focalizar aspectos de geração do manifesto.  Esse exemplo gera uma implantação do [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] totalmente funcional.  
  
> [!NOTE]
>  Para obter mais informações sobre a propriedade de `Thumbprint` usada na tarefa de `SignFile` neste exemplo, consulte [Tarefa SignFile](../msbuild/signfile-task.md).  
  
```  
<Project DefaultTargets="Build"  
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <ItemGroup>  
        <EntryPoint Include="SimpleWinApp.exe" />  
    </ItemGroup>  
  
    <PropertyGroup>  
        <Thumbprint>  
             <!-- Insert generated thumbprint here -->  
        </Thumbprint>  
    </PropertyGroup>  
  
    <Target Name="Build">  
  
        <GenerateApplicationManifest  
            AssemblyName="SimpleWinApp.exe"  
            AssemblyVersion="1.0.0.0"  
            EntryPoint="@(EntryPoint)"  
            OutputManifest="SimpleWinApp.exe.manifest">  
            <Output  
                ItemName="ApplicationManifest"  
                TaskParameter="OutputManifest"/>  
        </GenerateApplicationManifest>  
  
        <GenerateDeploymentManifest  
                AssemblyName="SimpleWinApp.application"  
                AssemblyVersion="1.0.0.0"  
                EntryPoint="@(ApplicationManifest)"  
                Install="false"  
                OutputManifest="SimpleWinApp.application">  
                <Output  
                    ItemName="DeployManifest"  
                    TaskParameter="OutputManifest"/>  
        </GenerateDeploymentManifest>  
  
        <SignFile  
            CertificateThumbprint="$(Thumbprint)"  
            SigningTarget="@(ApplicationManifest)"/>  
  
        <SignFile  
            CertificateThumbprint="$(Thumbprint)"  
            SigningTarget="@(DeployManifest)"/>  
  
    </Target>  
</Project>  
```  
  
## Exemplo  
 Esse exemplo usa as tarefas `GenerateApplicationManifest` e `GenerateDeploymentManifest` para gerar manifestos de aplicativo e implantação [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] para um aplicativo com vários arquivos e assemblies.  
  
> [!NOTE]
>  No exemplo abaixo, todos os binários do aplicativo são predefinidos para focalizar aspectos de geração do manifesto.  Esse exemplo gera uma implantação do [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] totalmente funcional.  
  
> [!NOTE]
>  Para obter mais informações sobre a propriedade de `Thumbprint` usada na tarefa de `SignFile` neste exemplo, consulte [Tarefa SignFile](../msbuild/signfile-task.md).  
  
```  
<Project DefaultTargets="Build"  
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <ItemGroup>  
        <EntryPoint Include="SimpleWinApp.exe" />  
    </ItemGroup>  
  
    <PropertyGroup>  
        <Thumbprint>  
             <!-- Insert generated thumbprint here -->  
        </Thumbprint>  
        <DeployUrl>  
            <!-- Insert the deployment URL here -->  
        </DeployUrl>  
        <SupportUrl>  
            <!-- Insert the support URL here -->  
        </SupportUrl>  
    </PropertyGroup>  
  
    <Target Name="Build">  
  
    <ItemGroup>  
        <EntryPoint Include="SimpleWinApp.exe"/>  
        <Dependency Include="ClassLibrary1.dll">  
            <AssemblyType>Managed</AssemblyType>  
            <DependencyType>Install</DependencyType>  
        </Dependency>  
        <Dependency Include="ClassLibrary2.dll">  
            <AssemblyType>Managed</AssemblyType>  
            <DependencyType>Install</DependencyType>  
            <Group>Secondary</Group>  
        </Dependency>  
        <Dependency Include="MyAddIn1.dll">  
            <AssemblyType>Managed</AssemblyType>  
            <DependencyType>Install</DependencyType>  
            <TargetPath>Addins\MyAddIn1.dll</TargetPath>  
        </Dependency>  
        <Dependency Include="ClassLibrary3.dll">  
            <AssemblyType>Managed</AssemblyType>  
            <DependencyType>Prerequisite</DependencyType>  
        </Dependency>  
  
        <File Include="Text1.txt">  
            <TargetPath>Text\Text1.txt</TargetPath>  
            <Group>Text</Group>  
        </File>  
        <File Include="DataFile1.xml ">  
            <TargetPath>Data\DataFile1.xml</TargetPath>  
            <IsDataFile>true</IsDataFile>  
        </File>  
  
        <IconFile Include="Heart.ico"/>  
        <ConfigFile Include="app.config">  
            <TargetPath>SimpleWinApp.exe.config</TargetPath>  
        </ConfigFile>  
        <BaseManifest Include="app.manifest"/>  
    </ItemGroup>  
  
    <Target Name="Build">  
  
        <GenerateApplicationManifest  
            AssemblyName="SimpleWinApp.exe"  
            AssemblyVersion="1.0.0.0"  
            ConfigFile="@(ConfigFile)"  
            Dependencies="@(Dependency)"  
            Description="TestApp"  
            EntryPoint="@(EntryPoint)"  
            Files="@(File)"  
            IconFile="@(IconFile)"  
            InputManifest="@(BaseManifest)"  
            OutputManifest="SimpleWinApp.exe.manifest">  
            <Output  
                ItemName="ApplicationManifest"  
                TaskParameter="OutputManifest"/>  
        </GenerateApplicationManifest>  
  
        <GenerateDeploymentManifest  
            AssemblyName="SimpleWinApp.application"  
            AssemblyVersion="1.0.0.0"  
            DeploymentUrl="$(DeployToUrl)"  
            Description="TestDeploy"  
            EntryPoint="@(ApplicationManifest)"  
            Install="true"  
            OutputManifest="SimpleWinApp.application"  
            Product="SimpleWinApp"  
            Publisher="Microsoft"  
            SupportUrl="$(SupportUrl)"  
            UpdateEnabled="true"  
            UpdateInterval="3"  
            UpdateMode="Background"  
            UpdateUnit="weeks">  
            <Output  
                ItemName="DeployManifest"  
                TaskParameter="OutputManifest"/>  
        </GenerateDeploymentManifest>  
  
        <SignFile  
            CertificateThumbprint="$(Thumbprint)"  
            SigningTarget="@(ApplicationManifest)"/>  
  
        <SignFile  
            CertificateThumbprint="$(Thumbprint)"  
            SigningTarget="@(DeployManifest)"/>  
  
    </Target>  
</Project>  
```  
  
## Exemplo  
 Esse exemplo usa a tarefa `GenerateApplicationManifest` para gerar um manifesto nativo para o aplicativo Test.exe, fazendo referência a um componente nativo Alpha.dll e a um componente COM isolado Bravo.dll.  
  
 Esse exemplo gera o Test.exe.manifest, fazendo o aplicativo XCOPY implantável aproveitar o COM de Registro Gratuito.  
  
> [!NOTE]
>  No exemplo abaixo, todos os binários do aplicativo são predefinidos para focalizar aspectos de geração do manifesto.  Esse exemplo gera uma implantação do [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] totalmente funcional.  
  
```  
<Project DefaultTargets="Build" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <ItemGroup>  
        <File Include="Test.exe" />  
        <Dependency Include="Alpha.dll">  
            <AssemblyType>Native</AssemblyType>  
            <DependencyType>Install</DependencyType>  
        </Dependency>  
        <ComComponent Include="Bravo.dll" />  
    </ItemGroup>  
  
    <Target Name="Build">  
        <GenerateApplicationManifest  
            AssemblyName="Test.exe"  
            AssemblyVersion="1.0.0.0"  
            Dependencies="@(Dependency)"  
            Files="@(File)"  
            IsolatedComReferences="@(ComComponent)"  
            ManifestType="Native">  
            <Output  
                ItemName="ApplicationManifest"  
                TaskParameter="OutputManifest"/>  
        </GenerateApplicationManifest>  
  
    </Target>  
</Project>  
```  
  
## Consulte também  
 [ \(tarefas\)](../msbuild/msbuild-tasks.md)   
 [Tarefa GenerateDeploymentManifest](../msbuild/generatedeploymentmanifest-task.md)   
 [Tarefa SignFile](../msbuild/signfile-task.md)   
 [Referência de tarefas](../msbuild/msbuild-task-reference.md)