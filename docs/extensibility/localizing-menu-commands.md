---
title: Localizando os comandos de Menu | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- localize
- localization
- vsct
- menu commands
- localize visual studio
- localize vsct
ms.assetid: b04ee0f6-82ea-47e6-853a-72382267d6da
caps.latest.revision: 11
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
ms.translationtype: MT
ms.sourcegitcommit: 4a36302d80f4bc397128e3838c9abf858a0b5fe8
ms.openlocfilehash: 13910907c6041884cc0a1414fd0bfd82757a7639
ms.contentlocale: pt-br
ms.lasthandoff: 09/26/2017

---
# <a name="localizing-menu-commands"></a>Localizando os comandos de Menu
Você pode fornecer o texto localizado para o menu e barra de ferramentas comandos por meio da criação de arquivos. VSCT localizada e localizados os arquivos. resx para seu VSPackage e, em seguida, atualizar os arquivos de projeto incorporar as alterações.  
  
 Para obter informações sobre como localizar a experiência de instalação, consulte [Localizando VSIX pacotes](../extensibility/localizing-vsix-packages.md).  
  
## <a name="localizing-command-names"></a>Localizando os nomes de comando  
 VSPackages, comandos de menu e botões de barra de ferramentas são definidas no arquivo. VSCT.  
  
1.  Em **Solution Explorer**, altere o nome do arquivo. VSCT do *filename*. VSCT para *filename*.en US.vsct.  
  
2.  Faça uma cópia do *filename*.en-US.vsct para cada idioma de localizado.  
  
     Nome de cada cópia *filename*.* Localidade*. VSCT, onde *localidade* é um nome de cultura específica. Para obter uma lista de valores de nome de cultura, consulte [IDs de localidade atribuídas pela Microsoft](https://msdn.microsoft.com/en-us/library/windows/apps/jj657969.aspx).  
  
     Essas *filename*.* Localidade*arquivos. VSCT conterá o texto do menu localizada para o seu pacote.  
  
3.  Abrir cada *filename*.* Localidade*arquivo. VSCT para localizar o texto.  
  
    1.  Modificar o [ButtonText](../extensibility/buttontext-element.md) elemento valores conforme apropriado para o idioma específico.  
  
    2.  Se você fornecerá ícones localizadas, modifique o [Bitmap](../extensibility/bitmap-element.md) valores para apontar para os arquivos de destino.  
  
     O exemplo a seguir mostra o texto do botão espanhol e inglês de um comando Abrir uma janela de ferramenta do Gerenciador de árvore de família.  
  
     [FamilyTree.en-US.vsct]  
  
    ```xml  
    <Button guid="guidLocalizedPackageCmdSet" id="cmdidFamilyTree" priority="0x0100" type="Button">  
      <Parent guid="guidSHLMainMenu" id="IDG_VS_WNDO_OTRWNDWS1"/>  
      <Icon guid="guidImages" id="bmpPic2" />  
      <Strings>  
        <CommandName>cmdidFamilyTree</CommandName>  
        <ButtonText>Family Tree Explorer</ButtonText>  
      </Strings>  
    </Button>  
    ```  
  
     [FamilyTree.es-ES.vsct]  
  
    ```xml  
    <Button guid="guidLocalizedPackageCmdSet" id="cmdidFamilyTree" priority="0x0100" type="Button">  
      <Parent guid="guidSHLMainMenu" id="IDG_VS_WNDO_OTRWNDWS1"/>  
      <Icon guid="guidImages" id="bmpPic2" />  
      <Strings>  
        <CommandName>cmdidFamilyTree</CommandName>  
        <ButtonText>Explorar el arbol genealogico</ButtonText>  
      </Strings>  
    </Button>  
  
    ```  
  
## <a name="localizing-other-text-resources"></a>Localizando outros recursos de texto  
 Recursos de texto diferentes nomes de comando são definidos em arquivos de recurso (. resx).  
  
1.  Renomeie VSPackage.resx para VSPackage.en-us.  
  
2.  Faça uma cópia do arquivo VSPackage.en-US para cada idioma localizado.  
  
     Nome de cada cópia VSPackage. *Localidade*. resx, onde *localidade* é um nome de cultura específica.  
  
3.  Renomear resx para Resources.en-us.  
  
4.  Faça uma cópia do arquivo Resources.en-US para cada idioma localizado.  
  
     Nome de cada cópia de recursos. *Localidade*. resx, onde *localidade* é um nome de cultura específica.  
  
5.  Abra cada arquivo. resx para modificar os valores de cadeia de caracteres de acordo com o idioma específico e a cultura. O exemplo a seguir mostra a definição de recurso localizado para a barra de título de uma janela de ferramenta.  
  
     [Resources.en-US]  
  
    ```xml  
    <data name="ToolWindowTitle" xml:space="preserve">  
      <value>Family Tree Explorer</value>  
    </data>  
    ```  
  
     [Resources.es-ES.resx]  
  
    ```xml  
    <data name="ToolWindowTitle" xml:space="preserve">  
      <value>Explorador del arbol genealogico</value>  
    </data>  
  
    ```  
  
## <a name="incorporating-localized-resources-into-the-project"></a>A incorporação de recursos localizados no projeto  
 Você deve modificar o arquivo assemblyinfo.cs e o arquivo de projeto para incorporar os recursos localizados.  
  
1.  Do **propriedades** nó **Solution Explorer**, abra assemblyinfo.cs ou AssemblyInfo. vb no editor.  
  
2.  Adicione a seguinte entrada.  
  
    ```csharp  
    [assembly: NeutralResourcesLanguage("en-US", UltimateResourceFallbackLocation.Satellite)]  
    ```  
  
     Isso define o inglês (EUA) como o idioma padrão.  
  
3.  Descarregue o projeto.  
  
4.  Abra o arquivo de projeto no editor.  
  
5.  Localize o `ItemGroup` elemento que contém `EmbeddedResource` elementos.  
  
6.  No `EmbeddedResource` elemento que chama VSPackage.en-US, substitua o `ManifestResourceName` elemento com um `LogicalName` elemento, definido como `VSPackage.en-US.Resources`, da seguinte maneira.  
  
    ```xml  
    <EmbeddedResource Include="VSPackage.en-US.resx">  
      <MergeWithCTO>true</MergeWithCTO>  
      <LogicalName>VSPackage.en-US.Resources</LogicalName>  
    </EmbeddedResource>  
    ```  
  
7.  Para cada idioma localizado, copie o `EmbeddedResource` elemento para VsPackage.en-US e defina o **incluir** atributo e **LogicalName** elemento da cópia para a localidade de destino, conforme mostrado no exemplo a seguir exemplo.  
  
8.  Para cada um localizado `VSCTCompile` elemento, adicionar um `ResourceName` elemento que aponta para `Menus.ctmenu`, conforme mostrado no exemplo a seguir.  
  
    ```xml  
    <ItemGroup>  
      <VSCTCompile Include="LocalizedPackage.es-ES.vsct">  
        <ResourceName>Menus.ctmenu</ResourceName>  
      </VSCTCompile>  
    </ItemGroup>  
    ```  
  
9. Salve o arquivo de projeto e recarregar o projeto.  
  
10. Compile o projeto.  
  
     Isso cria um assembly principal e assemblies de recurso para cada idioma. Para obter informações sobre como localizar o processo de implantação, consulte [Localizando VSIX pacotes](../extensibility/localizing-vsix-packages.md)  
  
## <a name="see-also"></a>Consulte também  
 [Comandos e Menus estendendo](../extensibility/extending-menus-and-commands.md)   
 [MenuCommands Vs. OleMenuCommands](../extensibility/menucommands-vs-olemenucommands.md)   
 [Globalizando e localizando aplicativos](../ide/globalizing-and-localizing-applications.md)
