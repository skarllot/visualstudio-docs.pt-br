---
title: "Criando uma extensão com um modelo de Item Editor | Documentos do Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], new - extensions
ms.assetid: fa3b993b-ab95-47fa-a38b-b788f3a5b2d8
caps.latest.revision: 16
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
ms.openlocfilehash: e3cf0b37f3271139fa38f098f56c7751166f245f
ms.lasthandoff: 02/22/2017

---
# <a name="creating-an-extension-with-an-editor-item-template"></a>Criando uma extensão com um modelo de Item Editor
Você pode usar modelos de item incluídos no SDK do Visual Studio para criar extensões de editor básico que adicionar classificadores ornamentos e margens no Editor. Os modelos de item editor estão disponíveis para projetos do Visual c# ou Visual Basic VSIX.  
  
## <a name="prerequisites"></a>Pré-requisitos  
 A partir do Visual Studio 2015, você não instale o SDK do Visual Studio no Centro de download. Ele é fornecido como um recurso opcional na instalação do Visual Studio. Você também pode instalar o SDK do VS mais tarde. Para obter mais informações, consulte [instalar o SDK do Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-classifier-extension"></a>Criando uma extensão de classificação  
 O modelo de item Editor classificador cria um classificador de editor que colore o texto apropriado (nesse caso, tudo) em qualquer arquivo de texto.  
  
1.  No **novo projeto** caixa de diálogo caixa, expanda **Visual C#** ou **Visual Basic** e, em seguida, clique em **extensibilidade**. No **modelos** , selecione **projeto VSIX**. Na caixa **Nome**, digite `TestClassifier`. Clique em **OK**.  
  
2.  No **Solution Explorer**, com o botão direito no nó do projeto e selecione **Adicionar / Novo Item**. Vá para o Visual c# **extensibilidade** nó e selecione **Editor classificador**. Deixe o nome de arquivo padrão (EditorClassifier1.cs).  
  
3.  Há três arquivos de código, da seguinte maneira:  
  
    -   EditorClassifier1.cs contém a `EditorClassifier1` classe.  
  
    -   EditorClassifier1ClassificationDefinition.cs contém a `OEditorClassifier1ClassificationDefinition` classe.  
  
    -   EditorClassifier1Format.cs contém a `EditorClassifier1Format` classe.  
  
    -   EditorClassifier1Provider.cs contém a `EditorClassifier1Provider` classe.  
  
4.  Compile o projeto e iniciar a depuração. A instância experimental do Visual Studio é exibida.  
  
     Se você abrir um arquivo de texto, todo o texto está sublinhado em um plano de fundo violeta.  
  
## <a name="creating-a-text-relative-adornment-extension"></a>Criando uma extensão de adorno relativos a texto  
 O modelo de adorno de texto do Editor cria um adorno de texto relativo que decora todas as ocorrências do caractere de texto 'a' usando uma caixa com um contorno vermelho e um plano de fundo azul. Ele é relativo ao texto porque a caixa sempre sobreposições 'a' caracteres, mesmo quando eles são movidos ou reformatados.  
  
1.  No **novo projeto** caixa de diálogo caixa, expanda **Visual C#** ou **Visual Basic** e, em seguida, clique em **extensibilidade**. No **modelos** , selecione **projeto VSIX**. Na caixa **Nome**, digite `TestAdornment`. Clique em **OK**.  
  
2.  No **Solution Explorer**, com o botão direito no nó do projeto e selecione **Adicionar / Novo Item**. Vá para o Visual c# **extensibilidade** nó e selecione **adorno do Editor de texto**. Deixe o nome de arquivo padrão (TextAdornment1.cs/vb).  
  
3.  Existem dois arquivos de código, da seguinte maneira:  
  
    -   TextAdornment1.cs contém a `TextAdornment1` classe.  
  
    -   extAdornment1TextViewCreationListener.cs contém a `TextAdornment1TextViewCreationListener` classe.  
  
4.  Compile o projeto e iniciar a depuração. A instância experimental aparece. Se você abrir um arquivo de texto, as 'a' caracteres no texto são realçados em vermelho em um plano de fundo azul.  
  
## <a name="creating-a-viewport-relative-adornment-extension"></a>Criando uma extensão de adorno relativo do visor  
 O modelo de adorno de visor do Editor cria um adorno de visor relativo que adiciona uma caixa violeta com um contorno vermelho no canto superior direito do visor.  
  
> [!NOTE]
>  O *visor* é a área de exibição de texto que está sendo exibida.  
  
#### <a name="to-create-a-viewport-adornment-extension-by-using-the-editor-viewport-adornment-template"></a>Criar uma extensão de adorno do visor, usando o modelo de adorno de visor do Editor  
  
1.  No **novo projeto** caixa de diálogo caixa, expanda **Visual C#** ou **Visual Basic** e, em seguida, clique em **extensibilidade**. No **modelos** , selecione **projeto VSIX**. Na caixa **Nome**, digite `ViewportAdornment`. Clique em **OK**.  
  
2.  No **Solution Explorer**, com o botão direito no nó do projeto e selecione **Adicionar / Novo Item**. Vá para o Visual c# **extensibilidade** nó e selecione **Editor visor adorno**. Deixe o nome de arquivo padrão (ViewportAdornment1.cs/vb).  
  
3.  Existem dois arquivos de código, da seguinte maneira:  
  
    -   ViewportAdornment1.cs contém a `ViewportAdornment1` classe.  
  
    -   ViewportAdornment1TextViewCreationListener.cs contém a `ViewportAdornment1TextViewCreationListener` classe  
  
4.  Compile o projeto e iniciar a depuração. A instância experimental aparece. Se você criar um novo arquivo de texto, uma caixa violeta com um contorno vermelho é exibida no canto superior direito do visor.  
  
## <a name="creating-a-margin-extension"></a>Criando uma extensão de margem  
 O modelo de margem do Editor cria uma margem verde que aparece junto com as palavras "Hello world!" abaixo da barra de rolagem horizontal.  
  
#### <a name="to-create-a-margin-extension-by-using-the-editor-margin-template"></a>Criar uma extensão de margem usando o modelo de margem do Editor  
  
1.  No **novo projeto** caixa de diálogo caixa, expanda **Visual C#** ou **Visual Basic** e, em seguida, clique em **extensibilidade**. No **modelos** , selecione **projeto VSIX**. Na caixa **Nome**, digite `MarginExtension`. Clique em **OK**.  
  
2.  No **Solution Explorer**, com o botão direito no nó do projeto e selecione **Adicionar / Novo Item**. Vá para o Visual c# **extensibilidade** nó e selecione **Editor visor adorno**. Deixe o nome de arquivo padrão (EditorMargin1.cs/vb).  
  
3.  Existem dois arquivos de código, da seguinte maneira:  
  
    -   EditorMargin1.cs contém a `EditorMargin1` classe.  
  
    -   EditorMargin1Factory.cs contém a `EditorMargin1Factory` classe.  
  
4.  Compilar esse projeto e iniciar a depuração. A instância experimental aparece. Se você abrir um arquivo de texto, uma margem verde com as palavras "Hello EditorMargin1" é exibida abaixo da barra de rolagem horizontal.  
  
## <a name="see-also"></a>Consulte também  
 [Serviço de linguagem e pontos de extensão de Editor](../extensibility/language-service-and-editor-extension-points.md)
