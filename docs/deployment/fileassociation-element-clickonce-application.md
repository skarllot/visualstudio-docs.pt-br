---
title: "Elemento &lt;fileAssociation&gt;(aplicativo ClickOnce) | Microsoft Docs"
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
  - "Elemento <fileAssociation> (manifesto do aplicativo ClickOnce)"
  - "manifestos [ClickOnce], Elemento fileAssociation"
ms.assetid: 8f951b4f-54f9-412e-a9e5-af4e379fcf08
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Elemento &lt;fileAssociation&gt;(aplicativo ClickOnce)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Identifica uma extensão de arquivo a ser associada do aplicativo.  
  
## Sintaxe  
  
```  
<fileAssociation  
    xmlns="urn:schemas-microsoft-com:clickonce.v1"  
    extension  
    description  
    progid  
    defaultIcon  
/>  
```  
  
## Elementos e atributos  
 O `fileAssociation` elemento é opcional.  O elemento tem os seguintes atributos.  
  
|Atributo|Descrição|  
|--------------|---------------|  
|`extension`|Obrigatório.  A extensão de arquivo a ser associado ao aplicativo.|  
|`description`|Obrigatório.  Uma descrição do tipo de arquivo para uso pelo shell.|  
|`progid`|Obrigatório.  Um nome que identifica o tipo de arquivo.|  
|`defaultIcon`|Obrigatório.  Especifica o ícone a ser usado para arquivos com esta extensão.  O arquivo de ícone deve ser especificado usando o [Elemento \<file\>](../Topic/%3Cfile%3E%20Element%20\(ClickOnce%20Application\).md) dentro do [Elemento \<assembly\>](../deployment/assembly-element-clickonce-application.md) que contém este elemento.|  
  
## Comentários  
 Este elemento deve incluir uma referência ao namespace XML para "urn: schemas\-microsoft\-com:clickonce.v1".  Se a `<fileAssociation>` elemento é usado, ele deve vir após a `<application>` elemento pai [Elemento \<assembly\>](../deployment/assembly-element-clickonce-application.md).  
  
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]não substituirão as associações de arquivo existente.  No entanto, um aplicativo de ClickOnce pode substituir a extensão de arquivo para o usuário atual apenas.  Após a desinstalação do aplicativo ClickOnce, ClickOnce exclui a associação de arquivo para o usuário e a associação de por máquina está ativa novamente.  
  
## Exemplo  
 O exemplo de código a seguir ilustra `fileAssociation` o manifesto de elementos em um aplicativo para um aplicativo de editor de texto implantado usando [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)].  Este exemplo de código também inclui o [Elemento \<file\>](../Topic/%3Cfile%3E%20Element%20\(ClickOnce%20Application\).md) exigido pelo `defaultIcon` atributo.  
  
```  
<file name="text.ico" size="4286">  
  <hash>  
    <dsig:Transforms>  
      <dsig:Transform Algorithm="urn:schemas-microsoft-com:HashTransforms.Identity" />  
    </dsig:Transforms>  
    <dsig:DigestMethod Algorithm="http://www.w3.org/2000/09/xmldsig#sha1" />  
    <dsig:DigestValue>0joAqhmfeBb93ZneZv/oTMP2brY=</dsig:DigestValue>  
  </hash>  
</file>  
<file name="writing.ico" size="9662">  
  <hash>  
    <dsig:Transforms>  
      <dsig:Transform Algorithm="urn:schemas-microsoft-com:HashTransforms.Identity" />  
    </dsig:Transforms>  
    <dsig:DigestMethod Algorithm="http://www.w3.org/2000/09/xmldsig#sha1" />  
    <dsig:DigestValue>2cL2U7cm13nG40v9MQdxYKazIwI=</dsig:DigestValue>  
  </hash>  
</file>  
<fileAssociation xmlns="urn:schemas-microsoft-com:clickonce.v1" extension=".text" description="Text  Document (ClickOnce)" progid="Text.Document" defaultIcon="text.ico" />  
<fileAssociation xmlns="urn:schemas-microsoft-com:clickonce.v1" extension=".writing" description="Writings (ClickOnce)" progid="Writing.Document" defaultIcon="writing.ico" />  
```  
  
## Consulte também  
 [Manifesto de aplicativo ClickOnce](../deployment/clickonce-application-manifest.md)