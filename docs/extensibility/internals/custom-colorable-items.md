---
title: Itens pode ser coloridos personalizados | Documentos do Microsoft
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
- language services, custom colorable items
ms.assetid: b4d0ddee-c04b-48dc-ba82-f6068570cef0
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
ms.openlocfilehash: 4bb762e96186c7c87fb1180383b98fac9179709d
ms.lasthandoff: 02/22/2017

---
# <a name="custom-colorable-items"></a>Itens pode ser coloridos personalizados
Você pode substituir a lista de tipos para colorir, como palavras-chave e comentários, Implementando itens pode ser coloridos personalizados como parte de seu serviço de linguagem.  
  
## <a name="user-settings-of-colorable-items"></a>Configurações do usuário de itens pode ser coloridos  
 Você pode exibir o **fontes e cores** caixa de diálogo selecionando **opções** no **ferramentas** menu e, em seguida, selecionando **fontes e cores** em **ambiente**. Quando você seleciona uma exibição, como **Editor de texto** ou **janela comando**, o **exibir itens** caixa de listagem exibe todos os itens pode ser coloridos para essa exibição. Você pode exibir e alterar a fonte, tamanho, cor de primeiro plano e cor de plano de fundo para cada item pode ser colorido. As opções são armazenadas em cache no registro e acessadas pelo nome do item pode ser colorido.  
  
## <a name="presentation-of-colorable-items"></a>Apresentação dos itens pode ser coloridos  
 Como o IDE manipula substituições do usuário de itens pode ser coloridos no **fontes e cores** caixa de diálogo, você precisa apenas fornecer cada item personalizado pode ser colorido com um nome. Esse nome é o que aparece no **exibir itens** lista. Os itens pode ser coloridos aparecem em ordem alfabética. Para agrupar itens de pode ser colorido personalizados do seu serviço de linguagem, você pode começar cada nome com seu nome de idioma, por exemplo **NewLanguage - comentário** e **NewLanguage - palavra-chave**.  
  
> [!CAUTION]
>  Você deve incluir o nome do idioma no nome do item pode ser colorido para evitar colisões com nomes de item pode ser colorido existentes. Se você alterar o nome de um dos itens pode ser coloridos durante o desenvolvimento, você deve redefinir o cache foi criado na primeira vez em que os itens pode ser coloridos foram acessados. Você pode redefinir o cache experimental com a ferramenta CreateExpInstance, que é instalado com o SDK do Visual Studio, normalmente no diretório  
>   
>  **C:\Program arquivos (x86) \Microsoft Visual Studio 14.0\VSSDK\VisualStudioIntegration\Tools\Bin**  
>   
>  Para redefinir o cache, chame `CreateExpInstance /Reset`. Para obter mais informações sobre CreateExpInstance, consulte [CreateExpInstance utilitário](../../extensibility/internals/createexpinstance-utility.md).  
  
 O primeiro item na lista de itens pode ser coloridos nunca é referenciado. O primeiro item corresponde a um item pode ser colorido índice de 0, e [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] sempre fornece as cores padrão de texto e atributos para aquele item. A maneira mais fácil de lidar com esse item não referenciado é fornecer um item pode ser colorido de espaço reservado em sua lista como o primeiro item.  
  
## <a name="implementing-custom-colorable-items"></a>Implementação de itens pode ser coloridos personalizados  
  
1.  Defina o que deve ser colorido no seu idioma, por exemplo, palavra-chave, operadores e identificador.  
  
2.  Crie uma enumeração desses itens pode ser colorido.  
  
3.  Associe os tipos de token retornados de um analisador ou scanner com os valores enumerados.  
  
     Por exemplo, os valores que representam os tipos de token pode ser os mesmos valores na enumeração de itens pode ser colorido personalizados.  
  
4.  Na implementação do <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A>método no seu <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer>de objeto, preencher a lista de atributos com os valores de enumeração pode ser colorido de itens personalizados correspondentes aos tipos de token retornados do analisador ou scanner.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> </xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A>  
  
5.  Na mesma classe que implementa a <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo>interface, implemente a <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems>interface e seus dois métodos <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetItemCount%2A>e <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetColorableItem%2A>.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetColorableItem%2A> </xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetItemCount%2A> </xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems> </xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo>  
  
6.  Implementar o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem>interface.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem>  
  
7.  Se você deseja oferecer suporte a valores de cor de 24 bits ou alto, também implemente o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem>interface.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem>  
  
8.  No seu objeto de serviço de linguagem, crie uma lista que contém seu <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem>objetos, um para cada item pode ser colorido pode identificar o analisador ou scanner.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem>  
  
     Você pode acessar cada item na lista usando o valor da enumeração de itens pode ser colorido personalizados. Use os valores de enumeração como um índice na lista. O primeiro item na lista nunca será acessado, pois ele corresponde ao texto padrão de estilo que [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] sempre lida com propriamente dito. Você pode compensar isso inserindo um item pode ser colorido de espaço reservado no início da lista.  
  
9. Na implementação do <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetItemCount%2A>método, retornar o número de itens em sua lista de itens pode ser colorido personalizados.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetItemCount%2A>  
  
10. Na implementação do <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetColorableItem%2A>método, retornar o item pode ser colorido solicitado da sua lista.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetColorableItem%2A>  
  
 Para obter um exemplo de como implementar o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem>e <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem>interfaces, consulte <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem>.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem> </xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem> </xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem>  
  
## <a name="see-also"></a>Consulte também  
 [Modelo de um serviço de linguagem herdado](../../extensibility/internals/model-of-a-legacy-language-service.md)   
 [Cores de sintaxe no editores personalizados](../../extensibility/syntax-coloring-in-custom-editors.md)   
 [Sintaxe de cores em um serviço de linguagem herdado](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)   
 [Implementando a coloração de sintaxe](../../extensibility/internals/implementing-syntax-coloring.md)   
 [Como: usar itens pode ser coloridos internos](../../extensibility/internals/how-to-use-built-in-colorable-items.md)
