---
title: "Passo a passo: Chamando o SDK do Visual Studio usando a automa&#231;&#227;o | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "explicações passo a passo [Visual Studio SDK] chamando com automação"
ms.assetid: ca4dab48-632c-4c2a-8c84-57c027e37987
caps.latest.revision: 31
caps.handback.revision: 31
manager: "douge"
---
# Passo a passo: Chamando o SDK do Visual Studio usando a automa&#231;&#227;o
Este passo a passo ilustra como criar um suplemento do Visual Studio que consome um serviço do Visual Studio. O suplemento que criar obtém um provedor de serviços e usa\-o para obter um serviço. Você pode usar essa mesma técnica para obter qualquer serviço proffered do Visual Studio. Para obter mais informações sobre os serviços e provedores de serviços, consulte [Usando e fornecer serviços](../extensibility/using-and-providing-services.md). Os procedimentos a seguir demonstram como criar um suplemento e, em seguida, obter um serviço de suplemento.  
  
## Criando um suplemento  
 Nesta seção, você deve criar um suplemento do Visual Studio usando o modelo de projeto Visual Studio Add\-In.  
  
#### Para criar um suplemento  
  
1.  Criar um novo projeto do Visual Studio \(**arquivo\/novo\/projeto**\).  
  
2.  No painel esquerdo do **novo projeto** caixa de diálogo caixa, expanda o **Other Project Types** nó e clique o **extensibilidade** nó. Selecione **Visual Studio em**.  
  
3.  Criar um novo suplemento no projeto chamado `Addin`.  
  
     No [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Add\-In wizard, clique em **próximo**.  
  
4.  Sobre o **Select a Programming Language**  selecione **Criar Suplemento usando o Visual c\#** ou **Criar Suplemento usando o Visual Basic**.  
  
5.  Sobre o **Select an Application Host** selecione **Microsoft Visual Studio \< versão \>**.  
  
6.  No **Insira um nome e descrição** página, digite `MyAddin` no **nome** caixa e `MyAddin Walkthrough` no **Descrição** caixa.  
  
7.  No **Escolher opções de suplemento** página, selecione a opção para um item de menu de ferramentas em **você gostaria de criar o comando barra da interface do usuário para o suplemento?**. Desmarque as outras caixas de seleção.  
  
8.  Aceite todos os outros padrões.  
  
9. Crie a solução e verifique se ele é compilado sem erros.  
  
## Obtenção de um serviço de um suplemento  
 As etapas a seguir irão orientá\-lo por meio da aquisição de um serviço de seu suplemento.  
  
#### Para obter um serviço  
  
1.  Abra o arquivo Connect.cs ou VB e adicione essas linhas para o `using` \(c\#\) ou `Imports` instruções \(Visual Basic\):  
  
     [!CODE [VSSDKAddin#1](../CodeSnippet/VS_Snippets_VSSDK/vssdkaddin#1)]  
  
2.  Clique com botão direito no nó do projeto no **Solution Explorer** e adicionar essas referências .NET:  
  
    ```  
    Microsoft.VisualStudio.OLE.Interop Microsoft.VisualStudio.Shell.Interop  
    ```  
  
3.  Adicione estas linhas de código para o `if(commandName == "Addin.Connect.Addin")` ou `If commandName = "Addin.Connect.Addin" Then` cláusula do `Exec` método:  
  
     [!CODE [VSSDKAddin#2](../CodeSnippet/VS_Snippets_VSSDK/vssdkaddin#2)]  
  
     Esse código converte o objeto de aplicativo atual \(tipo `DTE2`\) em um `IOleServiceProvider`, em seguida, chama `QueryService` para obter o <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell> service. Esse serviço fornece um <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> interface. O <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ShowMessageBox%2A> método exibe uma caixa de mensagem quando o suplemento é executado.  
  
4.  Criar e iniciar o projeto de suplemento no modo de depuração pressionando F5.  
  
     Isso inicia outra instância do [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
5.  No novo [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] instância no **ferramentas** menu, clique em **Addin**. A caixa de mensagem exibirá o seguinte:  
  
    ```  
    MyAddin Inside Addin.Connect  
    ```  
  
## Consulte também  
 [How to: Deactivate and Remove an Add\-In](../Topic/How%20to:%20Deactivate%20and%20Remove%20an%20Add-In.md)