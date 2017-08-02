---
title: "Suporte a ferramentas de navegação de símbolo | Documentos do Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- symbols, symbol-browsing tools
- browsers, symbol browsers
- symbol-browsing tools
- libraries
- IVsLibrary2 interface, symbol-browsing tools
- IVsSimpleLibrary2 interface, symbol-browsing tools
- symbol-browsing tools, library manager
- symbols
- libraries, symbol-browsing tools
ms.assetid: 70d8c9e5-4b0b-4a69-b3b3-90f36debe880
caps.latest.revision: 26
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
ms.openlocfilehash: 5db94cadcdc545196cb716803711e2895fcaae3c
ms.lasthandoff: 02/22/2017

---
# <a name="supporting-symbol-browsing-tools"></a>Suporte a ferramentas de navegação de símbolo
**Pesquisador de objetos**, **Class View**, **Pesquisador de chamadas** e **Find Symbol Results** ferramentas fornecem símbolo procurando recursos no Visual Studio. Essas ferramentas exibem modos de exibição de árvore hierárquica de símbolos e mostram as relações entre os símbolos na árvore. Os símbolos podem representar objetos, namespaces, classes, membros de classe e outros elementos de linguagem contidos em vários componentes. Os componentes incluem projetos do Visual Studio, externos [!INCLUDE[dnprdnshort](../../code-quality/includes/dnprdnshort_md.md)] componentes e bibliotecas de tipos (. tlb). Para obter mais informações, consulte [Exibindo a estrutura do código](../../ide/viewing-the-structure-of-code.md).  
  
## <a name="symbol-browsing-libraries"></a>Bibliotecas de navegação de símbolo  
 Como um implementador de linguagem, você pode estender os recursos de navegação de símbolo do Visual Studio criando bibliotecas que controlar os símbolos em seus componentes e fornecem a lista de símbolos para o Gerenciador de objetos do Visual Studio por meio de um conjunto de interfaces. Uma biblioteca é descrita pelo <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleLibrary2>interface.</xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleLibrary2> O Gerenciador de objetos do Visual Studio responde às solicitações para novos dados a partir das ferramentas de navegação de símbolo obtendo os dados de bibliotecas e organizá-las. Posteriormente, ele preenche ou atualiza as ferramentas com os dados solicitados. Para obter uma referência para o Gerenciador de objetos do Visual Studio, <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2>, passar o <xref:Microsoft.VisualStudio.Shell.Interop.SVsObjectManager>serviço ID para o `GetService` método.</xref:Microsoft.VisualStudio.Shell.Interop.SVsObjectManager> </xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2>  
  
 Cada biblioteca deve registrar com o Gerenciador de objetos do Visual Studio, que coleta as informações sobre todas as bibliotecas. Para registrar uma biblioteca, chamar o <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2.RegisterSimpleLibrary%2A>método.</xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2.RegisterSimpleLibrary%2A> Dependendo de qual ferramenta inicia a solicitação, o Gerenciador de objetos do Visual Studio encontra a biblioteca apropriada e solicita os dados. Os dados são transferidos entre as bibliotecas e o [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Gerenciador de objetos em listas de símbolos descritos pelo <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2>interface.</xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2>  
  
 O [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Gerenciador de objeto é responsável pela atualização periódica de ferramentas de navegação de símbolo para refletir os dados mais atuais contidos nas bibliotecas.  
  
 O diagrama a seguir contém um exemplo dos principais elementos do processo do exchange de solicitações/dados entre uma biblioteca e o Gerenciador de objetos do Visual Studio. As interfaces no diagrama são parte de um aplicativo de código gerenciado.  
  
 ![Fluxo de dados entre uma biblioteca e o Gerenciador de objetos](~/docs/extensibility/internals/media/callbrowserdiagram.gif "CallBrowserDiagram")  
  
 Para fornecer a lista de símbolos para o Gerenciador de objetos do Visual Studio, você deve primeiro registrar a biblioteca com o Gerenciador de objetos do Visual Studio ao chamar o <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2.RegisterSimpleLibrary%2A>método.</xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2.RegisterSimpleLibrary%2A> Depois que a biblioteca é registrada, o Gerenciador de objetos do Visual Studio solicita certas informações sobre os recursos da biblioteca. Por exemplo, ele solicita os sinalizadores de biblioteca e suporte categorias chamando o <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleLibrary2.GetLibFlags2%2A>e <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleLibrary2.GetSupportedCategoryFields2%2A>métodos.</xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleLibrary2.GetSupportedCategoryFields2%2A> </xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleLibrary2.GetLibFlags2%2A> Em algum momento, quando uma das ferramentas solicita dados desta biblioteca, o Gerenciador de objeto solicita o nível superior da lista de símbolos chamando o <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleLibrary2.GetList2%2A>método.</xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleLibrary2.GetList2%2A> Em resposta, a biblioteca fabrica uma lista de símbolos e o expõe para o Gerenciador de objetos do Visual Studio por meio de <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2>interface.</xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2> O [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Gerenciador de objetos determina quantos itens estão na lista chamando o <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetItemCount%2A>método.</xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetItemCount%2A> Todas as solicitações seguintes relacionam a um determinado item na lista e fornecem o número de índice do item em cada solicitação. O Gerenciador de objetos do Visual Studio continua para coletar as informações sobre o tipo, a acessibilidade e outras propriedades do item ao chamar o <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetCategoryField2%2A>método.</xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetCategoryField2%2A>  
  
 Determina o nome do item ao chamar o <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetTextWithOwnership%2A>método e solicita as informações de ícone chamando o <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetDisplayData%2A>método.</xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetDisplayData%2A> </xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetTextWithOwnership%2A> O ícone é exibido à esquerda do nome do item e descreve o tipo de item, a acessibilidade e outras propriedades.  
  
 O [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] objeto Gerenciador de chamadas de <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetExpandable3%2A>método para determinar se um determinado item de lista expansível e possui itens filhos.</xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetExpandable3%2A> Se a interface do usuário envia uma solicitação para expandir um elemento, o Gerenciador de objetos solicita a lista de filhos de símbolos chamando o <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetList2%2A>método.</xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetList2%2A> O processo continua com diferentes partes da árvore que está sendo criado sob demanda.  
  
> [!NOTE]
>  Para implementar um provedor de símbolo de código nativo, use o <xref:Microsoft.VisualStudio.Shell.Interop.IVsLibrary2>e <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectList2>interfaces.</xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectList2> </xref:Microsoft.VisualStudio.Shell.Interop.IVsLibrary2>  
  
## <a name="see-also"></a>Consulte também  
 [Como: registrar uma biblioteca com o Gerenciador de objeto](../../extensibility/internals/how-to-register-a-library-with-the-object-manager.md)   
 [Como: expor listas de símbolos fornecidos pela biblioteca para o Gerenciador de objetos](../../extensibility/internals/how-to-expose-lists-of-symbols-provided-by-the-library-to-the-object-manager.md)   
 [Como: identificar símbolos em uma biblioteca](../../extensibility/internals/how-to-identify-symbols-in-a-library.md)
