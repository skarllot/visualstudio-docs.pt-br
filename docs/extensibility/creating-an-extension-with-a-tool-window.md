---
title: "Criando uma extensão com uma janela de ferramentas | Documentos do Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 585b0a3a-f85b-4f92-81bb-9ca499bb8a89
caps.latest.revision: 5
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 24179997deb1824f91486dfe56d456218cb858a0
ms.lasthandoff: 02/22/2017

---
# <a name="creating-an-extension-with-a-tool-window"></a>Criando uma extensão com uma janela de ferramentas
Neste procedimento, você aprenderá a usar o modelo de projeto do VSIX e **janela da ferramenta personalizada** modelo de item para criar uma extensão com uma janela de ferramenta.  
  
## <a name="prerequisites"></a>Pré-requisitos  
 A partir do Visual Studio 2015, você não instale o SDK do Visual Studio no Centro de download. Ele é fornecido como um recurso opcional na instalação do Visual Studio. Você também pode instalar o SDK do VS mais tarde. Para obter mais informações, consulte [instalar o SDK do Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).  
  
### <a name="creating-a-tool-window"></a>Criando uma janela de ferramenta  
  
1.  Crie um projeto do VSIX chamado **FirstWindow**. Você pode encontrar o modelo de projeto do VSIX no **novo projeto** caixa de diálogo em **Visual c# / extensibilidade**.  
  
2.  Quando o projeto é aberto, adicione um modelo de item da janela de ferramenta chamado **FirstWindow**. No **Solution Explorer**, com o botão direito no nó do projeto e selecione **Adicionar / Novo Item**. No **Adicionar Novo Item** caixa de diálogo, vá para **Visual c# / extensibilidade** e selecione **janela da ferramenta personalizada**. No **nome** campo na parte inferior da janela, altere o nome de arquivo da janela de ferramenta **FirstWindow.cs**.  
  
3.  Compile o projeto e iniciar a depuração.  
  
     A instância experimental do Visual Studio é exibida. Para obter mais informações sobre a instância experimental, consulte [a instância Experimental](../extensibility/the-experimental-instance.md).  
  
4.  Na instância experimental, vá para **exibição / Other Windows**.  
  
     Você deve ver um item de menu **FirstWindow**. Clique nele.  
  
     Você deverá ver uma janela de ferramenta com o título **FirstWindow** e dizer um botão **Click Me!.**
