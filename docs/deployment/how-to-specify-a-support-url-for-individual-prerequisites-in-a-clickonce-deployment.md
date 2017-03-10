---
title: "Como especificar uma URL de suporte para pr&#233;-requisitos individuais em uma implanta&#231;&#227;o do ClickOnce | Microsoft Docs"
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
  - "implantação ClickOnce, pré-requisitos"
  - "implantação ClickOnce, URLs"
ms.assetid: 590742c3-a286-4160-aa75-7a441bb2207b
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Como especificar uma URL de suporte para pr&#233;-requisitos individuais em uma implanta&#231;&#227;o do ClickOnce
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

A [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] implantação pode testar um número de pré\-requisitos que devem estar disponíveis no computador cliente para o [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicativo seja executado.  Elas incluem a versão mínima necessária da [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)], a versão do sistema operacional e todos os assemblies que devem ser pré\-instalado no cache global de assemblies \(GAC\).  [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)], no entanto, não é possível instalar qualquer um desses pré\-requisitos propriamente dito; Se um pré\-requisito não for encontrado, ele simplesmente pára a instalação e exibe uma caixa de diálogo explicando por que a instalação falhou.  
  
 Há dois métodos para instalar os pré\-requisitos.  Você pode instalá\-las usando um aplicativo de bootstrapper.  Como alternativa, você pode especificar um URL de suporte para pré\-requisitos individuais, o que é exibido para os usuários na caixa de diálogo se o pré\-requisito não for encontrado.  A página referenciada por essa URL pode conter links para instruções sobre como instalar os pré\-requisitos necessários.  Se um aplicativo não especificar um URL de suporte para um pré\-requisito individual, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] exibe o URL de suporte especificado no manifesto de implantação para o aplicativo como um todo, se ela estiver definida.  
  
 Enquanto [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], MageUI.exe e Mage podem todos ser usado para gerar [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] implantações, nenhuma dessas ferramentas apóiam especificando um URL de suporte para pré\-requisitos individuais.  Este documento descreve como modificar a sua implantação manifesto de aplicativo e manifesto de implantação incluir esses URLs de suporte.  
  
### Especificando um URL de suporte para um pré\-requisito individual  
  
1.  Abra o manifesto do aplicativo \(o arquivo. manifest\) para seu [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicativo em um editor de texto.  
  
2.  Para um pré\-requisito do sistema operacional, adicionar o `supportUrl` de atributo para o `dependentOS` elemento:  
  
    ```  
     <dependency>  
        <dependentOS supportUrl="http://www.adatum.com/MyApplication/wrongOSFound.htm">  
          <osVersionInfo>  
            <os majorVersion="5" minorVersion="1" buildNumber="2600" servicePackMajor="0" servicePackMinor="0" />  
          </osVersionInfo>  
        </dependentOS>  
      </dependency>  
    ```  
  
3.  Para um pré\-requisito para uma determinada versão do common language runtime, adicione a `supportUrl` de atributo para o `dependentAssembly` entrada que especifica a dependência de tempo de execução de linguagem comum:  
  
    ```  
      <dependency>  
        <dependentAssembly dependencyType="preRequisite" allowDelayedBinding="true" supportUrl=" http://www.adatum.com/MyApplication/wrongClrVersionFound.htm">  
          <assemblyIdentity name="Microsoft.Windows.CommonLanguageRuntime" version="4.0.30319.0" />  
        </dependentAssembly>  
      </dependency>  
    ```  
  
4.  Para um pré\-requisito para um assembly que deve ser pré\-instalado no cache global de assemblies, defina a `supportUrl` para o `dependentAssembly` o elemento que especifica o assembly necessário:  
  
    ```  
      <dependency>  
        <dependentAssembly dependencyType="preRequisite" allowDelayedBinding="true" supportUrl=" http://www.adatum.com/MyApplication/missingSampleGACAssembly.htm">  
          <assemblyIdentity name="SampleGACAssembly" version="5.0.0.0" publicKeyToken="04529dfb5da245c5" processorArchitecture="msil" language="neutral" />  
        </dependentAssembly>  
      </dependency>  
    ```  
  
5.  Opcional.  Para aplicativos que se destinam a.NET Framework 4, abra o manifesto de implantação \(o arquivo. Application\) para seu [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicativo em um editor de texto.  
  
6.  Para um.NET pré\-requisito Framework 4, adicione a `supportUrl` de atributo para o `compatibleFrameworks` elemento:  
  
    ```  
    <compatibleFrameworks  xmlns="urn:schemas-microsoft-com:clickonce.v2" supportUrl="http://adatum.com/MyApplication/CompatibleFrameworks.htm">  
      <framework targetVersion="4.0" profile="Client" supportedRuntime="4.0.30319" />  
      <framework targetVersion="4.0" profile="Full" supportedRuntime="4.0.30319" />  
    </compatibleFrameworks>  
    ```  
  
7.  Depois de você ter alterado manualmente o manifesto do aplicativo, você deve assinar novamente o manifesto do aplicativo usando o certificado digital, e em seguida, atualizar e assinar novamente o manifesto da implantação.  Você deve usar o Mage ou de ferramentas do SDK do MageUI.exe para realizar essa tarefa, como gerar esses arquivos usando [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] apaga as alterações manuais.  Para obter mais informações sobre como usar Mage para assinar novamente os manifestos, consulte [Como assinar manifestos de aplicativo e implantação novamente](../deployment/how-to-re-sign-application-and-deployment-manifests.md).  
  
## Segurança do .NET Framework  
 A URL de suporte não é exibido na caixa de diálogo se o aplicativo estiver marcado para ser executado em confiança parcial.  
  
## Consulte também  
 [Mage.exe \(Ferramenta de Geração e Edição de Manifesto\)](../Topic/Mage.exe%20\(Manifest%20Generation%20and%20Editing%20Tool\).md)   
 [Instruções passo a passo: implantando um aplicativo ClickOnce manualmente](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)   
 [Elemento \<compatibleFrameworks\>](../Topic/%3CcompatibleFrameworks%3E%20Element%20\(ClickOnce%20Deployment\).md)   
 [ClickOnce e Authenticode](../deployment/clickonce-and-authenticode.md)   
 [Pré\-requisitos de implantação de aplicativos](../deployment/application-deployment-prerequisites.md)