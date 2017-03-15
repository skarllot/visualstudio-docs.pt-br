---
title: "Walkthrough: Debug an XSLT Style Sheet | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 3db9fa5a-f619-4cb6-86e7-64b364e58e5d
caps.latest.revision: 2
caps.handback.revision: 2
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Walkthrough: Debug an XSLT Style Sheet
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

As etapas nessa explicação passo a passo demonstra como usar o depurador XSLT.  As etapas incluem variáveis de exibição, pontos de interrupção, e percorrendo o código.  A folha de estilos localiza os livros que custam abaixo do preço médio de livro.  
  
### Para preparar\-se para esse passo a passo  
  
1.  Feche soluções abertas.  
  
2.  Copie os dois arquivos de exemplo para seu computador local.  
  
## Iniciar a depuração  
  
#### Para iniciar a depuração  
  
1.  No menu de **Arquivo** , aponte para **Abrir**, e clique **Arquivo**.  
  
2.  Localize o arquivo de belowAvg.xsl e clique **Abrir**.  
  
     A folha de estilos é aberta no editor XML.  
  
3.  Clique no botão procurar \(**...**\) no campo **Entrada** da janela de propriedades do documento.  
  
4.  Localize o arquivo de books.xml e clique **Abrir**.  
  
     Isso define o arquivo de documento de origem que é usado para a transformação XSLT.  
  
5.  Clique com o botão direito do mouse na tag de início de `xsl:if` , aponte para **Ponto de Interrupção**, clique **Inserir Ponto de Interrupção**.  
  
6.  Clique no botão de **Depurar XSL** na barra de ferramentas do editor XML.  
  
 Isso inicia o processo de depuração e abre várias o windows que são usadas pelo depurador.  
  
 Há duas janelas que exibem o documento de entrada e estilos sobrepor.  O depurador usar essas janelas para mostrar o estado atual de execução.  O depurador é posicionado no elemento de `xsl:if` de folha de estilos e no primeiro nó de livro no arquivo de books.xml.  
  
 A janela locais exibe todas as variáveis locais e seus valores atuais.  Isso inclui variáveis definidos na folha de estilos e também variáveis que o depurador usa para controlar os nós que estão atualmente no contexto.  
  
 A janela de **Saída XSL** exibe a saída de transformação XSL.  Essa janela é separada da janela de **Saída do Visual Studio** .  
  
## Observação de janela  
  
#### Para usar a janela de observação  
  
1.  No menu de **Depurar** , aponte para **Janelas**, aponte para **Inspeção**, e clique **Inspeção 1**.  
  
     Isso torna a observação 1 janela visível.  
  
2.  O tipo `$bookAverage` no campo de **Nome** e pressione ENTER.  
  
     O valor da variável de `$bookAverage` é exibido na janela.  
  
3.  O tipo `self::node()` no campo de **Nome** e pressione ENTER.  
  
     `self::node()` é uma expressão XPath que avalia ao nó atual de contexto.  O valor da expressão XPath de `self::node()` é o primeiro nó de livro.  Isso é alterado como nós progredimos com a transformação.  
  
4.  Expanda o nó de `self::node()` em seguida, expanda o nó de `price` .  
  
     Isso permite que você possa ver o valor do custo do livro e você pode facilmente compará\-lo ao valor de `$bookAverage` .  Porque o custo de livro abaixo de média, a condição de `xsl:if` deve obterá êxito.  
  
## Avançar no código  
 O depurador permite que você execute a linha de código por vez.  
  
#### Para depurar código  
  
1.  Pressione **F5** a continuar.  
  
     Porque o primeiro nó de livro tiver satisfeito a condição de `xsl:if` , o nó de livro é adicionada à janela de saída XSL.  O depurador continuará a ser executado até que está localizado novamente no elemento de `xsl:if` na folha de estilos.  O depurador é posicionado agora no segundo nó de livro no arquivo de books.xml.  
  
     Na janela Watch1 o valor de `self::node()` alterações no segundo nó de livro.  Examinando o valor do elemento de preço, você pode determinar que o preço está acima da média, então a condição de `xsl:if` deve falhar.  
  
2.  Pressione **F5** a continuar.  
  
     Porque o segundo nó de livro não está de acordo com a condição de `xsl:if` , o nó de livro não é adicionada à janela de saída XSL.  O depurador continuará a ser executado até que está localizado novamente no elemento de `xsl:if` na folha de estilos.  O depurador é posicionado agora no terceiro nó de `book` no arquivo de books.xml.  
  
     Na janela Watch1 o valor de `self::node()` alterações para o terceiro nó de livro.  Examinando o valor do elemento de `price` , você pode determinar que o preço abaixo de média, então a condição de `xsl:if` deve obterá êxito.  
  
3.  Pressione **F5** a continuar.  
  
     Porque a condição de `xsl:if` foi encontrada, o terceiro livro é adicionada à janela de saída XSL.  Todos os livros no documento XML foram processados e paradas do depurador.  
  
## Arquivos de exemplo  
 Os seguintes dois arquivos são usados por passo a passo.  
  
### belowAvg.xsl  
  
```  
<?xml version='1.0'?>  
<xsl:stylesheet version="1.0"  
      xmlns:xsl="http://www.w3.org/1999/XSL/Transform">  
  <xsl:output method="xml" encoding="utf-8"/>  
  <xsl:template match="/">  
    <xsl:variable name="bookCount" select="count(/bookstore/book)"/>  
    <xsl:variable name="bookTotal" select="sum(/bookstore/book/price)"/>  
    <xsl:variable name="bookAverage" select="$bookTotal div $bookCount"/>  
    <books>  
      <!--Books That Cost Below Average-->  
      <xsl:for-each select="/bookstore/book">  
        <xsl:if test="price < $bookAverage">  
          <xsl:copy-of select="."/>  
        </xsl:if>  
      </xsl:for-each>  
    </books>  
  </xsl:template>  
</xsl:stylesheet>  
```  
  
### books.xml  
  
```  
<?xml version='1.0'?>  
<!-- This file represents a fragment of a book store inventory database -->  
<bookstore>  
  <book genre="autobiography" publicationdate="1981" ISBN="1-861003-11-0">  
    <title>The Autobiography of Benjamin Franklin</title>  
    <author>  
      <first-name>Benjamin</first-name>  
      <last-name>Franklin</last-name>  
    </author>  
    <price>8.99</price>  
  </book>  
  <book genre="novel" publicationdate="1967" ISBN="0-201-63361-2">  
    <title>The Confidence Man</title>  
    <author>  
      <first-name>Herman</first-name>  
      <last-name>Melville</last-name>  
    </author>  
    <price>11.99</price>  
  </book>  
  <book genre="philosophy" publicationdate="1991" ISBN="1-861001-57-6">  
    <title>The Gorgias</title>  
    <author>  
      <name>Plato</name>  
    </author>  
    <price>9.99</price>  
  </book>  
</bookstore>  
```  
  
## Consulte também  
 [Debugging XSLT](../xml-tools/debugging-xslt.md)