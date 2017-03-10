---
title: "Como usar o ClickOnce para implantar aplicativos que podem ser executados em v&#225;rias vers&#245;es do .NET Framework | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-deployment"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "Aplicativos ClickOnce, várias versões do .NET Framework"
  - "implantação ClickOnce, várias versões do .NET Framework"
  - "implantando aplicativos [ClickOnce], várias versões do .NET Framework"
ms.assetid: e0a8c330-21bc-4eb2-b936-fd0f3c3221f1
caps.latest.revision: 17
caps.handback.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Como usar o ClickOnce para implantar aplicativos que podem ser executados em v&#225;rias vers&#245;es do .NET Framework
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Você pode implantar um aplicativo que se destina a várias versões do.NET Framework usando a tecnologia de implantação ClickOnce.  Isso requer que você gerar e atualizar os manifestos de aplicativo e implantação.  
  
> [!NOTE]
>  Antes de alterar o aplicativo use várias versões do.NET Framework, você deve garantir que seu aplicativo seja executado com várias versões do.NET Framework.  Versão common language runtime é diferente entre [!INCLUDE[net_v40_short](../debugger/includes/net_v40_short_md.md)] versus.NET Framework 2.0.NET Framework 3.0, e.NET Framework 3.5.  
  
 Esse processo requer as seguintes etapas:  
  
1.  Gere os manifestos de aplicativo e implantação.  
  
2.  Altere o manifesto de implantação para listar o múltiplo.NET Framework versões.  
  
3.  Altere o arquivo app. config para listar o compatível.NET Framework versões do tempo de execução.  
  
4.  Altere para marcar assemblies dependentes como o manifesto do aplicativo.Assemblies do NET Framework.  
  
5.  Assine o manifesto do aplicativo.  
  
6.  Atualizar e assinar o manifesto de implantação.  
  
### Para gerar os manifestos de aplicativo e implantação  
  
-   Use o Assistente de publicação ou página Publicar do Project Designer para publicar o aplicativo e gerar o aplicativo e os arquivos de manifesto de implantação.  Para obter mais informações, consulte [Como publicar um aplicativo ClickOnce usando o Assistente de Publicação](../Topic/How%20to:%20Publish%20a%20ClickOnce%20Application%20using%20the%20Publish%20Wizard.md) ou [Página de Publicação, Designer de Projeto](../ide/reference/publish-page-project-designer.md).  
  
### Para alterar o manifesto de implantação para listar o múltiplo.NET Framework versões  
  
1.  No diretório de publicação, abra o manifesto de implantação, usando o Editor de XML no Visual Studio.  O manifesto de implantação tem a extensão de nome de arquivo. Application.  
  
2.  Substitua o código XML entre o `<compatibleFrameworks xmlns="urn:schemas-microsoft-com:clickonce.v2">` e `</compatibleFrameworks>` elementos com o XML que lista os suportados.NET Framework versões do seu aplicativo.  
  
     A tabela a seguir mostra alguns dos disponíveis.NET Framework e o XML correspondente que podem ser adicionados para o manifesto de implantação.  
  
    |.NET Framework versão|XML|  
    |---------------------------|---------|  
    |Cliente 4|\< framework targetVersion \= "4.0" perfil \= "Cliente" supportedRuntime \= "4.0.30319" \/ \>|  
    |Total de 4|\< framework targetVersion \= "4.0" perfil \= "Total" supportedRuntime \= "4.0.30319" \/ \>|  
    |3,5 Cliente de|\< framework targetVersion \= "3.5" perfil \= "Cliente" supportedRuntime \= "2.0.50727" \/ \>|  
    |3,5 Total de|\< framework targetVersion \= "3.5" perfil \= "Total" supportedRuntime \= "2.0.50727" \/ \>|  
    |3.0|\< framework targetVersion \= "3.0" supportedRuntime \= "2.0.50727" \/ \>|  
  
### Para alterar o arquivo app. config para listar o compatível.NET Framework versões do runtime  
  
1.  No Solution Explorer, abra o arquivo app. config, usando o Editor de XML no Visual Studio.  
  
2.  O código XML entre substituir \(ou adicionar\) a `<startup>` e `</startup>` elementos com o XML que lista os suportados.NET Framework runtimes para seu aplicativo.  
  
     A tabela a seguir mostra alguns dos disponíveis.NET Framework e o XML correspondente que podem ser adicionados para o manifesto de implantação.  
  
    |.NET Framework versão de tempo de execução|XML|  
    |------------------------------------------------|---------|  
    |Cliente 4|\< versão supportedRuntime \= sku "v4.0.30319" \= ".NETFramework, versão \= v 4.0, o perfil de cliente de \= "\/ \>|  
    |Total de 4|\< versão supportedRuntime \= sku "v4.0.30319" \= ".NETFramework, versão \= v 4.0 "\/ \>|  
    |3,5 Total de|\< supportedRuntime version\="v2.0.50727"\/ \>|  
    |3,5 Cliente de|\< versão supportedRuntime \= "v2.0.50727" sku \= "Cliente" \/ \>|  
  
### Para alterar o manifesto do aplicativo para marcar assemblies dependentes como.Assemblies do NET Framework  
  
1.  No diretório de publicação, abra o manifesto do aplicativo, usando o Editor de XML no Visual Studio.  O manifesto de implantação tem a extensão de nome de arquivo. manifest.  
  
2.  Adicionar `group="framework"` à dependência XML para os assemblies sentinel \(`System.Core`, `WindowsBase`, `Sentinel.v3.5Client`, e `System.Data.Entity`\).  Por exemplo, o XML deve ser semelhante ao seguinte:  
  
    ```  
    <dependentAssembly dependencyType="preRequisite" allowDelayedBinding="true" group="framework">  
    ```  
  
3.  Atualizar o número da versão do `<assemblyIdentity>` elemento para Microsoft.Windows.CommonLanguageRuntime para o número de versão para o.NET Framework que é o menor denominador comum.  Por exemplo, se os destinos do aplicativo.NET Framework 3.5 e [!INCLUDE[net_v40_short](../debugger/includes/net_v40_short_md.md)], número da versão de uso o 2.0.50727.0 e o XML devem ser semelhante ao seguinte:  
  
    ```  
    <dependency>  
      <dependentAssembly dependencyType="preRequisite" allowDelayedBinding="true">  
        <assemblyIdentity name="Microsoft.Windows.CommonLanguageRuntime" version="2.0.50727.0" />  
      </dependentAssembly>  
    </dependency>  
    ```  
  
### Para atualizar e assinar novamente o aplicativo e implantação manifestos.  
  
-   Atualizar e assinar novamente os manifestos de aplicativo e implantação.  Para obter mais informações, consulte [Como assinar manifestos de aplicativo e implantação novamente](../deployment/how-to-re-sign-application-and-deployment-manifests.md).  
  
## Consulte também  
 [Publicando aplicativos ClickOnce](../deployment/publishing-clickonce-applications.md)   
 [Elemento \<compatibleFrameworks\>](../Topic/%3CcompatibleFrameworks%3E%20Element%20\(ClickOnce%20Deployment\).md)   
 [Elemento \<dependency\>](../deployment/dependency-element-clickonce-application.md)   
 [Manifesto de implantação do ClickOnce](../deployment/clickonce-deployment-manifest.md)   
 [Esquema de arquivos de configuração](../Topic/Configuration%20File%20Schema%20for%20the%20.NET%20Framework.md)