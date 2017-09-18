---
title: "Passo a passo: Acessando o objeto DTE de uma extensão de Editor | Documentos do Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], new - getting the DTE object
ms.assetid: c1f40bab-c6ec-45b0-8333-ea5ceb02a39d
caps.latest.revision: 22
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
ms.openlocfilehash: 6470fb1645c81cbac00fc2b842ab74d88d8d5378
ms.lasthandoff: 02/22/2017

---
# <a name="walkthrough-accessing-the-dte-object-from-an-editor-extension"></a>Passo a passo: Acessando o objeto DTE de uma extensão de Editor
Em VSPackages, você pode obter o objeto DTE chamando o <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A>método com o tipo do objeto DTE.</xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> Extensões do Managed Extensibility Framework (MEF), você pode importar <xref:Microsoft.VisualStudio.Shell.SVsServiceProvider>e, em seguida, chame o <xref:Microsoft.VisualStudio.Shell.ServiceProvider.GetService%2A>método com um tipo de <xref:EnvDTE.DTE>.</xref:EnvDTE.DTE> </xref:Microsoft.VisualStudio.Shell.ServiceProvider.GetService%2A> </xref:Microsoft.VisualStudio.Shell.SVsServiceProvider>  
  
## <a name="prerequisites"></a>Pré-requisitos  
 Para seguir este passo a passo, você deve instalar o SDK do Visual Studio. Para obter mais informações, consulte [Visual Studio SDK](../extensibility/visual-studio-sdk.md).  
  
## <a name="getting-the-dte-object"></a>Obtendo o objeto DTE  
  
#### <a name="to-get-the-dte-object-from-the-serviceprovider"></a>Para obter o objeto DTE do provedor de serviços  
  
1.  Crie um projeto do VSIX c# chamado `DTETest`. Adicionar um modelo de item Editor classificador e nomeie-o `DTETest`. Para obter mais informações, consulte [criando uma extensão com um modelo de Item Editor](../extensibility/creating-an-extension-with-an-editor-item-template.md).  
  
2.  Adicione as seguintes referências de assembly ao projeto:  
  
    -   EnvDTE  
  
    -   EnvDTE80  
  
    -   Microsoft.VisualStudio.Shell.Immutable.10.0  
  
3.  Vá até o arquivo DTETest.cs e adicione o seguinte `using` diretivas:  
  
    ```c#  
    using EnvDTE;  
    using EnvDTE80;  
    using Microsoft.VisualStudio.Shell;  
  
    ```  
  
4.  No `GetDTEProvider` da classe, importar <xref:Microsoft.VisualStudio.Shell.SVsServiceProvider>.</xref:Microsoft.VisualStudio.Shell.SVsServiceProvider>  
  
    ```c#  
    [Import]  
    internal SVsServiceProvider ServiceProvider = null;  
  
    ```  
  
5.  No método `GetClassifier()`, adicione o seguinte código.  
  
    ```c#  
    DTE dte = (DTE)ServiceProvider.GetService(typeof(DTE));  
  
    ```  
  
6.  Se você precisar usar o <xref:EnvDTE80.DTE2>interface, você pode converter o objeto DTE proprietário.</xref:EnvDTE80.DTE2>  
  
## <a name="see-also"></a>Consulte também  
 [Serviço de linguagem e pontos de extensão de Editor](../extensibility/language-service-and-editor-extension-points.md)
