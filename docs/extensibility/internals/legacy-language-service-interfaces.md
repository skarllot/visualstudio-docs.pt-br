---
title: "Interfaces de serviço de linguagem herdada | Documentos do Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- IVsLanguageInfo interface
- language services, objects
ms.assetid: 03b2d507-f463-417e-bc22-bdac68eeda52
caps.latest.revision: 24
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
ms.openlocfilehash: 5c6cc9b56ca85ae663d5910996f3bb721a18ee35
ms.lasthandoff: 02/22/2017

---
# <a name="legacy-language-service-interfaces"></a>Interfaces de serviço de linguagem herdada
Para qualquer linguagem de programação específica, pode haver apenas uma instância de um serviço de idioma por vez. No entanto, um serviço de idioma único pode servir a mais de um editor.  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]associa um serviço de linguagem qualquer editor específico. Portanto, quando você solicita uma operação de serviço de linguagem, você deve identificar o editor apropriado como um parâmetro.  
  
## <a name="common-interfaces-associated-with-language-services"></a>Interfaces comuns associadas aos serviços de linguagem  
 O editor obtém seu serviço de linguagem chamando <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider.QueryService%2A>sobre o VSPackage apropriado.</xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider.QueryService%2A> O SID (ID) passado na chamada de serviço identifica o serviço de linguagem que está sendo solicitado.  
  
 Você pode implementar as interfaces do serviço de linguagem principal em qualquer número de classes separadas. No entanto, uma abordagem comum é implementar as interfaces a seguir em uma única classe:  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo></xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo>  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems></xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems>  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageDebugInfo></xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageDebugInfo>  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageBlock>(opcional)</xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageBlock>  
  
 O <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo>interface deve ser implementada em todos os serviços de idioma.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> Ele fornece informações sobre seu serviço de linguagem, como o nome localizado da linguagem, as extensões de nome de arquivo associadas com o serviço de linguagem e como recuperar um colorizador.  
  
## <a name="additional-language-service-interfaces"></a>Interfaces de serviço de idioma adicionais  
 Outras interfaces podem ser fornecidos com o serviço de linguagem. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]solicita uma instância separada dessas interfaces para cada instância do buffer de texto. Portanto, você deve implementar cada uma dessas interfaces em seu próprio objeto. A tabela a seguir mostra as interfaces que exigem uma instância por instância de buffer de texto.  
  
|Interface|Descrição|  
|---------------|-----------------|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager></xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager>|Gerencia os adornos da janela de código, como a barra de menu suspenso. Você pode obter essa interface usando o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetCodeWindowManager%2A>método.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetCodeWindowManager%2A> Há um <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager>por janela de código.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager>|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer></xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer>|Colore delimitadores e palavras-chave. Você pode obter essa interface usando o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetColorizer%2A>método.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetColorizer%2A> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer>é chamado em tempo de pintura.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> Evitar o trabalho de computação intensiva dentro de <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer>ou desempenho poderia ser prejudicado.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer>|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData></xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData>|Fornece dicas de ferramenta do IntelliSense parâmetro. Quando o serviço de linguagem reconhece um caractere que indica que os dados método deve ser exibido como um parêntese de abertura, ele chama o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow.SetMethodData%2A>método para notificar o texto de exibição que o serviço de linguagem está pronto para exibir uma dica de ferramenta do parâmetro Info.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow.SetMethodData%2A> A exibição de texto, em seguida, chama de volta para o serviço de linguagem, usando os métodos do <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData>interface para obter as informações necessárias para exibir a dica de ferramenta.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData>|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet></xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet>|Fornece conclusão de instrução do IntelliSense. Quando o serviço de linguagem está pronto para exibir uma lista de conclusão, ele chama o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A>método no modo de texto.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A> A exibição de texto, em seguida, chama de volta para o serviço de linguagem, usando métodos no <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet>objeto.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet>|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter></xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter>|Permite a modificação do modo de exibição de texto usando o manipulador de comandos. A classe na qual você implementar o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter>interface também deve implementar o <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>interface.</xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> </xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter> Recupera a exibição de texto de <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter>objeto consultando o <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>objeto que é passado para o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A>método.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A> </xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> </xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter> Deve haver um <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter>objeto para cada modo de exibição.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter>|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget></xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>|Intercepta comandos que o usuário digita na janela de código. Saída de monitor da sua <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>implementação para fornecer informações de conclusão personalizadas e exibir modificação</xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget><br /><br /> Para passar o <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>objeto para o modo de texto chamada <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A>.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A> </xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>|  
  
## <a name="see-also"></a>Consulte também  
 [Desenvolvendo um serviço de linguagem herdado](../../extensibility/internals/developing-a-legacy-language-service.md)   
 [Lista de verificação: Criar um serviço de linguagem herdado](../../extensibility/internals/checklist-creating-a-legacy-language-service.md)
