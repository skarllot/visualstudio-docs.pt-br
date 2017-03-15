---
title: "Como depurar um controle ActiveX | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.controls.debug"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "depuração de contêiner do controle ActiveX [Visual Studio]"
  - "Controles ActiveX, depuração"
  - "contêineres, especificando para sessões de depuração"
  - "controles associados a dados, ActiveX"
  - "depurando controles ActiveX"
  - "contêiner de teste"
  - "testando [Visual Studio], Controles ActiveX"
  - "testando [Visual Studio], contêineres de teste"
ms.assetid: bbc02cf7-a7e6-44fe-99af-87a43e1d7251
caps.latest.revision: 16
caps.handback.revision: 16
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Como depurar um controle ActiveX
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

> [!NOTE]
>  As caixas de diálogo e os comandos de menu que você vê podem ser diferentes dos descritos na Ajuda, dependendo da sua edição ou das configurações ativas.  Para alterar as configurações, escolha Importar e Exportar Configurações no menu Ferramentas.  Para obter mais informações, consulte [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/pt-br/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
 Para depurar seu controle ActiveX, você deverá especificar um contêiner \(executável\) em que o controle será executado.  
  
### Para especificar um contêiner para a sessão de depuração  
  
1.  No Gerenciador de Soluções, selecione o projeto.  
  
2.  No menu **Exibir**, escolha **Páginas de Propriedades**.  
  
3.  Na caixa de diálogo **Páginas de Propriedades de Projeto**, abra a pasta **Propriedades de Configuração** e selecione **Depurando**.  
  
4.  Na categoria **Depurando**, localize a propriedade **Comando**.  
  
5.  Especifique o nome do caminho para o contêiner.  Por exemplo, C:\\Arquivos de Programas\\Internet Explorer\\IEXPLORE.EXE.  
  
6.  Se você especificar o Internet Explorer como o contêiner e estiver usando o Active Desktop, digite `/new` na caixa **Argumentos do Comando**.  
  
7.  Clique em **OK**.  
  
     Se você não especificar um contêiner na caixa de diálogo **Páginas de Propriedades do Projeto**, poderá especificar o contêiner quando iniciar a depuração.  Quando você selecionar um comando de execução para iniciar a depuração, a [caixa de diálogo Executável para Sessão de Depuração](../debugger/executable-for-debugging-session-dialog-box.md) é exibida.  Especifique o nome do caminho do contêiner na caixa de diálogo.  
  
## Consulte também  
 [Controles ActiveX](/visual-cpp/mfc/activex-controls)   
 [Testando propriedades e eventos com contêiner de teste](/visual-cpp/mfc/testing-properties-and-events-with-test-container)   
 [Depuração de COM e ActiveX](../debugger/com-and-activex-debugging.md)   
 [Depurando no Visual Studio](../debugger/debugging-in-visual-studio.md)