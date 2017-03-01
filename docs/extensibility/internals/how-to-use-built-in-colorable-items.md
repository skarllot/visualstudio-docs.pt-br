---
title: 'Como: usar itens pode ser coloridos internos | Documentos do Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- colorable items
- language services, built-in colorable items
ms.assetid: 5e5f3436-6bad-4fd2-8823-6a30353ba648
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
ms.openlocfilehash: c06dbad8a633e7b56462d1c870e199b757f23fb5
ms.lasthandoff: 02/22/2017

---
# <a name="how-to-use-built-in-colorable-items"></a>Como: usar itens pode ser coloridos internos
Antes de usar os itens pode ser coloridos internos, você deve primeiro sinalizar para o ambiente de desenvolvimento integrado (IDE) que você não está fornecendo seus próprios itens personalizados pode ser coloridos, que, nesse caso, seria <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems>objetos.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems> Você pode fazer isso definindo uma entrada de registro para o serviço de linguagem.  
  
### <a name="to-use-built-in-colorable-items"></a>Usar itens pode ser coloridos internos  
  
1.  Em HKEY_LOCAL_MACHINE\VisualStudio\\*x. y*\Languages\Language serviços\\*nome do idioma*, onde *x. y* é uma versão do [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] e *nome do idioma* é o nome da sua linguagem, crie um valor de entrada de Registro DWORD chamado `RequestStockColors`.  
  
2.  Definir o `RequestStockColors` o valor de entrada do registro para 1.  
  
     Depois de criar a entrada de registro, o colorizador <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A>método pode usar os membros de <xref:Microsoft.VisualStudio.TextManager.Interop.DEFAULTITEMS>enumeração para preencher a matriz de atributos de cor para uso pelo editor.</xref:Microsoft.VisualStudio.TextManager.Interop.DEFAULTITEMS> </xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A>  
  
    > [!NOTE]
    >  Não defina essa entrada do registro se estiver fornecendo itens pode ser coloridos personalizados. Para obter mais informações, consulte [itens pode ser colorido personalizados](../../extensibility/internals/custom-colorable-items.md).  
  
## <a name="see-also"></a>Consulte também  
 [Cores de sintaxe no editores personalizados](../../extensibility/syntax-coloring-in-custom-editors.md)   
 [Sintaxe de cores em um serviço de linguagem herdado](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)   
 [Implementando a coloração de sintaxe](../../extensibility/internals/implementing-syntax-coloring.md)   
 [Itens pode ser coloridos personalizados](../../extensibility/internals/custom-colorable-items.md)   
 [Registrar um serviço de linguagem herdado](../../extensibility/internals/registering-a-legacy-language-service2.md)
