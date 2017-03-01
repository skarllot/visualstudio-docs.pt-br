---
title: "Passo a passo: Vinculação de um tipo de conteúdo para uma extensão de nome de arquivo | Documentos do Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], new - link content type to file name extension
ms.assetid: 21ee64ce-9afe-4b08-94a0-8389cc4dc67c
caps.latest.revision: 24
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
ms.openlocfilehash: 112648fc2b6caa54c8647a5a4e65ff345fbecd42
ms.lasthandoff: 02/22/2017

---
# <a name="walkthrough-linking-a-content-type-to-a-file-name-extension"></a>Passo a passo: Vinculação de um tipo de conteúdo para uma extensão de nome de arquivo
Você pode definir seu próprio tipo de conteúdo e vincular uma extensão de nome de arquivo usando as extensões do editor Managed Extensibility Framework (MEF). Em alguns casos, a extensão de nome de arquivo já foi definida por um serviço de linguagem. No entanto, para usá-lo com o MEF você ainda deve vinculá-lo para um tipo de conteúdo.  
  
## <a name="prerequisites"></a>Pré-requisitos  
 A partir do Visual Studio 2015, você não instale o SDK do Visual Studio no Centro de download. Ele é fornecido como um recurso opcional na instalação do Visual Studio. Você também pode instalar o SDK do VS mais tarde. Para obter mais informações, consulte [instalar o SDK do Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-mef-project"></a>Criando um projeto MEF  
  
1.  Crie um projeto c# VSIX. (No **novo projeto** caixa de diálogo, selecione **Visual c# / extensibilidade**, em seguida, **projeto VSIX**.) Nomeie a solução `ContentTypeTest`.  
  
2.  No **source.extension.vsixmanifest** arquivo, vá para o **ativos** guia e defina o **tipo** campo **Microsoft.VisualStudio.MefComponent**, o **fonte** campo **um projeto na solução atual**e o **projeto** campo para o nome do projeto.  
  
## <a name="defining-the-content-type"></a>Definindo o tipo de conteúdo  
  
1.  Adicione um arquivo de classe e nomeie-o `FileAndContentTypes`.  
  
2.  Adicione referências aos assemblies a seguir:  
  
    1.  System.ComponentModel.Composition  
  
    2.  Microsoft.VisualStudio.Text.Logic  
  
    3.  Microsoft.VisualStudio.CoreUtility  
  
3.  Adicione o seguinte `using` diretivas.  
  
    ```c#  
    using System.ComponentModel.Composition;  
    using Microsoft.VisualStudio.Text.Classification;  
    using Microsoft.VisualStudio.Utilities;  
  
    ```  
  
4.  Declare uma classe estática que contém as definições.  
  
    ```c#  
    internal static class FileAndContentTypeDefinitions  
    {. . .}  
    ```  
  
5.  Nessa classe, exportar um <xref:Microsoft.VisualStudio.Utilities.ContentTypeDefinition>denominado "hid" e declarar sua definição base "texto".</xref:Microsoft.VisualStudio.Utilities.ContentTypeDefinition>  
  
    ```c#  
    internal static class FileAndContentTypeDefinitions  
    {  
        [Export]  
        [Name("hid")]  
        [BaseDefinition("text")]  
        internal static ContentTypeDefinition hidingContentTypeDefinition;  
    }  
    ```  
  
## <a name="linking-a-file-name-extension-to-a-content-type"></a>Vinculando uma extensão de nome de arquivo a um tipo de conteúdo  
  
-   Para mapear esse tipo de conteúdo para uma extensão de nome de arquivo, exportar um <xref:Microsoft.VisualStudio.Utilities.FileExtensionToContentTypeDefinition>que tem a extensão ". HID" e o tipo de conteúdo "hid".</xref:Microsoft.VisualStudio.Utilities.FileExtensionToContentTypeDefinition>  
  
    ```c#  
    internal static class FileAndContentTypeDefinitions  
    {  
         [Export]  
         [Name("hid")]  
         [BaseDefinition("text")]  
        internal static ContentTypeDefinition hidingContentTypeDefinition;  
  
         [Export]  
         [FileExtension(".hid")]  
         [ContentType("hid")]  
        internal static FileExtensionToContentTypeDefinition hiddenFileExtensionDefinition;  
    }  
    ```  
  
## <a name="adding-the-content-type-to-an-editor-export"></a>Adicionando o tipo de conteúdo para uma exportação de Editor  
  
1.  Crie uma extensão de editor. Por exemplo, você pode usar a extensão de glifo de margem descrita em [passo a passo: Criando um glifo de margem](../extensibility/walkthrough-creating-a-margin-glyph.md).  
  
2.  Adicione a classe definida neste procedimento.  
  
3.  Quando você exporta a extensão de classe, adicione uma <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>do tipo "hid" para o proprietário.</xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>  
  
    ```c#  
    [Export]  
    [ContentType("hid")]  
    ```  
  
## <a name="see-also"></a>Consulte também  
 [Serviço de linguagem e pontos de extensão de Editor](../extensibility/language-service-and-editor-extension-points.md)
