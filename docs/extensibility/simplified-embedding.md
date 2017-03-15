---
title: Simplificado inserindo | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], custom - simple view embedding
ms.assetid: f1292478-a57d-48ec-8c9e-88a23f04ffe5
caps.latest.revision: 16
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
ms.openlocfilehash: 318b3753f12458c99a88f367b570708c29095048
ms.lasthandoff: 02/22/2017

---
# <a name="simplified-embedding"></a>Simplificado incorporação
Inserindo simplificada é habilitado em um editor quando seu objeto de exibição de documento é pai (ou seja, feitas filho) [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]e o <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane>interface é implementada para lidar com seus comandos de janela.</xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane> Editores de incorporação simplificados não podem hospedar controles ativos. Os objetos usados para criar um editor com incorporação simplificado são mostrados na ilustração a seguir.  
  
 ![Gráfico do Editor de inserção simplificado](../extensibility/media/vssimplifiedembeddingeditor.gif "vsSimplifiedEmbeddingEditor")  
Editor de inserção simplificada  
  
> [!NOTE]
>  Os objetos nesta ilustração, somente o `CYourEditorFactory` objeto é necessária para criar um editor padrão baseado em arquivo. Se você estiver criando um editor personalizado, você não precisa implementar <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2>, porque seu editor provavelmente terá seu próprio mecanismo de persistência privada.</xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2> Para editores não personalizado, no entanto, você deve fazer isso.  
  
 Contidos em todas as interfaces implementadas para criar um editor com incorporação simplificado a `CYourEditorDocument` objeto. No entanto, para oferecer suporte a vários modos de exibição de dados de documentos, divida as interfaces em objetos separados de dados e exibição conforme indicado na tabela a seguir.  
  
|Interface|Local da interface|Uso|  
|---------------|---------------------------|---------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane></xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane>|Exibir|Fornece a conexão para a janela pai.|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget></xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>|Exibir|Controla os comandos.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser></xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser>|Exibir|Permite atualizações da barra de status.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsToolboxUser></xref:Microsoft.VisualStudio.Shell.Interop.IVsToolboxUser>|Exibir|Permite **Toolbox** itens.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsFileChangeEvents></xref:Microsoft.VisualStudio.Shell.Interop.IVsFileChangeEvents>|Dados|Envia notificações quando o arquivo for alterado.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat></xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat>|Dados|Habilita o recurso Salvar como para um tipo de arquivo.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2></xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2>|Dados|Permite a persistência para o documento.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsDocDataFileChangeControl></xref:Microsoft.VisualStudio.Shell.Interop.IVsDocDataFileChangeControl>|Dados|Permite a supressão de eventos de alteração de arquivo, como recarregar disparo.|
