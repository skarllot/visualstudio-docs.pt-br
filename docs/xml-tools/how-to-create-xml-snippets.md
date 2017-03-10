---
title: "How to: Create XML Snippets | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d8556dd7-1382-4af7-ba80-3e873c9416be
caps.latest.revision: 2
caps.handback.revision: 2
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# How to: Create XML Snippets
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

O editor XML pode ser usado para criar novos trechos XML.  O editor inclui um trecho XML, chamado “pequena notícias”, que é uma pequena notícias de texto constante para criar novos trechos XML.  
  
## Para criar um novo trecho XML  
 Para criar um novo trecho de código XML crie um novo arquivo XML e use o recurso de **Inserir Trecho** .  
  
1.  No menu de **Arquivo** , clique **Novo** e clique em **Arquivo**.  
  
2.  Clique **Arquivo XML** e clique em **Abrir**.  
  
3.  Clique com o botão direito do mouse no painel de editor e selecione **Inserir Trecho**.  
  
4.  **Trecho** A partir da lista e pressione ENTER.  
  
5.  Faça as alterações para o novo trecho.  
  
6.  No menu **Salvar XMLFile.xml**select de **Arquivo** .  
  
     A caixa de diálogo **Salvar Arquivo Como** é exibida.  
  
7.  Digite o nome para o novo trecho e selecione **Arquivos de trecho** de janela suspensa de **Salvar como tipo** .  
  
8.  Use a lista suspensa de **Salvar em** para alterar o local do arquivo a meus documentos \\ Visual Studio 2005 \\ trechos de código XML \\ \\ pasta meus trechos XML e para pressione **Salvar**.  
  
## Descrição de trecho  
 Esta seção descreve alguns dos elementos\-chave no trecho de texto constante.  Para obter mais informações sobre os elementos de esquema usados por trechos XML, consulte [Referência de esquema dos trechos de código](../ide/code-snippets-schema-reference.md).  
  
### Elemento SnippetType  
 Suporte do editor dois tipos de trecho:  
  
```  
<SnippetTypes>  
  <SnippetType>SurroundsWith</SnippetType>  
  <SnippetType>Expansion</SnippetType>  
</SnippetTypes>  
```  
  
 O tipo de `Expansion` determina se o trecho aparece quando você chama o comando de **Inserir Trecho** .  O tipo de `SurroundsWith` determina se o trecho aparece quando você chama o comando de **Com bordadura** .  
  
### Elemento Code  
 O elemento de `Code` define o texto XML que será inserido quando o trecho é chamado.  
  
> [!NOTE]
>  O texto de trecho XML deve ser incluído em uma seção de `<![CDATA[...]]>` .  
  
 O seguinte é o elemento de `Code` que é criado pelo trecho de texto constante.  
  
```  
<Code Language="XML">  
  <![CDATA[<test>  
  <name>$name$</name>  
  $selected$ $end$</test>]]>  
</Code>  
```  
  
 O elemento de `Code` inclui três variáveis.  
  
-   $name$ variável é definido pelo usuário.  Cria um elemento de `name` , que tem um valor editável que usa padrão “para nomear”.  As variáveis definidas pelo usuário são definidos usando o elemento de `Literal` .  
  
-   $selected$ é uma variável predefinido.  Representa o texto que foi selecionado no editor XML antes de chamar o trecho.  O posicionamento dessa variável determina onde o texto selecionado aparece no trecho de código que circunda a seleção.  
  
-   $end$ é uma variável predefinido.  Quando o usuário pressiona ENTER para concluir editar os campos de trecho de código, essa variável determina onde ao acento circunflexo \(^\) é movido.  
  
 O elemento acima de `Code` insira o seguinte texto XML:  
  
```  
<test>  
  <name>name</name>  
</test>  
```  
  
 O valor do elemento de nome é marcado como uma região editável.  
  
### Elemento Literal  
 O elemento de `Literal` é usado para identificar o texto de substituição que pode ser personalizada depois que é inserido no arquivo.  Por exemplo, cadeias de caracteres literais, os valores numéricos, e alguns nomes de variável podem ser declarados como literais.  Você pode definir qualquer número do trecho em literais XML e você pode referir\-lhes várias vezes dentro de trecho.  O código a seguir é um exemplo de um elemento de `Literal` que define um variável de $name$ cujo valor padrão é “nome”.  
  
```  
<Literal>  
  <ID>name</ID>  
  <Default>name</Default>  
</Literal  
```  
  
 Literais também podem se referir funções.  O editor XML inclui uma função chamada **LookupPrefix**.  A função de pesquisa **LookupPrefix** URI fornecido de namespace de local no documento XML que este trecho é chamado de e retorna o prefixo do namespace que é definido para esse namespace, se houver, e inclui o separador dois\-pontos \(:\) naquele nome.  O código a seguir é um exemplo de um elemento de `Literal` que usa a função de **LookupPrefix** .  
  
```  
<Literal Editable="false">  
   <ID>prefix</ID>  
   <Function>LookupPrefix("namespaceURI")</Function>  
</Literal>  
```  
  
 A variável de $prefix$ pode então ser usado em qualquer lugar no seu trecho XML.  
  
## Consulte também  
 [XML Snippets](../xml-tools/xml-snippets.md)   
 [How to: Use XML Snippets](../xml-tools/how-to-use-xml-snippets.md)   
 [How to: Generate an XML Snippet From an XML Schema](../Topic/How%20to:%20Generate%20an%20XML%20Snippet%20From%20an%20XML%20Schema.md)