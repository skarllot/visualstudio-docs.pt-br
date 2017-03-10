---
title: "Elemento &lt;dependency&gt; (implanta&#231;&#227;o do ClickOnce) | Microsoft Docs"
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
  - "Elemento <dependency> (manifesto da implantação do ClickOnce)"
ms.assetid: 9b4d2082-0347-4922-ac70-85f11b913039
caps.latest.revision: 27
caps.handback.revision: 27
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Elemento &lt;dependency&gt; (implanta&#231;&#227;o do ClickOnce)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Identifica a versão do aplicativo para instalar e o local do manifesto do aplicativo.  
  
## Sintaxe  
  
```  
  
      <dependency>   
   <dependentAssembly  
      preRequisite  
      visible  
      dependencyType  
      codeBase  
      size  
   >   
      <assemblyIdentity   
         name   
         version   
         publicKeyToken   
         processorArchitecture   
         language  
         type  
      />   
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
  
   </dependentAssembly>   
</dependency>  
```  
  
## Elementos e atributos  
 O `dependency` elemento é obrigatório.  Ela tem nenhum atributo.  Um manifesto de implantação pode ter vários `dependency` elementos.  
  
 O `dependency` elemento geralmente expressa as dependências do aplicativo principal em assemblies contidos em um [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicativo.  Se seu aplicativo Main.exe consome um assembly chamado DotNetAssembly.dll, o assembly deve estar listado em uma seção de dependência.  Dependência, no entanto, pode também express outros tipos de dependências, como dependências em uma versão específica do common language runtime, um assembly no cache global de assemblies \(GAC\) ou em um objeto COM.  Porque é uma tecnologia de implantação, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] não iniciarão o download e instalação desses tipos de dependências, mas ele impede que o aplicativo seja executado se uma ou mais das dependências especificadas não existe.  
  
## dependentAssembly  
 Obrigatório.  Esse elemento contém o `assemblyIdentity` elemento.  A tabela a seguir mostra os atributos do `dependentAssembly` oferece suporte.  
  
|Atributo|Descrição|  
|--------------|---------------|  
|`preRequisite`|Opcional.  Especifica que este assembly já deve existir no GAC.  Os valores válidos são  `true` e  `false`.  Se  `true`e o assembly especificado não existe no GAC, o aplicativo não funciona.|  
|`visible`|Opcional.  Identifica a identidade do aplicativo de nível superior, incluindo suas dependências.  Usado internamente pelo [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] para gerenciar o armazenamento de aplicativos e de ativação.|  
|`dependencyType`|Obrigatório.  A relação entre essa dependência e o aplicativo.  Os valores válidos são:<br /><br /> -   `instalar`.  Componente representa uma instalação separada do aplicativo atual.<br />-   `pré-requisito`.  Componente é exigido pelo aplicativo atual.|  
|`codebase`|Opcional.  O caminho completo para o manifesto do aplicativo.|  
|`size`|Opcional.  O tamanho do manifesto do aplicativo, em bytes.|  
  
## assemblyIdentity  
 Obrigatório.  Este elemento é filho de `dependentAssembly` elemento.  O conteúdo do `assemblyIdentity` deve ser a mesma descrita no [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] o manifesto de aplicativo.  A tabela a seguir mostra os atributos da `assemblyIdentity` elemento.  
  
|Atributo|Descrição|  
|--------------|---------------|  
|`Name`|Obrigatório.  Identifica o nome do aplicativo.|  
|`Version`|Obrigatório.  Especifica o número de versão do aplicativo, no seguinte formato:  `major.minor.build.revision`|  
|`publicKeyToken`|Obrigatório.  Especifica uma seqüência hexadecimal de 16 caracteres que representa os últimos 8 bytes de hash SHA\-1 da chave pública na qual o aplicativo ou assembly é assinado.  A chave pública usada para assinar deve ser 2048 bits ou superior.|  
|`processorArchitecture`|Obrigatório.  Especifica o microprocessador.  Os valores válidos são  `x86` para Windows de 32 bits e  `IA64` para Windows de 64 bits.|  
|`Language`|Opcional.  Identifica os códigos de idioma de duas partes do assembly.  Por exemplo, EN\-US, que significa para inglês \(EUA\).  O padrão é  `neutra`.  Esse elemento se encontra o `asmv2` espaço para nome.|  
|`type`|Opcional.  Para compatibilidade com Windows lado a lado com versões anteriores instalar o tecnologia.  O único valor permitido é  `win32`.|  
  
## hash  
 O `hash` elemento é um filho opcional de `file` elemento.  O `hash` elemento não tem nenhum atributo.  
  
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]usa um hash algorítmico de todos os arquivos em um aplicativo como uma verificação de segurança para garantir que nenhum dos arquivos foram alterados após a implantação.  Se a `hash` elemento não é incluído, essa verificação não será executada. Portanto, omitindo o `hash` elemento não é recomendado.  
  
## DSIG:TRANSFORMS  
 O `dsig:Transforms` elemento é um filho obrigatório da `hash` elemento.  O `dsig:Transforms` elemento não tem nenhum atributo.  
  
## DSIG:Transform  
 O `dsig:Transform` elemento é um filho obrigatório da `dsig:Transforms` elemento.  A tabela a seguir mostra os atributos da `dsig:Transform` elemento.  
  
|Atributo|Descrição|  
|--------------|---------------|  
|`Algorithm`|O algoritmo usado para calcular a compilação para este arquivo.  Atualmente o único valor usado pelo [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] é  `urn: schemas-microsoft-com:HashTransforms.Identity`.|  
  
## DSIG:DigestMethod  
 O `dsig:DigestMethod` elemento é um filho obrigatório da `hash` elemento.  A tabela a seguir mostra os atributos da `dsig:DigestMethod` elemento.  
  
|Atributo|Descrição|  
|--------------|---------------|  
|`Algorithm`|O algoritmo usado para calcular a compilação para este arquivo.  Atualmente o único valor usado pelo [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] é  `http://www.w3.org/2000/09/xmldsig#sha1`.|  
  
## DSIG:DigestValue  
 O `dsig:DigestValue` elemento é um filho obrigatório da `hash` elemento.  O `dsig:DigestValue` elemento não tem nenhum atributo.  Seu valor de texto é o hash computado para o arquivo especificado.  
  
## Comentários  
 Manifestos de implantação geralmente têm um único `assemblyIdentity` elemento que identifica o nome e versão do manifesto do aplicativo.  
  
## Exemplo  
 O seguinte código exemplo mostra um `dependency` elemento em um [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] o manifesto de implantação.  
  
```  
<!-- Identify the assembly dependencies -->  
<dependency>  
  <dependentAssembly dependencyType="install" allowDelayedBinding="true" codebase="MyApplication.exe" size="16384">  
    <assemblyIdentity name="MyApplication" version="0.0.0.0" cultural="neutral" processorArchitecture="msil" />  
    <hash>  
      <dsig:Transforms>  
        <dsig:Transform Algorithm="urn:schemas-microsoft-com:HashTransforms.Identity" />  
      </dsig:Transforms>  
      <dsig:DigestMethod Algorithm="http://www.w3.org/2000/09/xmldsig#sha1" />  
       <dsig:DigestValue>YzXYZJAvj9pgAG3y8jXUjC7AtHg=</dsig:DigestValue>  
    </hash>  
  </dependentAssembly>  
</dependency>  
```  
  
## Exemplo  
 O exemplo de código a seguir especifica uma dependência em um assembly já instalado no GAC.  
  
```  
<dependency>  
  <dependentAssembly dependencyType="preRequisite" allowDelayedBinding="true">  
    <assemblyIdentity name="GACAssembly" version="1.0.0.0" language="neutral" processorArchitecture="msil" />  
  </dependentAssembly>  
</dependency>  
```  
  
## Exemplo  
 O exemplo de código a seguir especifica uma dependência em uma versão específica do common language runtime.  
  
```  
<dependency>  
  <dependentAssembly dependencyType="preRequisite" allowDelayedBinding="true">  
    <assemblyIdentity name="Microsoft.Windows.CommonLanguageRuntime" version="2.0.50215.0" />  
  </dependentAssembly>  
</dependency>  
```  
  
## Exemplo  
 O exemplo de código a seguir especifica uma dependência do sistema operacional.  
  
```  
<dependency>  
   <dependentOS supportUrl="http://www.microsoft.com" description="Microsoft Windows Operating System">  
      <osVersionInfo>  
         <os majorVersion="4" minorVersion="10" />  
      </osVersionInfo>  
   </dependentOS>  
</dependency>  
```  
  
## Consulte também  
 [Manifesto de implantação do ClickOnce](../deployment/clickonce-deployment-manifest.md)   
 [Elemento \<dependency\>](../deployment/dependency-element-clickonce-application.md)