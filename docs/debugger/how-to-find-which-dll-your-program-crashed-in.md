---
title: "Como localizar em qual DLL o programa falhou | Microsoft Docs"
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
  - "vs.debug.dll"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "depurador, Falhas de DLL"
  - "depurando [Visual Studio], Falhas de DLL"
  - "DLLs, ordem de carga de"
  - "erros [depurador], Falhas de DLL"
  - "Caixa de diálogo Lista de Módulos"
  - "Janela Módulos"
ms.assetid: ecf62568-8b65-4a41-b8a4-e962ff2dfb71
caps.latest.revision: 17
caps.handback.revision: 17
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Como localizar em qual DLL o programa falhou
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

> [!NOTE]
>  As caixas de diálogo e os comandos de menu que você vê podem ser diferentes dos descritos na Ajuda, dependendo da sua edição ou das configurações ativas.  Para alterar as configurações, escolha Importar e Exportar Configurações no menu Ferramentas.  Para obter mais informações, consulte [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/pt-br/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
 Se houver falhas no aplicativo durante uma chamada a uma DLL do sistema ou o código de outra pessoa, você precisará descobrir qual DLL estava ativa quando a falha ocorreu.  Se você tiver uma falha em uma DLL fora de seu próprio programa, poderá identificar o local usando a janela **Módulos**.  
  
### Para descobrir onde ocorreu uma falha usando a janela Módulos  
  
1.  Observe o endereço onde a falha ocorreu.  
  
2.  No menu **Depurar**, escolha **Janelas** e clique em **Módulos**.  
  
3.  Na janela **Módulos**, localize a coluna **Endereço**.  Você poderá precisar usar a barra de rolagem para vê\-la.  
  
4.  Clique no botão **Endereço** na parte superior da coluna para classificar as DLLs por endereço.  
  
5.  Examine a lista classificada para localizar a DLL cujo intervalo de endereço contém o local da falha.  
  
6.  Examine as colunas **Nome** e **Caminho** para ver o nome e o caminho da DLL.  
  
## Consulte também  
 [Como depurar DLLs nativas](../Topic/How%20to:%20Debug%20Native%20DLLs.md)   
 [Como usar a janela Módulos](../debugger/how-to-use-the-modules-window.md)