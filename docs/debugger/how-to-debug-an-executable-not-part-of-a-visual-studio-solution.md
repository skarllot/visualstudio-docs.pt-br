---
title: "Como depurar um execut&#225;vel que n&#227;o fa&#231;a parte de uma solu&#231;&#227;o do Visual Studio | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
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
  - "JScript"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "depurando [Visual Studio], executáveis"
  - "arquivos executáveis, depurando fora de projetos"
  - "arquivos executáveis, importando"
ms.assetid: 3ea176e8-1ce5-42c4-b7a2-abe3a2765033
caps.latest.revision: 23
caps.handback.revision: 23
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Como depurar um execut&#225;vel que n&#227;o fa&#231;a parte de uma solu&#231;&#227;o do Visual Studio
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Às vezes, convém depurar um executável que não é parte de um projeto [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  Pode ser um executável criado fora do [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ou um executável que você recebeu de outra pessoa.  
  
 A resposta usual para esse problema é iniciar a parte externa executável do Visual Studio e anexá\-la a ele usando o depurador [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  Para obter mais informações, consulte[Anexar a processos em execução](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).  
  
 Anexar a um aplicativo requer algumas etapas manuais, por isso demora alguns segundos.  Este pequeno atraso significa que a anexação não ajudará se você estiver tentando depurar um problema que ocorre durante a inicialização.  Além disso, se você estiver depurando um programa que não aguarda a entrada do usuário, e fecha rapidamente, você poderá não ter tempo para anexar a ele.  Se você tiver o [!INCLUDE[vcprvc](../debugger/includes/vcprvc_md.md)] instalado, poderá criar um projeto EXE para tal programa.  
  
### Para criar um projeto EXE para um executável existente  
  
1.  No menu **Arquivo**, clique em **Abrir** e selecione **Projeto**.  
  
2.  Na caixa de diálogo **Abrir Projeto**, clique na lista suspensa ao lado da caixa **Nome do arquivo** e selecione **Todos os Arquivos de Projeto**.  
  
3.  Localize o executável e clique em **OK**.  
  
     Isso cria uma solução temporária que contém o executável.  
  
### Para importar um executável em uma solução do Visual Studio  
  
1.  No menu **Arquivo**, aponte para **Adicionar Projeto** e depois clique em **Projeto Existente**.  
  
2.  Na caixa de diálogo **Adicionar Projeto Existente**, clique na lista suspensa ao lado da caixa **Nome do arquivo** e selecione **Todos os Arquivos de Projeto**.  
  
3.  Localize e selecione o executável.  
  
4.  Clique em **OK**.  
  
5.  Inicie o executável escolhendo um comando de execução, como **Iniciar**, no menu **Depurar**.  
  
    > [!NOTE]
    >  Nem todas as linguagens de programação oferecem suporte a projetos EXE.  Instale o [!INCLUDE[vcprvc](../debugger/includes/vcprvc_md.md)] se precisar usar esse recurso.  
  
     Quando você estiver depurando um executável sem código\-fonte, os recursos de depuração disponíveis serão limitados, independente de você anexar a um executável em execução ou adicionar o executável a uma solução do [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  Se o arquivo executável for compilado sem informações de depuração em um formato compatível, os recursos disponíveis serão mais limitados.  Se você tiver o código\-fonte, a melhor abordagem será importar o código\-fonte para o [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] e criar uma compilação de depuração do executável no [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
## Consulte também  
 [Configurações de depuração e preparação](../debugger/debugger-settings-and-preparation.md)   
 [Segurança do depurador](../debugger/debugger-security.md)   
 [DBG Files](http://msdn.microsoft.com/pt-br/91e449e9-8b65-4123-960f-2107cd1f1cfd)