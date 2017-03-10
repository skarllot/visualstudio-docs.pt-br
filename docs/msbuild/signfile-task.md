---
title: "Tarefa SignFile | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/developer/msbuild/2003#SignFile"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "MSBuild, Tarefa SignFile"
  - "Tarefa SignFile [MSBuild]"
ms.assetid: edef1819-ddeb-4e09-95de-fc7063ba9388
caps.latest.revision: 19
caps.handback.revision: 19
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Tarefa SignFile
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Assina o arquivo especificado usando o certificado especificado.  
  
## Parâmetros  
 A tabela a seguir descreve os parâmetros da tarefa `SignFile`.  
  
 Observe que os certificados SHA\-256 são permitidos apenas em computadores que tenham o .NET 4.5 e superior.  
  
> [!WARNING]
>  A partir do Visual Studio 2013 Atualização 3, essa tarefa tem uma nova assinatura que permite que você especifique a versão da estrutura de destino do arquivo.  Você é incentivado a usar a nova assinatura sempre que possível, pois o processo do MSBuild usa hashes SHA\-256 somente quando a estrutura de destino for .NET 4.5 ou superior.  Se a estrutura de destino for .NET 4.0 ou abaixo, o hash SHA\-256 não será usado.  
  
|Parâmetro|Descrição|  
|---------------|---------------|  
|`CertificateThumbprint`|Parâmetro `String` obrigatório.<br /><br /> Especifica o certificado a ser usado para a assinatura.  Esse certificado deve estar no repositório pessoal do usuário atual.|  
|`SigningTarget`|Parâmetro <xref:Microsoft.Build.Framework.ITaskItem> obrigatório.<br /><br /> Especifica os arquivos a serem assinados com o certificado.|  
|`TimestampUrl`|Parâmetro `String` opcional.<br /><br /> Especifica a URL de um servidor de carimbo de data\/hora.|  
|`TargetFrameworkVersion`|A versão do .NET Framework que é usada para o destino.|  
  
## Comentários  
 Além dos parâmetros listados acima, essa tarefa herda parâmetros da classe <xref:Microsoft.Build.Utilities.Task>.  Para obter uma lista desses parâmetros adicionais e de suas descrições, consulte [Classe base Task](../msbuild/task-base-class.md).  
  
## Exemplo  
 O exemplo a seguir usa a tarefa `SignFile` para assinar os arquivos especificados na coleção de itens `FilesToSign` com o certificado especificado pela propriedade `Certificate`.  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <ItemGroup>  
        <FileToSign Include="File.exe" />  
    </ItemGroup>  
    <PropertyGroup>  
        <Certificate>Cert.cer</Certificate>  
    </PropertyGroup>  
    <Target Name="Sign">  
        <SignFile  
            CertificateThumbprint="$(CertificateThumbprint)"  
            SigningTarget="@(FileToSign)"   
            TargetFrameworkVersion="v4.5" />  
    </Target>  
</Project>  
```  
  
> [!NOTE]
>  A impressão digital do certificado é o hash SHA\-1 do certificado.  Para obter mais informações, consulte [Obter o hash SHA\-1 de um certificado de autoridade de certificação raiz confiável](http://msdn.microsoft.com/pt-br/dd641990-9a88-4228-a245-017797131a87).  
  
## Exemplo  
 O exemplo a seguir usa a tarefa `Exec` para assinar os arquivos especificados na coleção de itens `FilesToSign` com o certificado especificado pela propriedade `Certificate`.  Você pode usar isso para assinar arquivos do Windows Installer durante o processo de compilação.  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <ItemGroup>  
        <FileToSign Include="File.msi" />  
    </ItemGroup>  
    <PropertyGroup>  
        <Certificate>Cert.cer</Certificate>  
    </PropertyGroup>  
    <Target Name="Sign">  
        <Exec Command="signtool.exe sign /f CertFile /p Password "@(FileToSign)" "/>  
        <SignFile  
            CertificateThumbprint="$(CertificateThumbprint)"  
            SigningTarget="@(FileToSign)"   
            TargetFrameworkVersion="v4.0" />  
    </Target>  
</Project>  
```  
  
## Consulte também  
 [Referência de tarefas](../msbuild/msbuild-task-reference.md)   
 [ \(tarefas\)](../msbuild/msbuild-tasks.md)