---
title: "Como depurar no modo misto | Microsoft Docs"
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
  - "C++"
helpviewer_keywords: 
  - "depurando [Visual Studio], modo misto"
  - "depurando DLLs"
  - "depuração de modo misto"
ms.assetid: 2859067d-7fcc-46b0-a4df-8c2101500977
caps.latest.revision: 29
caps.handback.revision: 29
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Como depurar no modo misto
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Os procedimentos a seguir descrevem como depurar código gerenciado e código nativo, também conhecido depuração de modo misto.  Há dois cenários para fazer isso, dependendo de a DLL ou o aplicativo serem escritos em código nativo:  
  
-   O aplicativo de chamada que chama a DLL é escrito em código nativo.  Nesse caso, a DLL é gerenciada e os depuradores gerenciados e nativos devem estar habilitados para depurar ambos.  Você pode verificar isso na caixa de diálogo ou na janela **\<Projeto\> Páginas de Propriedades**.  Como você faz isso depende de a depuração ser iniciada do projeto de DLL ou do projeto de aplicativo de chamada.  
  
-   O aplicativo de chamada que chama a DLL é escrito em código gerenciado e sua DLL é escrita em código nativo.  
  
> [!NOTE]
>  As caixas de diálogo e os comandos de menu que você vê podem ser diferentes dos descritos na Ajuda, dependendo da sua edição ou das configurações ativas.  Para alterar as configurações, escolha **Importar e Exportar Configurações** no menu **Ferramentas**.  Para obter mais informações, consulte [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/pt-br/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### Para habilitar a depuração de modo misto  
  
1.  No **Gerenciador de Soluções**, selecione o projeto.  
  
2.  No menu **Exibir**, clique em **Páginas de Propriedades**.  
  
3.  Na caixa de diálogo **Páginas de Propriedades do \<Projeto\>**, expanda o nó **Propriedades de Configuração** e selecione **Depuração**.  
  
4.  Defina **Tipo de Depurador** como **Misto** ou **Automático**.  
  
## Consulte também  
 [Como depurar a partir de um projeto de DLL](../debugger/how-to-debug-from-a-dll-project.md)