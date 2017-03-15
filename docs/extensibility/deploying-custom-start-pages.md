---
title: "Implantação de páginas de início personalizados | Documentos do Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- package start page
- deploy start page
ms.assetid: 4a7eb360-de83-41d5-be53-3cfb160d19f9
caps.latest.revision: 21
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
ms.openlocfilehash: 9e99f022f1dec71b82c2261cae1d45705fe8dc7f
ms.lasthandoff: 02/22/2017

---
# <a name="deploying-custom-start-pages"></a>Implantação de páginas de início personalizado
Você pode implantar páginas de inicialização personalizada usando a implantação do VSIX ou copiando os arquivos nos locais corretos no computador de destino.  
  
## <a name="vsix-deployment-by-using-the-start-page-project-template"></a>Implantação do VSIX usando o modelo de projeto de página inicial  
 Quando você cria uma página inicial usando o modelo de projeto de página inicial e, em seguida, compile o projeto, o Visual Studio cria um arquivo. VSIX que você pode distribuir. Empacotar uma página inicial em um arquivo. VSIX oferece as seguintes opções para a implantação, dependendo do seu público-alvo:  
  
-   Você pode colocar o arquivo. VSIX em um compartilhamento de rede ou em um site público. Quando alguém abre o arquivo, a página de início é instalada automaticamente.  
  
-   Você pode carregar o arquivo. VSIX para o [Galeria do Visual Studio](http://go.microsoft.com/fwlink/?LinkID=123847) Web site para que os usuários podem instalá-lo usando **Extension Manager**.  
  
 O modelo de projeto de página inicial cria uma cópia da página de início do Visual Studio padrão para que você possa modificar a cópia e preservar o original.  
  
 Você pode obter o modelo de projeto de página inicial usando **Extension Manager** ou fazendo o download no site da Web.  
  
## <a name="vsix-deployment-without-using-the-start-page-project-template"></a>Implantação do VSIX sem usar o modelo de projeto de página inicial  
 Uma implantação bem-sucedida do VSIX requer uma extensão para ser instalado em pastas que são reconhecidas pelo processo de registro VSIX e pelo **Extension Manager**. Como o modelo de projeto de página inicial já especifica nas pastas corretas, é recomendável usar sempre que você deseja compactar uma extensão para a implantação do VSIX. No entanto, se você tiver um caso em que você não pode usar o modelo, você pode criar uma implantação de VSIX sem usá-lo.  
  
 Para criar uma implantação de VSIX sem usar o modelo de projeto de página inicial, primeiro crie um arquivo. VSIX para a página de início de uma destas duas maneiras:  
  
-   Adicionando os arquivos de página inicial personalizados para um projeto vazio do VSIX. Para obter mais informações, consulte [modelo de projeto do VSIX](../extensibility/vsix-project-template.md).  
  
-   Criando manualmente um arquivo. VSIX. Para obter mais informações, consulte [como: pacote manualmente uma extensão (implantação VSIX)](../misc/how-to-manually-package-an-extension-vsix-deployment.md).  
  
 Para o Visual Studio reconheça uma página inicial, o `Content Element` de manifesto do VSIX deve conter um `CustomExtension Element` que tem o `Type` atributo definido como `"StartPage"`. Uma extensão de página de início foi instalada usando a implantação do VSIX aparece no **Personalizar página inicial** lista o **inicialização** página de opções como **[extensão instalado]** *nome da extensão*.  
  
 Se o seu pacote de página inicial inclui assemblies, você deve adicionar um registro de caminho de associação para que fiquem disponíveis quando o Visual Studio inicia. Para fazer isso, certifique-se de que o pacote inclui um arquivo pkgdef que tem as seguintes informações.  
  
```  
[$RootKey$\BindingPaths\{Insert a new GUID here}]  
"$PackageFolder$"=""  
```  
  
### <a name="vsix-deployment-for-all-users"></a>Implantação do VSIX para todos os usuários  
 Por padrão, as extensões implantadas em pacotes VSIX instalam somente para o usuário atual. Você pode fazer uma instalação da página inicial para todos os usuários do computador de destino ao criar uma implantação de todos os usuários.  
  
##### <a name="to-create-an-all-users-deployment"></a>Para criar uma implantação de todos os usuários  
  
1.  Abra o arquivo vsixmanifest no modo de exibição de código.  
  
2.  No `Identifier` elemento do manifesto vsix, adicione um `AllUsers` elemento que possui um valor de `true`.  
  
    ```  
    <AllUsers>true</AllUsers>  
    ```  
  
     Isso faz com que o instalador vsix solicitar permissões de administrador e, em seguida, instalar os arquivos \Common7\IDE\Extensions.  
  
3.  Abra o arquivo pkgdef.  
  
4.  Modifique pkgdef para definir a página de início padrão em HKLM, adicionando o seguinte, onde *MyStartPage.xaml* é o nome do arquivo. XAML que contém a página inicial.  
  
     [$RootKey$ \StartPage\Default]  
  
     "Uri"="$PackageFolder$\\*MyStartPage.xaml*"  
  
     Isso informa ao Visual preparado para examinar o novo local da página inicial.  
  
## <a name="file-copy-deployment"></a>Implantação de cópia de arquivo  
 Você não precisa criar um arquivo. VSIX para implantar uma página de início personalizados. Em vez disso, você pode copiar a marcação e arquivos de suporte diretamente para a pasta do usuário \StartPages\. O **Personalizar página inicial** lista o **inicialização** opções página lista todos os arquivos. XAML nessa pasta, junto com o caminho — por exemplo, %USERPROFILE%\My Documents\Visual Studio *versão*\StartPages\\*nome do arquivo*. XAML. Se a página inicial inclui referências a assemblies particulares, você deve copiá-los e colá-los na pasta \PrivateAssemblies\.  
  
 Para distribuir uma página inicial que você criou sem embalagem-lo em um arquivo. VSIX, recomendamos que você use uma estratégia de cópia de arquivo básico, por exemplo, um script em lotes ou qualquer outra tecnologia de implantação que permite que você coloque os arquivos nos diretórios necessários.  
  
#### <a name="to-manually-install-a-custom-start-page"></a>Para instalar manualmente uma página de início personalizado  
  
1.  Copie o arquivo. XAML que contém a marcação de página inicial, junto com quaisquer arquivos de suporte que não seja de assemblies e colá-los na pasta de \StartPages\ do usuário.  
  
2.  Se a página de início requer que os assemblies, copiá-los e colá-los em... \\ *Pasta de instalação do visual Studio*\Common7\IDE\PrivateAssemblies\\.  
  
3.  No **Personalizar página inicial** lista o **inicialização** opções, selecione a nova página inicial. Para obter mais informações, consulte [Personalizando a página Iniciar](../ide/customizing-the-start-page-for-visual-studio.md).  
  
## <a name="see-also"></a>Consulte também  
 [Personalizando a página inicial](../ide/customizing-the-start-page-for-visual-studio.md)   
 [Adicionar o controle de usuário para a página inicial](../extensibility/adding-user-control-to-the-start-page.md)
