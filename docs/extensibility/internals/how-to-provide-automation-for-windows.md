---
title: "Como: fornecer automação do Windows | Documentos do Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- automation [Visual Studio SDK], tool windows
- tool windows, automation
ms.assetid: 512ab2a4-7987-4912-8f40-8804bf66f829
caps.latest.revision: 10
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
ms.openlocfilehash: 5efb7a435e9c5eb6d2af7eaf22d198261e486873
ms.lasthandoff: 02/22/2017

---
# <a name="how-to-provide-automation-for-windows"></a>Como: fornecer automação para Windows
Você pode fornecer automação para janelas de documento e ferramenta. Oferecendo automação é aconselhável sempre que você deseja disponibilizar os objetos de automação em uma janela, e o ambiente ainda não fornece um objeto de automação prontas, como ocorre com uma lista de tarefas.  
  
## <a name="automation-for-tool-windows"></a>Automação para janelas de ferramenta  
 O ambiente oferece automação em uma janela de ferramenta retornando um padrão <xref:EnvDTE.Window>objeto conforme explicado no procedimento a seguir:</xref:EnvDTE.Window>  
  
#### <a name="to-provide-automation-for-tool-windows"></a>Fornecem automação para janelas de ferramenta  
  
1.  Chamar o <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A>método por meio do ambiente com <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>como `VSFPROPID` para obter o `Window` objeto.</xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID> </xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A>  
  
2.  Quando um chamador solicita um objeto de automação de VSPackage específico para a janela da ferramenta por meio de <xref:EnvDTE.Window.Object%2A>, as chamadas de ambiente `QueryInterface` para `IExtensibleObject`, <xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibleObject>, ou o `IDispatch` interfaces.</xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibleObject> </xref:EnvDTE.Window.Object%2A> Ambos `IExtensibleObject` e `IVsExtensibleObject` fornecem um <xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibleObject.GetAutomationObject%2A>método.</xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibleObject.GetAutomationObject%2A>  
  
3.  Quando o ambiente, em seguida, chama o `GetAutomationObject` método passando `NULL`, responder, passando de volta o objeto VSPackage específico.  
  
4.  Se chamar `QueryInterface` para `IExtensibleObject` e `IVsExtensibleObject` falhar, em seguida, chama o ambiente `QueryInterface` para `IDispatch`.  
  
## <a name="automation-for-document-windows"></a>Automação para janelas de documento  
 Um padrão <xref:EnvDTE.Document>objeto também está disponível no ambiente, embora um editor pode ter sua própria implementação do `T:EnvDTE.Document` objeto implementando `IExtensibleObject` interface e respondendo a `GetAutomationObject`.</xref:EnvDTE.Document>  
  
 Além disso, um editor pode fornecer um objeto de automação específico VSPackage, recuperado por meio de <xref:EnvDTE.Document.Object%2A>método, Implementando a `IVsExtensibleObject` ou `IExtensibleObject` interfaces.</xref:EnvDTE.Document.Object%2A> O [VSSDK exemplos](../../misc/vssdk-samples.md) contribui com um objeto de automação específico do documento RTF.  
  
## <a name="see-also"></a>Consulte também  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibleObject></xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibleObject>
