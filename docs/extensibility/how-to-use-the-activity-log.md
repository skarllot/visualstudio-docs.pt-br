---
title: 'Como: usar o Log de atividades | Documentos do Microsoft'
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
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 19ef7828f480efff9d210599d86a723e1f3b209f
ms.lasthandoff: 02/22/2017

---
# <a name="how-to-use-the-activity-log"></a>Como: usar o Log de atividades
Os VSPackages pode gravar mensagens no log de atividade. Esse recurso é especialmente útil para depuração VSPackages em ambientes de varejo.  
  
> [!TIP]
>  O log de atividades é sempre ativado. O Visual Studio mantém um buffer progressivo de entradas de última cem, bem como as entradas de dez primeiros, que tem informações de configuração geral.  
  
### <a name="to-write-an-entry-to-the-activity-log"></a>Para gravar uma entrada no log de atividade  
  
1.  Inserir esse código no <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A>método ou em qualquer outro método, exceto o construtor de VSPackage:</xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A>  
  
    ```c#  
    IVsActivityLog log = GetService(typeof(SVsActivityLog)) as IVsActivityLog;  
    if (log == null) return;  
  
    int hr = log.LogEntry((UInt32)__ACTIVITYLOG_ENTRYTYPE.ALE_INFORMATION,  
        this.ToString(),  
        string.Format(CultureInfo.CurrentCulture,  
        "Called for: {0}", this.ToString()));  
    ```  
  
     Esse código obtém o <xref:Microsoft.VisualStudio.Shell.Interop.SVsActivityLog>de serviço e o converte para um <xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog>interface.</xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog> </xref:Microsoft.VisualStudio.Shell.Interop.SVsActivityLog> <xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog.LogEntry%2A>grava uma entrada informativa no log de atividade usando o contexto cultural atual.</xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog.LogEntry%2A>  
  
2.  Quando o VSPackage é carregado (normalmente, quando um comando é invocado, ou uma janela é aberta), o texto é gravado no log de atividade.  
  
### <a name="to-examine-the-activity-log"></a>Para examinar o log de atividades  
  
1.  Localizar o log de atividades na subpasta para dados do Visual Studio: *% AppData %*\Microsoft\VisualStudio\14.0\ActivityLog.XML...  
  
2.  Abra o log de atividades com qualquer editor de texto. Aqui está uma entrada típica:  
  
    ```  
    Called for: Company.MyApp.MyAppPackage ...  
    ```  
  
## <a name="robust-programming"></a>Programação robusta  
 Como o log de atividades é um serviço, o log de atividade não está disponível no construtor de VSPackage.  
  
 Você deve obter o log de atividades antes de gravar. Não armazenar em cache ou salvar o log de atividades para uso futuro.  
  
## <a name="see-also"></a>Consulte também  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog></xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog>   
 <xref:Microsoft.VisualStudio.Shell.Interop.__ACTIVITYLOG_ENTRYTYPE></xref:Microsoft.VisualStudio.Shell.Interop.__ACTIVITYLOG_ENTRYTYPE>   
 [Os VSPackages de solução de problemas](../extensibility/troubleshooting-vspackages.md)   
 [VSPackages](../extensibility/internals/vspackages.md)
