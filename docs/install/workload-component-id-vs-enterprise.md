---
title: IDs de carga de trabalho e de componente do Visual Studio Enterprise 2017 | Microsoft Docs
description: "Use as IDs de carga de trabalho e de componente para instalar o Visual Studio usando a linha de comando ou para especificar como uma dependência em um manifesto do VSIX"
keywords: 
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.date: 08/30/2017
ms.topic: article
helpviewer_keywords:
- workload ID, Visual Studio
- component ID, Visual Studio
- install Visual Studio, administrator guide
ms.service: 
ms.technology:
- vs-ide-install
- vs-ide-sdk
ms.assetid: be73e3af-d87b-4d14-bd08-2e4bda074fb3
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
ms.translationtype: HT
ms.sourcegitcommit: 96018963278cd1d53b226473baade41da1e98111
ms.openlocfilehash: e4a874f45f50da45e75c318622cfe15bac79ee0a
ms.contentlocale: pt-br
ms.lasthandoff: 09/06/2017

---

# <a name="visual-studio-enterprise-2017-component-directory"></a>Diretório de componentes do Visual Studio Enterprise 2017

As tabelas desta página listam as IDs que podem ser usadas para instalar o Visual Studio usando a linha de comando ou que podem ser especificadas como uma dependência em um manifesto do VSIX. Observe que adicionaremos outros componentes conforme atualizações forem liberadas para o Visual Studio.

Além disso, observe o seguinte sobre a página:

* Cada carga de trabalho tem sua própria seção, seguida pela ID da carga de trabalho e por uma tabela dos componentes que estão disponíveis para a carga de trabalho.
* Por padrão, os componentes **Obrigatórios** serão instalados durante a instalação da carga de trabalho. * Se preferir, também será possível instalar os componentes **Recomendados** e **Opcionais**.
* Também adicionamos uma seção que lista os componentes adicionais que não são afiliados a nenhuma carga de trabalho.

Ao definir dependências no manifesto do VSIX, é necessário especificar somente IDs de Componente. Use as tabelas desta página para determinar nossas dependências mínimas de componente. Em alguns cenários, isso pode significar que somente um componente de uma carga de trabalho é especificado. Em outros cenários, isso pode significar que vários componentes de uma única carga de trabalho ou que vários componentes de várias cargas de trabalho são especificados. Para obter mais informações, consulte a página [Como migrar projetos de extensibilidade para o Visual Studio 2017](../extensibility/how-to-migrate-extensibility-projects-to-visual-studio-2017.md).

Para obter mais informações sobre como usar essas IDs, consulte a página [Usar parâmetros de linha de comando para instalar o Visual Studio 2017](use-command-line-parameters-to-install-visual-studio.md). Além disso, para obter uma lista de IDs de carga de trabalho e de componente para outros produtos, consulte a página [IDs de carga de trabalho e de componente do Visual Studio 2017](workload-and-component-ids.md).

## <a name="visual-studio-core-editor-included-with-visual-studio-enterprise-2017"></a>Principal editor do Visual Studio (incluído no Visual Studio Enterprise 2017)

**ID:** Microsoft.VisualStudio.Workload.CoreEditor

**Descrição:** a experiência de shell do Visual Studio Core, incluindo a edição de código com reconhecimento de sintaxe, controle do código-fonte e gerenciamento de itens de trabalho.

### <a name="components-included-by-this-workload"></a>Componentes incluídos por essa carga de trabalho

ID do componente | Nome | Versão | Tipo de dependência
--- | --- | --- | ---
Microsoft.VisualStudio.Component.CoreEditor | Editor do Visual Studio Core | 15.0.26606.0 | Necessária


## <a name="azure-development"></a>Desenvolvimento do Azure

**ID:** Microsoft.VisualStudio.Workload.Azure

**Descrição:** SDK, ferramentas e projetos do Azure para o desenvolvimento de aplicativos na nuvem e a criação de recursos.

### <a name="components-included-by-this-workload"></a>Componentes incluídos por essa carga de trabalho

ID do componente | Nome | Versão | Tipo de dependência
--- | --- | --- | ---
Component.Microsoft.VisualStudio.RazorExtension | Razor Language Services | 15.0.26720.2 | Necessária
Component.Microsoft.VisualStudio.Web.AzureFunctions | Ferramentas Microsoft Azure WebJobs | 15.0.26720.2 | Necessária
Component.WebSocket | WebSocket4Net | 15.0.26606.0 | Necessária
Microsoft.Component.ClickOnce | Publicação ClickOnce | 15.0.26208.0 | Necessária
Microsoft.Component.MSBuild | MSBuild | 15.0.26208.0 | Necessária
Microsoft.Component.NetFX.Core.Runtime | Tempo de execução do .NET Core | 15.0.26208.0 | Necessária
Microsoft.Net.Component.4.5.1.TargetingPack | Pacote de direcionamento do .NET Framework 4.5.1 | 15.0.26621.2 | Necessária
Microsoft.Net.Component.4.5.2.TargetingPack | Pacote de direcionamento do .NET Framework 4.5.2 | 15.0.26621.2 | Necessária
Microsoft.Net.Component.4.5.TargetingPack | Pacote de direcionamento do .NET Framework 4.5 | 15.0.26621.2 | Necessária
Microsoft.Net.Component.4.6.1.SDK | SDK do .NET Framework 4.6.1 | 15.0.26621.2 | Necessária
Microsoft.Net.Component.4.6.1.TargetingPack | Pacote de direcionamento do .NET Framework 4.6.1 | 15.0.26621.2 | Necessária
Microsoft.Net.Component.4.6.TargetingPack | Pacote de direcionamento do .NET Framework 4.6 | 15.0.26621.2 | Necessária
Microsoft.Net.Component.4.TargetingPack | Pacote de direcionamento do .NET Framework 4 | 15.0.26621.2 | Necessária
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | Ferramentas de desenvolvimento do .NET Framework 4.6.1 | 15.0.26606.0 | Necessária
Microsoft.Net.ComponentGroup.TargetingPacks.Common | Ferramentas de desenvolvimento do .NET Framework 4 a 4.6 | 15.0.26606.0 | Necessária
Microsoft.Net.Core.Component.SDK | Ferramentas de desenvolvimento do .NET Core 1.0 a 1.1 | 15.0.26606.0 | Necessária
Microsoft.NetCore.ComponentGroup.Web | Ferramentas de desenvolvimento do .NET Core 1.0 a 1.1 | 15.0.26621.2 | Necessária
Microsoft.VisualStudio.Component.AppInsights.Tools | Ferramentas de Análise do Desenvolvedor | 15.0.26621.2 | Necessária
Microsoft.VisualStudio.Component.Azure.AuthoringTools | Ferramentas de Criação do Azure | 15.0.26621.2 | Necessária
Microsoft.VisualStudio.Component.Azure.ClientLibs | Bibliotecas do Azure para .NET | 15.0.26208.0 | Necessária
Microsoft.VisualStudio.Component.Azure.Compute.Emulator | Emulador de Computação do Azure | 15.0.26621.2 | Necessária
Microsoft.VisualStudio.Component.Azure.Storage.Emulator | Emulador de Armazenamento do Azure | 15.0.26621.2 | Necessária
Microsoft.VisualStudio.Component.Azure.Waverton | Principais ferramentas dos Serviços de Nuvem do Azure | 15.0.26208.0 | Necessária
Microsoft.VisualStudio.Component.CloudExplorer | Cloud Explorer | 15.0.26711.1 | Necessária
Microsoft.VisualStudio.Component.Common.Azure.Tools | Ferramentas de conectividade e publicação | 1.10.50614.2 | Necessária
Microsoft.VisualStudio.Component.IISExpress | IIS Express  | 15.0.26208.0 | Necessária
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | Diagnóstico do JavaScript | 15.0.26606.0 | Necessária
Microsoft.VisualStudio.Component.JavaScript.TypeScript | Suporte às linguagens JavaScript e TypeScript | 15.0.26606.0 | Necessária
Microsoft.VisualStudio.Component.ManagedDesktop.Core | Núcleo da carga de trabalho de área de trabalho gerenciada | 15.0.26419.1 | Necessária
Microsoft.VisualStudio.Component.NuGet | Gerenciador de pacotes NuGet | 15.0.26621.2 | Necessária
Microsoft.VisualStudio.Component.PortableLibrary | Pacote de direcionamento da Biblioteca Portátil do .NET | 15.0.26208.0 | Necessária
Microsoft.VisualStudio.Component.Roslyn.Compiler | Compiladores Roslyn do C# e Visual Basic | 15.0.26208.0 | Necessária
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# e Visual Basic | 15.0.26711.1 | Necessária
Microsoft.VisualStudio.Component.SQL.ADAL | Tempo de execução do SQL ADAL | 15.0.26606.0 | Necessária
Microsoft.VisualStudio.Component.SQL.CLR | Tipos de dados CLR do SQL Server | 15.0.26208.0 | Necessária
Microsoft.VisualStudio.Component.SQL.CMDUtils | Utilitários de linha de comando do SQL Server | 15.0.26208.0 | Necessária
Microsoft.VisualStudio.Component.SQL.DataSources | Fontes de dados para suporte do SQL Server | 15.0.26621.2 | Necessária
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | SQL Server Express 2016 LocalDB | 15.0.26208.0 | Necessária
Microsoft.VisualStudio.Component.SQL.NCLI | SQL Server Native Client | 15.0.26208.0 | Necessária
Microsoft.VisualStudio.Component.SQL.SSDT | Ferramentas de dados do SQL Server | 15.0.26208.0 | Necessária
Microsoft.VisualStudio.Component.Static.Analysis.Tools | Ferramentas de análise estática | 15.0.26208.0 | Necessária
Microsoft.VisualStudio.Component.TextTemplating | Transformação de modelo de texto | 15.0.26208.0 | Necessária
Microsoft.VisualStudio.Component.TypeScript.2.3 | SDK do TypeScript 2.3 | 15.0.26621.2 | Necessária
Microsoft.VisualStudio.Component.VisualStudioData | Fontes de dados e referências de serviço | 15.0.26208.0 | Necessária
Microsoft.VisualStudio.Component.Web | Ferramentas de desenvolvimento do ASP.NET e para a Web | 15.0.26606.0 | Necessária
Microsoft.VisualStudio.Component.WebDeploy | Implantação da Web | 15.0.26208.0 | Necessária
Microsoft.VisualStudio.ComponentGroup.Azure.Prerequisites | Pré-requisitos de desenvolvimento do Azure | 15.0.26711.1 | Necessária
Microsoft.VisualStudio.ComponentGroup.AzureFunctions | Ferramentas Microsoft Azure WebJobs | 15.0.26720.2 | Necessária
Microsoft.VisualStudio.ComponentGroup.Web | Ferramentas de desenvolvimento do ASP.NET e para a Web | 15.0.26606.0 | Necessária
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | Desenvolvimento do ASP.NET e para a Web | 15.0.26606.0 | Necessária
Microsoft.Component.Azure.DataLake.Tools | Ferramentas Azure Data Lake e Stream Analytics | 15.0.26730.0 | Recomendado
Microsoft.VisualStudio.Component.Azure.MobileAppsSdk | SDK dos Aplicativos Móveis do Azure | 15.0.26504.0 | Recomendado
Microsoft.VisualStudio.Component.Azure.ResourceManager.Tools | Principais ferramentas do Azure Resource Manager | 15.0.26504.0 | Recomendado
Microsoft.VisualStudio.Component.Azure.ServiceFabric.Tools | Ferramentas do Service Fabric | 15.0.26208.0 | Recomendado
Microsoft.VisualStudio.Component.DiagnosticTools | Ferramentas de criação de perfil do .NET | 15.0.26711.1 | Recomendado
Microsoft.VisualStudio.Component.IntelliTrace.FrontEnd | IntelliTrace | 15.0.26606.0 | Recomendado
Microsoft.VisualStudio.ComponentGroup.Azure.CloudServices | Ferramentas dos Serviços de Nuvem do Azure | 15.0.26504.0 | Recomendado
Microsoft.VisualStudio.ComponentGroup.Azure.ResourceManager.Tools | Ferramentas do Azure Resource Manager | 15.0.26711.1 | Recomendado
Microsoft.Net.Component.4.6.2.SDK | SDK do .NET Framework 4.6.2 | 15.0.26208.0 | Opcional
Microsoft.Net.Component.4.6.2.TargetingPack | Pacote de direcionamento do .NET Framework 4.6.2 | 15.0.26208.0 | Opcional
Microsoft.Net.Component.4.7.SDK | SDK do .NET Framework 4.7 | 15.0.26419.1 | Opcional
Microsoft.Net.Component.4.7.TargetingPack | Pacote de direcionamento do .NET Framework 4.7 | 15.0.26621.2 | Opcional
Microsoft.Net.ComponentGroup.4.6.2.DeveloperTools | Ferramentas de desenvolvimento do .NET Framework 4.6.2 | 15.0.26621.2 | Opcional
Microsoft.Net.ComponentGroup.4.7.DeveloperTools | Ferramentas de desenvolvimento do .NET Framework 4.7 | 15.0.26606.0 | Opcional
Microsoft.VisualStudio.Component.Azure.Storage.AzCopy | AzCopy do Armazenamento do Azure | 15.0.26621.2 | Opcional
Microsoft.VisualStudio.Component.PowerShell.Tools | Ferramentas do PowerShell | 3.0.552 | Opcional
Microsoft.VisualStudio.Component.Wcf.Tooling | Windows Communication Foundation | 15.0.26606.0 | Opcional


## <a name="data-storage-and-processing"></a>Armazenamento de dados e processamento

**ID:** Microsoft.VisualStudio.Workload.Data

**Descrição:** conectar, desenvolver e testar soluções de dados usando o SQL Server, Azure Data Lake, Hadoop ou Azure ML.

### <a name="components-included-by-this-workload"></a>Componentes incluídos por essa carga de trabalho

ID do componente | Nome | Versão | Tipo de dependência
--- | --- | --- | ---
Component.Microsoft.VisualStudio.RazorExtension | Razor Language Services | 15.0.26720.2 | Recomendado
Component.Redgate.ReadyRoll | Redgate ReadyRoll Core | 1.14.2.3918 | Recomendado
Component.Redgate.SQLPrompt.VsPackage | Redgate SQL Prompt Core | 8.0.2.1513 | Recomendado
Component.Redgate.SQLSearch.VSExtension | Redgate SQL Search | 2.4.2.1439 | Recomendado
Component.WebSocket | WebSocket4Net | 15.0.26606.0 | Recomendado
Microsoft.Component.Azure.DataLake.Tools | Ferramentas Azure Data Lake e Stream Analytics | 15.0.26730.0 | Recomendado
Microsoft.Component.ClickOnce | Publicação ClickOnce | 15.0.26208.0 | Recomendado
Microsoft.Component.MSBuild | MSBuild | 15.0.26208.0 | Recomendado
Microsoft.Net.Component.4.5.1.TargetingPack | Pacote de direcionamento do .NET Framework 4.5.1 | 15.0.26621.2 | Recomendado
Microsoft.Net.Component.4.5.2.TargetingPack | Pacote de direcionamento do .NET Framework 4.5.2 | 15.0.26621.2 | Recomendado
Microsoft.Net.Component.4.5.TargetingPack | Pacote de direcionamento do .NET Framework 4.5 | 15.0.26621.2 | Recomendado
Microsoft.Net.Component.4.6.1.SDK | SDK do .NET Framework 4.6.1 | 15.0.26621.2 | Recomendado
Microsoft.Net.Component.4.6.1.TargetingPack | Pacote de direcionamento do .NET Framework 4.6.1 | 15.0.26621.2 | Recomendado
Microsoft.Net.Component.4.6.TargetingPack | Pacote de direcionamento do .NET Framework 4.6 | 15.0.26621.2 | Recomendado
Microsoft.Net.Component.4.TargetingPack | Pacote de direcionamento do .NET Framework 4 | 15.0.26621.2 | Recomendado
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | Ferramentas de desenvolvimento do .NET Framework 4.6.1 | 15.0.26606.0 | Recomendado
Microsoft.Net.ComponentGroup.TargetingPacks.Common | Ferramentas de desenvolvimento do .NET Framework 4 a 4.6 | 15.0.26606.0 | Recomendado
Microsoft.VisualStudio.Component.AppInsights.Tools | Ferramentas de Análise do Desenvolvedor | 15.0.26621.2 | Recomendado
Microsoft.VisualStudio.Component.Azure.AuthoringTools | Ferramentas de Criação do Azure | 15.0.26621.2 | Recomendado
Microsoft.VisualStudio.Component.Azure.ClientLibs | Bibliotecas do Azure para .NET | 15.0.26208.0 | Recomendado
Microsoft.VisualStudio.Component.Azure.Compute.Emulator | Emulador de Computação do Azure | 15.0.26621.2 | Recomendado
Microsoft.VisualStudio.Component.Azure.Storage.Emulator | Emulador de Armazenamento do Azure | 15.0.26621.2 | Recomendado
Microsoft.VisualStudio.Component.Azure.Waverton | Principais ferramentas dos Serviços de Nuvem do Azure | 15.0.26208.0 | Recomendado
Microsoft.VisualStudio.Component.CloudExplorer | Cloud Explorer | 15.0.26711.1 | Recomendado
Microsoft.VisualStudio.Component.Common.Azure.Tools | Ferramentas de conectividade e publicação | 1.10.50614.2 | Recomendado
Microsoft.VisualStudio.Component.IISExpress | IIS Express  | 15.0.26208.0 | Recomendado
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | Diagnóstico do JavaScript | 15.0.26606.0 | Recomendado
Microsoft.VisualStudio.Component.JavaScript.TypeScript | Suporte às linguagens JavaScript e TypeScript | 15.0.26606.0 | Recomendado
Microsoft.VisualStudio.Component.ManagedDesktop.Core | Núcleo da carga de trabalho de área de trabalho gerenciada | 15.0.26419.1 | Recomendado
Microsoft.VisualStudio.Component.NuGet | Gerenciador de pacotes NuGet | 15.0.26621.2 | Recomendado
Microsoft.VisualStudio.Component.PortableLibrary | Pacote de direcionamento da Biblioteca Portátil do .NET | 15.0.26208.0 | Recomendado
Microsoft.VisualStudio.Component.Roslyn.Compiler | Compiladores Roslyn do C# e Visual Basic | 15.0.26208.0 | Recomendado
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# e Visual Basic | 15.0.26711.1 | Recomendado
Microsoft.VisualStudio.Component.SQL.ADAL | Tempo de execução do SQL ADAL | 15.0.26606.0 | Recomendado
Microsoft.VisualStudio.Component.SQL.CLR | Tipos de dados CLR do SQL Server | 15.0.26208.0 | Recomendado
Microsoft.VisualStudio.Component.SQL.CMDUtils | Utilitários de linha de comando do SQL Server | 15.0.26208.0 | Recomendado
Microsoft.VisualStudio.Component.SQL.DataSources | Fontes de dados para suporte do SQL Server | 15.0.26621.2 | Recomendado
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | SQL Server Express 2016 LocalDB | 15.0.26208.0 | Recomendado
Microsoft.VisualStudio.Component.SQL.NCLI | SQL Server Native Client | 15.0.26208.0 | Recomendado
Microsoft.VisualStudio.Component.SQL.SSDT | Ferramentas de dados do SQL Server | 15.0.26208.0 | Recomendado
Microsoft.VisualStudio.Component.Static.Analysis.Tools | Ferramentas de análise estática | 15.0.26208.0 | Recomendado
Microsoft.VisualStudio.Component.TextTemplating | Transformação de modelo de texto | 15.0.26208.0 | Recomendado
Microsoft.VisualStudio.Component.TypeScript.2.3 | SDK do TypeScript 2.3 | 15.0.26621.2 | Recomendado
Microsoft.VisualStudio.Component.VisualStudioData | Fontes de dados e referências de serviço | 15.0.26208.0 | Recomendado
Microsoft.VisualStudio.Component.Web | Ferramentas de desenvolvimento do ASP.NET e para a Web | 15.0.26606.0 | Recomendado
Microsoft.VisualStudio.Component.WebDeploy | Implantação da Web | 15.0.26208.0 | Recomendado
Microsoft.VisualStudio.ComponentGroup.Web | Ferramentas de desenvolvimento do ASP.NET e para a Web | 15.0.26606.0 | Recomendado
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | Desenvolvimento do ASP.NET e para a Web | 15.0.26606.0 | Recomendado
Microsoft.VisualStudio.Component.FSharp | Suporte à linguagem F# | 15.0.26606.0 | Opcional


## <a name="data-science-and-analytical-applications"></a>Ciência de dados e aplicativos analíticos

**ID:** Microsoft.VisualStudio.Workload.DataScience

**Descrição:** linguagens e ferramentas para criar aplicativos de ciência de dados, incluindo Python, R e F#.

### <a name="components-included-by-this-workload"></a>Componentes incluídos por essa carga de trabalho

ID do componente | Nome | Versão | Tipo de dependência
--- | --- | --- | ---
Component.Anaconda3.x64 | Anaconda3 64 bits (4.4.0) | 4.4.0 | Recomendado
Component.Microsoft.VisualStudio.RazorExtension | Razor Language Services | 15.0.26720.2 | Recomendado
Microsoft.Component.CookiecutterTools | Suporte do modelo Cookiecutter | 15.0.26621.2 | Recomendado
Microsoft.Component.PythonTools | Suporte da linguagem Python | 15.0.26730.0 | Recomendado
Microsoft.Component.PythonTools.Web | Suporte Web do Python | 15.0.26606.0 | Recomendado
Microsoft.Component.VC.Runtime.UCRTSDK | SDK do CRT Universal do Windows | 15.0.26208.0 | Recomendado
Microsoft.Net.Component.4.6.1.TargetingPack | Pacote de direcionamento do .NET Framework 4.6.1 | 15.0.26621.2 | Recomendado
Microsoft.VisualStudio.Component.Common.Azure.Tools | Ferramentas de conectividade e publicação | 1.10.50614.2 | Recomendado
Microsoft.VisualStudio.Component.FSharp | Suporte à linguagem F# | 15.0.26606.0 | Recomendado
Microsoft.VisualStudio.Component.JavaScript.TypeScript | Suporte às linguagens JavaScript e TypeScript | 15.0.26606.0 | Recomendado
Microsoft.VisualStudio.Component.NuGet | Gerenciador de pacotes NuGet | 15.0.26621.2 | Recomendado
Microsoft.VisualStudio.Component.R.Open | Microsoft R Client (3.3.2) | 15.0.26606.0 | Recomendado
Microsoft.VisualStudio.Component.RHost | Suporte de tempo de execução para ferramentas de desenvolvimento do R | 15.0.26621.2 | Recomendado
Microsoft.VisualStudio.Component.Roslyn.Compiler | Compiladores Roslyn do C# e Visual Basic | 15.0.26208.0 | Recomendado
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# e Visual Basic | 15.0.26711.1 | Recomendado
Microsoft.VisualStudio.Component.RTools | Suporte à linguagem R | 15.0.26606.0 | Recomendado
Microsoft.VisualStudio.Component.SQL.CLR | Tipos de dados CLR do SQL Server | 15.0.26208.0 | Recomendado
Microsoft.VisualStudio.Component.Static.Analysis.Tools | Ferramentas de análise estática | 15.0.26208.0 | Recomendado
Microsoft.VisualStudio.Component.TypeScript.2.3 | SDK do TypeScript 2.3 | 15.0.26621.2 | Recomendado
Microsoft.VisualStudio.Component.VisualStudioData | Fontes de dados e referências de serviço | 15.0.26208.0 | Recomendado
Microsoft.VisualStudio.Component.WebDeploy | Implantação da Web | 15.0.26208.0 | Recomendado
Microsoft.VisualStudio.Component.Windows81SDK | SDK do Windows 8.1 | 15.0.26208.0 | Recomendado
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | Desenvolvimento do ASP.NET e para a Web | 15.0.26606.0 | Recomendado
Component.Anaconda2.x64 | Anaconda2 64 bits (4.4.0) | 4.4.0 | Opcional
Component.Anaconda2.x86 | Anaconda2 32 bits (4.4.0) | 4.4.0 | Opcional
Component.Anaconda3.x86 | Anaconda3 32 bits (4.4.0) | 4.4.0 | Opcional
Microsoft.ComponentGroup.PythonTools.NativeDevelopment | Ferramentas de desenvolvimento nativo do Python | 15.0.26730.0 | Opcional
Microsoft.VisualStudio.Component.Graphics.Tools | Depurador de gráficos e criador de perfil de GPU do DirectX | 15.0.26208.0 | Opcional
Microsoft.VisualStudio.Component.Graphics.Win81 | SDK das Ferramentas de Gráficos do Windows 8.1 | 15.0.26208.0 | Opcional
Microsoft.VisualStudio.Component.VC.140 | Conjunto de ferramentas do VC++ 2015.3 v140 para área de trabalho (x86,x64) | 15.0.26720.2 | Opcional
Microsoft.VisualStudio.Component.VC.CoreIde | Principais recursos do Visual Studio C++ | 15.0.26606.0 | Opcional
Microsoft.VisualStudio.Component.VC.DiagnosticTools | Ferramentas de criação de perfil do C++ | 15.0.26720.2 | Opcional
Microsoft.VisualStudio.Component.VC.Tools.x86.x64 | Conjunto de ferramentas do VC++ 2017 v141 (x86, x64) | 15.0.26621.2 | Opcional
Microsoft.VisualStudio.Component.Windows10SDK | Tempo de execução C Universal do Windows | 15.0.26621.2 | Opcional
Microsoft.VisualStudio.Component.Windows10SDK.15063.Desktop | SDK do Windows 10 (10.0.15063.0) para Desktop C++ x86 e x64 | 15.0.26621.2 | Opcional
Microsoft.VisualStudio.Component.Windows10SDK.15063.UWP | SDK do Windows 10 (10.0.15063.0) para UWP: C#, VB, JS | 15.0.26621.2 | Opcional
Microsoft.VisualStudio.Component.Windows10SDK.15063.UWP.Native | SDK do Windows 10 (10.0.15063.0) para UWP: C++ | 15.0.26621.2 | Opcional


## <a name="net-desktop-development"></a>Desenvolvimento de área de trabalho do .NET

**ID:** Microsoft.VisualStudio.Workload.ManagedDesktop

**Descrição:** criar aplicativos do WPF, do Windows Forms e de console usando C#, Visual Basic e F#.

### <a name="components-included-by-this-workload"></a>Componentes incluídos por essa carga de trabalho

ID do componente | Nome | Versão | Tipo de dependência
--- | --- | --- | ---
Microsoft.Component.ClickOnce | Publicação ClickOnce | 15.0.26208.0 | Necessária
Microsoft.Component.MSBuild | MSBuild | 15.0.26208.0 | Necessária
Microsoft.Net.Component.4.6.1.SDK | SDK do .NET Framework 4.6.1 | 15.0.26621.2 | Necessária
Microsoft.Net.Component.4.6.1.TargetingPack | Pacote de direcionamento do .NET Framework 4.6.1 | 15.0.26621.2 | Necessária
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | Ferramentas de desenvolvimento do .NET Framework 4.6.1 | 15.0.26606.0 | Necessária
Microsoft.VisualStudio.Component.Debugger.JustInTime | Depurador Just-In-Time | 15.0.26621.2 | Necessária
Microsoft.VisualStudio.Component.ManagedDesktop.Core | Núcleo da carga de trabalho de área de trabalho gerenciada | 15.0.26419.1 | Necessária
Microsoft.VisualStudio.Component.ManagedDesktop.Prerequisites | Ferramentas de desenvolvimento de área de trabalho do .NET | 15.0.26621.2 | Necessária
Microsoft.VisualStudio.Component.PortableLibrary | Pacote de direcionamento da Biblioteca Portátil do .NET | 15.0.26208.0 | Necessária
Microsoft.VisualStudio.Component.Roslyn.Compiler | Compiladores Roslyn do C# e Visual Basic | 15.0.26208.0 | Necessária
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# e Visual Basic | 15.0.26711.1 | Necessária
Microsoft.VisualStudio.Component.SQL.CLR | Tipos de dados CLR do SQL Server | 15.0.26208.0 | Necessária
Microsoft.VisualStudio.Component.Static.Analysis.Tools | Ferramentas de análise estática | 15.0.26208.0 | Necessária
Microsoft.VisualStudio.Component.TextTemplating | Transformação de modelo de texto | 15.0.26208.0 | Necessária
Microsoft.VisualStudio.Component.VisualStudioData | Fontes de dados e referências de serviço | 15.0.26208.0 | Necessária
Microsoft.ComponentGroup.Blend | Blend for Visual Studio | 15.0.26711.1 | Recomendado
Microsoft.Net.Component.4.5.1.TargetingPack | Pacote de direcionamento do .NET Framework 4.5.1 | 15.0.26621.2 | Recomendado
Microsoft.Net.Component.4.5.2.TargetingPack | Pacote de direcionamento do .NET Framework 4.5.2 | 15.0.26621.2 | Recomendado
Microsoft.Net.Component.4.5.TargetingPack | Pacote de direcionamento do .NET Framework 4.5 | 15.0.26621.2 | Recomendado
Microsoft.Net.Component.4.6.TargetingPack | Pacote de direcionamento do .NET Framework 4.6 | 15.0.26621.2 | Recomendado
Microsoft.Net.Component.4.TargetingPack | Pacote de direcionamento do .NET Framework 4 | 15.0.26621.2 | Recomendado
Microsoft.Net.ComponentGroup.TargetingPacks.Common | Ferramentas de desenvolvimento do .NET Framework 4 a 4.6 | 15.0.26606.0 | Recomendado
Microsoft.VisualStudio.Component.DiagnosticTools | Ferramentas de criação de perfil do .NET | 15.0.26711.1 | Recomendado
Microsoft.VisualStudio.Component.EntityFramework | Ferramentas do Entity Framework 6 | 15.0.26208.0 | Recomendado
Microsoft.VisualStudio.Component.IntelliTrace.FrontEnd | IntelliTrace | 15.0.26606.0 | Recomendado
Microsoft.VisualStudio.Component.LiveUnitTesting | Live Unit Testing | 15.0.26720.2 | Recomendado
Component.Dotfuscator | Proteção PreEmptive – Dotfuscator | 15.0.26208.0 | Opcional
Microsoft.Net.Component.4.6.2.SDK | SDK do .NET Framework 4.6.2 | 15.0.26208.0 | Opcional
Microsoft.Net.Component.4.6.2.TargetingPack | Pacote de direcionamento do .NET Framework 4.6.2 | 15.0.26208.0 | Opcional
Microsoft.Net.Component.4.7.SDK | SDK do .NET Framework 4.7 | 15.0.26419.1 | Opcional
Microsoft.Net.Component.4.7.TargetingPack | Pacote de direcionamento do .NET Framework 4.7 | 15.0.26621.2 | Opcional
Microsoft.Net.ComponentGroup.4.6.2.DeveloperTools | Ferramentas de desenvolvimento do .NET Framework 4.6.2 | 15.0.26621.2 | Opcional
Microsoft.Net.ComponentGroup.4.7.DeveloperTools | Ferramentas de desenvolvimento do .NET Framework 4.7 | 15.0.26606.0 | Opcional
Microsoft.Net.Core.Component.SDK | Ferramentas de desenvolvimento do .NET Core 1.0 a 1.1 | 15.0.26606.0 | Opcional
Microsoft.NetCore.ComponentGroup.DevelopmentTools | Ferramentas de desenvolvimento do .NET Core 1.0 a 1.1 | 15.0.26606.0 | Opcional
Microsoft.VisualStudio.Component.CodeClone | Clone de Código | 15.0.26208.0 | Opcional
Microsoft.VisualStudio.Component.CodeMap | Mapa de Códigos | 15.0.26208.0 | Opcional
Microsoft.VisualStudio.Component.DependencyValidation.Enterprise | Validação de dependência dinâmica | 15.0.26208.0 | Opcional
Microsoft.VisualStudio.Component.FSharp | Suporte à linguagem F# | 15.0.26606.0 | Opcional
Microsoft.VisualStudio.Component.GraphDocument | Editor DGML | 15.0.26208.0 | Opcional
Microsoft.VisualStudio.Component.IISExpress | IIS Express  | 15.0.26208.0 | Opcional
Microsoft.VisualStudio.Component.NuGet | Gerenciador de pacotes NuGet | 15.0.26621.2 | Opcional
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | SQL Server Express 2016 LocalDB | 15.0.26208.0 | Opcional
Microsoft.VisualStudio.Component.SQL.NCLI | SQL Server Native Client | 15.0.26208.0 | Opcional
Microsoft.VisualStudio.Component.Wcf.Tooling | Windows Communication Foundation | 15.0.26606.0 | Opcional
Microsoft.VisualStudio.Component.WebDeploy | Implantação da Web | 15.0.26208.0 | Opcional
Microsoft.VisualStudio.ComponentGroup.ArchitectureTools.Managed | Ferramentas de arquitetura e análise | 15.0.26208.0 | Opcional


## <a name="game-development-with-unity"></a>Desenvolvimento de jogos com Unity

**ID:** Microsoft.VisualStudio.Workload.ManagedGame

**Descrição:** criar jogos 2D e 3D com o Unity, um ambiente de desenvolvimento avançado de plataforma cruzada.

### <a name="components-included-by-this-workload"></a>Componentes incluídos por essa carga de trabalho

ID do componente | Nome | Versão | Tipo de dependência
--- | --- | --- | ---
Microsoft.Net.Component.3.5.DeveloperTools | Ferramentas de desenvolvimento do .NET Framework 3.5 | 15.0.26621.2 | Necessária
Microsoft.VisualStudio.Component.Roslyn.Compiler | Compiladores Roslyn do C# e Visual Basic | 15.0.26208.0 | Necessária
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# e Visual Basic | 15.0.26711.1 | Necessária
Microsoft.VisualStudio.Component.Static.Analysis.Tools | Ferramentas de análise estática | 15.0.26208.0 | Necessária
Microsoft.VisualStudio.Component.Unity | Ferramentas do Visual Studio para Unity | 15.0.26730.10 | Necessária
Component.UnityEngine | Editor do Unity 5.6 | 15.0.26730.10 | Recomendado


## <a name="linux-development-with-c"></a>Desenvolvimento de Linux com C++

**ID:** Microsoft.VisualStudio.Workload.NativeCrossPlat

**Descrição:** criar e depurar aplicativos executados em um ambiente Linux.

### <a name="components-included-by-this-workload"></a>Componentes incluídos por essa carga de trabalho

ID do componente | Nome | Versão | Tipo de dependência
--- | --- | --- | ---
Component.MDD.Linux | Desenvolvimento do Visual C++ para Linux | 15.0.26711.1 | Necessária
Microsoft.VisualStudio.Component.VC.CoreIde | Principais recursos do Visual Studio C++ | 15.0.26606.0 | Necessária
Microsoft.VisualStudio.Component.Windows10SDK | Tempo de execução C Universal do Windows | 15.0.26621.2 | Necessária


## <a name="desktop-development-with-c"></a>Desenvolvimento de área de trabalho com o C++

**ID:** Microsoft.VisualStudio.Workload.NativeDesktop

**Descrição:** criar aplicativos clássicos baseados no Windows usando o poder do conjunto de ferramentas do Visual C++, ATL e recursos opcionais como MFC e C++/CLI.

### <a name="components-included-by-this-workload"></a>Componentes incluídos por essa carga de trabalho

ID do componente | Nome | Versão | Tipo de dependência
--- | --- | --- | ---
Microsoft.Component.MSBuild | MSBuild | 15.0.26208.0 | Necessária
Microsoft.VisualStudio.Component.ClassDesigner | Designer de Classe | 15.0.26208.0 | Necessária
Microsoft.VisualStudio.Component.CodeMap | Mapa de Códigos | 15.0.26208.0 | Necessária
Microsoft.VisualStudio.Component.Debugger.JustInTime | Depurador Just-In-Time | 15.0.26621.2 | Necessária
Microsoft.VisualStudio.Component.GraphDocument | Editor DGML | 15.0.26208.0 | Necessária
Microsoft.VisualStudio.Component.Roslyn.Compiler | Compiladores Roslyn do C# e Visual Basic | 15.0.26208.0 | Necessária
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | SQL Server Express 2016 LocalDB | 15.0.26208.0 | Necessária
Microsoft.VisualStudio.Component.SQL.NCLI | SQL Server Native Client | 15.0.26208.0 | Necessária
Microsoft.VisualStudio.Component.TextTemplating | Transformação de modelo de texto | 15.0.26208.0 | Necessária
Microsoft.VisualStudio.Component.VC.CoreIde | Principais recursos do Visual Studio C++ | 15.0.26606.0 | Necessária
Microsoft.VisualStudio.Component.VC.Redist.14.Latest | Atualização Redistribuível do Visual C++ 2017 | 15.0.26606.0 | Necessária
Microsoft.VisualStudio.ComponentGroup.ArchitectureTools.Native | Ferramentas de arquitetura para o C++ | 15.0.26208.0 | Necessária
Microsoft.VisualStudio.ComponentGroup.NativeDesktop.Core | Principais recursos de área de trabalho do Visual C++ | 15.0.26621.2 | Necessária
Component.Microsoft.VisualStudio.RazorExtension | Razor Language Services | 15.0.26720.2 | Recomendado
Microsoft.VisualStudio.Component.Graphics.Tools | Depurador de gráficos e criador de perfil de GPU do DirectX | 15.0.26208.0 | Recomendado
Microsoft.VisualStudio.Component.Graphics.Win81 | SDK das Ferramentas de Gráficos do Windows 8.1 | 15.0.26208.0 | Recomendado
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# e Visual Basic | 15.0.26711.1 | Recomendado
Microsoft.VisualStudio.Component.Static.Analysis.Tools | Ferramentas de análise estática | 15.0.26208.0 | Recomendado
Microsoft.VisualStudio.Component.VC.CMake.Project | Ferramentas do Visual C++ para CMake | 15.0.26621.2 | Recomendado
Microsoft.VisualStudio.Component.VC.DiagnosticTools | Ferramentas de criação de perfil do C++ | 15.0.26720.2 | Recomendado
Microsoft.VisualStudio.Component.VC.Tools.x86.x64 | Conjunto de ferramentas do VC++ 2017 v141 (x86, x64) | 15.0.26621.2 | Recomendado
Microsoft.VisualStudio.Component.Windows10SDK.15063.Desktop | SDK do Windows 10 (10.0.15063.0) para Desktop C++ x86 e x64 | 15.0.26621.2 | Recomendado
Microsoft.VisualStudio.Component.Windows10SDK.15063.UWP | SDK do Windows 10 (10.0.15063.0) para UWP: C#, VB, JS | 15.0.26621.2 | Recomendado
Microsoft.VisualStudio.Component.Windows10SDK.15063.UWP.Native | SDK do Windows 10 (10.0.15063.0) para UWP: C++ | 15.0.26621.2 | Recomendado
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | Desenvolvimento do ASP.NET e para a Web | 15.0.26606.0 | Recomendado
Component.Incredibuild | IncrediBuild - Aceleração de Build | 15.0.26720.2 | Opcional
Component.IncredibuildMenu | IncrediBuildMenu | 1.5.0.1 | Opcional
Microsoft.Component.VC.Runtime.UCRTSDK | SDK do CRT Universal do Windows | 15.0.26208.0 | Opcional
Microsoft.Net.Component.4.6.1.SDK | SDK do .NET Framework 4.6.1 | 15.0.26621.2 | Opcional
Microsoft.Net.Component.4.6.1.TargetingPack | Pacote de direcionamento do .NET Framework 4.6.1 | 15.0.26621.2 | Opcional
Microsoft.VisualStudio.Component.VC.140 | Conjunto de ferramentas do VC++ 2015.3 v140 para área de trabalho (x86,x64) | 15.0.26720.2 | Opcional
Microsoft.VisualStudio.Component.VC.ATL | Suporte ao Visual C++ ATL | 15.0.26621.2 | Opcional
Microsoft.VisualStudio.Component.VC.ATLMFC | Suporte ao MFC e ATL (x86 e x64) | 15.0.26621.2 | Opcional
Microsoft.VisualStudio.Component.VC.ClangC2 | Clang/C2 (experimental) | 15.0.26724.1 | Opcional
Microsoft.VisualStudio.Component.VC.CLI.Support | Suporte ao C++/CLI | 15.0.26621.2 | Opcional
Microsoft.VisualStudio.Component.VC.Modules.x86.x64 | Módulos de Biblioteca Padrão (experimental) | 15.0.26720.2 | Opcional
Microsoft.VisualStudio.Component.Windows10SDK.10240 | SDK do Windows 10 (10.0.10240.0) | 15.0.26208.0 | Opcional
Microsoft.VisualStudio.Component.Windows10SDK.10586 | SDK do Windows 10 (10.0.10586.0) | 15.0.26208.0 | Opcional
Microsoft.VisualStudio.Component.Windows10SDK.14393 | SDK do Windows 10 (10.0.14393.0) | 15.0.26208.0 | Opcional
Microsoft.VisualStudio.Component.Windows81SDK | SDK do Windows 8.1 | 15.0.26208.0 | Opcional
Microsoft.VisualStudio.Component.WinXP | Suporte do Windows XP para C++ | 15.0.26208.0 | Opcional
Microsoft.VisualStudio.ComponentGroup.NativeDesktop.Win81 | SDK do Windows 8.1 e SDK do UCRT | 15.0.26208.0 | Opcional
Microsoft.VisualStudio.ComponentGroup.NativeDesktop.WinXP | Suporte do Windows XP para C++ | 15.0.26208.0 | Opcional


## <a name="game-development-with-c"></a>Desenvolvimento de jogos com C++

**ID:** Microsoft.VisualStudio.Workload.NativeGame

**Descrição:** usar todo o poder do C++ para criar jogos profissionais da plataforma DirectX, Unreal ou Cocos2d.

### <a name="components-included-by-this-workload"></a>Componentes incluídos por essa carga de trabalho

ID do componente | Nome | Versão | Tipo de dependência
--- | --- | --- | ---
Microsoft.VisualStudio.Component.VC.Redist.14.Latest | Atualização Redistribuível do Visual C++ 2017 | 15.0.26606.0 | Necessária
Microsoft.VisualStudio.Component.Graphics.Tools | Depurador de gráficos e criador de perfil de GPU do DirectX | 15.0.26208.0 | Recomendado
Microsoft.VisualStudio.Component.Graphics.Win81 | SDK das Ferramentas de Gráficos do Windows 8.1 | 15.0.26208.0 | Recomendado
Microsoft.VisualStudio.Component.Static.Analysis.Tools | Ferramentas de análise estática | 15.0.26208.0 | Recomendado
Microsoft.VisualStudio.Component.VC.CoreIde | Principais recursos do Visual Studio C++ | 15.0.26606.0 | Recomendado
Microsoft.VisualStudio.Component.VC.DiagnosticTools | Ferramentas de criação de perfil do C++ | 15.0.26720.2 | Recomendado
Microsoft.VisualStudio.Component.VC.Tools.x86.x64 | Conjunto de ferramentas do VC++ 2017 v141 (x86, x64) | 15.0.26621.2 | Recomendado
Microsoft.VisualStudio.Component.Windows10SDK.15063.Desktop | SDK do Windows 10 (10.0.15063.0) para Desktop C++ x86 e x64 | 15.0.26621.2 | Recomendado
Microsoft.VisualStudio.Component.Windows10SDK.15063.UWP | SDK do Windows 10 (10.0.15063.0) para UWP: C#, VB, JS | 15.0.26621.2 | Recomendado
Microsoft.VisualStudio.Component.Windows10SDK.15063.UWP.Native | SDK do Windows 10 (10.0.15063.0) para UWP: C++ | 15.0.26621.2 | Recomendado
Component.Android.NDK.R12B | NDK do Android (R12B) | 12.1.9 | Opcional
Component.Android.SDK19 | Instalação do SDK do Android (níveis de API 19 e 21) | 15.0.26621.2 | Opcional
Component.Android.SDK22 | Instalação do SDK do Android (nível de API 22) | 15.0.26208.0 | Opcional
Component.Android.SDK23 | Instalação do SDK do Android (nível de API 23) | 15.0.26606.0 | Opcional
Component.Ant | Apache Ant (1.9.3) | 1.9.3.7 | Opcional
Component.Cocos | Cocos | 15.0.26621.2 | Opcional
Component.Incredibuild | IncrediBuild - Aceleração de Build | 15.0.26720.2 | Opcional
Component.IncredibuildMenu | IncrediBuildMenu | 1.5.0.1 | Opcional
Component.JavaJDK | Java SE Development Kit (8.0.1120.15) | 15.0.26403.0 | Opcional
Component.MDD.Android | Ferramentas de desenvolvimento do Android para C++ | 15.0.26606.0 | Opcional
Component.Unreal | Instalador do Unreal Engine | 15.0.26621.2 | Opcional
Component.Unreal.Android | Suporte ao Visual Studio Android para Unreal Engine | 15.0.26724.1 | Opcional
Microsoft.Component.VC.Runtime.UCRTSDK | SDK do CRT Universal do Windows | 15.0.26208.0 | Opcional
Microsoft.Net.Component.4.5.1.TargetingPack | Pacote de direcionamento do .NET Framework 4.5.1 | 15.0.26621.2 | Opcional
Microsoft.Net.Component.4.5.2.TargetingPack | Pacote de direcionamento do .NET Framework 4.5.2 | 15.0.26621.2 | Opcional
Microsoft.Net.Component.4.5.TargetingPack | Pacote de direcionamento do .NET Framework 4.5 | 15.0.26621.2 | Opcional
Microsoft.Net.Component.4.6.1.SDK | SDK do .NET Framework 4.6.1 | 15.0.26621.2 | Opcional
Microsoft.Net.Component.4.6.1.TargetingPack | Pacote de direcionamento do .NET Framework 4.6.1 | 15.0.26621.2 | Opcional
Microsoft.Net.Component.4.6.TargetingPack | Pacote de direcionamento do .NET Framework 4.6 | 15.0.26621.2 | Opcional
Microsoft.Net.Component.4.TargetingPack | Pacote de direcionamento do .NET Framework 4 | 15.0.26621.2 | Opcional
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | Ferramentas de desenvolvimento do .NET Framework 4.6.1 | 15.0.26606.0 | Opcional
Microsoft.Net.ComponentGroup.TargetingPacks.Common | Ferramentas de desenvolvimento do .NET Framework 4 a 4.6 | 15.0.26606.0 | Opcional
Microsoft.VisualStudio.Component.Roslyn.Compiler | Compiladores Roslyn do C# e Visual Basic | 15.0.26208.0 | Opcional
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# e Visual Basic | 15.0.26711.1 | Opcional
Microsoft.VisualStudio.Component.Windows10SDK | Tempo de execução C Universal do Windows | 15.0.26621.2 | Opcional
Microsoft.VisualStudio.Component.Windows10SDK.10240 | SDK do Windows 10 (10.0.10240.0) | 15.0.26208.0 | Opcional
Microsoft.VisualStudio.Component.Windows10SDK.10586 | SDK do Windows 10 (10.0.10586.0) | 15.0.26208.0 | Opcional
Microsoft.VisualStudio.Component.Windows10SDK.14393 | SDK do Windows 10 (10.0.14393.0) | 15.0.26208.0 | Opcional
Microsoft.VisualStudio.Component.Windows81SDK | SDK do Windows 8.1 | 15.0.26208.0 | Opcional
Microsoft.VisualStudio.ComponentGroup.NativeDesktop.Win81 | SDK do Windows 8.1 e SDK do UCRT | 15.0.26208.0 | Opcional


## <a name="mobile-development-with-c"></a>Desenvolvimento móvel com C++

**ID:** Microsoft.VisualStudio.Workload.NativeMobile

**Descrição:** criar aplicativos de plataforma cruzada para o iOS, Android ou Windows usando o C++.

### <a name="components-included-by-this-workload"></a>Componentes incluídos por essa carga de trabalho

ID do componente | Nome | Versão | Tipo de dependência
--- | --- | --- | ---
Microsoft.VisualStudio.Component.VC.CoreIde | Principais recursos do Visual Studio C++ | 15.0.26606.0 | Necessária
Component.Android.NDK.R13B | NDK do Android (R13B) | 13.1.6 | Recomendado
Component.Android.SDK19 | Instalação do SDK do Android (níveis de API 19 e 21) | 15.0.26621.2 | Recomendado
Component.Android.SDK22 | Instalação do SDK do Android (nível de API 22) | 15.0.26208.0 | Recomendado
Component.Ant | Apache Ant (1.9.3) | 1.9.3.7 | Recomendado
Component.MDD.Android | Ferramentas de desenvolvimento do Android para C++ | 15.0.26606.0 | Recomendado
Component.Android.NDK.R12B | NDK do Android (R12B) | 12.1.9 | Opcional
Component.Android.NDK.R12B_3264 | NDK do Android (R12B) (32 bits) | 12.1.10 | Opcional
Component.Android.NDK.R13B_3264 | NDK do Android (R13B) (32 bits) | 13.1.7 | Opcional
Component.Android.SDK23 | Instalação do SDK do Android (nível de API 23) | 15.0.26606.0 | Opcional
Component.Google.Android.Emulator.API23.V2 | Emulador do Google Android (nível de API 23) | 15.0.26711.1 | Opcional
Component.HAXM | Intel HAXM (Hardware Accelerated Execution Manager) | 15.0.26208.0 | Opcional
Component.Incredibuild | IncrediBuild - Aceleração de Build | 15.0.26720.2 | Opcional
Component.IncredibuildMenu | IncrediBuildMenu | 1.5.0.1 | Opcional
Component.JavaJDK | Java SE Development Kit (8.0.1120.15) | 15.0.26403.0 | Opcional
Component.MDD.IOS | Ferramentas de desenvolvimento do iOS para C++ | 15.0.26621.2 | Opcional


## <a name="net-core-cross-platform-development"></a>Desenvolvimento de plataforma cruzada do .NET Core

**ID:** Microsoft.VisualStudio.Workload.NetCoreTools

**Descrição:** criar aplicativos de plataforma cruzada usando o .NET Core, ASP.NET Core, HTML, JavaScript e ferramentas de desenvolvimento de contêiner.

### <a name="components-included-by-this-workload"></a>Componentes incluídos por essa carga de trabalho

ID do componente | Nome | Versão | Tipo de dependência
--- | --- | --- | ---
Microsoft.Net.Core.Component.SDK | Ferramentas de desenvolvimento do .NET Core 1.0 a 1.1 | 15.0.26606.0 | Necessária
Microsoft.NetCore.ComponentGroup.Web | Ferramentas de desenvolvimento do .NET Core 1.0 a 1.1 | 15.0.26621.2 | Necessária
Component.Microsoft.VisualStudio.RazorExtension | Razor Language Services | 15.0.26720.2 | Recomendado
Component.WebSocket | WebSocket4Net | 15.0.26606.0 | Recomendado
Microsoft.Component.ClickOnce | Publicação ClickOnce | 15.0.26208.0 | Recomendado
Microsoft.Component.MSBuild | MSBuild | 15.0.26208.0 | Recomendado
Microsoft.Net.Component.4.5.1.TargetingPack | Pacote de direcionamento do .NET Framework 4.5.1 | 15.0.26621.2 | Recomendado
Microsoft.Net.Component.4.5.2.TargetingPack | Pacote de direcionamento do .NET Framework 4.5.2 | 15.0.26621.2 | Recomendado
Microsoft.Net.Component.4.5.TargetingPack | Pacote de direcionamento do .NET Framework 4.5 | 15.0.26621.2 | Recomendado
Microsoft.Net.Component.4.6.1.SDK | SDK do .NET Framework 4.6.1 | 15.0.26621.2 | Recomendado
Microsoft.Net.Component.4.6.1.TargetingPack | Pacote de direcionamento do .NET Framework 4.6.1 | 15.0.26621.2 | Recomendado
Microsoft.Net.Component.4.6.TargetingPack | Pacote de direcionamento do .NET Framework 4.6 | 15.0.26621.2 | Recomendado
Microsoft.Net.Component.4.TargetingPack | Pacote de direcionamento do .NET Framework 4 | 15.0.26621.2 | Recomendado
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | Ferramentas de desenvolvimento do .NET Framework 4.6.1 | 15.0.26606.0 | Recomendado
Microsoft.Net.ComponentGroup.TargetingPacks.Common | Ferramentas de desenvolvimento do .NET Framework 4 a 4.6 | 15.0.26606.0 | Recomendado
Microsoft.VisualStudio.Component.AppInsights.Tools | Ferramentas de Análise do Desenvolvedor | 15.0.26621.2 | Recomendado
Microsoft.VisualStudio.Component.Azure.AuthoringTools | Ferramentas de Criação do Azure | 15.0.26621.2 | Recomendado
Microsoft.VisualStudio.Component.Azure.ClientLibs | Bibliotecas do Azure para .NET | 15.0.26208.0 | Recomendado
Microsoft.VisualStudio.Component.Azure.Compute.Emulator | Emulador de Computação do Azure | 15.0.26621.2 | Recomendado
Microsoft.VisualStudio.Component.Azure.Storage.Emulator | Emulador de Armazenamento do Azure | 15.0.26621.2 | Recomendado
Microsoft.VisualStudio.Component.Azure.Waverton | Principais ferramentas dos Serviços de Nuvem do Azure | 15.0.26208.0 | Recomendado
Microsoft.VisualStudio.Component.CloudExplorer | Cloud Explorer | 15.0.26711.1 | Recomendado
Microsoft.VisualStudio.Component.Common.Azure.Tools | Ferramentas de conectividade e publicação | 1.10.50614.2 | Recomendado
Microsoft.VisualStudio.Component.DiagnosticTools | Ferramentas de criação de perfil do .NET | 15.0.26711.1 | Recomendado
Microsoft.VisualStudio.Component.DockerTools | Ferramentas de desenvolvimento de contêiner | 15.0.26724.1 | Recomendado
Microsoft.VisualStudio.Component.IISExpress | IIS Express  | 15.0.26208.0 | Recomendado
Microsoft.VisualStudio.Component.IntelliTrace.FrontEnd | IntelliTrace | 15.0.26606.0 | Recomendado
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | Diagnóstico do JavaScript | 15.0.26606.0 | Recomendado
Microsoft.VisualStudio.Component.JavaScript.TypeScript | Suporte às linguagens JavaScript e TypeScript | 15.0.26606.0 | Recomendado
Microsoft.VisualStudio.Component.LiveUnitTesting | Live Unit Testing | 15.0.26720.2 | Recomendado
Microsoft.VisualStudio.Component.ManagedDesktop.Core | Núcleo da carga de trabalho de área de trabalho gerenciada | 15.0.26419.1 | Recomendado
Microsoft.VisualStudio.Component.NuGet | Gerenciador de pacotes NuGet | 15.0.26621.2 | Recomendado
Microsoft.VisualStudio.Component.PortableLibrary | Pacote de direcionamento da Biblioteca Portátil do .NET | 15.0.26208.0 | Recomendado
Microsoft.VisualStudio.Component.Roslyn.Compiler | Compiladores Roslyn do C# e Visual Basic | 15.0.26208.0 | Recomendado
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# e Visual Basic | 15.0.26711.1 | Recomendado
Microsoft.VisualStudio.Component.SQL.ADAL | Tempo de execução do SQL ADAL | 15.0.26606.0 | Recomendado
Microsoft.VisualStudio.Component.SQL.CLR | Tipos de dados CLR do SQL Server | 15.0.26208.0 | Recomendado
Microsoft.VisualStudio.Component.SQL.CMDUtils | Utilitários de linha de comando do SQL Server | 15.0.26208.0 | Recomendado
Microsoft.VisualStudio.Component.SQL.DataSources | Fontes de dados para suporte do SQL Server | 15.0.26621.2 | Recomendado
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | SQL Server Express 2016 LocalDB | 15.0.26208.0 | Recomendado
Microsoft.VisualStudio.Component.SQL.NCLI | SQL Server Native Client | 15.0.26208.0 | Recomendado
Microsoft.VisualStudio.Component.SQL.SSDT | Ferramentas de dados do SQL Server | 15.0.26208.0 | Recomendado
Microsoft.VisualStudio.Component.Static.Analysis.Tools | Ferramentas de análise estática | 15.0.26208.0 | Recomendado
Microsoft.VisualStudio.Component.TextTemplating | Transformação de modelo de texto | 15.0.26208.0 | Recomendado
Microsoft.VisualStudio.Component.TypeScript.2.3 | SDK do TypeScript 2.3 | 15.0.26621.2 | Recomendado
Microsoft.VisualStudio.Component.VisualStudioData | Fontes de dados e referências de serviço | 15.0.26208.0 | Recomendado
Microsoft.VisualStudio.Component.Web | Ferramentas de desenvolvimento do ASP.NET e para a Web | 15.0.26606.0 | Recomendado
Microsoft.VisualStudio.Component.WebDeploy | Implantação da Web | 15.0.26208.0 | Recomendado
Microsoft.VisualStudio.ComponentGroup.Web | Ferramentas de desenvolvimento do ASP.NET e para a Web | 15.0.26606.0 | Recomendado
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | Desenvolvimento do ASP.NET e para a Web | 15.0.26606.0 | Recomendado
Microsoft.VisualStudio.ComponentGroup.IISDevelopment | Suporte ao IIS no tempo de desenvolvimento | 15.0.26720.2 | Opcional


## <a name="mobile-development-with-net"></a>Desenvolvimento móvel com o .NET

**ID:** Microsoft.VisualStudio.Workload.NetCrossPlat

**Descrição:** criar aplicativos de plataforma cruzada para o iOS, Android ou Windows usando o Xamarin.

### <a name="components-included-by-this-workload"></a>Componentes incluídos por essa carga de trabalho

ID do componente | Nome | Versão | Tipo de dependência
--- | --- | --- | ---
Microsoft.Net.Component.4.6.1.SDK | SDK do .NET Framework 4.6.1 | 15.0.26621.2 | Necessária
Microsoft.Net.Component.4.6.1.TargetingPack | Pacote de direcionamento do .NET Framework 4.6.1 | 15.0.26621.2 | Necessária
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | Ferramentas de desenvolvimento do .NET Framework 4.6.1 | 15.0.26606.0 | Necessária
Microsoft.VisualStudio.Component.PortableLibrary | Pacote de direcionamento da Biblioteca Portátil do .NET | 15.0.26208.0 | Necessária
Component.Android.NDK.R13B | NDK do Android (R13B) | 13.1.6 | Recomendado
Component.Android.SDK23 | Instalação do SDK do Android (nível de API 23) | 15.0.26606.0 | Recomendado
Component.Google.Android.Emulator.API23.V2 | Emulador do Google Android (nível de API 23) | 15.0.26711.1 | Recomendado
Component.HAXM | Intel HAXM (Hardware Accelerated Execution Manager) | 15.0.26208.0 | Recomendado
Component.JavaJDK | Java SE Development Kit (8.0.1120.15) | 15.0.26403.0 | Recomendado
Component.Xamarin | Xamarin | 15.0.26711.1 | Recomendado
Component.Xamarin.Inspector | Xamarin Workbooks | 15.0.26606.0 | Recomendado
Component.Xamarin.Profiler | Criador de perfil do Xamarin | 15.0.26711.1 | Recomendado
Component.Xamarin.RemotedSimulator | Xamarin Remoted Simulator | 15.0.26711.1 | Recomendado
Microsoft.VisualStudio.Component.FSharp | Suporte à linguagem F# | 15.0.26606.0 | Recomendado
Microsoft.VisualStudio.Component.Merq | Ferramentas internas comuns do Xamarin | 15.0.26720.2 | Recomendado
Microsoft.VisualStudio.Component.MonoDebugger | Depurador mono | 15.0.26720.2 | Recomendado
Microsoft.VisualStudio.Component.NuGet | Gerenciador de pacotes NuGet | 15.0.26621.2 | Recomendado
Microsoft.VisualStudio.Component.Roslyn.Compiler | Compiladores Roslyn do C# e Visual Basic | 15.0.26208.0 | Recomendado
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# e Visual Basic | 15.0.26711.1 | Recomendado
Microsoft.VisualStudio.Component.Static.Analysis.Tools | Ferramentas de análise estática | 15.0.26208.0 | Recomendado
Microsoft.Component.ClickOnce | Publicação ClickOnce | 15.0.26208.0 | Opcional
Microsoft.Component.NetFX.Native | .NET Nativo | 15.0.26208.0 | Opcional
Microsoft.VisualStudio.Component.AppInsights.Tools | Ferramentas de Análise do Desenvolvedor | 15.0.26621.2 | Opcional
Microsoft.VisualStudio.Component.CodeClone | Clone de Código | 15.0.26208.0 | Opcional
Microsoft.VisualStudio.Component.CodeMap | Mapa de Códigos | 15.0.26208.0 | Opcional
Microsoft.VisualStudio.Component.DependencyValidation.Enterprise | Validação de dependência dinâmica | 15.0.26208.0 | Opcional
Microsoft.VisualStudio.Component.DiagnosticTools | Ferramentas de criação de perfil do .NET | 15.0.26711.1 | Opcional
Microsoft.VisualStudio.Component.GraphDocument | Editor DGML | 15.0.26208.0 | Opcional
Microsoft.VisualStudio.Component.Graphics | Editores de imagens e modelos 3D | 15.0.26621.2 | Opcional
Microsoft.VisualStudio.Component.Phone.Emulator.15063 | Emulador móvel do Windows 10 (atualização dos criadores) | 15.0.26711.1 | Opcional
Microsoft.VisualStudio.Component.SQL.CLR | Tipos de dados CLR do SQL Server | 15.0.26208.0 | Opcional
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | SQL Server Express 2016 LocalDB | 15.0.26208.0 | Opcional
Microsoft.VisualStudio.Component.SQL.NCLI | SQL Server Native Client | 15.0.26208.0 | Opcional
Microsoft.VisualStudio.Component.VisualStudioData | Fontes de dados e referências de serviço | 15.0.26208.0 | Opcional
Microsoft.VisualStudio.Component.Windows10SDK.15063.UWP | SDK do Windows 10 (10.0.15063.0) para UWP: C#, VB, JS | 15.0.26621.2 | Opcional
Microsoft.VisualStudio.ComponentGroup.ArchitectureTools.Managed | Ferramentas de arquitetura e análise | 15.0.26208.0 | Opcional
Microsoft.VisualStudio.ComponentGroup.UWP.Xamarin | Ferramentas da Plataforma Universal do Windows para Xamarin | 15.0.26606.0 | Opcional


## <a name="aspnet-and-web-development"></a>Desenvolvimento do ASP.NET e para a Web

**ID:** Microsoft.VisualStudio.Workload.NetWeb

**Descrição:** criar aplicativos Web usando o ASP.NET, ASP.NET Core, HTML, JavaScript e ferramentas de desenvolvimento de contêiner.

### <a name="components-included-by-this-workload"></a>Componentes incluídos por essa carga de trabalho

ID do componente | Nome | Versão | Tipo de dependência
--- | --- | --- | ---
Microsoft.Net.Core.Component.SDK | Ferramentas de desenvolvimento do .NET Core 1.0 a 1.1 | 15.0.26606.0 | Necessária
Microsoft.NetCore.ComponentGroup.Web | Ferramentas de desenvolvimento do .NET Core 1.0 a 1.1 | 15.0.26621.2 | Necessária
Component.Microsoft.VisualStudio.RazorExtension | Razor Language Services | 15.0.26720.2 | Recomendado
Component.WebSocket | WebSocket4Net | 15.0.26606.0 | Recomendado
Microsoft.Component.ClickOnce | Publicação ClickOnce | 15.0.26208.0 | Recomendado
Microsoft.Component.MSBuild | MSBuild | 15.0.26208.0 | Recomendado
Microsoft.Net.Component.4.5.1.TargetingPack | Pacote de direcionamento do .NET Framework 4.5.1 | 15.0.26621.2 | Recomendado
Microsoft.Net.Component.4.5.2.TargetingPack | Pacote de direcionamento do .NET Framework 4.5.2 | 15.0.26621.2 | Recomendado
Microsoft.Net.Component.4.5.TargetingPack | Pacote de direcionamento do .NET Framework 4.5 | 15.0.26621.2 | Recomendado
Microsoft.Net.Component.4.6.1.SDK | SDK do .NET Framework 4.6.1 | 15.0.26621.2 | Recomendado
Microsoft.Net.Component.4.6.1.TargetingPack | Pacote de direcionamento do .NET Framework 4.6.1 | 15.0.26621.2 | Recomendado
Microsoft.Net.Component.4.6.TargetingPack | Pacote de direcionamento do .NET Framework 4.6 | 15.0.26621.2 | Recomendado
Microsoft.Net.Component.4.TargetingPack | Pacote de direcionamento do .NET Framework 4 | 15.0.26621.2 | Recomendado
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | Ferramentas de desenvolvimento do .NET Framework 4.6.1 | 15.0.26606.0 | Recomendado
Microsoft.Net.ComponentGroup.TargetingPacks.Common | Ferramentas de desenvolvimento do .NET Framework 4 a 4.6 | 15.0.26606.0 | Recomendado
Microsoft.VisualStudio.Component.AppInsights.Tools | Ferramentas de Análise do Desenvolvedor | 15.0.26621.2 | Recomendado
Microsoft.VisualStudio.Component.Azure.AuthoringTools | Ferramentas de Criação do Azure | 15.0.26621.2 | Recomendado
Microsoft.VisualStudio.Component.Azure.ClientLibs | Bibliotecas do Azure para .NET | 15.0.26208.0 | Recomendado
Microsoft.VisualStudio.Component.Azure.Compute.Emulator | Emulador de Computação do Azure | 15.0.26621.2 | Recomendado
Microsoft.VisualStudio.Component.Azure.Storage.Emulator | Emulador de Armazenamento do Azure | 15.0.26621.2 | Recomendado
Microsoft.VisualStudio.Component.Azure.Waverton | Principais ferramentas dos Serviços de Nuvem do Azure | 15.0.26208.0 | Recomendado
Microsoft.VisualStudio.Component.CloudExplorer | Cloud Explorer | 15.0.26711.1 | Recomendado
Microsoft.VisualStudio.Component.Common.Azure.Tools | Ferramentas de conectividade e publicação | 1.10.50614.2 | Recomendado
Microsoft.VisualStudio.Component.DiagnosticTools | Ferramentas de criação de perfil do .NET | 15.0.26711.1 | Recomendado
Microsoft.VisualStudio.Component.DockerTools | Ferramentas de desenvolvimento de contêiner | 15.0.26724.1 | Recomendado
Microsoft.VisualStudio.Component.EntityFramework | Ferramentas do Entity Framework 6 | 15.0.26208.0 | Recomendado
Microsoft.VisualStudio.Component.IISExpress | IIS Express  | 15.0.26208.0 | Recomendado
Microsoft.VisualStudio.Component.IntelliTrace.FrontEnd | IntelliTrace | 15.0.26606.0 | Recomendado
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | Diagnóstico do JavaScript | 15.0.26606.0 | Recomendado
Microsoft.VisualStudio.Component.JavaScript.TypeScript | Suporte às linguagens JavaScript e TypeScript | 15.0.26606.0 | Recomendado
Microsoft.VisualStudio.Component.LiveUnitTesting | Live Unit Testing | 15.0.26720.2 | Recomendado
Microsoft.VisualStudio.Component.ManagedDesktop.Core | Núcleo da carga de trabalho de área de trabalho gerenciada | 15.0.26419.1 | Recomendado
Microsoft.VisualStudio.Component.NuGet | Gerenciador de pacotes NuGet | 15.0.26621.2 | Recomendado
Microsoft.VisualStudio.Component.PortableLibrary | Pacote de direcionamento da Biblioteca Portátil do .NET | 15.0.26208.0 | Recomendado
Microsoft.VisualStudio.Component.Roslyn.Compiler | Compiladores Roslyn do C# e Visual Basic | 15.0.26208.0 | Recomendado
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# e Visual Basic | 15.0.26711.1 | Recomendado
Microsoft.VisualStudio.Component.SQL.ADAL | Tempo de execução do SQL ADAL | 15.0.26606.0 | Recomendado
Microsoft.VisualStudio.Component.SQL.CLR | Tipos de dados CLR do SQL Server | 15.0.26208.0 | Recomendado
Microsoft.VisualStudio.Component.SQL.CMDUtils | Utilitários de linha de comando do SQL Server | 15.0.26208.0 | Recomendado
Microsoft.VisualStudio.Component.SQL.DataSources | Fontes de dados para suporte do SQL Server | 15.0.26621.2 | Recomendado
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | SQL Server Express 2016 LocalDB | 15.0.26208.0 | Recomendado
Microsoft.VisualStudio.Component.SQL.NCLI | SQL Server Native Client | 15.0.26208.0 | Recomendado
Microsoft.VisualStudio.Component.SQL.SSDT | Ferramentas de dados do SQL Server | 15.0.26208.0 | Recomendado
Microsoft.VisualStudio.Component.Static.Analysis.Tools | Ferramentas de análise estática | 15.0.26208.0 | Recomendado
Microsoft.VisualStudio.Component.TextTemplating | Transformação de modelo de texto | 15.0.26208.0 | Recomendado
Microsoft.VisualStudio.Component.TypeScript.2.3 | SDK do TypeScript 2.3 | 15.0.26621.2 | Recomendado
Microsoft.VisualStudio.Component.VisualStudioData | Fontes de dados e referências de serviço | 15.0.26208.0 | Recomendado
Microsoft.VisualStudio.Component.Wcf.Tooling | Windows Communication Foundation | 15.0.26606.0 | Recomendado
Microsoft.VisualStudio.Component.Web | Ferramentas de desenvolvimento do ASP.NET e para a Web | 15.0.26606.0 | Recomendado
Microsoft.VisualStudio.Component.WebDeploy | Implantação da Web | 15.0.26208.0 | Recomendado
Microsoft.VisualStudio.ComponentGroup.Web | Ferramentas de desenvolvimento do ASP.NET e para a Web | 15.0.26606.0 | Recomendado
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | Desenvolvimento do ASP.NET e para a Web | 15.0.26606.0 | Recomendado
Microsoft.Net.Component.4.6.2.SDK | SDK do .NET Framework 4.6.2 | 15.0.26208.0 | Opcional
Microsoft.Net.Component.4.6.2.TargetingPack | Pacote de direcionamento do .NET Framework 4.6.2 | 15.0.26208.0 | Opcional
Microsoft.Net.Component.4.7.SDK | SDK do .NET Framework 4.7 | 15.0.26419.1 | Opcional
Microsoft.Net.Component.4.7.TargetingPack | Pacote de direcionamento do .NET Framework 4.7 | 15.0.26621.2 | Opcional
Microsoft.Net.ComponentGroup.4.6.2.DeveloperTools | Ferramentas de desenvolvimento do .NET Framework 4.6.2 | 15.0.26621.2 | Opcional
Microsoft.Net.ComponentGroup.4.7.DeveloperTools | Ferramentas de desenvolvimento do .NET Framework 4.7 | 15.0.26606.0 | Opcional
Microsoft.VisualStudio.Component.CodeClone | Clone de Código | 15.0.26208.0 | Opcional
Microsoft.VisualStudio.Component.CodeMap | Mapa de Códigos | 15.0.26208.0 | Opcional
Microsoft.VisualStudio.Component.DependencyValidation.Enterprise | Validação de dependência dinâmica | 15.0.26208.0 | Opcional
Microsoft.VisualStudio.Component.FSharp | Suporte à linguagem F# | 15.0.26606.0 | Opcional
Microsoft.VisualStudio.Component.GraphDocument | Editor DGML | 15.0.26208.0 | Opcional
Microsoft.VisualStudio.Component.TestTools.WebLoadTest | Ferramentas de desempenho para a Web e de teste de carga | 15.0.26606.0 | Opcional
Microsoft.VisualStudio.ComponentGroup.ArchitectureTools.Managed | Ferramentas de arquitetura e análise | 15.0.26208.0 | Opcional
Microsoft.VisualStudio.ComponentGroup.IISDevelopment | Suporte ao IIS no tempo de desenvolvimento | 15.0.26720.2 | Opcional
Microsoft.VisualStudio.Web.Mvc4.ComponentGroup | ASP.NET MVC 4 | 15.0.26606.0 | Opcional


## <a name="nodejs-development"></a>Desenvolvimento do Node.js

**ID:** Microsoft.VisualStudio.Workload.Node

**Descrição:** criar aplicativos de rede escaláveis usando o Node.js, um tempo de execução JavaScript controlado por evento assíncrono. 

### <a name="components-included-by-this-workload"></a>Componentes incluídos por essa carga de trabalho

ID do componente | Nome | Versão | Tipo de dependência
--- | --- | --- | ---
Component.Microsoft.VisualStudio.RazorExtension | Razor Language Services | 15.0.26720.2 | Necessária
Component.WebSocket | WebSocket4Net | 15.0.26606.0 | Necessária
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | Diagnóstico do JavaScript | 15.0.26606.0 | Necessária
Microsoft.VisualStudio.Component.JavaScript.TypeScript | Suporte às linguagens JavaScript e TypeScript | 15.0.26606.0 | Necessária
Microsoft.VisualStudio.Component.Node.Tools | Suporte ao Node.js | 15.0.26621.2 | Necessária
Microsoft.VisualStudio.Component.Roslyn.Compiler | Compiladores Roslyn do C# e Visual Basic | 15.0.26208.0 | Necessária
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# e Visual Basic | 15.0.26711.1 | Necessária
Microsoft.VisualStudio.Component.Static.Analysis.Tools | Ferramentas de análise estática | 15.0.26208.0 | Necessária
Microsoft.VisualStudio.Component.TypeScript.2.3 | SDK do TypeScript 2.3 | 15.0.26621.2 | Necessária
Microsoft.VisualStudio.Component.WebDeploy | Implantação da Web | 15.0.26208.0 | Necessária
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | Desenvolvimento do ASP.NET e para a Web | 15.0.26606.0 | Necessária
Microsoft.VisualStudio.Component.Common.Azure.Tools | Ferramentas de conectividade e publicação | 1.10.50614.2 | Recomendado
Microsoft.VisualStudio.Component.Git | Git para Windows | 15.0.26208.0 | Recomendado
Microsoft.VisualStudio.Component.AppInsights.Tools | Ferramentas de Análise do Desenvolvedor | 15.0.26621.2 | Opcional
Microsoft.VisualStudio.Component.DiagnosticTools | Ferramentas de criação de perfil do .NET | 15.0.26711.1 | Opcional
Microsoft.VisualStudio.Component.VC.CoreIde | Principais recursos do Visual Studio C++ | 15.0.26606.0 | Opcional
Microsoft.VisualStudio.Component.VC.Tools.x86.x64 | Conjunto de ferramentas do VC++ 2017 v141 (x86, x64) | 15.0.26621.2 | Opcional


## <a name="officesharepoint-development"></a>Desenvolvimento para Office/SharePoint

**ID:** Microsoft.VisualStudio.Workload.Office

**Descrição:** criar suplementos do Office e SharePoint, soluções do SharePoint e suplementos do VSTO usando o C#, VB e JavaScript.

### <a name="components-included-by-this-workload"></a>Componentes incluídos por essa carga de trabalho

ID do componente | Nome | Versão | Tipo de dependência
--- | --- | --- | ---
Component.Microsoft.VisualStudio.RazorExtension | Razor Language Services | 15.0.26720.2 | Necessária
Component.WebSocket | WebSocket4Net | 15.0.26606.0 | Necessária
Microsoft.Component.ClickOnce | Publicação ClickOnce | 15.0.26208.0 | Necessária
Microsoft.Component.MSBuild | MSBuild | 15.0.26208.0 | Necessária
Microsoft.Net.Component.4.5.2.TargetingPack | Pacote de direcionamento do .NET Framework 4.5.2 | 15.0.26621.2 | Necessária
Microsoft.Net.Component.4.5.TargetingPack | Pacote de direcionamento do .NET Framework 4.5 | 15.0.26621.2 | Necessária
Microsoft.Net.Component.4.6.1.SDK | SDK do .NET Framework 4.6.1 | 15.0.26621.2 | Necessária
Microsoft.Net.Component.4.6.1.TargetingPack | Pacote de direcionamento do .NET Framework 4.6.1 | 15.0.26621.2 | Necessária
Microsoft.Net.Component.4.TargetingPack | Pacote de direcionamento do .NET Framework 4 | 15.0.26621.2 | Necessária
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | Ferramentas de desenvolvimento do .NET Framework 4.6.1 | 15.0.26606.0 | Necessária
Microsoft.VisualStudio.Component.AppInsights.Tools | Ferramentas de Análise do Desenvolvedor | 15.0.26621.2 | Necessária
Microsoft.VisualStudio.Component.Common.Azure.Tools | Ferramentas de conectividade e publicação | 1.10.50614.2 | Necessária
Microsoft.VisualStudio.Component.Debugger.JustInTime | Depurador Just-In-Time | 15.0.26621.2 | Necessária
Microsoft.VisualStudio.Component.IISExpress | IIS Express  | 15.0.26208.0 | Necessária
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | Diagnóstico do JavaScript | 15.0.26606.0 | Necessária
Microsoft.VisualStudio.Component.JavaScript.TypeScript | Suporte às linguagens JavaScript e TypeScript | 15.0.26606.0 | Necessária
Microsoft.VisualStudio.Component.ManagedDesktop.Core | Núcleo da carga de trabalho de área de trabalho gerenciada | 15.0.26419.1 | Necessária
Microsoft.VisualStudio.Component.ManagedDesktop.Prerequisites | Ferramentas de desenvolvimento de área de trabalho do .NET | 15.0.26621.2 | Necessária
Microsoft.VisualStudio.Component.NuGet | Gerenciador de pacotes NuGet | 15.0.26621.2 | Necessária
Microsoft.VisualStudio.Component.PortableLibrary | Pacote de direcionamento da Biblioteca Portátil do .NET | 15.0.26208.0 | Necessária
Microsoft.VisualStudio.Component.Roslyn.Compiler | Compiladores Roslyn do C# e Visual Basic | 15.0.26208.0 | Necessária
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# e Visual Basic | 15.0.26711.1 | Necessária
Microsoft.VisualStudio.Component.Sharepoint.Tools | Office Developer Tools para Visual Studio | 15.0.26606.0 | Necessária
Microsoft.VisualStudio.Component.SQL.ADAL | Tempo de execução do SQL ADAL | 15.0.26606.0 | Necessária
Microsoft.VisualStudio.Component.SQL.CLR | Tipos de dados CLR do SQL Server | 15.0.26208.0 | Necessária
Microsoft.VisualStudio.Component.SQL.CMDUtils | Utilitários de linha de comando do SQL Server | 15.0.26208.0 | Necessária
Microsoft.VisualStudio.Component.SQL.DataSources | Fontes de dados para suporte do SQL Server | 15.0.26621.2 | Necessária
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | SQL Server Express 2016 LocalDB | 15.0.26208.0 | Necessária
Microsoft.VisualStudio.Component.SQL.NCLI | SQL Server Native Client | 15.0.26208.0 | Necessária
Microsoft.VisualStudio.Component.SQL.SSDT | Ferramentas de dados do SQL Server | 15.0.26208.0 | Necessária
Microsoft.VisualStudio.Component.Static.Analysis.Tools | Ferramentas de análise estática | 15.0.26208.0 | Necessária
Microsoft.VisualStudio.Component.TextTemplating | Transformação de modelo de texto | 15.0.26208.0 | Necessária
Microsoft.VisualStudio.Component.TypeScript.2.3 | SDK do TypeScript 2.3 | 15.0.26621.2 | Necessária
Microsoft.VisualStudio.Component.VisualStudioData | Fontes de dados e referências de serviço | 15.0.26208.0 | Necessária
Microsoft.VisualStudio.Component.Wcf.Tooling | Windows Communication Foundation | 15.0.26606.0 | Necessária
Microsoft.VisualStudio.Component.Web | Ferramentas de desenvolvimento do ASP.NET e para a Web | 15.0.26606.0 | Necessária
Microsoft.VisualStudio.Component.WebDeploy | Implantação da Web | 15.0.26208.0 | Necessária
Microsoft.VisualStudio.Component.Workflow | Windows Workflow Foundation | 15.0.26606.0 | Necessária
Microsoft.VisualStudio.ComponentGroup.Web | Ferramentas de desenvolvimento do ASP.NET e para a Web | 15.0.26606.0 | Necessária
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | Desenvolvimento do ASP.NET e para a Web | 15.0.26606.0 | Necessária
Microsoft.VisualStudio.Component.TeamOffice | VSTO (Visual Studio Tools para Office) | 15.0.26606.0 | Recomendado
Microsoft.VisualStudio.Component.IntelliTrace.FrontEnd | IntelliTrace | 15.0.26606.0 | Opcional


## <a name="python-development"></a>Desenvolvimento do Python

**ID:** Microsoft.VisualStudio.Workload.Python

**Descrição:** edição, depuração, desenvolvimento interativo e controle do código-fonte para o Python.

### <a name="components-included-by-this-workload"></a>Componentes incluídos por essa carga de trabalho

ID do componente | Nome | Versão | Tipo de dependência
--- | --- | --- | ---
Component.CPython3.x64 | Python 3 64 bits (3.6.2) | 3.6.2 | Recomendado
Component.Microsoft.VisualStudio.RazorExtension | Razor Language Services | 15.0.26720.2 | Recomendado
Microsoft.Component.CookiecutterTools | Suporte do modelo Cookiecutter | 15.0.26621.2 | Recomendado
Microsoft.Component.PythonTools | Suporte da linguagem Python | 15.0.26730.0 | Recomendado
Microsoft.Component.PythonTools.Web | Suporte Web do Python | 15.0.26606.0 | Recomendado
Microsoft.Component.VC.Runtime.UCRTSDK | SDK do CRT Universal do Windows | 15.0.26208.0 | Recomendado
Microsoft.VisualStudio.Component.Common.Azure.Tools | Ferramentas de conectividade e publicação | 1.10.50614.2 | Recomendado
Microsoft.VisualStudio.Component.JavaScript.TypeScript | Suporte às linguagens JavaScript e TypeScript | 15.0.26606.0 | Recomendado
Microsoft.VisualStudio.Component.Roslyn.Compiler | Compiladores Roslyn do C# e Visual Basic | 15.0.26208.0 | Recomendado
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# e Visual Basic | 15.0.26711.1 | Recomendado
Microsoft.VisualStudio.Component.SQL.CLR | Tipos de dados CLR do SQL Server | 15.0.26208.0 | Recomendado
Microsoft.VisualStudio.Component.Static.Analysis.Tools | Ferramentas de análise estática | 15.0.26208.0 | Recomendado
Microsoft.VisualStudio.Component.TypeScript.2.3 | SDK do TypeScript 2.3 | 15.0.26621.2 | Recomendado
Microsoft.VisualStudio.Component.VisualStudioData | Fontes de dados e referências de serviço | 15.0.26208.0 | Recomendado
Microsoft.VisualStudio.Component.WebDeploy | Implantação da Web | 15.0.26208.0 | Recomendado
Microsoft.VisualStudio.Component.Windows81SDK | SDK do Windows 8.1 | 15.0.26208.0 | Recomendado
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | Desenvolvimento do ASP.NET e para a Web | 15.0.26606.0 | Recomendado
Component.Anaconda2.x64 | Anaconda2 64 bits (4.4.0) | 4.4.0 | Opcional
Component.Anaconda2.x86 | Anaconda2 32 bits (4.4.0) | 4.4.0 | Opcional
Component.Anaconda3.x64 | Anaconda3 64 bits (4.4.0) | 4.4.0 | Opcional
Component.Anaconda3.x86 | Anaconda3 32 bits (4.4.0) | 4.4.0 | Opcional
Component.CPython2.x64 | Python 2 64 bits (2.7.13) | 2.7.13 | Opcional
Component.CPython2.x86 | Python 2 32 bits (2.7.13) | 2.7.13 | Opcional
Component.CPython3.x86 | Python 3 32 bits (3.6.2) | 3.6.2 | Opcional
Component.WebSocket | WebSocket4Net | 15.0.26606.0 | Opcional
Microsoft.Component.ClickOnce | Publicação ClickOnce | 15.0.26208.0 | Opcional
Microsoft.Component.MSBuild | MSBuild | 15.0.26208.0 | Opcional
Microsoft.Component.NetFX.Native | .NET Nativo | 15.0.26208.0 | Opcional
Microsoft.Component.PythonTools.UWP | Suporte ao Python IoT | 15.0.26606.0 | Opcional
Microsoft.ComponentGroup.PythonTools.NativeDevelopment | Ferramentas de desenvolvimento nativo do Python | 15.0.26730.0 | Opcional
Microsoft.Net.Component.4.5.1.TargetingPack | Pacote de direcionamento do .NET Framework 4.5.1 | 15.0.26621.2 | Opcional
Microsoft.Net.Component.4.5.2.TargetingPack | Pacote de direcionamento do .NET Framework 4.5.2 | 15.0.26621.2 | Opcional
Microsoft.Net.Component.4.5.TargetingPack | Pacote de direcionamento do .NET Framework 4.5 | 15.0.26621.2 | Opcional
Microsoft.Net.Component.4.6.1.SDK | SDK do .NET Framework 4.6.1 | 15.0.26621.2 | Opcional
Microsoft.Net.Component.4.6.1.TargetingPack | Pacote de direcionamento do .NET Framework 4.6.1 | 15.0.26621.2 | Opcional
Microsoft.Net.Component.4.6.TargetingPack | Pacote de direcionamento do .NET Framework 4.6 | 15.0.26621.2 | Opcional
Microsoft.Net.Component.4.TargetingPack | Pacote de direcionamento do .NET Framework 4 | 15.0.26621.2 | Opcional
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | Ferramentas de desenvolvimento do .NET Framework 4.6.1 | 15.0.26606.0 | Opcional
Microsoft.Net.ComponentGroup.TargetingPacks.Common | Ferramentas de desenvolvimento do .NET Framework 4 a 4.6 | 15.0.26606.0 | Opcional
Microsoft.VisualStudio.Component.AppInsights.Tools | Ferramentas de Análise do Desenvolvedor | 15.0.26621.2 | Opcional
Microsoft.VisualStudio.Component.Azure.AuthoringTools | Ferramentas de Criação do Azure | 15.0.26621.2 | Opcional
Microsoft.VisualStudio.Component.Azure.ClientLibs | Bibliotecas do Azure para .NET | 15.0.26208.0 | Opcional
Microsoft.VisualStudio.Component.Azure.Compute.Emulator | Emulador de Computação do Azure | 15.0.26621.2 | Opcional
Microsoft.VisualStudio.Component.Azure.Storage.Emulator | Emulador de Armazenamento do Azure | 15.0.26621.2 | Opcional
Microsoft.VisualStudio.Component.Azure.Waverton | Principais ferramentas dos Serviços de Nuvem do Azure | 15.0.26208.0 | Opcional
Microsoft.VisualStudio.Component.ClassDesigner | Designer de Classe | 15.0.26208.0 | Opcional
Microsoft.VisualStudio.Component.CodeClone | Clone de Código | 15.0.26208.0 | Opcional
Microsoft.VisualStudio.Component.CodeMap | Mapa de Códigos | 15.0.26208.0 | Opcional
Microsoft.VisualStudio.Component.DiagnosticTools | Ferramentas de criação de perfil do .NET | 15.0.26711.1 | Opcional
Microsoft.VisualStudio.Component.GraphDocument | Editor DGML | 15.0.26208.0 | Opcional
Microsoft.VisualStudio.Component.Graphics | Editores de imagens e modelos 3D | 15.0.26621.2 | Opcional
Microsoft.VisualStudio.Component.Graphics.Tools | Depurador de gráficos e criador de perfil de GPU do DirectX | 15.0.26208.0 | Opcional
Microsoft.VisualStudio.Component.Graphics.Win81 | SDK das Ferramentas de Gráficos do Windows 8.1 | 15.0.26208.0 | Opcional
Microsoft.VisualStudio.Component.IISExpress | IIS Express  | 15.0.26208.0 | Opcional
Microsoft.VisualStudio.Component.IntelliTrace.FrontEnd | IntelliTrace | 15.0.26606.0 | Opcional
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | Diagnóstico do JavaScript | 15.0.26606.0 | Opcional
Microsoft.VisualStudio.Component.ManagedDesktop.Core | Núcleo da carga de trabalho de área de trabalho gerenciada | 15.0.26419.1 | Opcional
Microsoft.VisualStudio.Component.NuGet | Gerenciador de pacotes NuGet | 15.0.26621.2 | Opcional
Microsoft.VisualStudio.Component.PortableLibrary | Pacote de direcionamento da Biblioteca Portátil do .NET | 15.0.26208.0 | Opcional
Microsoft.VisualStudio.Component.SQL.ADAL | Tempo de execução do SQL ADAL | 15.0.26606.0 | Opcional
Microsoft.VisualStudio.Component.SQL.CMDUtils | Utilitários de linha de comando do SQL Server | 15.0.26208.0 | Opcional
Microsoft.VisualStudio.Component.SQL.DataSources | Fontes de dados para suporte do SQL Server | 15.0.26621.2 | Opcional
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | SQL Server Express 2016 LocalDB | 15.0.26208.0 | Opcional
Microsoft.VisualStudio.Component.SQL.NCLI | SQL Server Native Client | 15.0.26208.0 | Opcional
Microsoft.VisualStudio.Component.SQL.SSDT | Ferramentas de dados do SQL Server | 15.0.26208.0 | Opcional
Microsoft.VisualStudio.Component.TextTemplating | Transformação de modelo de texto | 15.0.26208.0 | Opcional
Microsoft.VisualStudio.Component.VC.140 | Conjunto de ferramentas do VC++ 2015.3 v140 para área de trabalho (x86,x64) | 15.0.26720.2 | Opcional
Microsoft.VisualStudio.Component.VC.CoreIde | Principais recursos do Visual Studio C++ | 15.0.26606.0 | Opcional
Microsoft.VisualStudio.Component.VC.DiagnosticTools | Ferramentas de criação de perfil do C++ | 15.0.26720.2 | Opcional
Microsoft.VisualStudio.Component.VC.Tools.x86.x64 | Conjunto de ferramentas do VC++ 2017 v141 (x86, x64) | 15.0.26621.2 | Opcional
Microsoft.VisualStudio.Component.Web | Ferramentas de desenvolvimento do ASP.NET e para a Web | 15.0.26606.0 | Opcional
Microsoft.VisualStudio.Component.Windows10SDK | Tempo de execução C Universal do Windows | 15.0.26621.2 | Opcional
Microsoft.VisualStudio.Component.Windows10SDK.10586 | SDK do Windows 10 (10.0.10586.0) | 15.0.26208.0 | Opcional
Microsoft.VisualStudio.Component.Windows10SDK.15063.Desktop | SDK do Windows 10 (10.0.15063.0) para Desktop C++ x86 e x64 | 15.0.26621.2 | Opcional
Microsoft.VisualStudio.Component.Windows10SDK.15063.UWP | SDK do Windows 10 (10.0.15063.0) para UWP: C#, VB, JS | 15.0.26621.2 | Opcional
Microsoft.VisualStudio.Component.Windows10SDK.15063.UWP.Native | SDK do Windows 10 (10.0.15063.0) para UWP: C++ | 15.0.26621.2 | Opcional
Microsoft.VisualStudio.ComponentGroup.Web | Ferramentas de desenvolvimento do ASP.NET e para a Web | 15.0.26606.0 | Opcional


## <a name="universal-windows-platform-development"></a>Desenvolvimento na Plataforma Universal do Windows

**ID:** Microsoft.VisualStudio.Workload.Universal

**Descrição:** criar aplicativos para a Plataforma Universal do Windows com o C#, VB, JavaScript ou, opcionalmente, o C++.

### <a name="components-included-by-this-workload"></a>Componentes incluídos por essa carga de trabalho

ID do componente | Nome | Versão | Tipo de dependência
--- | --- | --- | ---
Component.Microsoft.VisualStudio.RazorExtension | Razor Language Services | 15.0.26720.2 | Necessária
Component.WebSocket | WebSocket4Net | 15.0.26606.0 | Necessária
Microsoft.Component.ClickOnce | Publicação ClickOnce | 15.0.26208.0 | Necessária
Microsoft.Component.NetFX.Native | .NET Nativo | 15.0.26208.0 | Necessária
Microsoft.ComponentGroup.Blend | Blend for Visual Studio | 15.0.26711.1 | Necessária
Microsoft.Net.Component.4.5.TargetingPack | Pacote de direcionamento do .NET Framework 4.5 | 15.0.26621.2 | Necessária
Microsoft.Net.Component.4.6.1.SDK | SDK do .NET Framework 4.6.1 | 15.0.26621.2 | Necessária
Microsoft.VisualStudio.Component.AppInsights.Tools | Ferramentas de Análise do Desenvolvedor | 15.0.26621.2 | Necessária
Microsoft.VisualStudio.Component.DiagnosticTools | Ferramentas de criação de perfil do .NET | 15.0.26711.1 | Necessária
Microsoft.VisualStudio.Component.Graphics | Editores de imagens e modelos 3D | 15.0.26621.2 | Necessária
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | Diagnóstico do JavaScript | 15.0.26606.0 | Necessária
Microsoft.VisualStudio.Component.JavaScript.TypeScript | Suporte às linguagens JavaScript e TypeScript | 15.0.26606.0 | Necessária
Microsoft.VisualStudio.Component.NuGet | Gerenciador de pacotes NuGet | 15.0.26621.2 | Necessária
Microsoft.VisualStudio.Component.PortableLibrary | Pacote de direcionamento da Biblioteca Portátil do .NET | 15.0.26208.0 | Necessária
Microsoft.VisualStudio.Component.Roslyn.Compiler | Compiladores Roslyn do C# e Visual Basic | 15.0.26208.0 | Necessária
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# e Visual Basic | 15.0.26711.1 | Necessária
Microsoft.VisualStudio.Component.SQL.CLR | Tipos de dados CLR do SQL Server | 15.0.26208.0 | Necessária
Microsoft.VisualStudio.Component.Static.Analysis.Tools | Ferramentas de análise estática | 15.0.26208.0 | Necessária
Microsoft.VisualStudio.Component.TypeScript.2.3 | SDK do TypeScript 2.3 | 15.0.26621.2 | Necessária
Microsoft.VisualStudio.Component.UWP.Support | Ferramentas da Plataforma Universal do Windows | 15.0.26621.2 | Necessária
Microsoft.VisualStudio.Component.VisualStudioData | Fontes de dados e referências de serviço | 15.0.26208.0 | Necessária
Microsoft.VisualStudio.Component.Windows10SDK.15063.UWP | SDK do Windows 10 (10.0.15063.0) para UWP: C#, VB, JS | 15.0.26621.2 | Necessária
Microsoft.VisualStudio.ComponentGroup.UWP.Cordova | Ferramentas da Plataforma Universal do Windows para Cordova | 15.0.26711.1 | Necessária
Microsoft.VisualStudio.ComponentGroup.UWP.Xamarin | Ferramentas da Plataforma Universal do Windows para Xamarin | 15.0.26606.0 | Necessária
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | Desenvolvimento do ASP.NET e para a Web | 15.0.26606.0 | Necessária
Microsoft.VisualStudio.Component.IntelliTrace.FrontEnd | IntelliTrace | 15.0.26606.0 | Recomendado
Microsoft.Component.VC.Runtime.OSSupport | Tempo de execução Visual C++ para UWP | 15.0.26621.2 | Opcional
Microsoft.VisualStudio.Component.CodeClone | Clone de Código | 15.0.26208.0 | Opcional
Microsoft.VisualStudio.Component.CodeMap | Mapa de Códigos | 15.0.26208.0 | Opcional
Microsoft.VisualStudio.Component.DependencyValidation.Enterprise | Validação de dependência dinâmica | 15.0.26208.0 | Opcional
Microsoft.VisualStudio.Component.GraphDocument | Editor DGML | 15.0.26208.0 | Opcional
Microsoft.VisualStudio.Component.Graphics.Tools | Depurador de gráficos e criador de perfil de GPU do DirectX | 15.0.26208.0 | Opcional
Microsoft.VisualStudio.Component.Graphics.Win81 | SDK das Ferramentas de Gráficos do Windows 8.1 | 15.0.26208.0 | Opcional
Microsoft.VisualStudio.Component.Phone.Emulator.15063 | Emulador móvel do Windows 10 (atualização dos criadores) | 15.0.26711.1 | Opcional
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | SQL Server Express 2016 LocalDB | 15.0.26208.0 | Opcional
Microsoft.VisualStudio.Component.SQL.NCLI | SQL Server Native Client | 15.0.26208.0 | Opcional
Microsoft.VisualStudio.Component.VC.CoreIde | Principais recursos do Visual Studio C++ | 15.0.26606.0 | Opcional
Microsoft.VisualStudio.Component.VC.Tools.ARM | Compiladores e bibliotecas do Visual C++ para o ARM | 15.0.26621.2 | Opcional
Microsoft.VisualStudio.Component.VC.Tools.x86.x64 | Conjunto de ferramentas do VC++ 2017 v141 (x86, x64) | 15.0.26621.2 | Opcional
Microsoft.VisualStudio.Component.Windows10SDK.10240 | SDK do Windows 10 (10.0.10240.0) | 15.0.26208.0 | Opcional
Microsoft.VisualStudio.Component.Windows10SDK.10586 | SDK do Windows 10 (10.0.10586.0) | 15.0.26208.0 | Opcional
Microsoft.VisualStudio.Component.Windows10SDK.14393 | SDK do Windows 10 (10.0.14393.0) | 15.0.26208.0 | Opcional
Microsoft.VisualStudio.Component.Windows10SDK.15063.UWP.Native | SDK do Windows 10 (10.0.15063.0) para UWP: C++ | 15.0.26621.2 | Opcional
Microsoft.VisualStudio.ComponentGroup.ArchitectureTools.Managed | Ferramentas de arquitetura e análise | 15.0.26208.0 | Opcional
Microsoft.VisualStudio.ComponentGroup.UWP.VC | Ferramentas da Plataforma Universal do Windows para C++ | 15.0.26621.2 | Opcional


## <a name="visual-studio-extension-development"></a>Desenvolvimento de extensões do Visual Studio

**ID:** Microsoft.VisualStudio.Workload.VisualStudioExtension

**Descrição:** criar complementos e extensões para o Visual Studio, incluindo novos comandos, analisadores de código e janelas de ferramentas.

### <a name="components-included-by-this-workload"></a>Componentes incluídos por essa carga de trabalho

ID do componente | Nome | Versão | Tipo de dependência
--- | --- | --- | ---
Microsoft.Component.ClickOnce | Publicação ClickOnce | 15.0.26208.0 | Necessária
Microsoft.Net.Component.4.6.1.SDK | SDK do .NET Framework 4.6.1 | 15.0.26621.2 | Necessária
Microsoft.Net.Component.4.6.1.TargetingPack | Pacote de direcionamento do .NET Framework 4.6.1 | 15.0.26621.2 | Necessária
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | Ferramentas de desenvolvimento do .NET Framework 4.6.1 | 15.0.26606.0 | Necessária
Microsoft.VisualStudio.Component.PortableLibrary | Pacote de direcionamento da Biblioteca Portátil do .NET | 15.0.26208.0 | Necessária
Microsoft.VisualStudio.ComponentGroup.VisualStudioExtension.Prerequisites | Pré-requisitos para o desenvolvimento de extensões do Visual Studio | 15.0.26208.0 | Necessária
Microsoft.VisualStudio.Component.CodeClone | Clone de Código | 15.0.26208.0 | Recomendado
Microsoft.VisualStudio.Component.CodeMap | Mapa de Códigos | 15.0.26208.0 | Recomendado
Microsoft.VisualStudio.Component.DependencyValidation.Enterprise | Validação de dependência dinâmica | 15.0.26208.0 | Recomendado
Microsoft.VisualStudio.Component.DiagnosticTools | Ferramentas de criação de perfil do .NET | 15.0.26711.1 | Recomendado
Microsoft.VisualStudio.Component.GraphDocument | Editor DGML | 15.0.26208.0 | Recomendado
Microsoft.VisualStudio.Component.IntelliTrace.FrontEnd | IntelliTrace | 15.0.26606.0 | Recomendado
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | SQL Server Express 2016 LocalDB | 15.0.26208.0 | Recomendado
Microsoft.VisualStudio.Component.SQL.NCLI | SQL Server Native Client | 15.0.26208.0 | Recomendado
Microsoft.VisualStudio.ComponentGroup.ArchitectureTools.Managed | Ferramentas de arquitetura e análise | 15.0.26208.0 | Recomendado
Component.Dotfuscator | Proteção PreEmptive – Dotfuscator | 15.0.26208.0 | Opcional
Microsoft.Component.MSBuild | MSBuild | 15.0.26208.0 | Opcional
Microsoft.Component.VC.Runtime.OSSupport | Tempo de execução Visual C++ para UWP | 15.0.26621.2 | Opcional
Microsoft.Net.Component.4.6.TargetingPack | Pacote de direcionamento do .NET Framework 4.6 | 15.0.26621.2 | Opcional
Microsoft.VisualStudio.Component.AppInsights.Tools | Ferramentas de Análise do Desenvolvedor | 15.0.26621.2 | Opcional
Microsoft.VisualStudio.Component.ClassDesigner | Designer de Classe | 15.0.26208.0 | Opcional
Microsoft.VisualStudio.Component.DslTools | SDK de Modelagem | 15.0.26711.1 | Opcional
Microsoft.VisualStudio.Component.NuGet | Gerenciador de pacotes NuGet | 15.0.26621.2 | Opcional
Microsoft.VisualStudio.Component.Roslyn.Compiler | Compiladores Roslyn do C# e Visual Basic | 15.0.26208.0 | Opcional
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# e Visual Basic | 15.0.26711.1 | Opcional
Microsoft.VisualStudio.Component.Static.Analysis.Tools | Ferramentas de análise estática | 15.0.26208.0 | Opcional
Microsoft.VisualStudio.Component.TextTemplating | Transformação de modelo de texto | 15.0.26208.0 | Opcional
Microsoft.VisualStudio.Component.VC.ATL | Suporte ao Visual C++ ATL | 15.0.26621.2 | Opcional
Microsoft.VisualStudio.Component.VC.ATLMFC | Suporte ao MFC e ATL (x86 e x64) | 15.0.26621.2 | Opcional
Microsoft.VisualStudio.Component.VC.CoreIde | Principais recursos do Visual Studio C++ | 15.0.26606.0 | Opcional
Microsoft.VisualStudio.Component.VC.Tools.x86.x64 | Conjunto de ferramentas do VC++ 2017 v141 (x86, x64) | 15.0.26621.2 | Opcional
Microsoft.VisualStudio.Component.VSSDK | SDK do Visual Studio | 15.0.26621.2 | Opcional


## <a name="mobile-development-with-javascript"></a>Desenvolvimento móvel com JavaScript

**ID:** Microsoft.VisualStudio.Workload.WebCrossPlat

**Descrição:** criar aplicativos Android, iOS e UWP usando as Ferramentas para Apache Cordova.

### <a name="components-included-by-this-workload"></a>Componentes incluídos por essa carga de trabalho

ID do componente | Nome | Versão | Tipo de dependência
--- | --- | --- | ---
Component.CordovaToolset.6.3.1 | Conjunto de ferramentas do Cordova 6.3.1 | 15.0.26504.0 | Necessária
Component.Microsoft.VisualStudio.RazorExtension | Razor Language Services | 15.0.26720.2 | Necessária
Component.WebSocket | WebSocket4Net | 15.0.26606.0 | Necessária
Microsoft.VisualStudio.Component.Cordova | Desenvolvimento móvel com os principais recursos do JavaScript | 15.0.26606.0 | Necessária
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | Diagnóstico do JavaScript | 15.0.26606.0 | Necessária
Microsoft.VisualStudio.Component.JavaScript.ProjectSystem | JavaScript ProjectSystem e Ferramentas Compartilhadas | 15.0.26606.0 | Necessária
Microsoft.VisualStudio.Component.JavaScript.TypeScript | Suporte às linguagens JavaScript e TypeScript | 15.0.26606.0 | Necessária
Microsoft.VisualStudio.Component.Roslyn.Compiler | Compiladores Roslyn do C# e Visual Basic | 15.0.26208.0 | Necessária
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# e Visual Basic | 15.0.26711.1 | Necessária
Microsoft.VisualStudio.Component.Static.Analysis.Tools | Ferramentas de análise estática | 15.0.26208.0 | Necessária
Microsoft.VisualStudio.Component.TypeScript.2.3 | SDK do TypeScript 2.3 | 15.0.26621.2 | Necessária
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | Desenvolvimento do ASP.NET e para a Web | 15.0.26606.0 | Necessária
Component.Android.SDK23 | Instalação do SDK do Android (nível de API 23) | 15.0.26606.0 | Opcional
Component.Google.Android.Emulator.API23.V2 | Emulador do Google Android (nível de API 23) | 15.0.26711.1 | Opcional
Component.HAXM | Intel HAXM (Hardware Accelerated Execution Manager) | 15.0.26208.0 | Opcional
Component.JavaJDK | Java SE Development Kit (8.0.1120.15) | 15.0.26403.0 | Opcional
Microsoft.Component.ClickOnce | Publicação ClickOnce | 15.0.26208.0 | Opcional
Microsoft.Component.NetFX.Native | .NET Nativo | 15.0.26208.0 | Opcional
Microsoft.VisualStudio.Component.AppInsights.Tools | Ferramentas de Análise do Desenvolvedor | 15.0.26621.2 | Opcional
Microsoft.VisualStudio.Component.DiagnosticTools | Ferramentas de criação de perfil do .NET | 15.0.26711.1 | Opcional
Microsoft.VisualStudio.Component.Git | Git para Windows | 15.0.26208.0 | Opcional
Microsoft.VisualStudio.Component.Graphics | Editores de imagens e modelos 3D | 15.0.26621.2 | Opcional
Microsoft.VisualStudio.Component.Phone.Emulator.15063 | Emulador móvel do Windows 10 (atualização dos criadores) | 15.0.26711.1 | Opcional
Microsoft.VisualStudio.Component.SQL.CLR | Tipos de dados CLR do SQL Server | 15.0.26208.0 | Opcional
Microsoft.VisualStudio.Component.VisualStudioData | Fontes de dados e referências de serviço | 15.0.26208.0 | Opcional
Microsoft.VisualStudio.Component.Windows10SDK.15063.UWP | SDK do Windows 10 (10.0.15063.0) para UWP: C#, VB, JS | 15.0.26621.2 | Opcional
Microsoft.VisualStudio.ComponentGroup.UWP.Cordova | Ferramentas da Plataforma Universal do Windows para Cordova | 15.0.26711.1 | Opcional

## <a name="unaffiliated-components"></a>Componentes não afiliados

Estes são os componentes que não são incluídos com nenhuma carga de trabalho, mas que podem ser selecionados como um componente individual.

ID do componente | Nome | Versão
--- | --- | ---
Component.Android.Emulator | Emulador do Visual Studio para Android | 15.0.26711.1
Component.Android.NDK.R11C | NDK do Android (R11C) | 11.3.13
Component.Android.NDK.R11C_3264 | NDK do Android (R11C) (32 bits) | 11.3.15
Component.GitHub.VisualStudio | Extensão do GitHub para Visual Studio | 2.2.0.10
Microsoft.Component.Blend.SDK.WPF | SDK do Blend for Visual Studio para .NET | 15.0.26711.1
Microsoft.Component.HelpViewer | Visualizador da Ajuda | 15.0.26711.1
Microsoft.VisualStudio.Component.LinqToSql | Ferramentas do LINQ to SQL | 15.0.26208.0
Microsoft.VisualStudio.Component.Phone.Emulator | Emulador do Windows 10 Mobile (Edição de Aniversário) | 15.0.26711.1
Microsoft.VisualStudio.Component.TestTools.CodedUITest | Teste de interface do usuário codificado | 15.0.26606.0
Microsoft.VisualStudio.Component.TestTools.Core | Principais recursos das ferramentas de teste | 15.0.26606.0
Microsoft.VisualStudio.Component.TestTools.FeedbackClient | Microsoft Feedback Client | 15.0.26711.1
Microsoft.VisualStudio.Component.TestTools.MicrosoftTestManager | Microsoft Test Manager | 15.0.26606.0
Microsoft.VisualStudio.Component.TypeScript.2.0 | SDK do TypeScript 2.0 | 15.0.26504.0
Microsoft.VisualStudio.Component.TypeScript.2.1 | SDK do TypeScript 2.1 | 15.0.26208.0
Microsoft.VisualStudio.Component.TypeScript.2.2 | SDK do TypeScript 2.2 | 15.0.26504.0

## <a name="see-also"></a>Consulte também

* [Carga de trabalho do Visual Studio e IDs do componente](workload-and-component-ids.md)
* [Guia do administrador do Visual Studio](visual-studio-administrator-guide.md)
* [Usar parâmetros de linha de comando para instalar o Visual Studio](use-command-line-parameters-to-install-visual-studio.md)
  * [Exemplos de parâmetro de linha de comando](command-line-parameter-examples.md)
* [Criar uma instalação offline do Visual Studio](create-an-offline-installation-of-visual-studio.md)

