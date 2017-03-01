---
title: "Conclusão de instrução em um serviço de linguagem herdado | Documentos do Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- statement completion
- language services, statement completion
ms.assetid: 617439dc-3f0e-4e5f-b346-3e4e7fcf3c1b
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
ms.openlocfilehash: 89589d3ea16ab4ddbe14e85162d7f46ade9ab2c4
ms.lasthandoff: 02/22/2017

---
# <a name="statement-completion-in-a-legacy-language-service"></a>Conclusão de instrução em um serviço de linguagem herdado
Conclusão de instrução é o processo pelo qual o serviço de linguagem ajuda os usuários a concluir uma palavra-chave language ou elemento que eles tenham sido iniciados digitando no editor de núcleo. Este tópico discute como funciona a conclusão de instrução e como implementá-lo em seu serviço de linguagem.  
  
 Serviços de linguagem herdada são implementados como parte de um VSPackage, mas a maneira mais recente para implementar recursos de serviço de linguagem é usar extensões MEF. Para obter mais informações sobre a nova maneira de implementar a conclusão de instrução, consulte [passo a passo: exibindo a conclusão de instrução](../../extensibility/walkthrough-displaying-statement-completion.md).  
  
> [!NOTE]
>  É recomendável que você comece a usar o novo editor de API assim que possível. Isso irá melhorar o desempenho do seu serviço de linguagem e lhe permitem tirar proveito dos novos recursos do editor.  
  
## <a name="implementing-statement-completion"></a>Implementação de conclusão de instrução  
 No editor de núcleo, a conclusão da instrução ativa uma interface de usuário especial que interativamente torna mais fácil e rapidamente escrever código. Conclusão de instrução ajuda exibindo classes ou objetos pertinentes quando eles forem necessários, que evita precise se lembrar de elementos específicos ou precisar procurá-los em um tópico de referência da Ajuda.  
  
 Para implementar a conclusão de instrução, o idioma deve ter um gatilho de conclusão de instrução, que pode ser analisado. Por exemplo, [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] usa um operador ponto (.), enquanto [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] usa uma seta (operador->). Um serviço de linguagem pode usar mais de um gatilho para iniciar a conclusão de instrução. Os gatilhos são programados no filtro de comando.  
  
## <a name="command-filters-and-triggers"></a>Filtros de comando e gatilhos  
 Filtros de comando interceptam as ocorrências do disparador ou disparadores. Para adicionar o filtro de comando no modo de exibição, implementar o <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>da interface e anexá-lo ao modo de exibição ao chamar o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A>método.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A> </xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> Você pode usar o mesmo filtro de comando (<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>) para todos os aspectos do seu serviço de linguagem, como a conclusão de instrução, marcadores de erro e dicas de método.</xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> Para obter mais informações, consulte [comandos do serviço de linguagem herdado interceptando](../../extensibility/internals/intercepting-legacy-language-service-commands.md).  
  
 Quando o gatilho é inserido no editor — especificamente, o buffer de texto — seu serviço de linguagem, em seguida, chama o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A>método.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A> Isso faz com que o editor abrir a interface do usuário para que o usuário pode escolher entre os candidatos de conclusão de instrução. Esse método exige que você implemente <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet>e o <xref:Microsoft.VisualStudio.TextManager.Interop.UpdateCompletionFlags>sinalizadores como parâmetros.</xref:Microsoft.VisualStudio.TextManager.Interop.UpdateCompletionFlags> </xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet> A lista de itens de conclusão é exibida em uma caixa de lista de rolagem. Como o usuário continua a digitar, a seleção na caixa de listagem é atualizada para refletir que a correspondência mais próxima aos últimos caracteres digitados. O editor de núcleo implementa a interface do usuário para conclusão de instrução, mas o serviço de linguagem deve implementar o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet>interface para definir um conjunto de itens de conclusão de candidato para a instrução.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet>  
  
## <a name="see-also"></a>Consulte também  
 [Interceptação de comandos de serviço de linguagem herdado](../../extensibility/internals/intercepting-legacy-language-service-commands.md)
