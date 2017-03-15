---
title: "Colocando um controle de usu&#225;rio em uma janela de ferramenta | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "janelas de ferramentas, adicionando controles de usuário"
  - "controles de usuário [Visual Studio SDK], adicionando a janelas de ferramenta"
  - "controles de usuário [SDK do Visual Studio]"
ms.assetid: 869f3195-e152-4e61-802c-51d6b7ba3e36
caps.latest.revision: 29
caps.handback.revision: 29
manager: "douge"
---
# Colocando um controle de usu&#225;rio em uma janela de ferramenta
Este passo a passo demonstra como adicionar um controle de usuário para uma janela de ferramenta.  
  
 Um controle de usuário é uma coleção de controles do Windows ligadas em um controle. Para adicionar um controle de usuário para uma janela da ferramenta, tudo o que você realmente precisa fazer é ter o controle de usuário na **Toolbox**. O controle de usuário que é usado neste passo a passo é o controle de relógio desenvolvido em [Instruções passo a passo: criando um controle composto com o Visual C\#](../Topic/Walkthrough:%20Authoring%20a%20Composite%20Control%20with%20Visual%20C%23.md).  
  
## Pré-requisitos  
 Para seguir este passo a passo, você deve instalar o SDK do Visual Studio. Para obter mais informações, consulte [SDK do Visual Studio](../extensibility/visual-studio-sdk.md).  
  
## Criando o controle de usuário  
  
1.  Siga as etapas em [Instruções passo a passo: criando um controle composto com o Visual C\#](../Topic/Walkthrough:%20Authoring%20a%20Composite%20Control%20with%20Visual%20C%23.md) para criar o controle de relógio. Não crie o controle de relógio do alarme.  
  
> [!NOTE]
>  As etapas a seguir pressupõem que você nomeou o controle de relógio `ctlClock`.  
  
## Criando uma extensão da janela de ferramenta  
  
1.  Crie um projeto do VSIX chamado `MyToolWindowPackageUC` que tem uma janela de ferramenta chamada `MyToolWindow`. Se você precisar de ajuda para fazer isso, consulte [Criando uma extensão com uma janela de ferramentas](../extensibility/creating-an-extension-with-a-tool-window.md).  
  
## Adicionando o controle de usuário  
  
1.  Em **Solution Explorer**, com o botão direito na solução **MyToolWindowPackageUC**, aponte para **Add**, e, em seguida, clique em **projeto existente**.  
  
2.  No **Adicionar projeto existente** caixa de diálogo, abra o projeto ctlClockLib e selecione o arquivo de projeto ctlClock.lib.csproj. Clique em **OK**. Isso permite que o controle de usuário que você pode usar no designer.  
  
3.  Em **Solution Explorer**, MyToolWindowControl.cs e selecione **View Designer**. Isso abre o designer de formulários que mostra o controle gerado para a janela da ferramenta.  
  
4.  Abra o **Toolbox**, localize a seção rotulada **ctlClockLib componentes** e clique duas vezes o **ctlClock** controle nessa seção para adicionar o controle ao formulário. Tão logo você ocultar o **Toolbox**, você deve ver um tempo exibir em seu formulário de janela de ferramenta.  
  
5.  No designer, selecione o controle de relógio que acabou de adicionar e alterar o **âncora** propriedade simplesmente estar **superior**.  
  
6.  Em **Solution Explorer**, com o botão direito no nó do projeto ctlClockLib e, em seguida, clique em **propriedades**.  
  
7.  Sobre o **assinatura** selecione **assinar o assembly**. No **Escolher um arquivo de chave de nome forte** clique em **\< procurar \>** e navegue até o arquivo key.snk no **MyToolWindowPackageUC** a pasta do projeto.  
  
8.  Compile o programa e verifique se que não existem erros. Esta etapa registra o VSPackage e sua janela de ferramenta com o Visual Studio.  
  
9. Pressione F5 para abrir uma instância do Visual Studio no hive experimental.  
  
10. No Visual Studio experimental, sobre o **exibição** aponte para **outras janelas** e, em seguida, clique em **MyToolWindow**. Isso exibe a janela de ferramenta, que tem um tempo de execução a exibir.  
  
## Consulte também  
 [Instruções passo a passo: criando um controle composto com o Visual C\#](../Topic/Walkthrough:%20Authoring%20a%20Composite%20Control%20with%20Visual%20C%23.md)