---
title: "How to: Use XML Snippets | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 3a27375b-81cc-48f6-a884-e1cb8c4f78f5
caps.latest.revision: 2
caps.handback.revision: 2
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# How to: Use XML Snippets
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Você pode chamar trechos XML usando os dois seguintes comandos no menu de atalho do editor XML.  O comando de **Inserir Trecho** inserir o trecho de código XML a posição do cursor.  O comando de **Circundar com** envolve o trecho de código XML ao redor do texto selecionado.  Cada pequena notícias XML designou tipos de notícias pequena.  Os tipos de trecho determinar se o trecho está disponível com o comando de **Inserir Trecho** , o comando de **Circundar com** , ou ambos.  
  
 Depois que o trecho XML foi adicionado ao editor, todos os campos editáveis no trecho estão realçados em amarelo, e o cursor está localizado no primeiro campo editável.  
  
## Inserir Trecho  
 Os procedimentos a seguir descrevem como acessar o comando de **Inserir Trecho** .  
  
> [!NOTE]
>  O comando de **Inserir Trecho** também está disponível com o atalho de teclado \(CTRL\+K, então CTRL\+X\).  
  
#### Para inserir trechos do menu de atalho  
  
1.  Posicionar o cursor onde você deseja inserir o trecho XML.  
  
2.  Clique com o botão direito do mouse e selecione **Inserir Trecho**.  
  
     Uma lista de trechos disponíveis XML é exibida.  
  
3.  Selecione um trecho de lista usando o mouse, ou digitando o nome do trecho e pressionando TAB ou ENTER.  
  
#### Para inserir trechos usando o menu do IntelliSense  
  
1.  Posicionar o cursor onde você deseja inserir o trecho XML.  
  
2.  No menu de **Editar** , aponte para **IntelliSense**, e selecione **Inserir Trecho**.  
  
     Uma lista de trechos disponíveis XML é exibida.  
  
3.  Selecione um trecho de lista usando o mouse ou digitando o nome do trecho e pressionando TAB ou ENTRE\-O.  
  
#### Para inserir trechos com o IntelliSense concluir a lista de palavras  
  
1.  Posicionar o cursor onde você deseja inserir o trecho XML.  
  
2.  Comece a digitar o trecho XML que você deseja adicionar ao seu arquivo.  Se o preenchimento automático é ativada, a lista de palavras completo do IntelliSense é exibida.  Se não for exibido, para pressionar CTRL\+BARRA DE ESPAÇOS para ativar\-lo.  
  
3.  Selecione o trecho XML da lista de palavras completo.  
  
4.  Pressione a tecla TAB, TAB para invocar o trecho XML.  
  
> [!NOTE]
>  Pode haver casos quando o trecho XML não é chamado.  Por exemplo, se você tentar inserir um elemento de `xs:complexType` dentro de um nó de `xs:element` , o editor não gerencia um trecho XML.  Quando um elemento de `xs:complexType` é usado dentro de um nó de `xs:element` , não houver nenhum atributo ou subelements necessário, o editor não tem nenhum dados para inserir.  
  
#### Para inserir trechos usando o nome do atalho  
  
1.  Posicionar o cursor onde você deseja inserir o trecho XML.  
  
2.  Tipo `<` no painel do editor.  
  
3.  Pressione ESC para fechar a lista de palavras completo do IntelliSense.  
  
4.  Digite o nome do atalho de trecho de código, e pressione a tecla TAB para invocar o trecho XML.  
  
## Envolver com  
 Os procedimentos a seguir descrevem como acessar o comando de **Circundar com** .  
  
> [!NOTE]
>  O comando de **Circundar com** também está disponível com o atalho de teclado \(CTRL\+K, então CTRL\+S\).  
  
#### Para usar a bordadura com o menu de contexto  
  
1.  Selecione o texto para colocar no editor XML.  
  
2.  Clique com o botão direito do mouse e selecione **Circundar com**.  
  
     Uma lista de bordadura disponíveis com trechos XML é exibida.  
  
3.  Selecione um trecho de lista usando o mouse, ou digitando o nome do trecho e pressionando TAB ou ENTER.  
  
#### Para usar a bordadura com um menu do Intellisense  
  
1.  Selecione o texto para colocar no editor XML.  
  
2.  No menu de **Editar** , aponte para **IntelliSense**, e selecione **Circundar com**.  
  
     Uma lista de bordadura disponíveis com trechos XML é exibida.  
  
3.  Selecione um trecho de lista usando o mouse, ou digitando o nome do trecho e pressionando TAB ou ENTER.  
  
## Usando trechos de código XML  
 Uma vez que você escolher um trecho XML, o texto de trecho de código é inserido automaticamente a posição do cursor.  Todos os campos editáveis no trecho são realçadas, e o primeiro campo editável é automaticamente selecionado.  O campo selecionado é convertido.  
  
 Quando um campo é selecionado, você pode digitar um novo valor para o campo.  Pressione a tecla TAB verificará através dos campos editáveis de trecho; pressionando ciclos de SHIFT\+TAB através delass em ordem inversa.  Clicando em um campo colocar o cursor no campo, e clique duas vezes em um campo selecioná\-lo.  Quando um campo é realçado, uma dica de ferramenta pode ser exibido, oferecendo uma descrição do campo.  
  
 Somente a primeira instância de um campo dado é editável.  Quando esse campo é realçado, as outras instâncias do campo são descritas.  Quando você altera o valor de um campo editável, o campo ele alterado everywhere é usado no trecho.  
  
 Pressionando ENTER ou o ESC cancela a edição de campo e retorna o editor a normal.  
  
 As cores padrão para campos editáveis de trecho de código podem ser alteradas alterando a configuração do campo de trecho de código no painel de **Fontes e Cores** da caixa de diálogo **Opção**s.  Para obter mais informações, consulte [Como alterar fontes e cores usadas no Editor](../Topic/How%20to:%20Change%20Fonts%20and%20Colors%20in%20the%20Editor.md).  
  
## Consulte também  
 [XML Snippets](../xml-tools/xml-snippets.md)   
 [How to: Generate an XML Snippet From an XML Schema](../Topic/How%20to:%20Generate%20an%20XML%20Snippet%20From%20an%20XML%20Schema.md)   
 [How to: Create XML Snippets](../xml-tools/how-to-create-xml-snippets.md)