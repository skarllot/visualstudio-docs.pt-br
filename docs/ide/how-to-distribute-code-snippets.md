---
title: "Como distribuir trechos de código | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- code snippets, distributing
ms.assetid: 5f717abd-e167-47ae-818c-6b0bae100ceb
caps.latest.revision: 16
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
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
ms.translationtype: Human Translation
ms.sourcegitcommit: 47057e9611b824c17077b9127f8d2f8b192d6eb8
ms.openlocfilehash: 8700d4814494aafb6558f354d5904ed647c1f5a7
ms.contentlocale: pt-br
ms.lasthandoff: 05/13/2017

---
# <a name="how-to-distribute-code-snippets"></a>Como distribuir trechos de código
Você pode simplesmente fornecer seus trechos de código a seus amigos e fazer com que instalem os trechos em seus próprios computadores usando o Gerenciador de Trechos de Código. No entanto, se você tiver vários trechos para distribuir ou gostaria de distribuí-los mais amplamente, inclua seu arquivo de trecho em uma extensão do Visual Studio, que usuários do Visual Studio podem instalar.  

 Você deve instalar o SDK do Visual Studio para criar extensões do Visual Studio. Localize a versão do VSSDK que corresponde à sua instalação do Visual Studio em [Downloads do Visual Studio](https://www.visualstudio.com/downloads/).  

## <a name="setting-up-the-extension"></a>Configurando a extensão  
 Neste procedimento, usaremos o mesmo trecho de código Hello World criado no [Passo a passo: criando um trecho de código](../ide/walkthrough-creating-a-code-snippet.md). Forneceremos o texto .snippet, portanto, você não precisa voltar e criar um.  

1.  Crie um novo projeto do VSIX chamado **TestSnippet**. (**Arquivo/Novo/Projeto/Visual C# (ou Visual Basic/Extensibilidade**)  

2.  No projeto **TestSnippet**, adicione um novo arquivo XML e chame-o de **VBCodeSnippet.snippet**. Substitua o conteúdo pelo seguinte:  

    ```xml  
    <?xml version="1.0" encoding="utf-8"?>  
    <CodeSnippets  
        xmlns="http://schemas.microsoft.com/VisualStudio/2005/CodeSnippet">  
      <CodeSnippet Format="1.0.0">  
        <Header>  
          <Title>Hello World VB</Title>  
          <Shortcut>HelloWorld</Shortcut>  
          <Description>Inserts code</Description>  
          <Author>MSIT</Author>  
          <SnippetTypes>  
            <SnippetType>Expansion</SnippetType>  
            <SnippetType>SurroundsWith</SnippetType>  
          </SnippetTypes>  
        </Header>  
        <Snippet>  
          <Code Language="VB">  
            <![CDATA[Console.WriteLine("Hello, World!")]]>  
          </Code>  
        </Snippet>  
      </CodeSnippet>  
    </CodeSnippets>  
    ```  

#### <a name="setting-up-the-directory-structure"></a>Configurando a estrutura de diretório  

1.  No Gerenciador de Soluções, selecione o nó do projeto e adicione uma pasta que tenha o nome que você deseja que o trecho tenha no Gerenciador de Trechos de Código. Neste caso, deve ser **HelloWorldVB**.  

2.  Mova o arquivo .snippet para a pasta **HelloWorldVB**.  

3.  Selecione o arquivo .snippet no Gerenciador de Soluções e, na janela **Propriedades**, garanta que **Ação de Build** esteja definida como **Conteúdo**; **Copiar para Diretório de Saída** esteja definido como **Copiar Sempre**; e **Incluir em VSIX** esteja definido como **true**.  

#### <a name="adding-the-pkgdef-file"></a>Adicionando o arquivo .pkgdef  

1.  Adicione um arquivo de texto à pasta **HelloWorldVB** e dê a ele o nome de **HelloWorldVB.pkgdef**. Esse arquivo é usado para adicionar determinadas chaves ao Registro. Nesse caso, ele adiciona uma nova chave a  

     **HKCU\Software\Microsoft\VisualStudio\14.0\Languages\CodeExpansions\Basic**.  

2.  Adicione as seguintes linhas ao arquivo.  

    ```  
    // Visual Basic   
    [$RootKey$\Languages\CodeExpansions\Basic\Paths]   
    "HelloWorldVB"="$PackageFolder$"  
    ```  

     Se você examinar essa chave, poderá ver como especificar diferentes idiomas.  

3.  Selecione o arquivo .pkgdef no Gerenciador de Soluções e, na janela **Propriedades**, garanta que **Ação de Build** esteja definida como **Conteúdo**; **Copiar para Diretório de Saída** esteja definido como **Copiar Sempre**; e **Incluir em VSIX** esteja definido como **true**.  

4.  Adicione o arquivo .pkgdef como um ativo no manifesto VSIX. No arquivo source.extension.vsixmanifest, vá para a guia **Ativos** e clique em **Novo**.  

5.  Na caixa de diálogo **Adicionar Novo Ativo**, defina o **Tipo** como **Microsoft.VisualStudio.VsPackage**; o **Tipo** como **Arquivo no filesystem**; e o **Caminho** como **HelloWorldVB.pkgdef** (que deve aparecer na lista suspensa).  

### <a name="testing-the-snippet"></a>Testando o trecho  

1.  Agora você pode verificar se o trecho de código funciona na instância experimental do Visual Studio. A instância experimental é uma segunda cópia do Visual Studio, que é separada daquela que você usa para escrever código. Ela permite que você trabalhe em uma extensão sem afetar seu ambiente de desenvolvimento.  

2.  Compile o projeto e comece a depuração. Uma segunda instância do Visual Studio deve ser exibida.  

3.  Na instância experimental, vá para **Ferramentas /Gerenciador de Trechos de Código** e defina a **Linguagem** como **Básica**. Você deve ver HelloWorldVB como uma das pastas e ser capaz de expandir a pasta para ver o trecho HelloWorldVB.  

4.  Teste o trecho. Na instância experimental, abra um projeto do Visual Basic e abra um dos arquivos de código. Coloque o cursor em algum lugar no código, clique com o botão direito do mouse e, no menu de contexto, selecione **Inserir Trecho**.  

5.  Você deve ver HelloWorldVB como uma das pastas. Clique duas vezes nesse item. Você deve ver um pop-up **Inserir Snippet: HellowWorldVB >** que tem uma lista suspensa **HelloWorldVB**. Clique na lista suspensa HelloWorldVB. Você deve ver a seguinte linha adicionada ao arquivo:  

    ```vb  
    Console.WriteLine("Hello, World!")  
    ```  

## <a name="see-also"></a>Consulte também  
 [Trechos de código](../ide/code-snippets.md)

