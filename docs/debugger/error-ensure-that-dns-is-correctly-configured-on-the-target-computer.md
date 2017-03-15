---
title: "Erro: verifique se o DNS est&#225; configurado corretamente no computador de destino | Microsoft Docs"
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
  - "vs.debug.error.callback_dns_failed"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
ms.assetid: 2d364caf-73af-4186-bf9b-af186331cbe8
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Erro: verifique se o DNS est&#225; configurado corretamente no computador de destino
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Ao tentar fazer a depuração remota, você pode receber a seguinte mensagem de erro:  
  
```  
Error: The Visual Studio Remote Debugger on the target computer cannot connect back to this computer. Ensure that DNS is correctly configured on the target computer.  
```  
  
 Esse erro ocorre quando o computador de destino não pode resolver o nome do computador host do depurador do Visual Studio.  Verifique as configurações DNS no computador de destino.  
  
-   Para obter informações sobre como exibir a configuração de DNS no Windows 8.1, Vista, Windows 7, Windows Server 2012, Windows Server 2008 ou Windows Server 2008 R2, fazer isso: no **Iniciar** menu, escolha **Ajuda e suporte**, e procure por configurações TCP\/IP de alteração.  
  
-   Para obter mais informações, vá para [site do Microsoft Windows](http://go.microsoft.com/fwlink/?LinkId=252720) e procure por configurações TCP\/IP de alteração.  
  
 Se você não conseguir resolver o problema de DNS, tente executar o Depurador Remoto em uma conta diferente.  Esse erro ocorre somente quando você está executando o Depurador Remoto sob a conta Serviço de Rede ou Sistema Local.  Se você executar o Depurador Remoto em outra conta, ele poderá usar a autenticação NTLM, que não exige DNS.  .  Para o procedimento, consulte [Erro: o serviço Depurador Remoto do Visual Studio no computador de destino não pode se reconectar a este computador](../debugger/error-the-visual-studio-remote-debugger-service-on-the-target-computer-cannot-connect-back-to-this-computer.md).