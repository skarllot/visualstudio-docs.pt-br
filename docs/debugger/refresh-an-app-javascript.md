---
title: "Atualizar um aplicativo (JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "depuração, atualizando páginas [aplicativos da Windows Store]"
  - "DOM Explorer, Atualizar [aplicativos da Windows Store]"
  - "Depuração de JavaScript, atualizando páginas [aplicativos da Windows Store]"
  - "Atualizar [aplicativos da Windows Store]"
ms.assetid: fd99ee60-fa94-46df-8b17-369f60bfd908
caps.latest.revision: 20
caps.handback.revision: 20
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Atualizar um aplicativo (JavaScript)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

![Applies to Windows and Windows Phone](../debugger/media/windows_and_phone_content.png "windows\_and\_phone\_content")  
  
 Você pode fazer alterações no código durante a depuração e depois atualizar um aplicativo da Windows Store usando JavaScript escolhendo o botão **Atualizar Aplicativo do Windows**, na barra de ferramentas **Depurar**.  Dessa forma, o aplicativo é recarregado sem parar e reiniciar o depurador.  O recurso Atualizar permite que você modifique o código HTML, CSS e JavaScript e veja rapidamente o resultado.  Este recurso tem suporte para os dois aplicativos da Windows Store e da Windows Phone Store.  
  
 A atualização não mantém o estado do aplicativo nem reflete as seguintes alterações feitas no aplicativo:  
  
-   Alterações no arquivo de manifesto do pacote, inclusive nas imagens especificadas no manifesto do pacote.  
  
-   Alterações em referências, como a adição ou a remoção de uma referência de SDK, ou alterações nos componentes do Tempo de Execução do Windows \(arquivos .winmd\).  
  
-   Alterações em recursos, como as efetuadas nas cadeias de caracteres dos arquivos .resjson.  
  
-   Alterações em arquivos de projeto que resultam em mudanças de nome de caminho, novos arquivos de projeto ou arquivos excluídos.  
  
-   Alterações em propriedades de projetos e de itens, como as feitas no dispositivo de depuração selecionado, ou alterações na ação de pacote para um arquivo \(na janela Propriedades\).  
  
> [!IMPORTANT]
>  Ao alterar referências, alterar o manifesto do pacote ou fazer outras alterações especificadas na lista anterior, você precisa interromper e reiniciar o depurador para atualizar os arquivos de origem HTML, CSS e JavaScript.  
  
### Para atualizar um aplicativo  
  
1.  No Visual Studio, crie um novo projeto usando o modelo de projeto do Aplicativo de Navegação.  
  
     Este pode ser um aplicativo da Windows Store, da Windows Phone Store ou um aplicativo universal.  
  
2.  Com o modelo aberto no Visual Studio, escolha um destino de depuração.  
  
     Se um projeto do Windows Phone for seu projeto de inicialização atual, selecione o emulador do Windows Phone para o destino de depuração.  Do contrário, selecione **Simulador** ou **Computador Local**.  
  
     ![Select debug target list](../debugger/media/js_select_target.png "JS\_Select\_Target")  
  
3.  Pressione F5 para executar o aplicativo no modo de depuração.  
  
4.  Alterne para o Visual Studio.  \(Pressione F12.\)  
  
5.  Em **Gerenciador de Soluções**, na pasta **pages** \> **home**, abra o arquivo home.html.  
  
6.  Altere o texto do título da página, de  
  
    ```html  
    Welcome to yourAppName!  
    ```  
  
     para outra coisa, por exemplo:  
  
    ```html  
    Hello!  
    ```  
  
7.  Clique no botão **Atualizar aplicativo do Windows**, que tem esta aparência: ![Atualizar botão de aplicativo do Windows](~/debugger/media/js_refresh.png "JS\_Refresh").  \(Ou pressione F4.\)  
  
8.  Altere para o aplicativo.  O aplicativo é recarregado sem que o depurador seja reiniciado, e o novo título da página é exibido.  
  
## Consulte também  
 [Guia de início rápido: depurar HTML e CSS](../debugger/quickstart-debug-html-and-css.md)