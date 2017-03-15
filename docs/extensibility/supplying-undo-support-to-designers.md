---
title: Fornecendo suporte aos Designers de desfazer | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- designers [Visual Studio SDK], undo support
ms.assetid: 43eb1f14-b129-404a-8806-5bf9b099b67b
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
ms.sourcegitcommit: 5658ecf52637a38bc3c2a5ad9e85b2edebf7d445
ms.openlocfilehash: 95e6873d0a3b254fa8f34144253a44c0a8cab60d
ms.lasthandoff: 02/22/2017

---
# <a name="supplying-undo-support-to-designers"></a>Fornecendo suporte à função desfazer para Designers
Designers, como editores, geralmente precisam oferecer suporte a operações de desfazer para que os usuários podem reverter as alterações recentes ao modificar um elemento de código.  
  
 A maioria dos designers implementados no Visual Studio tem suporte à função desfazer automaticamente fornecido pelo ambiente de.  
  
 Implementações de designer que precisam fornecer suporte para o recurso de desfazer:  
  
-   Fornecer gerenciamento desfazer Implementando a classe base abstrata<xref:System.ComponentModel.Design.UndoEngine></xref:System.ComponentModel.Design.UndoEngine>  
  
-   Suportam de CodeDOM e persistência forneça Implementando o <xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService>e o <xref:System.ComponentModel.Design.IComponentChangeService>classes.</xref:System.ComponentModel.Design.IComponentChangeService> </xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService>  
  
 Para obter mais informações sobre como escrever designers usando [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)], consulte [Estendendo suporte em tempo de Design](http://msdn.microsoft.com/Library/d6ac8a6a-42fd-4bc8-bf33-b212811297e2).  
  
 O [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] fornece uma infraestrutura de desfazer padrão por:  
  
-   Fornecendo implementações de gerenciamento por meio de desfazer o <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine>e <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine.UndoUnit>classes.</xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine.UndoUnit> </xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine>  
  
-   Fornecendo suporte de CodeDOM através do padrão e persistência <xref:System.ComponentModel.Design.Serialization.CodeDomComponentSerializationService>e <xref:System.ComponentModel.Design.IComponentChangeService>implementações.</xref:System.ComponentModel.Design.IComponentChangeService> </xref:System.ComponentModel.Design.Serialization.CodeDomComponentSerializationService>  
  
## <a name="obtaining-undo-support-automatically"></a>Como obter suporte à função desfazer automaticamente  
 Qualquer designer criado no [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] tem suporte à função desfazer automática e completa se, o designer:  
  
-   Usa um <xref:System.Windows.Forms.Control>com base em classe de interface do usuário.</xref:System.Windows.Forms.Control>  
  
-   Emprega a geração de código padrão com base no CodeDOM e sistema de análise de persistência e geração de código.  
  
     Para obter mais informações sobre como trabalhar com o suporte de CodeDOM do Visual Studio, consulte [geração dinâmica de código fonte e compilação](http://msdn.microsoft.com/Library/d077a3e8-bd81-4bdf-b6a3-323857ea30fb)  
  
## <a name="when-to-use-explicit-designer-undo-support"></a>Quando usar o suporte à função desfazer de Designer explícita  
 Designers devem fornecer seu próprio gerenciamento de desfazer se eles usam uma interface gráfica do usuário, conhecida como um adaptador de exibição, que não seja aquele fornecido pelo <xref:System.Windows.Forms.Control>.</xref:System.Windows.Forms.Control>  
  
 Um exemplo disso pode estar criando um produto com uma interface de design gráfico baseada na web, em vez de um [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] com base em interface gráfica.  
  
 Nesses casos, é necessário registrar esse adaptador de exibição com [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] usando <xref:Microsoft.VisualStudio.Shell.Design.ProvideViewAdapterAttribute>e fornecer gerenciamento explícito de desfazer.</xref:Microsoft.VisualStudio.Shell.Design.ProvideViewAdapterAttribute>  
  
 Designers precisam fornecer suportam de CodeDOM e persistência se não usar o [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] modelo de geração de código fornecido a <xref:System.CodeDom>espaço de nome.</xref:System.CodeDom>  
  
## <a name="undo-support-features-of-the-designer"></a>Recursos de suporte do Designer de desfazer  
 O SDK do ambiente fornece implementações padrão dessas interfaces necessárias para fornecer desfazer suporte que pode ser usado pelos designers não usando <xref:System.Windows.Forms.Control>com base em classes para suas interfaces de usuário ou o modelo padrão de CodeDOM e persistência.</xref:System.Windows.Forms.Control>  
  
 O <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine>classe deriva de [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] <xref:System.ComponentModel.Design.UndoEngine>usando uma implementação da classe a <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoManager>classe para gerenciar operações de desfazer.</xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoManager> </xref:System.ComponentModel.Design.UndoEngine> </xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine>  
  
 O Visual Studio fornece o seguinte recurso para desfazer designer:  
  
-   Funcionalidade de desfazer vinculado em vários designers.  
  
-   Secundárias em um designer podem interagir com seus pais, implementando <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoUnit>e <xref:Microsoft.VisualStudio.OLE.Interop.IOleParentUndoUnit>em <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine.UndoUnit>.</xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine.UndoUnit> </xref:Microsoft.VisualStudio.OLE.Interop.IOleParentUndoUnit> </xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoUnit>  
  
 O SDK de ambiente oferece suporte de CodeDOM e persistência, fornecendo:  
  
-   <xref:System.ComponentModel.Design.Serialization.CodeDomComponentSerializationService>como um implementações das<xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService></xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService></xref:System.ComponentModel.Design.Serialization.CodeDomComponentSerializationService>  
  
 Um <xref:System.ComponentModel.Design.IComponentChangeService>fornecido pelo [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]' host de design.</xref:System.ComponentModel.Design.IComponentChangeService>  
  
## <a name="using-the-environment-sdk-features-to-supply-undo-support"></a>Usando os recursos do SDK de ambiente para fornecer suporte à função desfazer  
 Para obter suporte à função desfazer, um objeto que implementa um designer deve:  
  
-   Instanciar e inicializar uma instância do <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine>classe com uma validade <xref:System.IServiceProvider>implementação.</xref:System.IServiceProvider> </xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine>  
  
-   Isso <xref:System.IServiceProvider>classe deve fornecer os seguintes serviços:</xref:System.IServiceProvider>  
  
    -   <xref:System.ComponentModel.Design.IDesignerHost>.</xref:System.ComponentModel.Design.IDesignerHost>  
  
    -   <xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService></xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService>  
  
         Designers usando [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] serialização CodeDOM pode optar por usar <xref:System.ComponentModel.Design.Serialization.CodeDomComponentSerializationService>fornecido com o [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] como sua implementação de <xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService>.</xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService> </xref:System.ComponentModel.Design.Serialization.CodeDomComponentSerializationService>  
  
         Nesse caso, a <xref:System.IServiceProvider>classe fornecida para o <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine>construtor deve retornar esse objeto como uma implementação de <xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService>classe.</xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService> </xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine> </xref:System.IServiceProvider>  
  
    -   <xref:System.ComponentModel.Design.IComponentChangeService></xref:System.ComponentModel.Design.IComponentChangeService>  
  
         Usando o padrão de designers <xref:System.ComponentModel.Design.DesignSurface>fornecido pelo [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] host de design são garantidos para terem uma implementação padrão da <xref:System.ComponentModel.Design.IComponentChangeService>classe</xref:System.ComponentModel.Design.IComponentChangeService> </xref:System.ComponentModel.Design.DesignSurface>  
  
 Designers de implementar um <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine>baseado em Desfazer mecanismo controla automaticamente as alterações se:</xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine>  
  
-   Alterações de propriedade são feitas por meio de <xref:System.ComponentModel.TypeDescriptor>objeto.</xref:System.ComponentModel.TypeDescriptor>  
  
-   <xref:System.ComponentModel.Design.IComponentChangeService>eventos são gerados manualmente quando uma alteração não pode ser desfeita é confirmada.</xref:System.ComponentModel.Design.IComponentChangeService>  
  
-   Modificação no designer foi criada dentro do contexto de <xref:System.ComponentModel.Design.DesignerTransaction>.</xref:System.ComponentModel.Design.DesignerTransaction>  
  
-   O designer opta por criar explicitamente desfazer unidades usando a unidade de desfazer padrão fornecida por uma implementação de <xref:System.ComponentModel.Design.UndoEngine.UndoUnit>ou a implementação de específicas do Visual Studio <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine.UndoUnit>que deriva de <xref:System.ComponentModel.Design.UndoEngine.UndoUnit>e também fornece uma implementação de dois <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoUnit>e <xref:Microsoft.VisualStudio.OLE.Interop.IOleParentUndoUnit>.</xref:Microsoft.VisualStudio.OLE.Interop.IOleParentUndoUnit> </xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoUnit> </xref:System.ComponentModel.Design.UndoEngine.UndoUnit> </xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine.UndoUnit> </xref:System.ComponentModel.Design.UndoEngine.UndoUnit>  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.ComponentModel.Design.UndoEngine></xref:System.ComponentModel.Design.UndoEngine>   
 <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine></xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine>   
 [Estendendo o suporte ao tempo de Design](http://msdn.microsoft.com/Library/d6ac8a6a-42fd-4bc8-bf33-b212811297e2)
