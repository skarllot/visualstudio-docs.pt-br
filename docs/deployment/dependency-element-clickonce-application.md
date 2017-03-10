---
title: "Elemento &lt;dependency&gt;(aplicativo ClickOnce) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-deployment"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "urn:schemas-microsoft-com:asm.v2#osVersionInfo"
  - "urn:schemas-microsoft-com:asm.v2#os"
  - "http://www.w3.org/2000/09/xmldsig#Transform"
  - "urn:schemas-microsoft-com:asm.v2#dependency"
  - "http://www.w3.org/2000/09/xmldsig#DigestValue"
  - "urn:schemas-microsoft-com:asm.v2#assemblyIdentity"
  - "http://www.w3.org/2000/09/xmldsig#DigestMethod"
  - "http://www.w3.org/2000/09/xmldsig#Transforms"
  - "urn:schemas-microsoft-com:asm.v2#hash"
  - "urn:schemas-microsoft-com:asm.v2#dependentAssembly"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "Elemento <dependency> (manifesto do aplicativo ClickOnce)"
  - "manifestos [ClickOnce], elemento dependency"
ms.assetid: 09d6a1e0-60f8-4fbd-843b-8e49ee3115a3
caps.latest.revision: 34
caps.handback.revision: 34
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Elemento &lt;dependency&gt;(aplicativo ClickOnce)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Identifica uma dependência de plataforma ou assembly é necessária para o aplicativo.  
  
## Sintaxe  
  
```  
  
      <dependency>  
   <dependentOS  
      supportURL  
      description  
   >  
      <osVersionInfo>  
         <os  
            majorVersion  
            minorVersion  
            buildNumber  
            servicePackMajor  
            servicePackMinor  
            productType  
            suiteType  
         />   
      </osVersionInfo>  
   </dependentOS>  
   <dependentAssembly  
      dependencyType  
      allowDelayedBinding  
      group  
      codeBase  
      size  
   >  
      <assemblyIdentity  
         name  
         version  
         processorArchitecture  
         language  
      >  
         <hash>  
            <dsig:Transforms>  
               <dsig:Transform  
                  Algorithm  
            />  
            </dsig:Transforms>  
            <dsig:DigestMethod />  
            <dsig:DigestValue>  
            </dsig:DigestValue>  
    </hash>  
  
      </assemblyIdentity>  
   </dependentAssembly>  
</dependency>  
```  
  
## Elementos e atributos  
 O `dependency` elemento é obrigatório.  Pode haver várias instâncias do `dependency` no manifesto do aplicativo mesmo.  
  
 O `dependency` elemento sem atributos e contém os seguintes elementos filho.  
  
### dependentOS  
 Opcional.  Contém o `osVersionInfo` elemento.  O `dependentOS` e `dependentAssembly` elementos são mutuamente exclusivos: um ou outro deve existir para um `dependency` elemento, mas não ambos.  
  
 `dependentOS`suporta os seguintes atributos.  
  
|Atributo|Descrição|  
|--------------|---------------|  
|`supportUrl`|Opcional.  Especifica uma URL de suporte para a plataforma dependente.  Essa URL é mostrada ao usuário se encontra\-se obrigatórios da plataforma.|  
|`description`|Opcional.  Descreve, em formato legível, o sistema operacional, descrito pelo `dependentOS` elemento.|  
  
### osVersionInfo  
 Obrigatório.  Este elemento é filho do `dependentOS` elemento e contém o `os` elemento.  Este elemento possui sem atributos.  
  
### sistema operacional  
 Obrigatório.  Este elemento é filho de `osVersionInfo` elemento.  Este elemento possui os seguintes atributos.  
  
|Atributo|Descrição|  
|--------------|---------------|  
|`majorVersion`|Obrigatório.  Especifica o número de versão principal do sistema operacional.|  
|`minorVersion`|Obrigatório.  Especifica o número de versão secundária do sistema operacional.|  
|`buildNumber`|Obrigatório.  Especifica o número de compilação do sistema operacional.|  
|`servicePackMajor`|Obrigatório.  Especifica o número principal do service pack do sistema operacional.|  
|`servicePackMinor`|Opcional.  Especifica o número secundário do service pack do sistema operacional.|  
|`productType`|Opcional.  Identifica o valor do tipo de produto.  Valid values are `server`, `workstation`, and `domainController`.  Por exemplo, para o Windows 2000 Professional, esse valor do atributo é `workstation`.|  
|`suiteType`|Opcional.  Identifica um conjunto de produtos disponível no sistema ou o tipo de configuração do sistema.  Valid values are `backoffice`, `blade`, `datacenter`, `enterprise`, `home`, `professional`, `smallbusiness`, `smallbusinessRestricted`, and `terminal`.  Por exemplo, para o Windows 2000 Professional, esse valor do atributo é `professional`.|  
  
### dependentAssembly  
 Opcional.  Contém o `assemblyIdentity` elemento.  O `dependentOS` e `dependentAssembly` elementos são mutuamente exclusivos: um ou outro deve existir para um `dependency` elemento, mas não ambos.  
  
 `dependentAssembly`tem os seguintes atributos.  
  
|Atributo|Descrição|  
|--------------|---------------|  
|`dependencyType`|Obrigatório.  Especifica o tipo de dependência.  Os valores válidos são `preprequisite` e `install`.  Um `install` assembly é instalado como parte do [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicativo.  A `prerequisite` assembly deve estar presente no cache global de assemblies \(GAC\) antes do [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] pode instalar o aplicativo.|  
|`allowDelayedBinding`|Obrigatório.  Especifica se o assembly pode ser carregado por meio de programação em tempo de execução.|  
|`group`|Opcional.  Se a `dependencyType` atributo está definido como `install`, designa um grupo nomeado de módulos \(assemblies\) que podem ser instalados somente sob demanda.  Para obter mais informações, consulte [Instruções passo a passo: baixando assemblies por demanda com a API de implantação do ClickOnce usando o designer](../Topic/Walkthrough:%20Downloading%20Assemblies%20on%20Demand%20with%20the%20ClickOnce%20Deployment%20API%20Using%20the%20Designer.md).<br /><br /> Se definido como `framework` e o `dependencyType` atributo está definido como `prerequisite`, designa o assembly como parte da.NET Framework.  O cache de composição global \(GAC\) não estiver marcado para este assembly ao instalar em [!INCLUDE[net_v40_short](../debugger/includes/net_v40_short_md.md)] e versões posteriores.|  
|`codeBase`|Necessário quando o `dependencyType` atributo está definido como `install`.  O caminho para o assembly dependente.  Talvez um caminho absoluto ou um caminho relativo para o código do manifesto de base.  Esse caminho deve ser um URI válido para que o manifesto do assembly válido.|  
|`size`|Necessário quando o `dependencyType` atributo está definido como `install`.  O tamanho do assembly dependente, em bytes.|  
  
### assemblyIdentity  
 Obrigatório.  Este elemento é filho de `dependentAssembly` elemento e tem os seguintes atributos.  
  
|Atributo|Descrição|  
|--------------|---------------|  
|`name`|Obrigatório.  Identifica o nome do aplicativo.|  
|`version`|Obrigatório.  Especifica o número de versão do aplicativo no seguinte formato:  `major.minor.build.revision`|  
|`publicKeyToken`|Opcional.  Especifica uma seqüência hexadecimal de 16 caracteres que representa os últimos 8 bytes da `SHA-1` o valor da chave pública na qual o aplicativo ou assembly é assinado de hash.  A chave pública usada para assinar o catálogo deve ser 2048 bits ou mais.|  
|`processorArchitecture`|Opcional.  Especifica o processador.  Os valores válidos são  `x86` para Windows de 32 bits e  `I64` para Windows de 64 bits.|  
|`language`|Opcional.  Identifica os códigos de idioma de duas partes, como, por exemplo, EN\-US, do assembly.|  
  
### hash  
 O `hash` elemento é um filho opcional de `assemblyIdentity` elemento.  O `hash` elemento não tem nenhum atributo.  
  
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]usa um hash algorítmico de todos os arquivos em um aplicativo como uma verificação de segurança, para garantir que nenhum dos arquivos foram alterados após a implantação.  Se a `hash` elemento não é incluído, essa verificação não será executada. Portanto, omitindo o `hash` elemento não é recomendado.  
  
### DSIG:TRANSFORMS  
 O `dsig:Transforms` elemento é um filho obrigatório da `hash` elemento.  O `dsig:Transforms` elemento não tem nenhum atributo.  
  
### DSIG:Transform  
 O `dsig:Transform` elemento é um filho obrigatório da `dsig:Transforms` elemento.  O `dsig:Transform` elemento tem os seguintes atributos.  
  
|Atributo|Descrição|  
|--------------|---------------|  
|`Algorithm`|O algoritmo usado para calcular a compilação para este arquivo.  Atualmente o único valor usado pelo [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] é  `urn: schemas-microsoft-com:HashTransforms.Identity`.|  
  
### DSIG:DigestMethod  
 O `dsig:DigestMethod` elemento é um filho obrigatório da `hash` elemento.  O `dsig:DigestMethod` elemento tem os seguintes atributos.  
  
|Atributo|Descrição|  
|--------------|---------------|  
|`Algorithm`|O algoritmo usado para calcular a compilação para este arquivo.  Atualmente o único valor usado pelo [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] é  `http://www.w3.org/2000/09/xmldsig#sha1`.|  
  
### DSIG:DigestValue  
 O `dsig:DigestValue` elemento é um filho obrigatório da `hash` elemento.  O `dsig:DigestValue` elemento não tem nenhum atributo.  Seu valor de texto é o hash computado para o arquivo especificado.  
  
## Comentários  
 Todos os assemblies usados por seu aplicativo devem ter um correspondente `dependency` elemento.  Assemblies dependentes não incluem módulos \(assemblies\) que deve ser pré\-instalado no cache global de assemblies como assemblies da plataforma.  
  
## Exemplo  
 O exemplo de código a seguir ilustra `dependency` elementos em um [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] o manifesto de aplicativo.  Este exemplo de código é parte de um exemplo maior fornecido para a [Manifesto de aplicativo ClickOnce](../deployment/clickonce-application-manifest.md) tópico.  
  
```  
<dependency>  
  <dependentOS>  
    <osVersionInfo>  
      <os   
        majorVersion="4"   
        minorVersion="10"   
        buildNumber="0"   
        servicePackMajor="0" />  
    </osVersionInfo>  
  </dependentOS>  
</dependency>  
<dependency>  
  <dependentAssembly  
    dependencyType="preRequisite"  
    allowDelayedBinding="true">  
    <assemblyIdentity  
      name="Microsoft.Windows.CommonLanguageRuntime"  
      version="4.0.20506.0" />  
  </dependentAssembly>  
</dependency>  
  
<dependency>  
  <dependentAssembly  
    dependencyType="install"  
    allowDelayedBinding="true"  
    codebase="MyApplication.exe"  
    size="4096">  
    <assemblyIdentity  
      name="MyApplication"  
      version="1.0.0.0"  
      language="neutral"  
      processorArchitecture="x86" />  
    <hash>  
      <dsig:Transforms>  
        <dsig:Transform Algorithm="urn:schemas-microsoft-com:HashTransforms.Identity" />  
      </dsig:Transforms>  
      <dsig:DigestMethod Algorithm="http://www.w3.org/2000/09/xmldsig#sha1" />  
      <dsig:DigestValue>DpTW7RzS9IeT/RBSLj54vfTEzNg=</dsig:DigestValue>  
    </hash>  
  </dependentAssembly>  
</dependency>  
```  
  
## Consulte também  
 [Manifesto de aplicativo ClickOnce](../deployment/clickonce-application-manifest.md)   
 [Elemento \<dependency\>](../deployment/dependency-element-clickonce-deployment.md)