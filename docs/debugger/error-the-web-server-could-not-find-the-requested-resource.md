---
title: "Erro: o servidor Web n&#227;o conseguiu localizar o recurso solicitado | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "depurador, erros de aplicativo Web"
ms.assetid: 1ceeaf30-918c-42bb-ace1-96944530fef3
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Erro: o servidor Web n&#227;o conseguiu localizar o recurso solicitado
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Devido aos critérios de segurança, o IIS retornou um erro genérico.  
  
 Uma das possíveis causas é a configuração de segurança do servidor.  O IIS 6.0 e versões anteriores usaram um programa complementar, conhecido como URLScan, para filtrar solicitações suspeitas e malformadas.  O IIS 7.0 tem a Filtragem de Solicitações incorporada pelo mesmo motivo.  Em ambos os casos, a filtragem demasiadamente restritiva pode impedir que o Visual Studio depure o servidor.  
  
 Há várias causas possíveis para esse erro.  Algumas das causas mais comuns incluem um problema com a instalação ou a configuração do IIS, a configuração do site ou permissões no sistema de arquivos.  Você pode tentar acessar o recurso com um navegador.  Dependendo de como o IIS é configurado, você pode ter que usar um navegador local no servidor ou inspecionar o log de erros do IIS para obter uma mensagem de erro detalhada.  
  
 Para obter mais informações sobre como solucionar problemas do IIS, consulte [Gerenciamento e administração do IIS](http://go.microsoft.com/fwlink/?LinkId=255872).  
  
## Consulte também  
 [Ferramenta de segurança UrlScan](http://www.microsoft.com/technet/security/tools/urlscan.mspx)   
 [Erro: o servidor Web foi bloqueado e está bloqueando o verbo DEBUG](../debugger/error-the-web-server-has-been-locked-down-and-is-blocking-the-debug-verb.md)