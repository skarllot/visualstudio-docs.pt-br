---
title: "Como usar o Visualizador de &#193;rvore WPF | Microsoft Docs"
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
helpviewer_keywords: 
  - "depuração, WPF"
  - "WPF, depuração"
ms.assetid: 2a1bf1cd-90f9-4d06-9fb4-1bfc925afef3
caps.latest.revision: 18
caps.handback.revision: 18
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Como usar o Visualizador de &#193;rvore WPF
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Você pode usar o visualizador de árvore do WPF para explorar a árvore visual de um objeto do WPF e exibir as propriedades de dependência do WPF para os objetos contidos nessa árvore.  Para obter mais informações sobre árvores visuais, consulte [Árvores no WPF](../Topic/Trees%20in%20WPF.md).  Para obter mais informações sobre propriedades de dependência, consulte [Visão geral de propriedades da dependência](../Topic/Dependency%20Properties%20Overview.md).  
  
 Quando você abrir o visualizador de árvore do WPF, verá dois painéis: a **Árvore Visual** à esquerda e o painel **Propriedades de** *Name***:***Type* à direita.  Selecione qualquer objeto no painel **Árvore Visual** e o painel **Propriedades de** *Name***:***Type* será automaticamente atualizado para mostrar as propriedades desse objeto.  
  
### Para abrir o visualizador de árvore do WPF  
  
1.  Em uma DataTip, em uma janela **Inspeção**, **Autos** ou **Locais**, ao lado do nome do objeto do WPF, clique na seta adjacente ao ícone de lupa.  
  
     Uma lista de visualizadores é exibida.  
  
2.  Clique em **Visualizador de árvore do WPF**.  
  
### Para pesquisar a árvore visual  
  
-   No painel **Árvore Visual**, digite a cadeia de caracteres que deseja procurar na caixa **Procurar**.  
  
     O visualizador de árvore do WPF localiza imediatamente o primeiro objeto na árvore visual que corresponde à cadeia de caracteres digitada.  Digite mais caracteres para localizar uma correspondência mais precisa.  
  
    -   Para ir para a próxima correspondência na árvore visual, clique em **Avançar**.  
  
    -   Para voltar à correspondência anterior, clique em **Ant**.  
  
    -   Para limpar os critérios de pesquisa, clique em **Limpar**.  
  
### Para pesquisar a lista de propriedades  
  
-   No painel **Propriedades de** *Name***:***Type*, na caixa **Filtrar**, digite a cadeia de caracteres que deseja procurar.  
  
     O visualizador de árvore do WPF localiza imediatamente as propriedades que correspondem à cadeia de caracteres digitada; agora, a lista exibe apenas as propriedades que correspondem à cadeia de caracteres digitada.  Digite mais caracteres para localizar uma correspondência mais precisa.  
  
    -   Para limpar os critérios de pesquisa, clique em **Limpar**.  
  
### Para fechar o visualizador  
  
-   Clique no ícone **Fechar** no canto superior direito da caixa de diálogo.  
  
## Consulte também  
 [Como usar um visualizador](../Topic/How%20to:%20Use%20a%20Visualizer.md)   
 [Visualizadores](../debugger/create-custom-visualizers-of-data.md)   
 [Árvores no WPF](../Topic/Trees%20in%20WPF.md)   
 [Visão geral de propriedades da dependência](../Topic/Dependency%20Properties%20Overview.md)