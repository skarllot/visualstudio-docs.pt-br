---
title: "Adicionando ícones a comandos de Menu | Documentos do Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- icons [Visual Studio], adding to toolbars
- toolbars [Visual Studio], adding icons to commands
- commands [Visual Studio], adding icons
ms.assetid: 362a0c7e-5729-4297-a83f-1aba1a37fd44
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
ms.openlocfilehash: 7f6bbd0b40a66b89998a95af7e7d8043849ff0c8
ms.lasthandoff: 02/22/2017

---
# <a name="adding-icons-to-menu-commands"></a>Adicionando ícones a comandos de Menu
Comandos podem aparecer nos menus e barras de ferramentas. Na barra de ferramentas, é comum para um comando a ser exibido com apenas um ícone (para economizar espaço) ao mesmo tempo em menus que um comando normalmente aparece com um ícone e texto.  
  
 Ícones são 16 pixels de largura por 16 pixels de altura e podem ser a intensidade de cor de 8 bits (256 cores) ou intensidade de cor de 32 bits (cor true). ícones de cor de&32; bits são preferenciais. Ícones normalmente são organizados em uma única linha horizontal em um único bitmap, embora vários bitmaps são permitidos. Esse bitmap é declarado no arquivo. VSCT juntamente com os ícones individuais disponíveis no bitmap. Consulte a referência para o [Bitmaps elemento](../extensibility/bitmaps-element.md) para obter mais detalhes.  
  
## <a name="adding-an-icon-to-a-command"></a>Adicionando um ícone para um comando  
 O procedimento a seguir pressupõe que você tenha um projeto de VSPackage existente com um comando de menu. Para saber como fazer isso, consulte [criando uma extensão com um comando de Menu](../extensibility/creating-an-extension-with-a-menu-command.md).  
  
1.  Crie um bitmap com uma profundidade de cores de 32 bits. Um ícone é sempre 16x16 para que esse bitmap deve ser 16 pixels de altura e um múltiplo de 16 pixels de largura.  
  
     Cada ícone é colocado no bitmap próximos uns dos outros em uma única linha. Use o canal alfa para indicar locais de transparência em cada ícone.  
  
     Se você usar uma profundidade de cores de 8 bits, use magenta, `RGB(255,0,255)`, como a transparência. No entanto, os ícones de cor de 32 bits são preferenciais.  
  
2.  Copie o arquivo de ícone para o diretório de recursos em seu projeto de VSPackage. No Solution Explorer, adicione o ícone ao projeto. (Selecionar recursos, no menu de contexto, clique em Adicionar, clique em seguida Item existente e selecione o arquivo de ícone.)  
  
3.  Abra o arquivo. VSCT no editor.  
  
4.  Adicionar uma `GuidSymbol` elemento com um nome de **testIcon**. Criar um GUID (**ferramentas / criar GUID**, em seguida, selecione **formato do registro** e clique em Copiar) e cole-a na `value` atributo. O resultado deve ter esta aparência:  
  
    ```xml  
    <!-- Create your own GUID -->  
    <GuidSymbol name="testIcon" value="{00000000-0000-0000-0000-0000}">  
    ```  
  
5.  Adicione um `<IDSymbol>` para o ícone. O `name` atributo é a ID do ícone e o `value` indica sua posição na fita, se houver. Se houver apenas um ícone, adicione 1. O resultado deve ter esta aparência:  
  
    ```xml  
    <!-- Create your own GUID -->  
    <GuidSymbol name="testIcon" value="{00000000-0000-0000-0000-0000}">  
        <IDSymbol name="testIcon1" value="1" />  
    </GuidSymbol>  
    ```  
  
6.  Criar um `<Bitmap>` no `<Bitmaps>` seção do arquivo. VSCT para representar o bitmap que contém os ícones.  
  
    -   Definir o `guid` valor para o nome do `<GuidSymbol>` elemento que você criou na etapa anterior.  
  
    -   Definir o `href` valor para o caminho relativo do arquivo de bitmap (neste caso **recursos\\<icon file=""></icon>\>**.  
  
    -   Definir o `usedList` valor para o IDSymbol que você criou anteriormente. Esse atributo especifica uma lista delimitada por vírgulas dos ícones a serem usados em VSPackage. Ícones não está na lista são excluídos do formulário de compilação.  
  
         O bloco de Bitmap deve ter esta aparência:  
  
        ```xml  
        <Bitmap guid="testIcon" href="Resources\<icon file name>" usedList="testIcon1"/>  
        ```  
  
7.  Existentes no `<Button>` elemento, defina o `Icon` elemento para os valores de GUIDSymbol e IDSymbol que você criou anteriormente. Aqui está um exemplo de um elemento de botão com esses valores:  
  
    ```xml  
    <Button guid="guidAddIconCmdSet" id="cmdidMyCommand" priority="0x0100" type="Button">  
        <Parent guid="guidAddIconCmdSet" id="MyMenuGroup" />  
        <Icon guid="testIcon" id="testIcon1" />  
        <Strings>  
            <ButtonText>My Command name</ButtonText>  
        </Strings>  
    </Button>  
    ```  
  
8.  O ícone de teste. Compile o projeto e iniciar a depuração. Na instância experimental, localize o comando. Ele deve mostrar o ícone adicionado.  
  
## <a name="see-also"></a>Consulte também  
 [Estendendo Menus e comandos](../extensibility/extending-menus-and-commands.md)   
 [Referência de esquema XML VSCT](../extensibility/vsct-xml-schema-reference.md)
