---
title: "Caixa de di&#225;logo Configurar Firewall para Depura&#231;&#227;o Remota | Microsoft Docs"
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
  - "vs.debug.firewallconfiguration"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "JScript"
helpviewer_keywords: 
  - "Caixa de diálogo Configurar Firewall para Depuração Remota"
  - "firewalls, configurando para depuração remota"
  - "depuração remota, configurando firewalls"
ms.assetid: 5dff3393-fdeb-4129-a2f6-31f653107a82
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Caixa de di&#225;logo Configurar Firewall para Depura&#231;&#227;o Remota
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Essa caixa de diálogo aparece quando o Firewall do Windows bloqueia o depurador de receber informações pela rede. Para continuar a depuração remota, você deve abrir um buraco no firewall para que o depurador possa receber informações.  
  
> [!CAUTION]
>  Abrir um buraco no Firewall pode expor o computador a ameaças de segurança que o Firewall foi projetado para bloquear. Abrir um buraco para depuração remota desbloqueia as portas 4020 e 4021 no Visual Studio 2015. Em outras versões do Visual Studio, outros números de porta são usados. Para obter mais informações, consulte [Atribuições de porta do depurador remoto](../debugger/remote-debugger-port-assignments.md). Além disso, ele permite que o depurador abra portas adicionais. Para obter mais informações, consulte [Configurar o Firewall do Windows para a depuração remota](../debugger/configure-the-windows-firewall-for-remote-debugging.md).  
  
## Lista UIElement  
 **Cancelar a depuração remota**  
 Cancela a tentativa de depuração remota. Configurações de segurança do seu computador permanecem intactas.  
  
 **Desbloquear a depuração remota de computadores na rede local \(sub\-rede\)**  
 Habilita a depuração remota de computadores na sub\-rede local. Isso pode abrir vulnerabilidades em computadores na sub\-rede local, mas o firewall continua bloqueando informações que vêm de fora da sub\-rede.  
  
 **Desbloquear a depuração remota de qualquer computador**  
 Habilita a depuração remota de computadores em qualquer lugar na rede. Essa configuração é menos segura.  
  
## Consulte também  
 [Segurança do depurador](../debugger/debugger-security.md)   
 [Configurar as Ferramentas Remotas no dispositivo](../Topic/Set%20Up%20the%20Remote%20Tools%20on%20the%20Device.md)   
 [Referência de interface do usuário de depuração](../debugger/debugging-user-interface-reference.md)