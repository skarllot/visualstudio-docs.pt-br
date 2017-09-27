---
title: 'Como: usar o Log de atividades | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- VSPackages, debugging
- VSPackages, troubleshooting
ms.assetid: bb3d3322-0e5e-4dd5-b93a-24d5fbcd2ffd
caps.latest.revision: 29
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: MT
ms.sourcegitcommit: 4a36302d80f4bc397128e3838c9abf858a0b5fe8
ms.openlocfilehash: a1ddf51d02d9e20f6806f8bc202f8a08166876d6
ms.contentlocale: pt-br
ms.lasthandoff: 09/26/2017

---
# <a name="how-to-use-the-activity-log"></a>Como: usar o Log de atividades
VSPackages pode gravar mensagens no log de atividade. Esse recurso é especialmente útil para depuração VSPackages em ambientes de varejo.  
  
> [!TIP]
>  O log de atividades é sempre ativado. O Visual Studio manterá um buffer sem interrupção de entradas de última cem, bem como as entradas de dez primeiros, que tem informações de configuração geral.  
  
### <a name="to-write-an-entry-to-the-activity-log"></a>Para gravar uma entrada para o log de atividades  
  
1.  Inserir este código no <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> método ou em qualquer outro método, exceto o VSPackage construtor:  
  
    ```csharp  
    IVsActivityLog log = GetService(typeof(SVsActivityLog)) as IVsActivityLog;  
    if (log == null) return;  
  
    int hr = log.LogEntry((UInt32)__ACTIVITYLOG_ENTRYTYPE.ALE_INFORMATION,  
        this.ToString(),  
        string.Format(CultureInfo.CurrentCulture,  
        "Called for: {0}", this.ToString()));  
    ```  
  
     Esse código obtém a <xref:Microsoft.VisualStudio.Shell.Interop.SVsActivityLog> de serviço e converte-o para um <xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog> interface. <xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog.LogEntry%2A>grava uma entrada informativa no log de atividade usando o contexto cultural atual.  
  
2.  Quando o VSPackage é carregado (normalmente, quando um comando é invocado, ou uma janela é aberta), o texto é escrito para o log de atividades.  
  
### <a name="to-examine-the-activity-log"></a>Para examinar o log de atividades  
  
1.  Localizar o log de atividades na subpasta para dados do Visual Studio: *% AppData %*\Microsoft\VisualStudio\15.0\ActivityLog.XML...  
  
2.  Abra o log de atividades com qualquer editor de texto. Aqui está uma entrada típica:  
  
    ```  
    Called for: Company.MyApp.MyAppPackage ...  
    ```  
  
## <a name="robust-programming"></a>Programação robusta  
 Como o log de atividades é um serviço, o log de atividades não está disponível no construtor VSPackage.  
  
 Você deve obter o log de atividades antes de gravar. Não armazenar em cache ou salvar o log de atividades para uso futuro.  
  
## <a name="see-also"></a>Consulte também  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog>   
 <xref:Microsoft.VisualStudio.Shell.Interop.__ACTIVITYLOG_ENTRYTYPE>   
 [Solucionando problemas de VSPackages](../extensibility/troubleshooting-vspackages.md)   
 [VSPackages](../extensibility/internals/vspackages.md)

