---
title: "Passo a passo: Criando um servi&#231;o WCF simples no Windows Forms | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "WCF, passo a passo [Visual Studio]"
  - "WCF, o Visual Studio tools para"
  - "Serviços WCF"
  - "Serviços WCF, passo a passo"
ms.assetid: 5fef1a64-27a4-4f10-aa57-29023e28a2d6
caps.latest.revision: 25
caps.handback.revision: 25
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Passo a passo: Criando um servi&#231;o WCF simples no Windows Forms
Este passo a passo demonstra como criar um simples [!INCLUDE[vsindigo](../data-tools/includes/vsindigo_md.md)] de serviço, testá\-lo e, em seguida, acessá\-lo de um aplicativo Windows Forms.  
  
 [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
## Criando o serviço  
  
#### Para criar um serviço WCF  
  
1.  Sobre o **arquivo** aponte para **novo** e, em seguida, clique em **projeto**.  
  
2.  No **novo projeto** caixa de diálogo caixa, expanda o **Visual Basic** ou **Visual C\#** nó e clique em **WCF**, seguido por **WCF Service Library**. Clique em **OK** para abrir o projeto.  
  
     ![The WCF Service Library project](../data-tools/media/wcf1.PNG "wcf1")  
  
    > [!NOTE]
    >  Isso cria um serviço de trabalho que pode ser testado e acessado. As duas etapas a seguir demonstram como você pode modificar o método padrão para usar um tipo de dados diferente. Em um aplicativo real, você também poderia adicionar suas próprias funções para o serviço.  
  
3.  ![The IService1 file](../data-tools/media/wcf2.png "wcf2")  
  
     Em **Solution Explorer**, clique duas vezes em Iservice1 ou IService1. cs e localize a seguinte linha:  
  
     [!code-cs[WCFWalkthrough#4](../data-tools/codesnippet/CSharp/walkthrough-creating-a-simple-wcf-service-in-windows-forms_1.cs)]
     [!code-vb[WCFWalkthrough#4](../data-tools/codesnippet/VisualBasic/walkthrough-creating-a-simple-wcf-service-in-windows-forms_1.vb)]  
  
     Alterar o tipo para o `value` parâmetro para `String`:  
  
     [!code-cs[WCFWalkthrough#1](../data-tools/codesnippet/CSharp/walkthrough-creating-a-simple-wcf-service-in-windows-forms_2.cs)]
     [!code-vb[WCFWalkthrough#1](../data-tools/codesnippet/VisualBasic/walkthrough-creating-a-simple-wcf-service-in-windows-forms_2.vb)]  
  
     No código acima, observe o `<OperationContract()>` ou `[OperationContract]` atributos. Esses atributos são obrigatórios para qualquer método exposto pelo serviço.  
  
4.  ![The Service1 file](../data-tools/media/wcf3.png "wcf3")  
  
     Em **Solution Explorer**, clique duas vezes em Service1. vb ou Service1. cs e localize a seguinte linha:  
  
     [!code-vb[WCFWalkthrough#5](../data-tools/codesnippet/VisualBasic/walkthrough-creating-a-simple-wcf-service-in-windows-forms_3.vb)]
     [!code-cs[WCFWalkthrough#5](../data-tools/codesnippet/CSharp/walkthrough-creating-a-simple-wcf-service-in-windows-forms_3.cs)]  
  
     Alterar o tipo para o parâmetro de valor para `String`:  
  
     [!code-cs[WCFWalkthrough#2](../data-tools/codesnippet/CSharp/walkthrough-creating-a-simple-wcf-service-in-windows-forms_4.cs)]
     [!code-vb[WCFWalkthrough#2](../data-tools/codesnippet/VisualBasic/walkthrough-creating-a-simple-wcf-service-in-windows-forms_4.vb)]  
  
## O serviço de teste  
  
#### Para testar um serviço WCF  
  
1.  Pressione **F5** para executar o serviço. Um **cliente de teste do WCF** formulário será exibido e ele carregará o serviço.  
  
2.  No **cliente de teste do WCF** de formulário, clique duas vezes o **GetData** método sob **IService1**. O **GetData** guia será exibida.  
  
     ![The GetData&#40;&#41; method](../data-tools/media/wcf4.png "wcf4")  
  
3.  No **solicitação** caixa, selecione a **valor** campo e digite `Hello`.  
  
     ![The Value field](../data-tools/media/wcf5.png "wcf5")  
  
4.  Clique o **Invoke** botão. Se um **Aviso de segurança** caixa de diálogo for exibida, clique em **OK**. O resultado será exibido no **resposta** caixa.  
  
     ![The result in the Response box](../data-tools/media/wcf6.png "wcf6")  
  
5.  Sobre o **arquivo** menu, clique em **Exit** para fechar o formulário de teste.  
  
## Acessando o serviço  
  
#### Para fazer referência a um serviço WCF  
  
1.  Sobre o **arquivo** aponte para **Add** e, em seguida, clique em **novo projeto**.  
  
2.  No **novo projeto** caixa de diálogo caixa, expanda o **Visual Basic** ou **Visual C\#** nó e selecione **Windows**, e, em seguida, selecione **Windows Forms Application**. Clique em **OK** para abrir o projeto.  
  
     ![Windows Forms Application project](../data-tools/media/wcf7.png "wcf7")  
  
3.  Clique com botão direito **WindowsApplication1** e clique em **Add Service Reference**. O **Add Service Reference** caixa de diálogo será exibida.  
  
4.  No **Add Service Reference** caixa de diálogo, clique em **Discover**.  
  
     ![The Add Service Reference dialog box](../data-tools/media/wcf8.png "wcf8")  
  
     **Service1** será exibido no **serviços** painel.  
  
5.  Clique em **OK** para adicionar a referência de serviço.  
  
#### Para criar um aplicativo cliente  
  
1.  Em **Solution Explorer**, clique duas vezes em **Form1. vb** ou **Form1. CS** para abrir o Designer de formulários do Windows, se ele não ainda estiver aberto.  
  
2.  Do **Toolbox**, arraste um `TextBox` controle, um `Label` controle e um `Button` controle para o formulário.  
  
     ![Adding controls to the form](../data-tools/media/wcf9.png "wcf9")  
  
3.  Clique duas vezes o `Button`, e adicione o seguinte código no `Click` manipulador de eventos:  
  
     [!code-cs[WCFWalkthrough#3](../data-tools/codesnippet/CSharp/walkthrough-creating-a-simple-wcf-service-in-windows-forms_5.cs)]
     [!code-vb[WCFWalkthrough#3](../data-tools/codesnippet/VisualBasic/walkthrough-creating-a-simple-wcf-service-in-windows-forms_5.vb)]  
  
4.  Em **Solution Explorer**, clique com botão direito **WindowsApplication1** e clique em **Set as StartUp Project**.  
  
5.  Pressione **F5** para executar o projeto. Digite algum texto e clique no botão. Exibirá o rótulo "você digitou:" e o texto que você inseriu.  
  
     ![The form showing the result](../data-tools/media/wcf10.png "wcf10")  
  
## Consulte também  
 [Serviços do Windows Communication Foundation e WCF Data Services no Visual Studio](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md)