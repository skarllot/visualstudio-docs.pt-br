---
title: Hospedagem de IntelliSense | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - IntelliSense hosting
ms.assetid: 20c61f8a-d32d-47e2-9c67-bf721e2cbead
caps.latest.revision: 17
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
ms.openlocfilehash: 36533867916bfd88dffa52641e374bd66d9971da
ms.lasthandoff: 02/22/2017

---
# <a name="intellisense-hosting"></a>Hospedagem do IntelliSense
Visual Studio permite a hospedagem de IntelliSense. IntellSense hospedagem permite que você fornece o IntelliSense para código que não é hospedado por um editor de texto do Visual Studio.  
  
## <a name="intellisense-hosting-usage"></a>Uso de hospedagem do IntelliSense  
 No Visual Studio, qualquer código que tenha acesso a um conjunto de conclusão e um buffer de texto pode obter IntelliSense windows de qualquer lugar na interface do usuário (IU). Alguns cenários de exemplo disso são conclusão no **inspeção** janela ou da condição de uma janela de propriedades do ponto de interrupção.  
  
### <a name="implementation-interfaces"></a>Interfaces de implementação  
  
#### <a name="ivsintellisensehost"></a>IVsIntellisenseHost  
 Qualquer componente de interface do usuário que hospeda as janelas pop-up do IntelliSense deve oferecer suporte a <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost>interface.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost> A exibição de texto padrão principal editor inclui um estoque <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost>implementação para manter a funcionalidade IntelliSense atual de interface.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost> Geralmente, os métodos do <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost>da interface que representa um subconjunto do que é implementado no <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>interface.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> </xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost> O subconjunto inclui tratamento de UI IntelliSense, cursor e manipulação de seleção e funcionalidade de substituição de texto simples. Além disso, o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost>interface permite separado IntelliSense "subject" e "contexto" para que o IntelliSense pode ser fornecido para entidades que não existem diretamente no buffer de texto que está sendo usado para contexto.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost>  
  
#### <a name="ivsintellisensehostgethostflags"></a>IVsIntellisenseHost.GetHostFlags  
 Um <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost>interface provedor deve implementar o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.GetHostFlags%2A>método para permitir que um cliente para determinar que tipo de IntelliSense apresenta o host oferece suporte a.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.GetHostFlags%2A> </xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost>  
  
 Os sinalizadores de host, definidos em [IntelliSenseHostFlags](../extensibility/intellisensehostflags.md), estão resumidos abaixo.  
  
|Sinalizador de Host do IntelliSense|Descrição|  
|----------------------------|-----------------|  
|IHF_READONLYCONTEXT|A configuração desta sinalizador significa que o buffer de contexto é somente leitura e edição ocorrem somente dentro do texto de assunto.|  
|IHF_NOSEPERATESUBJECT|Definir esse sinalizador significa que existe não é nenhum assunto IntelliSense separado. A entidade existe no buffer de contexto, como no tradicionais <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>sistema IntelliSense.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>|  
|IHF_SINGLELINESUBJECT|A configuração desta sinalizador significa que a entidade não é multilinhas capaz, como em uma única linha Editar no **inspeção** janela.|  
|IHF_FORCECOMMITTOCONTEXT|Se esse sinalizador estiver definido e o buffer de contexto deve ser atualizado, o host permite que o sinalizador somente leitura no buffer de contexto a serem ignorados e edições para continuar.|  
|IHF_OVERTYPE|Edição (no assunto ou contexto) deve ser feito no modo sobrescrever.|  
  
#### <a name="ivsintellisensehostbeforecompletorcommit-and-ivsintellisensehostaftercompletorcommit"></a>IVsIntellisenseHost.BeforeCompletorCommit e IVsIntellisenseHost.AfterCompletorCommit  
 Esses métodos de retorno de chamada são chamados pela janela de conclusão antes e depois que o texto é confirmado, para habilitar o processamento pré e pós-processamento.  
  
#### <a name="ivsintellisensecompletor"></a>IVsIntellisenseCompletor  
 O <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseCompletor>interface é uma versão criáveis conjunta da janela de conclusão padrão que é usada pelo ambiente de desenvolvimento integrado (IDE).</xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseCompletor> Qualquer <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost>interface pode implementar rapidamente IntelliSense usando esta interface completor.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost>  
  
## <a name="see-also"></a>Consulte também  
 <xref:Microsoft.VisualStudio.TextManager.Interop></xref:Microsoft.VisualStudio.TextManager.Interop>
