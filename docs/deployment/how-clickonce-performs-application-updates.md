---
title: "Como o ClickOnce executa atualiza&#231;&#245;es de aplicativos | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
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
  - "implantação ClickOnce, atualizações"
  - "implantando aplicativos [ClickOnce], atualizações do aplicativo"
  - "atualizações, ClickOnce"
ms.assetid: d54313c2-cf0c-420d-b151-99953a95f0bb
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Como o ClickOnce executa atualiza&#231;&#245;es de aplicativos
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

ClickOnce usa as informações de versão do arquivo especificadas no manifesto de implantação do aplicativo para decidir se deseja atualizar os arquivos do aplicativo.  Após o início de uma atualização, o ClickOnce usa uma técnica chamada  *patch de arquivo* para evitar o download redundante de arquivos do aplicativo.  
  
## Patch de arquivo  
 Ao atualizar um aplicativo, ClickOnce não baixar todos os arquivos para a nova versão do aplicativo, a menos que os arquivos foram alterados.  Em vez disso, ele compara as assinaturas de hash dos arquivos especificados no manifesto do aplicativo para o aplicativo atual contra as assinaturas no manifesto para a nova versão.  Se as assinaturas de um arquivo forem diferentes, ClickOnce baixa a nova versão.  Se as assinaturas coincidirem, o arquivo não foi alterado de uma versão para a próxima.  Nesse caso, o ClickOnce copia o arquivo existente e a utiliza a nova versão do aplicativo.  Essa abordagem impede que o ClickOnce precisar baixar todo o aplicativo novamente, mesmo se apenas um ou dois arquivos foram alterados.  
  
 Patch de arquivo também funciona para assemblies que são baixados por demanda usando o <xref:System.Deployment.Application.ApplicationDeployment.DownloadFileGroup%2A> e <xref:System.Deployment.Application.ApplicationDeployment.DownloadFileGroupAsync%2A> métodos.  
  
 Se você usar Visual Studio para compilar o aplicativo, ele irá gerar novas assinaturas de hash para todos os arquivos sempre que você reconstruir o projeto inteiro.  Nesse caso, todos os assemblies serão baixados para o cliente, embora apenas alguns assemblies podem ter sido alteradas.  
  
 Patch de arquivo não funciona para arquivos que são marcados como dados e armazenados no diretório de dados.  Eles são sempre baixados independentemente da assinatura de hash do arquivo.  Para obter mais informações sobre o diretório de dados, consulte [Acessando dados locais e remotos em aplicativos ClickOnce](../deployment/accessing-local-and-remote-data-in-clickonce-applications.md).  
  
## Consulte também  
 [Escolhendo uma estratégia de atualização do ClickOnce](../deployment/choosing-a-clickonce-update-strategy.md)   
 [Escolhendo uma estratégia de implantação do ClickOnce](../deployment/choosing-a-clickonce-deployment-strategy.md)