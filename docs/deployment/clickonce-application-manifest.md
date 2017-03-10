---
title: "Manifesto de aplicativo ClickOnce | Microsoft Docs"
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
  - "manifestos de aplicativos [ClickOnce]"
  - "ClickOnce, manifestos de aplicativos"
ms.assetid: 29570cec-4e53-4660-a850-abc4fa150243
caps.latest.revision: 23
caps.handback.revision: 23
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Manifesto de aplicativo ClickOnce
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

A [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]manifesto de aplicativoé um arquivo XML que descreve um aplicativo que é implantado com [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)].  
  
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] manifestos de aplicativo têm os seguintes elementos e atributos.  
  
|Elemento|Descrição|Atributos|  
|--------------|---------------|---------------|  
|[Elemento \<assembly\>](../deployment/assembly-element-clickonce-application.md)|Necessário.  Elemento de nível superior.|`manifestVersion`|  
|[Elemento \<assemblyIdentity\>](../deployment/assemblyidentity-element-clickonce-application.md)|Necessário.  Identifica o assembly principal da [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicativo.|`name`<br /><br /> `version`<br /><br /> `publicKeyToken`<br /><br /> `processorArchitecture`<br /><br /> `language`|  
|[\< TrustInfo \> elemento](../deployment/trustinfo-element-clickonce-application.md)|Identifica os requisitos desegurança do aplicativo.|Nenhum|  
|[Elemento \<entryPoint\>](../deployment/entrypoint-element-clickonce-application.md)|Necessário.  Identifica o ponto de entrada de código do aplicativo .|`name`|  
|[Elemento \<dependency\>](../deployment/dependency-element-clickonce-application.md)|Necessário.  Identifica cada dependência necessária para o aplicativo seja executado.  Opcionalmente, identifica os assemblies que precisam ser pré\-instalado.|Nenhum|  
|[Elemento \<file\>](../Topic/%3Cfile%3E%20Element%20\(ClickOnce%20Application\).md)|Opcional.  Identifica cada arquivo de nonassembly que é usado pelo aplicativo.  Pode incluir dados de isolamento do modelo de objeto componente \(COM\) associados ao arquivo.|`name`<br /><br /> `size`<br /><br /> `group`<br /><br /> `optional`<br /><br /> `writeableType`|  
|[Elemento \<fileAssociation\>](../deployment/fileassociation-element-clickonce-application.md)|Opcional.  Identifica uma extensão de arquivo a ser associado ao aplicativo.|`extension`<br /><br /> `description`<br /><br /> `progid`<br /><br /> `defaultIcon`|  
  
## Comentários  
 O [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]o arquivo demanifesto de aplicativoidentifica um aplicativo implantado usando [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)].    Para obter mais informações sobre o [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)], consulte [Segurança e implantação do ClickOnce](../deployment/clickonce-security-and-deployment.md).  
  
## Local do arquivo  
 A [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]manifesto de aplicativoé específico para uma única versão de uma implantação.    Por esse motivo, eles devem ser armazenados separadamente dos manifestos de implantação .  A convenção comum é colocá\-los em um subdiretório nomeado de acordo com a versãoassociada.  
  
 O aplicativodemanifesto sempre deve ser assinados anteriores à implantação.   Se você alterar um aplicativomanifesto manualmente, use Mage para assinar novamente o aplicativomanifesto, atualização a implantaçãomanifestoe, em seguida, assinar novamente a implantaçãodomanifesto.      Para mais informações, consulte [Instruções passo a passo: implantando um aplicativo ClickOnce manualmente](../deployment/walkthrough-manually-deploying-a-clickonce-application.md).  
  
## Sintaxe do nome de arquivo  
 O nome de um [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]arquivo demanifesto do aplicativodeve ser o nome completo e a extensão do aplicativo conforme identificado na `assemblyIdentity` elemento, seguido pela extensão .o manifesto.    Por exemplo, um aplicativo manifesto que se refere ao Example.exe aplicativo usaria a seguinte sintaxe nome de arquivo .  
  
 `example.exe.manifest`  
  
## Exemplo  
 O exemplo de código a seguir mostra um aplicativomanifesto para um [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicativo.  
  
```  
<?xml version="1.0" encoding="utf-8"?>  
<asmv1:assembly xsi:schemaLocation="urn:schemas-microsoft-com:asm.v1 assembly.adaptive.xsd" manifestVersion="1.0" xmlns:asmv3="urn:schemas-microsoft-com:asm.v3" xmlns:dsig="http://www.w3.org/2000/09/xmldsig#" xmlns:co.v2="urn:schemas-microsoft-com:clickonce.v2" xmlns="urn:schemas-microsoft-com:asm.v2" xmlns:asmv1="urn:schemas-microsoft-com:asm.v1" xmlns:asmv2="urn:schemas-microsoft-com:asm.v2" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:co.v1="urn:schemas-microsoft-com:clickonce.v1">  
  <asmv1:assemblyIdentity name="My Application Deployment.exe" version="1.0.0.0" publicKeyToken="43cb1e8e7a352766" language="neutral" processorArchitecture="x86" type="win32" />  
  <application />  
  <entryPoint>  
    <assemblyIdentity name="MyApplication" version="1.0.0.0" language="neutral" processorArchitecture="x86" />  
    <commandLine file="MyApplication.exe" parameters="" />  
  </entryPoint>  
  <trustInfo>  
    <security>  
      <applicationRequestMinimum>  
        <PermissionSet Unrestricted="true" ID="Custom" SameSite="site" />  
        <defaultAssemblyRequest permissionSetReference="Custom" />  
      </applicationRequestMinimum>  
      <requestedPrivileges xmlns="urn:schemas-microsoft-com:asm.v3">  
        <!--  
          UAC Manifest Options  
          If you want to change the Windows User Account Control level replace the   
          requestedExecutionLevel node with one of the following.  
  
        <requestedExecutionLevel  level="asInvoker" uiAccess="false" />  
        <requestedExecutionLevel  level="requireAdministrator" uiAccess="false" />  
        <requestedExecutionLevel  level="highestAvailable" uiAccess="false" />  
  
         If you want to utilize File and Registry Virtualization for backward   
         compatibility then delete the requestedExecutionLevel node.  
    -->  
        <requestedExecutionLevel level="asInvoker" uiAccess="false" />  
      </requestedPrivileges>  
    </security>  
  </trustInfo>  
  <dependency>  
    <dependentOS>  
      <osVersionInfo>  
        <os majorVersion="4" minorVersion="10" buildNumber="0" servicePackMajor="0" />  
      </osVersionInfo>  
    </dependentOS>  
  </dependency>  
  <dependency>  
    <dependentAssembly dependencyType="preRequisite" allowDelayedBinding="true">  
      <assemblyIdentity name="Microsoft.Windows.CommonLanguageRuntime" version="4.0.20506.0" />  
    </dependentAssembly>  
  </dependency>  
  <dependency>  
    <dependentAssembly dependencyType="install" allowDelayedBinding="true" codebase="MyApplication.exe" size="4096">  
      <assemblyIdentity name="MyApplication" version="1.0.0.0" language="neutral" processorArchitecture="x86" />  
      <hash>  
        <dsig:Transforms>  
          <dsig:Transform Algorithm="urn:schemas-microsoft-com:HashTransforms.Identity" />  
        </dsig:Transforms>  
        <dsig:DigestMethod Algorithm="http://www.w3.org/2000/09/xmldsig#sha1" />  
        <dsig:DigestValue>DpTW7RzS9IeT/RBSLj54vfTEzNg=</dsig:DigestValue>  
      </hash>  
    </dependentAssembly>  
  </dependency>  
<publisherIdentity name="CN=DOMAINCONTROLLER\UserMe" issuerKeyHash="18312a18a21b215ecf4cdb20f5a0e0b0dd263c08" /><Signature Id="StrongNameSignature" xmlns="http://www.w3.org/2000/09/xmldsig#">  
…  
</Signature></r:issuer></r:license></msrel:RelData></KeyInfo></Signature></asmv1:assembly>  
```  
  
## Consulte também  
 [Publicando aplicativos ClickOnce](../deployment/publishing-clickonce-applications.md)