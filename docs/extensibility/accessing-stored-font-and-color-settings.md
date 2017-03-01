---
title: "Acessando configurações de cor e fonte armazenado | Documentos do Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- fonts, accessing stored settings
- font and color control [Visual Studio SDK], persistence
- colors, accessing stored settings
ms.assetid: beba7174-e787-45c2-b6ff-a60f67ad4998
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
ms.openlocfilehash: 7f9a13e81591dfb7fd908ebf1ebf92c9896949af
ms.lasthandoff: 02/22/2017

---
# <a name="accessing-stored-font-and-color-settings"></a>Acessando configurações de cor e fonte armazenado
O [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ambiente de desenvolvimento integrado (IDE) armazena configurações modificadas para fontes e cores no registro. Você pode usar o <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage>interface para acessar essas configurações.</xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage>  
  
## <a name="to-initiate-state-persistence-of-fonts-and-colors"></a>Para iniciar a persistência de estado de fontes e cores  
 Informações de fonte e cor são armazenadas por categoria no seguinte local do registro: [HKCU\SOFTWARE\Microsoft \Visual Studio\\*\<versão do Visual Studio >*\FontAndColors\\*\<CategoryGUID >*], onde * \<CategoryGUID >* é o GUID da categoria.  
  
 Portanto, para iniciar a persistência, um VSPackage deve:  
  
-   Obter um <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage>interface chamando `QueryService` em relação ao provedor de serviços globais.</xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage>  
  
     `QueryService`deve ser chamado usando um argumento de ID do serviço de `SID_SVsFontAndColorStorage` e um argumento de ID de interface de `IID_IVsFontAndColorStorage`.  
  
-   Use o <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.OpenCategory%2A>método para abrir uma categoria a ser mantido, usando o GUID da categoria e um sinalizador do modo como argumentos.</xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.OpenCategory%2A>  
  
     O modo especificado pelo `fFlags` argumento, é criado com valores de <xref:Microsoft.VisualStudio.Shell.Interop.__FCSTORAGEFLAGS>enumeração.</xref:Microsoft.VisualStudio.Shell.Interop.__FCSTORAGEFLAGS> Esse modo de controles:  
  
    -   As configurações que podem ser acessadas por meio de <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage>interface.</xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage>  
  
    -   Todas as configurações ou apenas aqueles que modificam os usuários e que são recuperáveis por meio do <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage>interface.</xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage>  
  
    -   A maneira de propagar as alterações nas configurações do usuário.  
  
    -   O formato dos valores de cor são usadas.  
  
## <a name="to-use-state-persistence-of-fonts-and-colors"></a>Para usar o estado persistência de fontes e cores  
 Cores e fontes persistentes envolve:  
  
-   Sincronizar as configurações de IDE com as configurações armazenadas no registro.  
  
-   Propagação de informações sobre a modificação do registro.  
  
-   Configurando e recuperando as configurações armazenadas no registro.  
  
 Sincronizar a configuração de armazenamento com as configurações de IDE é totalmente transparente. O IDE subjacente automaticamente grava as configurações atualizadas para **exibir itens** para as entradas do registro das categorias.  
  
 Se vários VSPackages compartilham uma categoria específica, um VSPackage deve exigir que os eventos são gerados quando os métodos do <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage>interface são usados para modificar as configurações de registro armazenados.</xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage>  
  
 Por padrão, a geração de eventos não está habilitada. Para habilitar a geração de eventos, uma categoria deve ser aberta usando <xref:Microsoft.VisualStudio.Shell.Interop.__FCSTORAGEFLAGS>.</xref:Microsoft.VisualStudio.Shell.Interop.__FCSTORAGEFLAGS> Isso faz com que o IDE chamar o <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorEvents>método que implementa um VSPackage.</xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorEvents>  
  
> [!NOTE]
>  Modificações por meio de **fontes e cores** página de propriedade geram eventos independentes do <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage>.</xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> Você pode usar a <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorCacheManager>interface para determinar se é necessária uma atualização de configurações de fonte e cor em cache antes de chamar os métodos de <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage>classe.</xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> </xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorCacheManager>  
  
### <a name="storing-and-retrieving-information"></a>Armazenar e recuperar informações  
 Para obter ou definir informações de que um usuário pode modificar para um item de exibição nomeada em uma categoria aberto, VSPackages chamar o <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetItem%2A>e <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.SetItem%2A>métodos.</xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.SetItem%2A> </xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetItem%2A>  
  
 Informações sobre a fonte de atributos para uma determinada categoria é obtida usando o <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetFont%2A>e <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.SetFont%2A>métodos.</xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.SetFont%2A> </xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetFont%2A>  
  
> [!NOTE]
>  O `fFlags` argumento que é passado para o <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.OpenCategory%2A>método categoria tiver sido aberto define o comportamento do <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetItem%2A>e o <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetFont%2A>métodos.</xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetFont%2A> </xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetItem%2A> </xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.OpenCategory%2A> Por padrão, essas itemsthat de aboutdisplay métodos somente retornam informações foram alteradas. No entanto, se uma categoria for aberta usando o <xref:Microsoft.VisualStudio.Shell.Interop.__FCSTORAGEFLAGS>sinalizador de exibição atualizada e inalterada itens podem ser acessados e <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetItem%2A> <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetFont%2A>.</xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetFont%2A> </xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetItem%2A> </xref:Microsoft.VisualStudio.Shell.Interop.__FCSTORAGEFLAGS>  
  
 Por padrão, apenas alterado **exibir itens** informações são mantidas no registro. O <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage>interface não pode ser usada para recuperar todas as configurações de fontes e cores.</xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage>  
  
> [!NOTE]
>  O <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetItem%2A>e o <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetFont%2A>métodos retornam REGDB_E_KEYMISSING, (0x80040152L) quando usá-los para recuperar informações sobre inalterado **exibir itens**.</xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetFont%2A> </xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetItem%2A>  
  
 As configurações de todos os **exibir itens** em uma determinada **categoria** pode ser obtida usando os métodos do `T:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults` interface.  
  
## <a name="see-also"></a>Consulte também  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage></xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage>   
 <xref:Microsoft.VisualStudio.Shell.Interop.__FCSTORAGEFLAGS></xref:Microsoft.VisualStudio.Shell.Interop.__FCSTORAGEFLAGS>   
 [Implementação de categorias personalizadas e exibir itens](../extensibility/implementing-custom-categories-and-display-items.md)
