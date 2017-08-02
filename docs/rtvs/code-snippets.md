---
title: "Trechos de código com Ferramentas do R para Visual Studio | Microsoft Docs"
ms.custom: 
ms.date: 4/28/2017
ms.prod: visual-studio-dev15
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-r
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 90bf4f87-e276-40cd-bc17-3dfb47ef1870
caps.latest.revision: 1
author: kraigb
ms.author: kraigb
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
ms.sourcegitcommit: 7a873df77756e5a957d327049566c8e0db1f3a8a
ms.openlocfilehash: 033a06b276b8a31e6c69b0eff68ee3f76dda1042
ms.contentlocale: pt-br
ms.lasthandoff: 05/12/2017

---

# <a name="code-snippets"></a>Trechos de código

Os trechos de código no Visual Studio fornecem atalhos para inserir rapidamente os blocos de código de comprimento arbitrário, ajudando a evitar a necessidade de digitar novamente códigos semelhantes. As RTVS (Ferramentas do R para Visual Studio) adicionam dezenas de trechos do R úteis na coleção do Visual Studio.

Para inserir um trecho, digite o nome abreviado do trecho (o IntelliSense é fornecido), em seguida, pressione Tab para inserir.

Alguns exemplos simples:

- digite `=` e, em seguida, pressione Tab e as RTVS o expandirão para o operador de atribuição `<-`.
- digite `>` e, em seguida, pressione Tab e as RTVS o expandirão para o operador de pipe `%>%`.

Trechos de código podem ser muito mais do que apenas preenchimento de caracteres. Por exemplo, eles podem poupar você de precisar se lembrar dos nomes dos parâmetros em chamadas de função complexas, como este trecho para ler um arquivo CSV com a função `read.csv`:

![Animação do uso de um trecho de código para inserir uma chamada de read.csv](~/rtvs/media/code-snippet-expansion.gif)

Nesse caso, à medida que você digita `readc`, o IntelliSense exibe uma lista de conclusão. Selecionar esse preenchimento no menu suspenso e pressionar Tab seleciona `readc` e pressionar Tab novamente expande o trecho. (Por esse motivo, a expansão de trecho de código geralmente é considerada como "digitar o trecho e pressionar a tecla Tab duas vezes"). Na maioria dos casos, a primeira Tab preenche a seleção do IntelliSense e a segunda Tab dispara a expansão.

Para ver todos os trechos disponíveis, abra a caixa de diálogo **Ferramentas > Gerenciador de Trechos de Código...** (Ctrl + K, B) e selecione **R** para **Linguagem**. Expanda os grupos e selecione trechos individuais para ver uma descrição e o texto de atalho:

![Caixa de diálogo de trechos de código para R](~/rtvs/media/code-snippet-dialog.png)

Para criar trechos de código personalizados, siga as instruções em [Instruções passo a passo: criando um trecho de código](../ide/walkthrough-creating-a-code-snippet.md). Por fim, um trecho de código é apenas um arquivo XML. Por exemplo, o seguinte é o trecho para a operação de pipe (atalho `>`)

Observe que um trecho de código é apenas um arquivo XML. Aqui está o trecho de código para o operador de pipe:

```xml
<?xml version="1.0" encoding="utf-8" ?>
<CodeSnippets  xmlns="http://schemas.microsoft.com/VisualStudio/2005/CodeSnippet">
  <CodeSnippet Format="1.0.0">
    <Header>
      <Title>Dplyr pipe</Title>
      <Shortcut>&gt;</Shortcut>
      <Description>Code snippet for '%&gt;%' operator</Description>
      <Author>Microsoft Corporation</Author>
      <SnippetTypes>
        <SnippetType>Expansion</SnippetType>
       </SnippetTypes>
    </Header>
    <Snippet>
      <Code Language="R">
        <![CDATA[ %>% $end$]]>
      </Code>
    </Snippet>
  </CodeSnippet>
</CodeSnippets>
```

Os arquivos XML de todos os trechos de código são instalados com as RTVS; o campo **Local** no **Gerenciador de trechos de código** fornece o caminho. Você também pode encontrá-los no código-fonte das RTVS no GitHub em [src/Package/Impl/Snippets](https://github.com/Microsoft/RTVS/tree/master/src/Package/Impl/Snippets).

