---
title: "Criando grupos reutilizáveis de botões | Documentos do Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- button groups, creating in VSPackages
- VSPackages, creating reusable button groups
- buttons, creating reusable groups
ms.assetid: 0c561617-fb86-476d-8bd1-c6e5e7464c65
caps.latest.revision: 44
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
ms.openlocfilehash: be0e05b5683fcae6ba5eb7b5e992c702d8a6472b
ms.lasthandoff: 02/22/2017

---
# <a name="creating-reusable-groups-of-buttons"></a>Criando grupos reutilizáveis de botões
Um grupo de comando é uma coleção de comandos que sempre aparecem juntos em um menu ou barra de ferramentas. Qualquer grupo de comando pode ser usado novamente, atribuindo a ela a menus pai diferente na seção do arquivo. VSCT CommandPlacements.  
  
 Comando agrupa normalmente contêm botões, mas também pode conter outros menus ou caixas de combinação.  
  
### <a name="to-create-a-reusable-group-of-buttons"></a>Para criar um grupo de botões de reutilizável  
  
1.  Crie um projeto do VSIX chamado `ReusableButtons`. Para obter mais informações, consulte [criando uma extensão com um comando de Menu](../extensibility/creating-an-extension-with-a-menu-command.md).  
  
2.  Quando o projeto é aberto, adicione um modelo de item de comando personalizada chamado **ReusableCommand**. No **Solution Explorer**, com o botão direito no nó do projeto e selecione **Adicionar / Novo Item**. No **Adicionar Novo Item** caixa de diálogo, vá para **Visual c# / extensibilidade** e selecione **comando personalizado**. No **nome** campo na parte inferior da janela, altere o nome do arquivo de comando para **ReusableCommand.cs**.  
  
3.  No arquivo VSCT, vá para a seção de símbolos e localize o elemento GuidSymbol que contém grupos e comandos para o projeto. Ele deve ser nomeado guidReusableCommandPackageCmdSet.  
  
4.  Adicione um IDSymbol para cada botão que você irá adicionar ao grupo, como no exemplo a seguir.  
  
    ```xml  
    <GuidSymbol name="guidReusableCommandPackageCmdSet" value="{7f383b2a-c6b9-4c1d-b4b8-a26dc5b60ca1}">  
        <IDSymbol name="MyMenuGroup" value="0x1020" />  
        <IDSymbol name="ReusableCommandId" value="0x0100" />  
        <IDSymbol name="SecondReusableCommandId" value="0x0200" />  
    </GuidSymbol>  
    ```  
  
     Por padrão, o modelo de item de comando cria um grupo chamado **MyGroup** e um botão que tem o nome que você forneceu, junto com uma entrada de IDSymbol para cada um.  
  
5.  Na seção grupos, crie um elemento de grupo que tem os mesmos atributos GUID e ID como aqueles fornecidos na seção de símbolos. Você também pode usar um grupo existente ou usar a entrada que é fornecida pelo modelo de comando, como no exemplo a seguir. Esse grupo aparece no **ferramentas** menu  
  
    ```xml  
    <Groups>  
        <Group guid="guidReusableCommandPackageCmdSet" id="MyMenuGroup" priority="0x0600">  
              <Parent guid="guidSHLMainMenu" id="IDM_VS_MENU_TOOLS"/>  
        </Group>  
    </Groups>  
    ```  
  
### <a name="to-create-a-group-of-buttons-for-reuse"></a>Para criar um grupo de botões para reutilização  
  
1.  Você pode colocar um menu ou um comando em um grupo usando o grupo como um pai na definição do comando ou menu ou colocando o comando ou o menu do grupo usando a seção CommandPlacements.  
  
     Na seção botões definir um botão que tenha o grupo como pai, ou use o botão que é fornecido pelo modelo de pacote, conforme mostrado no exemplo a seguir.  
  
    ```xml  
    <Button guid="guidReusableCommandPackageCmdSet" id="ReusableCommandId" priority="0x0100" type="Button">  
        <Parent guid="guidReusableCommandPackageCmdSet" id="MyMenuGroup" />  
        <Icon guid="guidImages" id="bmpPic1" />  
        <Strings>  
            <ButtonText>Invoke ReusableCommand</ButtonText>  
        </Strings>  
    </Button>  
    ```  
  
2.  Se um botão deve aparecer em mais de um grupo, crie uma entrada para ele na seção CommandPlacements, que deve ser colocada após a seção de comandos. Defina os atributos GUID e ID do elemento CommandPlacement para corresponder do botão que você deseja posicionar e, em seguida, defina o GUID e a ID do seu elemento pai do grupo de destino, conforme mostrado no exemplo a seguir.  
  
    ```xml  
    <CommandPlacements>  
        <CommandPlacement guid="guidReusableCommandPackageCmdSet" id="SecondReusableCommandId" priority="0x105">  
          <Parent guid="guidReusableCommandPackageCmdSet" id="MyMenuGroup" />  
        </CommandPlacement>  
    </CommandPlacements>  
    ```  
  
    > [!NOTE]
    >  O valor do campo prioridade determina a posição do comando no novo grupo de comando. Conjunto de prioridades no CommandPlacement elemento substituem aquelas definidas na definição do item. Comandos que têm valores de prioridade inferiores são exibidos antes de comandos que têm valores de prioridade mais alta. Valores de prioridade duplicados são permitidos, mas a posição relativa dos comandos que têm o mesmo valor de prioridade não pode ser garantida porque a ordem na qual o **devenv /setup** comando cria final interface do registro pode não estar consistente.  
  
### <a name="to-put-a-reusable-group-of-buttons-on-a-menu"></a>Colocar um grupo reutilizável de botões em um menu  
  
1.  Criar uma entrada de `CommandPlacements` seção. Definir o GUID e ID o `CommandPlacement` elemento para aqueles de seu grupo e definir o pai GUID e ID do local de destino.  
  
     A seção CommandPlacements deve ser colocada apenas após a seção de comandos:  
  
    ```xml  
    <CommandTable>  
    ...  
      <Commands>... </Commands>  
      <CommandPlacements>... </CommandPlacements>  
    ...   
    </CommandTable>  
    ```  
  
     Um grupo de comando pode ser incluído em mais de um menu. Menu pai pode ser aquele que você criou, que é fornecido pelo [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] (conforme descrito em ShellCmdDef.vsct ou SharedCmdDef.vsct), ou um que é definido em outro VSPackage. O número de camadas paternidade é ilimitado como menu pai está conectado, por fim, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ou um menu de atalho que é exibido por um VSPackage.  
  
     O exemplo a seguir coloca o grupo **Solution Explorer** barra de ferramentas, à direita dos outros botões.  
  
    ```xml  
    <CommandPlacements>  
        <CommandPlacement guid="guidReusableCommandPackageCmdSet" id="MyMenuGroup" priority="0xF00">  
          <Parent guid="guidSHLMainMenu" id="IDM_VS_TOOL_PROJWIN"/>  
        </CommandPlacement>  
    </CommandPlacements>  
    ```  
  
    ```xml  
    <CommandPlacements>  
      <CommandPlacement guid="guidButtonGroupCmdSet" id="MyMenuGroup"   
          priority="0x605">  
        <Parent guid="guidSHLMainMenu" id="IDM_VS_MENU_TOOLS" />  
      </CommandPlacement>  
    </CommandPlacements>  
  
    ```
