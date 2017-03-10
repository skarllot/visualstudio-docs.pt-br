---
title: "Vis&#227;o geral do cache do ClickOnce | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
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
  - "Aplicativos ClickOnce, cache"
  - "implantação ClickOnce, cache"
  - "Aplicativos do Windows, Implantação ClickOnce"
ms.assetid: e379921e-9ef1-4326-bbf3-53ba67925526
caps.latest.revision: 12
caps.handback.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Vis&#227;o geral do cache do ClickOnce
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Todos os [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicativos, se eles são instalados localmente ou hospedados on\-line, são armazenados no computador cliente em uma [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicativo  *cache*.  A [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] cache é uma família de diretórios ocultos sob o diretório de configurações de Local da pasta de documentos e configurações do usuário atual.  Esse cache contém todos os arquivos do aplicativo, incluindo assemblies, arquivos de configuração, aplicativos e configurações de usuário e o diretório de dados.  O cache também é responsável pela migração do diretório de dados do aplicativo para a versão mais recente.  Para obter mais informações sobre a migração de dados, consulte [Acessando dados locais e remotos em aplicativos ClickOnce](../deployment/accessing-local-and-remote-data-in-clickonce-applications.md).  
  
 Fornecendo um único local para armazenamento de aplicativos, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] assume a tarefa de gerenciar a instalação física de um aplicativo do usuário.  O cache também ajuda a isolar os aplicativos, mantendo os assemblies e arquivos de dados para todos os aplicativos e suas versões distintas separam uns dos outros.  Por exemplo, quando você atualiza um [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicativo, versão e seus recursos de dados são fornecidos com seus próprios diretórios no cache.  
  
## Cota de armazenamento de cache  
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]aplicativos hospedados on\-line são restritos a quantidade de espaço que eles podem ocupar, por uma que restringe o tamanho da cota da [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] cache.  O tamanho do cache se aplica a aplicativos on\-line de todos os do usuário; um único aplicativo parcialmente confiável, on\-line está limitado a que ocupa metade do espaço de cota.  Aplicativos instalados não são limitados pelo tamanho do cache e não contarão no limite de cache.  Para todas as [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] retém de aplicativos, o cache somente a versão atual e a versão instalada anteriormente.  
  
 Por padrão, os computadores cliente ter 250 MB de armazenamento para on\-line [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicativos.  Arquivos de dados não são contadas esse limite.  Um administrador de sistema pode ampliar ou reduzir essa cota em um determinado computador cliente, alterando a chave do registro, HKEY\_CURRENT\_USER\\Software\\Classes\\Software\\Microsoft\\Windows\\CurrentVersion\\Deployment\\OnlineAppQuotaInKB, que é um valor DWORD que expresse o tamanho do cache em kilobytes.  Por exemplo, para reduzir o tamanho do cache como 50 MB, você pode alterar esse valor para 51200.  
  
## Consulte também  
 [Acessando dados locais e remotos em aplicativos ClickOnce](../deployment/accessing-local-and-remote-data-in-clickonce-applications.md)