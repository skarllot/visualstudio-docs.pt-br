---
title: 'Como: criar um. Arquivo VSCT | Documentos do Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- VSCT files, creating
ms.assetid: b955f51c-f9f9-49c3-a8e4-63b6eb0e0341
caps.latest.revision: 19
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
ms.openlocfilehash: 24a0ebc360b10436119bf408ef72ef0fb01f306b
ms.lasthandoff: 02/22/2017

---
# <a name="how-to-create-a-vsct-file"></a>Como: criar um. Arquivo VSCT
Há várias maneiras de criar um arquivo de configuração (VSCT) da tabela de comando baseada em XML Visual Studio.  
  
-   Você pode criar um novo VSPackage no [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] modelo de pacote.  
  
-   Você pode usar o compilador de configuração de tabela do comando baseado em XML, Vsct.exe, para gerar um arquivo de um arquivo .ctc existente.  
  
-   Você pode usar Vsct.exe para gerar um arquivo. VSCT de um arquivo .cto existente.  
  
-   Você pode criar manualmente um novo arquivo. VSCT.  
  
 Este tópico explica como criar manualmente um novo arquivo. VSCT.  
  
### <a name="to-manually-create-a-new-vsct-file"></a>Para criar manualmente um novo arquivo. VSCT  
  
1.  Inicie o [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
2.  Sobre o **arquivo** , aponte para **novo**e, em seguida, clique em **arquivo**.  
  
3.  No **modelos** painel, clique em **arquivo XML** e, em seguida, clique em **abrir**.  
  
4.  Sobre o **exibição** menu, clique em **janela propriedades** para exibir as propriedades do arquivo XML.  
  
5.  No **propriedades** janela, clique no botão Procurar (...) na propriedade esquemas.  
  
6.  Na lista de esquemas XSD, selecione o esquema de vsct.xsd. Se não estiver na lista, clique em **adicionar** e, em seguida, localize o arquivo em uma unidade local. Clique em **Okey** quando tiver terminado.  
  
7.  No arquivo XML, digite `<CommandTable` e pressione TAB. A marca de fechamento digitando `>`.  
  
     Isso cria um arquivo. VSCT básica.  
  
8.  Preencha os elementos do arquivo XML que você deseja adicionar, de acordo com o [VSCT esquema](../../extensibility/vsct-xml-schema-reference.md). Para obter mais informações, consulte [criação. Arquivos de VSCT](../../extensibility/internals/authoring-dot-vsct-files.md)  
  
## <a name="compiling-the-code"></a>Compilando o código  
 Simplesmente adicionando um arquivo. VSCT para um projeto não causa compilá-lo. Você deve incorporá-lo no processo de compilação.  
  
### <a name="to-add-a-vsct-file-to-project-compilation"></a>Para adicionar um arquivo. VSCT para compilação de projeto  
  
1.  Abra o arquivo de projeto no editor. Se o projeto for carregado, você deve descarregá-lo primeiro.  
  
2.  Adicionar uma [elemento ItemGroup](../../msbuild/itemgroup-element-msbuild.md) que contém um elemento VSCTCompile, conforme mostrado no exemplo a seguir.  
  
    ```xml  
    <ItemGroup>  
      <VSCTCompile Include="TopLevelMenu.vsct">  
        <ResourceName>Menus.ctmenu</ResourceName>  
      </VSCTCompile>  
    </ItemGroup>  
  
    ```  
  
     O elemento ResourceName deve sempre ser definido como `Menus.ctmenu`.  
  
3.  Se seu projeto contém um arquivo. resx, adicione um elemento EmbeddedResource que contém um elemento MergeWithCTO, conforme mostrado no exemplo a seguir.  
  
    ```xml  
    <EmbeddedResource Include="VSPackage.resx">  
      <MergeWithCTO>true</MergeWithCTO>  
      <ManifestResourceName>VSPackage</ManifestResourceName>  
    </EmbeddedResource>  
  
    ```  
  
     Essa marcação deve ir dentro do elemento ItemGroup que contém recursos incorporados.  
  
4.  Abra o arquivo de pacote, geralmente chamado *ProjectName*Package.cs ou *ProjectName*Package.vb no editor.  
  
5.  Adicione um atributo ProvideMenuResource à classe de pacote, conforme mostrado no exemplo a seguir.  
  
    ```c#  
    [ProvideMenuResource("Menus.ctmenu", 1)]  
    ```  
  
     O primeiro valor do parâmetro deve corresponder ao valor do atributo ResourceName definido no arquivo de projeto.  
  
## <a name="see-also"></a>Consulte também  
 [Criação de páginas. Arquivos de VSCT](../../extensibility/internals/authoring-dot-vsct-files.md)   
 [Tabela de comando do Visual Studio (. Arquivos de VSCT)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)   
 [Como: criar um. Arquivo VSCT de uma já existente. Arquivos CTC](../../misc/how-to-create-a-dot-vsct-file-from-an-existing-dot-ctc-file.md)   
 [Como: criar um. Arquivo VSCT de uma já existente. Arquivo CTO](../../misc/how-to-create-a-dot-vsct-file-from-an-existing-dot-cto-file.md)   
 [Referência de esquema XML VSCT](../../extensibility/vsct-xml-schema-reference.md)
