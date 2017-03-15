---
title: "Como especificar o tempo de execução do .NET Framework | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Profiling Tools, .NET Framework versions
- .NET Framework versions,profililng
ms.assetid: d39f3579-719a-4f47-a97d-5b4232fe4c64
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Human Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 45baa5754e5ffb44edf948dc39fa80d2249e03f1

---
# <a name="how-to-specify-the-net-framework-runtime"></a>Como especificar o tempo de execução do .NET Framework
Com o lançamento do [!INCLUDE[net_v40_long](../code-quality/includes/net_v40_long_md.md)], os aplicativos podem ser compostos de módulos que foram compilados usando versões diferentes do tempo de execução do [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]. Por padrão, as Ferramentas de Criação de Perfil do [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] analisam o primeiro tempo de execução que é carregado pelo aplicativo. Você pode especificar o tempo de execução a ser analisado ao iniciar um aplicativo com o criador de perfil e ao anexar o criador de perfil a um aplicativo que já esteja em execução.  
  
 **Requisitos**  
  
-   [!INCLUDE[vsUltLong](../code-quality/includes/vsultlong_md.md)], [!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)], [!INCLUDE[vsPro](../code-quality/includes/vspro_md.md)]  
  
### <a name="to-specify-the-net-framework-run-time-to-profile-when-starting-an-application-with-the-profiler"></a>Para especificar o tempo de execução do .NET Framework a ser analisado ao iniciar um aplicativo com o criador de perfil  
  
1.  No **Gerenciador de Desempenho**, clique com o botão direito do mouse na sessão de desempenho, clique em **Propriedades** e, em seguida, clique em **Avançado**.  
  
     A caixa de listagem **Versão do CLR de Destino** exibe **Automático** e as versões de tempo de execução do [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] que estão instaladas no computador.  
  
2.  Execute uma das seguintes etapas:  
  
    -   Clique na versão do CLR que você deseja analisar.  
  
    -   Clique em **Automático** para analisar a primeira versão que é carregada pelo aplicativo.  
  
### <a name="to-specify-the-net-framework-run-time-to-profile-when-attaching-the-profiler-to-an-application"></a>Para especificar o tempo de execução do .NET Framework a ser analisado ao anexar o criador de perfil a um aplicativo  
  
1.  No menu Analisar, aponte para Criador de Perfil e, em seguida, clique em Anexar/Desanexar.  
  
2.  Na caixa de diálogo Anexar Criador de Perfil a Processo, clique no processo você deseja analisar.  
  
     A caixa de listagem **Versão do CLR de Destino** exibe **Automático** e as versões de tempo de execução do [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] que estão instaladas no computador.  
  
3.  Execute uma das seguintes etapas:  
  
    -   Clique na versão do CLR que você deseja analisar.  
  
    -   Clique em **Automático** para analisar a versão que é carregada quando o criador de perfil se anexa ao aplicativo.


<!--HONumber=Feb17_HO4-->


