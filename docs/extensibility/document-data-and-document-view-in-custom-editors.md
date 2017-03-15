---
title: Exibir dados de documentos e documentos em editores personalizados | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], custom - document data and document view
ms.assetid: 71eea623-f566-4feb-84cd-ca1ba71bc493
caps.latest.revision: 23
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
ms.openlocfilehash: d44bc84fd286ef058caa0e13b6d782a4d04caa80
ms.lasthandoff: 02/22/2017

---
# <a name="document-data-and-document-view-in-custom-editors"></a>Dados de documentos e visualização de documentos em editores personalizados
Um editor personalizado consiste em duas partes: um objeto de dados de documentos e um objeto de exibição de documento. Como os nomes sugerem, o objeto de dados de documento representa os dados de texto a ser exibido e o objeto de exibição de documento (ou "view") representa uma ou mais janelas para exibir o objeto de dados do documento.  
  
## <a name="document-data-object"></a>Objeto de dados de documento  
 Um objeto de dados de documentos é uma representação de dados de texto no buffer de texto. É um objeto COM que armazena o texto do documento e outras informações, lida com persistência de documento e permite que vários modos de exibição de seus dados. Para saber mais, veja  
  
 <xref:EnvDTE80.Window2.DocumentData%2A>e [janelas de documento](../extensibility/internals/document-windows.md).</xref:EnvDTE80.Window2.DocumentData%2A>  
  
 Designers e editores personalizados podem optar por usar o <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>seu próprios buffer personalizado ou objeto.</xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>segue o modelo de incorporação simplificado para um editor padrão, oferece suporte a vários modos de exibição e fornece interfaces de evento que são usados para gerenciar vários modos de exibição.</xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>  
  
## <a name="document-view-object"></a>Objeto de exibição de documento  
 Uma janela que exibe o código e outros textos é conhecida como um documento do modo de exibição ou. Quando você cria um editor, você pode escolher um modo de exibição único, no qual o texto é exibido em uma única janela, ou uma exibição vários, no qual o texto é exibido em mais de uma janela. Sua escolha depende de seu aplicativo. Por exemplo, se você precisar de uma edição lado a lado, escolha exibir vários. Cada exibição é associada uma entrada no ambiente de desenvolvimento integrado do (IDE) a tabela de documento (RDT) em execução. Modo windows pertencem a um projeto ou uma <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>objeto.</xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>  
  
 Se o editor dá suporte a vários modos de exibição de um objeto de dados de documento, em seguida, seus dados de documentos e objetos de exibição de documento devem ser separados. Caso contrário, eles podem ser agrupados. Para obter mais informações, consulte [suporte a várias exibições de documento](../extensibility/supporting-multiple-document-views.md).  
  
 O IDE notifica exibições sobre eventos (por exemplo, quando uma solução que contém um documento é fechada), correspondendo a um identificador de item (ItemID) para cada entrada na tabela de documento em execução. Para obter mais informações sobre isso, consulte [executando tabela Document](../extensibility/internals/running-document-table.md).  
  
 Há duas opções para criar um modo de exibição para um editor personalizado. Um é o modelo de ativação no local, em que a exibição é hospedada em uma janela usando um controle ActiveX ou um objeto de dados do documento. O segundo é o modelo de incorporação simplificado, onde o modo de exibição é hospedado por [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] e <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane>é implementado para lidar com comandos janela.</xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane> Para obter informações sobre o modelo de ativação no local, consulte [da ativação In loco](../misc/in-place-activation.md). Para obter informações sobre o modelo de incorporação simplificada, consulte [inserindo simplificado](../extensibility/simplified-embedding.md).  
  
## <a name="see-also"></a>Consulte também  
 [Suporte a vários modos de exibição de documento](../extensibility/supporting-multiple-document-views.md)   
 [Simplificado incorporação](../extensibility/simplified-embedding.md)   
 [Como: anexar modos de exibição para dados de documentos](../extensibility/how-to-attach-views-to-document-data.md)   
 [Gerenciamento de proprietário de bloqueio de documento](../extensibility/document-lock-holder-management.md)   
 [Modos de exibição únicos e multi-guia](../extensibility/single-and-multi-tab-views.md)   
 [Salvar um documento padrão](../extensibility/internals/saving-a-standard-document.md)   
 [A tabela de documento em execução e persistência](../extensibility/internals/persistence-and-the-running-document-table.md)   
 [Determinando qual Editor abre um arquivo em um projeto](../extensibility/internals/determining-which-editor-opens-a-file-in-a-project.md)   
 [Fábricas de editor](../extensibility/editor-factories.md)
