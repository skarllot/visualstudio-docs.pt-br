---
title: 'Como: criar marcadores de texto personalizado | Documentos do Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - custom text markers
ms.assetid: 6e32ed81-c604-4a32-9012-8db3bec7c846
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
ms.openlocfilehash: c9a78c8b7f1c79a155de5b300d51b0313722d44a
ms.lasthandoff: 02/22/2017

---
# <a name="how-to-create-custom-text-markers"></a>Como: criar marcadores de texto personalizado
Se você quiser criar um marcador de texto personalizado para enfatizar ou organizar o código, você deve executar as etapas a seguir:  
  
-   Registrar o novo marcador de texto, de forma que outras ferramentas podem acessá-lo  
  
-   Fornecer uma implementação padrão e a configuração do marcador de texto  
  
-   Criar um serviço que pode ser usado por outros processos para fazer uso do marcador de texto  
  
 Para obter detalhes sobre como aplicar um marcador de texto a uma região de código, consulte [como: usar marcadores de texto](../extensibility/how-to-use-text-markers.md).  
  
### <a name="to-register-a-custom-marker"></a>Para registrar um marcador personalizado  
  
1.  Crie uma entrada de registro da seguinte maneira:  
  
     HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\\*\<versão >*\Text Editor\External marcadores\\*\<MarkerGUID >*  
  
     *\<MarkerGUID >*é um `GUID` usado para identificar o marcador que está sendo adicionado  
  
     *\<Versão >* é a versão do [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], por exemplo 8.0  
  
     *\<PackageGUID >* é o GUID do VSPackage implementa o objeto de automação.  
  
    > [!NOTE]
    >  O caminho raiz do HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\\*\<versão >* pode ser substituído por uma raiz alternativa ao shell do Visual Studio é inicializado, para obter mais informações, consulte [opções de linha de comando](../extensibility/command-line-switches-visual-studio-sdk.md).  
  
2.  Criar quatro valores em HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\\*\<versão >*\Text Editor\External marcadores\\*\<MarkerGUID >*  
  
    -   (Padrão)  
  
    -   Serviço  
  
    -   DisplayName  
  
    -   Pacote  
  
    -   `Default`é uma entrada opcional do tipo REG_SZ. Quando definido, o valor da entrada é uma cadeia de caracteres que contém algumas informações de identificação útil, por exemplo "marcador de texto personalizado".  
  
    -   `Service`é uma entrada do tipo REG_SZ que contém a cadeia de caracteres do GUID do serviço que fornece o marcador de texto personalizado por proffering <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerTypeProvider>.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerTypeProvider> O formato é {XXXXXX XXXX XXXX XXXX XXXXXXXXX}.  
  
    -   `DisplayName`é uma entrada do tipo REG_SZ que contém a ID de recurso do nome do marcador de texto personalizado. O formato é #YYYY.  
  
    -   `Package`entrada de tipo REG_SZ contendo o `GUID` de VSPackage que fornece o serviço listado em serviço. O formato é {XXXXXX XXXX XXXX XXXX XXXXXXXXX}.  
  
### <a name="to-create-a-custom-text-marker"></a>Para criar um marcador de texto personalizado  
  
1.  Implementar o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsPackageDefinedTextMarkerType>interface.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsPackageDefinedTextMarkerType>  
  
     A implementação dessa interface define o comportamento e a aparência do seu tipo de marcador personalizado.  
  
     Essa interface é chamada quando  
  
    1.  Um usuário inicia o IDE pela primeira vez.  
  
    2.  Um usuário seleciona o **Redefinir padrões** botão no **fontes e cores** página de propriedade no **ambiente** pasta, localizada no painel esquerdo do **opções** obtido de caixa de diálogo o **ferramentas** menu do IDE.  
  
2.  Implementar o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerTypeProvider.GetTextMarkerType%2A>método, especificando que `IVsPackageDefinedTextMarkerType` implementação deve ser retornada com base no tipo de marcador GUID especificado na chamada do método.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerTypeProvider.GetTextMarkerType%2A>  
  
     O ambiente chama neste momento o primeiro método, o tipo de marcador personalizado é criado e especifica um GUID que identifica o tipo de marcador personalizado.  
  
### <a name="to-proffer-your-marker-type-as-a-service"></a>Para oferecer o tipo de marcador, como um serviço  
  
1.  Chame o <xref:Microsoft.VisualStudio.OLE.Interop.IOleComponentManager.QueryService%2A>método <xref:Microsoft.VisualStudio.Shell.Interop.SProfferService>.</xref:Microsoft.VisualStudio.Shell.Interop.SProfferService> </xref:Microsoft.VisualStudio.OLE.Interop.IOleComponentManager.QueryService%2A>  
  
     Um ponteiro para <xref:Microsoft.VisualStudio.Shell.Interop.IProfferService>é retornado.</xref:Microsoft.VisualStudio.Shell.Interop.IProfferService>  
  
2.  Chamar o <xref:Microsoft.VisualStudio.Shell.Interop.IProfferService.ProfferService%2A>método, especificando o GUID que identifica o serviço do tipo de marcador personalizado e fornecendo um ponteiro para sua implementação do <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>interface.</xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> </xref:Microsoft.VisualStudio.Shell.Interop.IProfferService.ProfferService%2A> O <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>implementação deve retornar um ponteiro para sua implementação de <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerTypeProvider>interface.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerTypeProvider> </xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>  
  
     Um cookie exclusivo identificando que seu serviço será retornado. Mais tarde você pode usar esse cookie revogue o seu serviço de tipo de marcador personalizado chamando o <xref:Microsoft.VisualStudio.Shell.Interop.IProfferService.RevokeService%2A>método o <xref:Microsoft.VisualStudio.Shell.Interop.IProfferService>interface especificar esse valor de cookie.</xref:Microsoft.VisualStudio.Shell.Interop.IProfferService> </xref:Microsoft.VisualStudio.Shell.Interop.IProfferService.RevokeService%2A>  
  
## <a name="see-also"></a>Consulte também  
 [Usar marcadores de texto com a API herdada](../extensibility/using-text-markers-with-the-legacy-api.md)   
 [Como: adicionar marcadores de texto padrão](../extensibility/how-to-add-standard-text-markers.md)   
 [Como: implementar marcadores de erro](../extensibility/how-to-implement-error-markers.md)   
 [Como: usar marcadores de texto](../extensibility/how-to-use-text-markers.md)
