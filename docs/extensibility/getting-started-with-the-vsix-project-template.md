---
title: "Introdução ao modelo de projeto do VSIX | Documentos do Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Visual Studio SDK, VSIX project template
ms.assetid: 89fac33e-9380-4723-9b45-048a6e16f0ed
caps.latest.revision: 25
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
ms.openlocfilehash: 4769af53c174f4a35387b4f3b7c8e853bb8ff9b5
ms.lasthandoff: 02/22/2017

---
# <a name="getting-started-with-the-vsix-project-template"></a>Introdução ao modelo de projeto do VSIX
Você pode usar o modelo de projeto do VSIX para criar uma extensão ou para uma extensão existente para a implantação do pacote. O modelo de projeto do VSIX tem versões do Visual Basic e Visual c# e é instalado como parte do SDK do Visual Studio.  
  
 O modelo de projeto do VSIX apenas consiste em um arquivo source.extension.vsixmanifest, que contém informações sobre a extensão e os ativos de que enviá-lo.  
  
 Para localizar o modelo de projeto do VSIX, você deve instalar o SDK do Visual Studio. Para obter mais informações, consulte [Visual Studio SDK](../extensibility/visual-studio-sdk.md).  
  
## <a name="deploying-a-custom-project-template-using-the-vsix-project-template"></a>Implantando um modelo de projeto personalizado usando o modelo de projeto do VSIX  
 As etapas a seguir mostram como usar o projeto do VSIX para empacotar um modelo de projeto que você pode compartilhar com outros desenvolvedores ou carregar a Galeria do Visual Studio.  
  
1.  Crie um modelo de projeto.  
  
    1.  Abra o projeto do qual criar um modelo. Esse projeto pode ser de qualquer tipo de projeto.  
  
    2.  Sobre o **arquivo** menu, clique em **exportar modelo**. Conclua as etapas do assistente.  
  
         Um arquivo. zip é criado no %USERPROFILE%\My Documents\Visual Studio * \<versão >*\My Exported Templates\\.  
  
2.  Crie um projeto vazio do VSIX.  
  
     Sobre o **arquivo** menu, clique em **novo** e, em seguida, clique em **projeto**. Selecione **Visual Basic** ou **Visual C#**. Sob o nó selecionado, selecione **extensibilidade**e, em seguida, selecione **projeto VSIX**.  
  
3.  Adicione o arquivo. zip para o projeto. Definir seu **Copy to Output Directory** propriedade `Copy Always`.  
  
4.  No **Solution Explorer**, clique duas vezes o `source.extension.vsixmanifest` arquivo para abri-lo no **Designer de manifesto VSIX**e, em seguida, faça as seguintes alterações:  
  
    -   Definir o **nome do produto** campo **meu modelo de projeto**.  
  
    -   Definir o **ID do produto** campo **MyProjectTemplate - 1**.  
  
    -   Definir o **autor** campo **Fabrikam**.  
  
    -   Definir o **descrição** campo **meu modelo de projeto**.  
  
    -   No **ativos** seção, adicione um **Microsoft.VisualStudio.ProjectTemplate** digite e defina o caminho para o nome do arquivo. zip.  
  
5.  Salve e feche o arquivo source.extension.vsixmanifest.  
  
6.  Compile o projeto.  
  
7.  No diretório de saída, clique duas vezes no arquivo. VSIX.  
  
8.  A **instalador VSIX** caixa de mensagem aparece. Siga as instruções para instalar a extensão.  
  
9. Feche o Visual Studio e, em seguida, abra-o novamente.  
  
10. Selecione **extensões e atualizações** (sobre o **ferramentas** menu) e selecione o **modelos** categoria. Uma das extensões disponíveis deve ser **meu modelo de projeto**.  
  
11. O novo modelo de projeto aparece no **novo projeto** caixa de diálogo no mesmo local que o modelo de projeto original. Por exemplo, se você criou um modelo chamado **VB Console** de um aplicativo de console do Visual Basic, **VB Console** aparece no mesmo painel como o Visual Basic **aplicativo de Console** modelo.  
  
#### <a name="to-specify-the-location-of-the-template-in-the-new-project-dialog-box"></a>Para especificar o local do modelo na caixa de diálogo Novo projeto  
  
1.  Pastas de modelos estão localizadas na *caminho de instalação do Visual Studio*\Common7\IDE\ProjectTemplates e *caminho de instalação do Visual Studio*\Common7\IDE\ItemTemplates diretórios. Os nomes das seções de nível superior na caixa de diálogo Novo projeto não exatamente corresponder aos nomes das pastas do modelo. Onde elas forem diferentes, use o nome da pasta do modelo.  
  
     Altere a extensão de arquivo. VSIX para. zip e, em seguida, abra o arquivo.  
  
2.  Crie uma nova pasta com o mesmo nome que a seção da caixa de diálogo Novo projeto, que o modelo deve aparecer na.  
  
3.  Se o modelo é exibido em uma subseção, crie uma subpasta de mesmo nome.  
  
4.  Mova o arquivo. zip de modelo para a nova pasta.  
  
5.  Altere a extensão. zip para. VSIX.  
  
6.  Abra o manifesto VSIX.  
  
7.  No manifesto VSIX, atualize o **ativos** caminho do modelo para que ele aponte para a raiz da árvore de diretório que contém o arquivo de modelo. Por exemplo, se o modelo estiver em \CSharp\Windows, a referência deve apontar para \CSharp.
