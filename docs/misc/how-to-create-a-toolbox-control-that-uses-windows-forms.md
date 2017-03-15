---
title: "Como: criar um controle de caixa de ferramentas que usa o Windows Forms | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Controle de caixa de ferramentas"
  - "WinForms"
  - "caixa de ferramentas"
ms.assetid: abbd3c3c-3a6e-4539-bd6c-a5891dead234
caps.latest.revision: 12
caps.handback.revision: 12
manager: "douge"
---
# Como: criar um controle de caixa de ferramentas que usa o Windows Forms
O modelo de controle de caixa de ferramentas do Windows Forms que está incluído no [!INCLUDE[vssdk_dev11_long](../misc/includes/vssdk_dev11_long_md.md)] permite que você crie controles de formulários do Windows que são adicionados automaticamente ao **Toolbox** quando a extensão é instalada. Este tópico mostra como usar o modelo para criar um **Toolbox** controle que você pode distribuir para outros usuários...  
  
> [!NOTE]
>  Para saber como baixar o SDK do Visual Studio, consulte [Visual Studio Extensibility Developer Center](http://go.microsoft.com/fwlink/?linkid=121964) no site do MSDN.  
  
## Criando um controle de caixa de ferramentas  
 Use o modelo de controle de caixa de ferramentas do Windows Forms para criar o projeto e, em seguida, criar uma interface do usuário \(IU\) no designer.  
  
#### Para criar um projeto de controle de caixa de ferramentas do Windows Forms  
  
1.  Sobre o **arquivo** menu, clique em **novo**, e, em seguida, clique em **projeto**.  
  
2.  No **novo projeto** caixa de diálogo **modelos instalados**, clique no nó para sua linguagem de programação preferencial e, em seguida, clique em **extensibilidade**. Na lista de tipos de projeto, selecione **controle de caixa de ferramentas do Windows Forms**.  
  
3.  No **nome** digite o nome que você deseja usar para o projeto. Clique em **OK**.  
  
     O Visual Studio cria uma solução que contém um controle de usuário, um atributo para colocar o controle **Toolbox**, e um VSIX de manifesto de implantação.  
  
#### Para criar o controle da interface do usuário  
  
1.  Em **Solution Explorer**, clique duas vezes em ToolboxControl.cs para abri\-lo no designer.  
  
2.  Do **Toolbox**, arraste os controles que você deseja para a superfície de design e organizá\-las de acordo com seu design.  
  
3.  No **propriedades** janela, defina as propriedades públicas no controle de usuário e no filho controles.  
  
## O controle de codificação  
 Por padrão, o controle será exibido no **Toolbox** como **ToolboxControl1** em uma **Toolbox** grupo item com o mesmo nome que sua solução. Você pode alterar esses nomes no arquivo ToolboxControl.cs.  
  
#### Para o controle do código  
  
1.  Em **Solution Explorer**, clique com botão direito ToolboxControl.cs e, em seguida, clique em **Exibir código** para abrir o arquivo no modo de exibição de código.  
  
2.  Na definição da classe parcial que implementa o controle, clique no nome de classe, clique em **Refatorar**, e, em seguida, clique em **Renomear**. Altere o nome da classe para o nome que você deseja exibir no **Toolbox** quando o controle está instalado.  
  
3.  Imediatamente acima da definição de classe, no `ProvideToolboxControl` declaração do atributo, altere o valor do primeiro parâmetro para o nome do grupo de itens que hospedará o controle o **Toolbox**.  
  
     A exemplo a seguir mostra o `ProvideToolboxControl` atributo e a definição da classe ajustado para um controle chamado `Counter` no `General` grupo de itens.  
  
     [!code-cs[ToolboxControlWinForms#07](../misc/codesnippet/CSharp/how-to-create-a-toolbox-control-that-uses-windows-forms_1.cs)]  
  
4.  Implemente as propriedades, métodos e eventos do controle.  
  
## Criação, teste e implantação  
 Pressionando F5 compila o projeto, que inclui um arquivo de implantação. VSIX e abre uma segunda instância do Visual Studio que tem o controle instalado no **Toolbox**.  
  
#### Para compilar e testar o controle  
  
1.  Pressione F5.  
  
2.  Na nova instância do Visual Studio, crie um projeto de aplicativo do Windows Forms.  
  
3.  Localize o controle no **Toolbox** e arraste\-o para a superfície de design.  
  
4.  No **propriedades** janela, verifique se as propriedades aparecem conforme o esperado.  
  
5.  Adicione qualquer código ou controles adicionais que são necessárias para testar seus métodos e eventos.  
  
6.  Pressione F5 para abrir o aplicativo de formulários do Windows.  
  
7.  Verifique se que as propriedades, métodos e eventos do seu controle se comportar conforme o esperado.  
  
#### Para implantar o controle  
  
1.  Depois de criar o projeto testado, abra a pasta \\bin\\debug\\ do projeto no Explorador de arquivos e localize o arquivo. VSIX.  
  
2.  Carregue o arquivo. VSIX em uma rede ou para um site da Web.  
  
     Se você carregar o arquivo para o [Galeria do Visual Studio](http://go.microsoft.com/fwlink/?LinkID=123847) site da Web, outros usuários podem usar **Extension Manager** no Visual Studio para localizar o controle e instalá\-lo.  
  
## Consulte também  
 [Criando um controle de caixa de ferramentas do WPF](../extensibility/creating-a-wpf-toolbox-control.md)