---
title: "Refer&#234;ncia de API n&#227;o gerenciada do ClickOnce | Microsoft Docs"
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
  - "CleanOnlineAppCache [ClickOnce não gerenciado]"
  - "interface CleanOnlineAppCacheW [ClickOnce não gerenciado]"
  - "ClickOnce, APIs não gerenciadas"
  - "GetDeploymentDataFromManifest [ClickOnce não gerenciado]"
  - "LaunchApplication [ClickOnce não gerenciado]"
ms.assetid: ec002138-4054-456d-bcc1-79ac2f4a4fd7
caps.latest.revision: 6
caps.handback.revision: 6
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Refer&#234;ncia de API n&#227;o gerenciada do ClickOnce
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]APIs públicas não gerenciadas a partir de dfshim.dll.  
  
## CleanOnlineAppCache  
 Limpa ou desinstala todos os aplicativos on\-line a partir do [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] cache do aplicativo.  
  
### Valor de retorno  
 Se bem\-sucedida, retorna S\_OK; Caso contrário, retorna um HRESULT que representa a falha.  Se ocorrer uma exceção gerenciada, retorna 0x80020009 \(DISP\_E\_EXCEPTION\).  
  
### Comentários  
 Chamar CleanOnlineAppCache iniciará o [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] de serviço se ele não estiver sendo executado.  
  
## GetDeploymentDataFromManifest  
 Recupera informações de implantação do URL de manifesto e ativação.  
  
### Parâmetros  
  
|Parâmetro|Descrição|Tipo|  
|---------------|---------------|----------|  
|`pcwzActivationUrl`|Um ponteiro para o `ActivationURL`.|LPCWSTR|  
|`pcwzPathToDeploymentManifest`|Um ponteiro para o `PathToDeploymentManifest`.|LPCWSTR|  
|`pwzApplicationIdentity`|Um ponteiro para um buffer para receber uma seqüência terminada por caractere nulo que especifica a identidade do aplicativo completo é retornado.|LPWSTR|  
|`pdwIdentityBufferLength`|Um ponteiro para uma DWORD que é o comprimento da `pwzApplicationIdentity` buffer, em WCHARs.  Isso inclui o espaço para o caractere de finalização NULL.|LPDWORD|  
|`pwzProcessorArchitecture`|Um ponteiro para um buffer para receber uma seqüência terminada por caractere nulo que especifica a arquitetura de processador da implantação do aplicativo, do manifesto.|LPWSTR|  
|`pdwArchitectureBufferLength`|Um ponteiro para uma DWORD que é o comprimento da `pwzProcessorArchitecture` buffer, em WCHARs.|LPDWORD|  
|`pwzApplicationManifestCodebase`|Um ponteiro para um buffer para receber uma seqüência terminada por caractere nulo que especifica o codebase do manifesto do aplicativo, do manifesto.|LPWSTR|  
|`pdwCodebaseBufferLength`|Um ponteiro para uma DWORD que é o comprimento da `pwzApplicationManifestCodebase` buffer, em WCHARs.|LPDWORD|  
|`pwzDeploymentProvider`|Um ponteiro para um buffer para receber uma seqüência terminada por caractere nulo que especifica o provedor de implantação do manifesto, se presente.  Caso contrário, uma seqüência vazia é retornada.|LPWSTR|  
|`pdwProviderBufferLength`|Um ponteiro para uma DWORD que é o comprimento da `pwzProviderBufferLength`.|LPDWORD|  
  
### Valor de retorno  
 Se bem\-sucedida, retorna S\_OK; Caso contrário, retorna um HRESULT que representa a falha.  Retorna HRESULTFROMWIN32\(ERROR\_INSUFFICIENT\_BUFFER\) se um buffer é muito pequeno.  
  
### Comentários  
 Ponteiros não pode ser nulos.  `pcwzActivationUrl`e `pcwzPathToDeploymentManifest` não pode estar vazio.  
  
 É responsabilidade do chamador para limpar o URL de ativação.  Por exemplo, a adição de escape caracteres onde são necessários ou removendo a seqüência de caracteres de consulta.  
  
 É responsabilidade do chamador para limitar o tamanho.  Por exemplo, o comprimento máximo da URL é 2 KB.  
  
## LaunchApplication  
 Inicia ou instala um aplicativo usando uma URL de implantação.  
  
### Parâmetros  
  
|Parâmetro|Descrição|Tipo|  
|---------------|---------------|----------|  
|`deploymentUrl`|Um ponteiro para uma seqüência terminada por caractere nulo que contém o URL do manifesto da implantação.|LPCWSTR|  
|`data`|Reservado para uso futuro.  Deve ser NULL.|LPVOID|  
|`flags`|Reservado para uso futuro.  Deve ser 0.|DWORD|  
  
### Valor de retorno  
 Se bem\-sucedida, retorna S\_OK; Caso contrário, retorna um HRESULT que representa a falha.  Se ocorrer uma exceção gerenciada, retorna 0x80020009 \(DISP\_E\_EXCEPTION\).  
  
## Consulte também  
 <xref:System.Deployment.Application.DeploymentServiceCom.CleanOnlineAppCache%2A>