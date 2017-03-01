---
title: "Detalhes de tempo de execução do controle de origem | Documentos do Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- source control [Visual Studio SDK], runtime details
ms.assetid: 1acd30e0-f98c-4bde-b9cd-4076845887df
caps.latest.revision: 12
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
ms.openlocfilehash: f9e50dfcb43dab80595a9f8f15e7ec4db164e060
ms.lasthandoff: 02/22/2017

---
# <a name="source-control-runtime-details"></a>Detalhes de tempo de execução do controle de origem
Um projeto é adicionado ao controle de origem quando o usuário adiciona um arquivo no projeto ao controle de origem, ou por meio de um controlador de automação, como um assistente. Um projeto não especifica para si mesmo que está sob controle de origem; Ele oferece suporte ao controle de origem, mas deve ser adicionado a ele manualmente.  
  
## <a name="registering-with-a-source-control-package"></a>Registrando um pacote de controle de origem  
 Quando um arquivo no seu projeto é adicionado ao controle de origem, o ambiente chama <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2.SetSccLocation%2A>para fornecer a você quatro cadeias de caracteres opacas que são usadas como cookies pelo sistema de controle de origem.</xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2.SetSccLocation%2A> Armazene cadeias de caracteres no arquivo de projeto. Essas cadeias de caracteres devem ser passadas para o Stub de controle de origem (o componente Visual Studio que gerencia pacotes de controle de origem) na inicialização do tipo de projeto chamando <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2.RegisterSccProject%2A>.</xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2.RegisterSccProject%2A> Isso por sua vez carrega o pacote de controle de origem apropriada e encaminha a chamada para sua implementação de `IVsSccManager2::RegisterSccProject`.  
  
## <a name="see-also"></a>Consulte também  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2.RegisterSccProject%2A></xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2.RegisterSccProject%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2.SetSccLocation%2A></xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2.SetSccLocation%2A>   
 [Suporte a controle de origem](../../extensibility/internals/supporting-source-control.md)
