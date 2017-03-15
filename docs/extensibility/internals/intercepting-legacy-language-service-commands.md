---
title: "Interceptação de comandos de serviço de linguagem herdado | Documentos do Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- commands, intercepting language service
- language services, intercepting commands
ms.assetid: eea69f03-349c-44bb-bd4f-4925c0dc3e55
caps.latest.revision: 13
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
ms.openlocfilehash: f2d663b885b43793f1a660d87fc735ce4549f0c0
ms.lasthandoff: 02/22/2017

---
# <a name="intercepting-legacy-language-service-commands"></a>Interceptação de comandos de serviço de linguagem herdado
Com [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], você pode ter os comandos de interceptação do serviço de linguagem que trataria a exibição de texto. Isso é útil para o comportamento específico do idioma que não gerencia a exibição de texto. Você pode interceptar esses comandos, adicionando um ou mais filtros de comando para a exibição de texto de seu serviço de linguagem.  
  
## <a name="getting-and-routing-the-command"></a>Obtendo e roteamento de comando  
 Um filtro de comando é um <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>objeto monitora certas sequências de caracteres ou chave comandos.</xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> Você pode associar mais de um filtro de comando com uma exibição de texto simples. Cada modo de exibição de texto mantém uma cadeia de comando filtros. Depois de criar um novo filtro de comando, você adicionar o filtro à cadeia para a exibição de texto apropriado.  
  
 Chamar o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A>método o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>para adicionar o filtro de comando para a cadeia.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> </xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A> Quando você chama <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A>, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] retorna outro filtro de comando para o qual você pode passar os comandos que o filtro de comando não processa.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A>  
  
 Você tem as seguintes opções para a manipulação de comando:  
  
-   Lidar com o comando e, em seguida, passar o comando para o próximo filtro de comando na cadeia.  
  
-   Lidar com o comando e não passam o comando para o próximo filtro de comando.  
  
-   Não tratar o comando e passar o comando para o próximo filtro de comando.  
  
-   Ignore o comando. Tratá-los no filtro atual e não o passe para o próximo filtro.  
  
 Para obter informações sobre quais comandos deve lidar com seu serviço de linguagem, consulte [comandos importantes para filtros de serviço de linguagem](../../extensibility/internals/important-commands-for-language-service-filters.md).
