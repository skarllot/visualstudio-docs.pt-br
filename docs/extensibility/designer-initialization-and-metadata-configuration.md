---
title: "Inicialização de Designer e a configuração de metadados | Documentos do Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- designers [Visual Studio SDK], initializing
- designers [Visual Studio SDK], configuring metadata
ms.assetid: f7fe9a7e-f669-4642-ad5d-186b2e6e6ec9
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
ms.sourcegitcommit: 5658ecf52637a38bc3c2a5ad9e85b2edebf7d445
ms.openlocfilehash: c0865b62cc2683a8197b5eb6cbc0599d6c063534
ms.lasthandoff: 02/22/2017

---
# <a name="designer-initialization-and-metadata-configuration"></a>Inicialização de Designer e a configuração de metadados
Manipulação dos atributos de metadados e o filtro associado a um designer ou o componente de designer fornece um mecanismo para aplicativos definir quais ferramentas são usadas por um designer específico para lidar com diferentes <xref:System.Type>objetos (como estruturas de dados, classes ou entidades gráficas), quando o designer está disponível e como o IDE do Visual Studio está configurado para suportar o designer (para instância que **Toolbox** categoria ou o guia está disponível).</xref:System.Type>  
  
 O [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] fornece vários mecanismos para facilitar o controle de um designer ou designer do componente de inicialização e a manipulação de seus metadados por um VSPackage.  
  
## <a name="initializing-metadata-and-configuration-information"></a>Inicializando os metadados e informações de configuração  
 Como eles são carregados sob demanda, VSPackages podem não ter sido carregados pelo [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ambiente antes da instanciação de um designer. Portanto, VSPackages não é possível usar o mecanismo padrão para a configuração de um designer ou o componente de designer na criação, que deve tratar um <xref:System.ComponentModel.Design.IDesignerEventService.DesignerCreated>evento.</xref:System.ComponentModel.Design.IDesignerEventService.DesignerCreated> Em vez disso, um VSPackage implementa uma instância do <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension>da interface e se registra para fornecer personalizações, conhecidas como extensões de superfície de design.</xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension>  
  
### <a name="customizing-initialization"></a>Personalizando a inicialização  
 Personalizar um designer, um componente ou uma superfície de design, envolve:  
  
1.  Modificando metadados de designer e alterando efetivamente como uma determinada <xref:System.Type>é acessado ou convertido.</xref:System.Type>  
  
     Isso geralmente é feito por meio de <xref:System.Drawing.Design.UITypeEditor>ou <xref:System.ComponentModel.TypeConverter>mecanismos.</xref:System.ComponentModel.TypeConverter> </xref:System.Drawing.Design.UITypeEditor>  
  
     Por exemplo, quando <xref:System.Windows.Forms>-designers com base são inicializados, o [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ambiente modifica o <xref:System.Drawing.Design.UITypeEditor>para <xref:System.Web.UI.WebControls.Image>objetos usados com o designer para usar o Gerenciador de recursos para obter bitmaps em vez do sistema de arquivos.</xref:System.Web.UI.WebControls.Image> </xref:System.Drawing.Design.UITypeEditor> </xref:System.Windows.Forms>  
  
2.  Integração com o ambiente, por exemplo, assinar eventos ou obter informações de configuração do projeto. Você pode obter informações de configuração do projeto e inscrever-se em eventos, obtendo o <xref:System.ComponentModel.Design.ITypeResolutionService>interface.</xref:System.ComponentModel.Design.ITypeResolutionService>  
  
3.  Modificação do ambiente do usuário ativando apropriado **Toolbox** categorias ou restringindo aplicabilidade do designer, aplicando uma instância do <xref:System.ComponentModel.ToolboxItemFilterAttribute>classe ao designer.</xref:System.ComponentModel.ToolboxItemFilterAttribute>  
  
### <a name="designer-initialization-by-a-vspackage"></a>Inicialização Designer por um VSPackage  
 Um VSPackage deve tratar a inicialização pelo designer:  
  
1.  Criar um objeto que implementa a <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension>classe.</xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension>  
  
    > [!NOTE]
    >  A <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension>classe nunca deve ser implementada no mesmo objeto que a <xref:Microsoft.VisualStudio.Shell.Package>classe.</xref:Microsoft.VisualStudio.Shell.Package> </xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension>  
  
2.  Registrar a classe de implementação <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension>como fornecer suporte para extensões do designer do VSPackage aplicando instâncias de <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtensionAttribute> <xref:Microsoft.VisualStudio.Shell.ProvideObjectAttribute>e <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute>para a classe fornecendo a implementação do VSPackage do <xref:Microsoft.VisualStudio.Shell.Package>.</xref:Microsoft.VisualStudio.Shell.Package> </xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute> </xref:Microsoft.VisualStudio.Shell.ProvideObjectAttribute> </xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtensionAttribute> </xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension>  
  
 Sempre que qualquer componente designer ou designer é criado, o [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ambiente:  
  
1.  Acessa a cada provedor de extensão de superfície de design de registrado.  
  
2.  Cria e inicializa uma instância de <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension>objeto da cada provedor extensão de superfície de design</xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension>  
  
3.  Chama cada provedor de extensão de superfície de design <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension.OnDesignerCreated%2A>método ou <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension.OnComponentCreated%2A>método (conforme apropriado).</xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension.OnComponentCreated%2A> </xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension.OnDesignerCreated%2A>  
  
 Ao implementar o <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension>do objeto como um membro de um VSPackage, é importante compreender que:</xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension>  
  
1.  O [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ambiente não fornece nenhum controle sobre quais metadados ou outras configurações de um determinado `DesignSurfaceExtension` modifica do provedor. É possível que dois ou mais `DesignSurfaceExtension` provedores modificando o mesmo recurso designer maneiras em conflito com a modificação final sendo definitiva. É indeterminado qual modificação é aplicada pela última vez.  
  
2.  É possível restringir explicitamente uma implementação do <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension>designers específicos, aplicando as instâncias do objeto <xref:System.ComponentModel.ToolboxItemFilterAttribute>para essa implementação.</xref:System.ComponentModel.ToolboxItemFilterAttribute> </xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension> Para obter mais informações sobre **Toolbox** item filtragem, consulte a <xref:System.ComponentModel.ToolboxItemFilterAttribute>e <xref:System.ComponentModel.ToolboxItemFilterType>.</xref:System.ComponentModel.ToolboxItemFilterType> </xref:System.ComponentModel.ToolboxItemFilterAttribute>  
  
## <a name="additional-metadata-provisioning"></a>Provisionamento de metadados adicionais  
 Um VSPackage pode alterar a configuração de um designer ou o componente designer diferente no tempo de design.  
  
 O <xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute>classe pode ser usada de forma programática, ou ser aplicadas a um VSPackage fornecendo um designer.</xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute>  
  
 Uma instância do <xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute>classe é usada para modificar os metadados de componentes criados em uma superfície de design.</xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute> Por exemplo, um pode substituir um navegador de propriedade padrão usado pelo <xref:System.Windows.Forms.CommonDialog>objetos com um navegador de propriedade personalizada.</xref:System.Windows.Forms.CommonDialog>  
  
 Modificações fornecidas por uma instância de <xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute>aplicada a implementação do VSPackage <xref:Microsoft.VisualStudio.Shell.Package>pode ter um dos dois escopos:</xref:Microsoft.VisualStudio.Shell.Package> </xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute>  
  
-   Global – para todas as novas instâncias de um determinado componente  
  
-   Local - pertence apenas à instância do componente criado em uma superfície de design fornecida pelo VSPackage atual.  
  
 O `IsGlobal` propriedade o <xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute>instância aplicada a implementação do VSPackage <xref:Microsoft.VisualStudio.Shell.Package>determina esse escopo.</xref:Microsoft.VisualStudio.Shell.Package> </xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute>  
  
 Aplicando o atributo para uma implementação de <xref:Microsoft.VisualStudio.Shell.Package>com o <xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute.IsGlobal%2A>propriedade do <xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute>objeto definido como `true`, conforme mostrado abaixo, altera o navegador para todo o [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ambiente:</xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute> </xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute.IsGlobal%2A> </xref:Microsoft.VisualStudio.Shell.Package>  
  
 `[ProvideDesignerMetadata(typeof(Color), typeof(CustomBrowser),`   `IsGlobal=true`  `)]`  
  
 `internal class MyPackage : Package {}`  
  
 Se o sinalizador global foi definido como `false`, em seguida, a alteração de metadados é local para o designer atual compatíveis com o VSPackage atual:  
  
 `[ProvideDesignerMetadata(typeof(Color), typeof(CustomBrowser),`   `IsGlobal=false`  `)]`  
  
 `internal class MyPackage : Package {}`  
  
> [!NOTE]
>  No momento, a superfície de design só oferece suporte a criação de componentes e, portanto, somente os componentes podem ter metadados locais. No exemplo acima, está tentando modificar uma propriedade, como o `Color` propriedade de um objeto. Se `false` foi passado para o sinalizador global, `CustomBrowser` nunca seria exibido, pois nunca na verdade, o designer cria uma instância de `Color`. Definir o sinalizador global `false` é útil para componentes, como controles, temporizadores e caixas de diálogo.  
  
## <a name="see-also"></a>Consulte também  
 <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension></xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension>   
 <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtensionAttribute></xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtensionAttribute>   
 <xref:System.ComponentModel.ToolboxItemFilterType></xref:System.ComponentModel.ToolboxItemFilterType>   
 [Estendendo o suporte ao tempo de Design](http://msdn.microsoft.com/Library/d6ac8a6a-42fd-4bc8-bf33-b212811297e2)
