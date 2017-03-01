---
title: Desativar avisos de compatibilidade para Plug-ins de controle de origem | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- source control plug-ins, turning off compatibility warnings
- compatibility warnings, turning off
ms.assetid: ba318e12-921b-4b7a-a8c2-12c712be1dbf
caps.latest.revision: 21
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
ms.sourcegitcommit: d5bc147592bfc36247c35f23ac2885055d096af3
ms.openlocfilehash: e1dda3bd8c41efcf74a1b27f764fdfbf817f8d63
ms.lasthandoff: 02/22/2017

---
# <a name="how-to-turn-off-compatibility-warnings-for-source-control-plug-ins"></a>Como: desativar avisos de compatibilidade para Plug-ins de controle de origem
Um usuário pode ver vários avisos de compatibilidade durante o emprego de controle de origem no [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Os avisos apresentados dependem dos recursos de plug-in de controle de origem e podem ser desabilitados como detalhada aqui.  
  
### <a name="to-disable-the-warning-to-ensure-optimal-source-control-integration-with-visual-studio"></a>Para desabilitar o aviso: "para garantir a integração de controle do código-fonte ideal com o Visual Studio..."  
  
-   Defina a seguinte entrada do registro (adicionando o valor se necessário):  
  
     HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0\SourceControl\DontDisplayCheckDotNETCompatible = DWORD:&00000;001  
  
     Esse aviso é exibido para todos os não -[!INCLUDE[vsvss](../extensibility/includes/vsvss_md.md)] plug-ins.  
  
### <a name="to-disable-the-warning-the-installed-source-control-provider-does-not-support-all-the-capabilities"></a>Para desabilitar o aviso: "o provedor de controle de origem instalado não oferece suporte a todos os recursos..."  
  
-   Defina os seguintes valores de dois registro (adicionando os valores se necessário):  
  
     HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0\SourceControl\WarnedOldMSSCCIProvider = DWORD:&00000;000  
  
     HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0\SourceControl\UseOldSCC = DWORD:&00000;001  
  
     Esse aviso é exibido se o plug-in de controle de origem não suporte explicitamente reentrância para vários projetos (isto é, se ele pode verificar em apenas um projeto e um arquivo por vez).  
  
     É melhor oferecer suporte a reentrância (`SCC_CAP_REENTRANT` capacidade); então irá remover esse aviso. Entretanto, se esse suporte não for possível, essas entradas do Registro podem ser definidas.  
  
## <a name="see-also"></a>Consulte também  
 [Sinalizadores de recurso](../extensibility/capability-flags.md)
