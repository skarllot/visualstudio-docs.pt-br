---
title: "Serviços de linguagem e o Editor de núcleo | Documentos do Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - language services
ms.assetid: e03199a6-ad5f-4075-bfba-8d36865112b7
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
ms.openlocfilehash: c78c3c5e450ffe348a8af2687e2b9b30b1128e8e
ms.lasthandoff: 02/22/2017

---
# <a name="language-services-and-the-core-editor"></a>Serviços de linguagem e o Editor de núcleo
Editores do Visual Studio são frequentemente associadas um serviço de linguagem. Entre outras coisas, um serviço de linguagem fornece coloração de sintaxe, conclusão de instrução, IntelliSense e formatação de texto.  
  
## <a name="core-editors-and-document-data-objects"></a>Editores de núcleo e objetos de dados de documento  
 Quando você acessar o editor de núcleo, você não criar dados de documentos e objetos de exibição de documento. O IDE cria e controla esses dois objetos, e obter identificadores para eles, fazendo as chamadas apropriadas em seu editor de implementação de fábrica.  
  
 Para obter mais informações, consulte [determinar qual Editor abre um arquivo em um projeto](../extensibility/internals/determining-which-editor-opens-a-file-in-a-project.md).  
  
## <a name="language-services-and-the-core-editor"></a>Serviços de linguagem e o Editor de núcleo  
 Implementando um serviço de linguagem, você pode controlar como os dados são exibidos no modo de exibição de documento. Um serviço de linguagem fornece informações e o comportamento é específico para um determinado idioma, como o Visual C++. Quando você cria um buffer de texto e determinar a extensão de nome de arquivo para o documento que está sendo aberto, o buffer de texto determina o serviço de idioma associado a essa extensão de nome de arquivo de uma chave do registro, HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Editors\\\Extensions {YourLanguageService GUID}. O VSPackage padrão Carregando procedimento, em seguida, carrega o VSPackage e é criada uma instância do seu serviço de linguagem.  
  
 Um serviço de linguagem básica é mostrado na ilustração a seguir.  
  
 ![Gráfico de modelo de serviço de linguagem](~/extensibility/media/vslanguageservicemodel.gif "vsLanguageServiceModel")  
Objetos de serviço de editor e o idioma principal  
  
 O objeto de dados de documento para o editor de núcleo é chamado de um buffer de texto e é representado pelo <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>objeto.</xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> O objeto de exibição de documento é chamado uma exibição de texto e é representado pelo <xref:Microsoft.VisualStudio.TextManager.Interop.VsCodeWindow>objeto.</xref:Microsoft.VisualStudio.TextManager.Interop.VsCodeWindow> Esses dois objetos interagem por meio do serviço de linguagem para fornecer uma visão unificada do editor principal. Informações do buffer de texto e exibir o texto é exibido em uma janela de documento chamado uma janela de código. O documento da janela de código é gerenciado por um Gerenciador de janela de código.  
  
## <a name="see-also"></a>Consulte também  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo></xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer></xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView></xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager></xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.VsCodeWindow></xref:Microsoft.VisualStudio.TextManager.Interop.VsCodeWindow>   
 [Fornecer um contexto de serviço de idioma usando a API herdada](../extensibility/providing-a-language-service-context-by-using-the-legacy-api.md)   
 [Hospedagem do IntelliSense](../extensibility/intellisense-hosting.md)   
 [Idiomas independentes](../extensibility/contained-languages.md)   
 [Desenvolvendo um serviço de linguagem herdado](../extensibility/internals/developing-a-legacy-language-service.md)
