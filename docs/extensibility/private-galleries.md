---
title: Galerias de privada | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- VSIX galleries, private
- private galleries, VSIX
ms.assetid: b6b3dee7-91c5-4556-9f69-0d56b675e83b
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 3e85f14684de28a0b96ace5d88b887d705c097e3
ms.contentlocale: pt-br
ms.lasthandoff: 02/22/2017

---
# <a name="private-galleries"></a>Galerias privadas
Você pode compartilhar controles, modelos e ferramentas que você desenvolve postando-os para uma *galeria particular* na intranet da sua organização, da seguinte maneira:  
  
-   Crie um átomo (RSS) para um local central configurado adequadamente (repositório) na sua intranet. Para obter mais informações, consulte [como: criar um Feed Atom para uma galeria privada](../extensibility/how-to-create-an-atom-feed-for-a-private-gallery.md).  
  
-   Distribua um arquivo pkgdef que descreve a galeria particular. Recomendamos essa configuração para administradores que desejam se conectar a uma galeria privada em vários computadores ao mesmo tempo.  
  
## <a name="adding-a-private-gallery-to-extensions-and-updates-in-visual-studio"></a>Adicionando uma galeria privada para extensões e atualizações no Visual Studio  
 Quando uma galeria privada estiver disponível, você pode adicioná-lo para **extensões e atualizações** no Visual Studio.  
  
 ![Gerenciador de extensões de caixa de diálogo Adicionar](../extensibility/media/em_adddialog.png "EM_AddDialog")  
  
#### <a name="to-add-a-private-gallery-to-extensions-and-updates"></a>Para adicionar uma galeria privada para extensões e atualizações  
  
1.  Na barra de menus, escolha **Ferramentas**, **Opções**.  
  
2.  No **ambiente** nó, selecione **extensões e atualizações**.  
  
3.  Escolha o botão **Adicionar**.  
  
4.  No **nome** , insira um nome para a Galeria privada, por exemplo, `My Gallery`.  
  
5.  No **URL** , insira a URL do feed Atom ou site do SharePoint que está hospedando a galeria particular.  
  
    1.  Se o host for um feed Atom que se conecta à Galeria privada, a URL seria semelhante a esta: http://www.mywebsite/mygallery/atom.xml.  Essa URL pode se referir a um arquivo ou um caminho de rede.  
  
    2.  Se o host for um site do SharePoint, a URL seria semelhante a esta: http://mysharepoint/sites/mygallery/forms/AllItems.aspx.  
  
### <a name="managing-private-galleries"></a>Gerenciando galerias privadas  
 Um administrador pode disponibilizar uma galeria privada em vários computadores ao mesmo tempo, modificando o registro do sistema em cada computador. Para fazer isso, crie um arquivo pkgdef que descreve as novas chaves de registro e seus valores.  O formato deste arquivo é da seguinte maneira.  
  
```  
[$RootKey$\ExtensionManager\Repositories\{UniqueGUID}]  
@={URI}  (REG_SZ)  
Disabled=0 | 1 (DWORD)  
Priority=0 (highest priority) ... MaxInt (lowest priority) (DWORD) (uint)  
Protocol=VSGallery|Atom|Sharepoint (REG_SZ)  
DisplayName={DisplayName} (REG_SZ)  
DisplayNameResourceID={ID} (REG_SZ)  
DisplayNamePackageGuid={GUID} (REG_SZ)  
  
```  
  
 Para obter mais informações, consulte [como: gerenciar uma privada Galeria por usando configurações do registro](../extensibility/how-to-manage-a-private-gallery-by-using-registry-settings.md).  
  
## <a name="installing-extensions-from-a-private-gallery"></a>Instalando extensões de uma galeria privada  
 Você pode procurar e instalar extensões do Visual Studio de uma galeria privada em **extensões e atualizações**. As etapas a seguir usam uma galeria particular chamada `My Gallery`.  
  
 ![Gerenciador de extensões instalando Galeria privada](../extensibility/media/em_.png "EM_")  
  
#### <a name="to-search-for-and-install-extensions-from-a-private-gallery"></a>Para procurar e instalar as extensões de uma galeria privada  
  
1.  Na barra de menus, escolha **ferramentas**, **extensões e atualizações**.  
  
2.  No painel esquerdo, selecione **extensões Online**e, em seguida, selecione **minha galeria**.  
  
3.  No painel direito, selecione uma extensão e, em seguida, escolha o **baixar** botão.  
  
## <a name="updating-extensions-from-a-private-gallery"></a>Extensões de atualização de uma galeria privada  
 Conforme novas versões de extensões do Visual Studio são lançadas na Galeria privada, você pode atualizar as extensões que você instalou. As etapas a seguir usam uma galeria particular chamada `My Repository`.  
  
 ![Atualização de galeria particular do Gerenciador de extensão](../extensibility/media/em_update.png "EM_Update")  
  
#### <a name="to-update-an-installed-extension-from-a-private-gallery"></a>Para atualizar uma extensão instalados de uma galeria privada  
  
1.  Na barra de menus, escolha **ferramentas**, **extensões e atualizações**.  
  
2.  No painel esquerdo, selecione **atualizações**e, em seguida, selecione **meu repositório**.  
  
3.  No painel direito, selecione uma extensão e, em seguida, escolha o **atualização** botão.  
  
## <a name="see-also"></a>Consulte também  
 [Localizando e usando extensões do Visual Studio](../ide/finding-and-using-visual-studio-extensions.md)   
 [Envio de extensões do Visual Studio](../extensibility/shipping-visual-studio-extensions.md)
