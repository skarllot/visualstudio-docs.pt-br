---
title: "Aviso: depura&#231;&#227;o de script desabilitada | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.scriptdisabled"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
ms.assetid: 323d2b1d-52a4-42f7-b4ad-96b4b0c23b8d
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Aviso: depura&#231;&#227;o de script desabilitada
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

A depuração de scripts está atualmente desabilitada no Internet Explorer  
  
 Esse aviso ocorre quando você tenta depurar o script sem habilitar a depuração de scripts no Internet Explorer.  Por razões de segurança, o Internet Explorer desabilita a depuração de scripts por padrão.  
  
### Para habilitar a depuração de scripts no Internet Explorer  
  
1.  No menu do Internet Explorer **Ferramentas**, escolha **Opções da Internet**.  
  
2.  Na caixa de diálogo **Opções da Internet**, clique na guia **Avançado**.  
  
3.  Na guia **Avançado**, examine a caixa **Configurações**, categoria **Navegação**.  
  
4.  Limpe **Desabilitar depuração de scripts \(Internet Explorer\)**.  
  
5.  Clique em **OK**.  
  
6.  Encerre e reinicie o Internet Explorer.  
  
     As novas configurações serão aplicadas.  
  
## Consulte também  
 [Como anexar ao script](../debugger/how-to-attach-to-script.md)